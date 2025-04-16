# registo-de-notas
Informática - 2º Ano_EDAI 
________________________________________________________________________________________________________________________


#armazena os dados dos alunos

dados = {}

# Outros dados uteis
melhor_aluno = ""
top_media = 0
alunos_com_nota_ruim = 0

qtd = int(input("Quantos alunos vao ser registados? "))

for idx in range(qtd):
    print(f"\n== Aluno {idx + 1} ==")
    nome_aluno = input("Nome: ")
    total_disciplinas = int(input(f"disciplinas do {nome_aluno}: "))

    registo_notas = []
    nota_fraca = False

    for nota_idx in range(total_disciplinas):
        valor = float(input(f"Nota {nota_idx + 1}: "))
        registo_notas.append(valor)
        if valor < 5:
            nota_fraca = True

    dados[nome_aluno] = registo_notas

    media_atual = sum(registo_notas) / len(registo_notas)

    if media_atual > top_media:
        top_media = media_atual
        melhor_aluno = nome_aluno

    if nota_fraca:
        alunos_com_nota_ruim += 1

#saida dos dados

print("\n=== REGISTOS ===")
for aluno, lista_notas in dados.items():
    print(f"{aluno}: {lista_notas}")

# Extras
print("\n=== REGISTO FINAL ===")
for aluno, lista_notas in dados.items():
    media_final = sum(lista_notas) / len(lista_notas)
    resultado = "✅ APROVADO" if media_final >= 10 else "❌ NÃO PASSOU"
    print(f"{aluno} - Media: {media_final:.1f} ({resultado})")

print(f"\nAlunos com nota inferior a 5: {alunos_com_nota_ruim}")
print(f"Aluno com melhor media: {melhor_aluno} ({top_media:.2f})")
