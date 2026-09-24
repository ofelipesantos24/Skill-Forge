# 🔧 Skill Forge

Gerador de `SKILL.md` para skills do Claude Code. Preencha um formulário e receba o arquivo pronto, com pré-visualização em tempo real, no padrão usado por projetos como [Superpowers](https://github.com/obra/superpowers) e Claude Code Templates.

Site 100% estático: sem backend, sem build, sem dependências. Tudo roda no navegador e nada do que você digita é enviado a servidores.

## O que é um SKILL.md

É um arquivo de metadados e instruções que ensina um agente (como o Claude Code) a reconhecer quando uma tarefa se encaixa em uma skill específica e como executá-la. Geralmente fica em uma pasta própria:

```
minha-skill/
  SKILL.md
  scripts/
  examples/
```

## Funcionalidades

- Formulário com nome (slug), título, descrição/gatilhos, categoria, licença, passos, restrições e autor
- Pré-visualização ao vivo do `SKILL.md`, atualizada a cada digitação
- Geração automática do slug (minúsculas, sem espaços, com hífen)
- Botão **Copiar** para a área de transferência
- Tema claro/escuro automático via `prefers-color-scheme`
- Layout responsivo (formulário e preview empilham em telas estreitas)
- Documentação embutida com boas práticas para escrever descrições que disparam a skill corretamente

## Estrutura do projeto

```
skill-forge/
├── index.html          # Página inicial
├── gerador.html        # Gerador de SKILL.md
├── documentacao.html   # Guia e boas práticas
└── README.md
```

| Arquivo | Descrição |
|---|---|
| `index.html` | Apresentação do projeto e atalhos para o gerador e a documentação |
| `gerador.html` | Formulário à esquerda, `SKILL.md` gerado à direita |
| `documentacao.html` | Explica cada campo e como escrever um bom campo `description` |

## Como usar

1. Baixe ou clone o projeto.
2. Abra o `index.html` no navegador (basta dar duplo clique, não precisa de servidor).
3. Vá em **Abrir o gerador** e preencha os campos.
4. Clique em **Copiar** e cole o conteúdo em um arquivo `SKILL.md` dentro da pasta da sua skill.

Se preferir servir localmente:

```bash
# Python
python3 -m http.server 8000

# ou Node.js
npx serve .
```

Depois acesse `http://localhost:8000`.

## Campos do gerador

| Campo | Para que serve |
|---|---|
| `name` | Identificador único da skill (slug), usado pelo agente e por marketplaces |
| `title` | Título curto exibido no cabeçalho do documento |
| `description` | O campo mais importante: é o que o agente lê para decidir **se** carrega a skill. Deve conter gatilhos claros |
| `category` | Ajuda humanos e marketplaces a organizar e descobrir a skill |
| `license` | Relevante ao publicar a skill publicamente (MIT, Apache-2.0 ou nenhuma) |
| `steps` | Sequência que o agente deve seguir, vira uma lista numerada |
| `notes` | Restrições explícitas: o que a skill nunca deve fazer |
| `author` | Autor da skill (opcional) |

## Exemplo de saída

```markdown
---
name: pdf-relatorio-mensal
description: Use esta skill sempre que o usuário pedir um relatório mensal em PDF a partir de uma planilha de vendas.
category: Documento / Arquivo
license: MIT
author: seu-usuario
---

# Gerador de Relatório Mensal em PDF

## Quando usar

Use esta skill sempre que o usuário pedir um relatório mensal em PDF a partir de uma planilha de vendas.

## Passos

1. Ler o arquivo de entrada
2. Validar formato
3. Gerar saída
4. Confirmar com o usuário

## Restrições

Nunca sobrescrever o arquivo original.

## Estrutura sugerida do repositório

pdf-relatorio-mensal/
  SKILL.md
  scripts/
  examples/
```

## Dicas para uma boa descrição

- Inclua exemplos concretos de pedidos do usuário que devem ativar a skill
- Mencione extensões de arquivo, ferramentas ou palavras-chave específicas
- Diga também quando **não** usar a skill, se houver ambiguidade com outra parecida

Mais detalhes na página `documentacao.html`.

## Tecnologias

- HTML5
- CSS3 (variáveis CSS, grid, flexbox)
- JavaScript puro (sem frameworks ou bibliotecas)

## Contribuindo

Sugestões e melhorias são bem-vindas. Abra uma issue ou envie um pull request.

## Licença

Defina aqui a licença do projeto (por exemplo, MIT).
