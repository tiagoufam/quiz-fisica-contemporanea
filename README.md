
# Quiz Educacional — GitHub Integrado (Starter)

Este repositório contém um **quiz web** que gera **QR Code** para acesso dos alunos, salva automaticamente cada tentativa **no próprio repositório GitHub** (pasta `resultados/`) e oferece um **dashboard para análise do professor** — tudo **gratuito** via GitHub Pages e GitHub API.

## 🚀 Publicação (GitHub Pages)
1. Crie um repositório novo no GitHub (público ou privado com Pages habilitado).
2. Suba estes arquivos na branch **`main`** (ou `gh-pages` se preferir).
3. Em **Settings → Pages**, escolha **Deploy from branch** e selecione a branch e a pasta **root**.
4. Aguarde a URL do **GitHub Pages** (ex.: `https://seu-usuario.github.io/seu-repo/`).

## 🔗 Como os alunos acessam
- Abra a página do projeto (GitHub Pages). O sistema **gera um QR Code** do link atual automaticamente.
- Projete o QR em sala. Os alunos leem o QR pelo celular, informam o nome e respondem.

## 💾 Salvamento dos resultados
Existem **dois modos**:
- **Modo Local (sem token):** resultados ficam no navegador do aluno (LocalStorage). Depois o professor pode **Exportar Todos os Dados** no dashboard.
- **Modo GitHub (recomendado):** informe **Usuário**, **Repositório** e um **Personal Access Token (PAT)** no início do app. Cada tentativa será gravada como um JSON em `resultados/` via GitHub API.

> **Importante:** por segurança, use **Fine-grained PAT**, com permissões mínimas **somente** para este repositório e com **expiração curta**. Evite publicar o token em arquivos do repositório.

## 🔑 Gerar Personal Access Token (resumo)
1. No GitHub: **Settings → Developer settings → Personal access tokens**.
2. Gere um **Fine-grained token** (ou classic, se necessário), com **Content: read & write** apenas para **um único repositório**.
3. Cole o token na tela de configuração do app (campo **Token de Acesso**).

## 🧪 Onde alterar as questões
No arquivo **`index.html`**, procure o array `QUESTOES` no `<script>` principal e edite/adicione perguntas, alternativas e metadados (descritor, competência, nível etc.).

## 📊 O que o dashboard entrega
- **Total de alunos**, **média** e **taxa de aprovação**;
- Tabela detalhada de tentativas (nome, % acerto, data/hora, status);
- **Análise por questão** (percentual de acerto, descritor);
- **Análise por descritor** (acertos/questões consolidado).

## 🧰 Pastas e arquivos
```
.
├── index.html          # Aplicação completa (quiz, QR, GitHub API, dashboard)
├── .nojekyll           # Evita processamento do Jekyll no GitHub Pages
└── resultados/
    └── .gitkeep        # Mantém a pasta no repositório
```

## ⚠️ Notas de segurança
- O token digitado é usado **no navegador** para chamar a API do GitHub. Prefira tokens **restritos e de curta duração**.
- Alternativa avançada: usar um backend (serverless/Cloudflare Workers/Actions) para receber as submissões e **não expor** o token ao cliente.

## 📥 Exportar dados
No **dashboard**, use **Exportar Todos os Dados** para baixar um `.json` com: configuração, questões, resultados e timestamp.

---

Feito para uso educacional e gratuito. Ajuste conforme o seu curso/disciplina.
