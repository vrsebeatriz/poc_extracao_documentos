# POC — Extração Estruturada de Documentos

**Desafio Técnico | Pesquisador em P&D — IA Generativa**

Bem-vindo(a) ao repositório da Prova de Conceito (POC) do desafio técnico para a posição de Pesquisador(a) em IA Generativa. Este repositório contém a implementação prática da solução proposta no **Dossiê de Investigação**.

## Objetivo da POC

A atual API de extração sofre com problemas de latência e custo devido à sua arquitetura de duas etapas (Interpretação seguida de Formatação). O objetivo desta POC é demonstrar uma abordagem alternativa e mais eficiente: um **Pipeline Unificado** utilizando uma única chamada de inferência com saída estruturada (JSON nativo via *Tool Use* / *Structured Outputs*).

Esta abordagem visa resolver ou minimizar os problemas de latência e custo operacional, lidando com eficácia tanto com documentos padronizados quanto com layouts complexos e extensos.

## Tecnologias Utilizadas

- **Linguagem:** Python
- **Ambiente:** Jupyter Notebook
- **Modelo da POC:** `gemini-2.5-flash` (Google DeepMind)
- **Bibliotecas:** `google-genai`, `pypdf`

## Estrutura do Repositório

- `poc_extracao_documentos.ipynb`: Notebook com a implementação completa, contendo a lógica de chamadas da API, as funções auxiliares e a execução dos três cenários de teste propostos.
- `resultados_poc.json`: Arquivo gerado pela execução da POC, contendo o output JSON extraído de cada um dos casos de uso.
- *`Dossie_Pesquisa.pdf`*: O Relatório de Viabilidade e Integração principal do desafio deve ser incluído neste repositório.

## Casos de Uso Implementados

A POC valida a solução processando três cenários distintos, extraindo métricas de custo e latência para cada um:

1. **Caso 1: Documento Estruturado (CNH)**
   - Extração pontual de campos predeterminados (Nome, CPF, Datas, Filiação) utilizando validação rígida de tipagem no JSON Schema.
2. **Caso 2: Documento Extenso (Paper The Claude 3 Model Family)**
   - Interpretação de documento acadêmico denso para extração do conteúdo formatado, mantendo estrutura hierárquica e sumarizando gráficos. *(Para adequação de contexto, limitou-se ao processamento das primeiras páginas, validando a viabilidade técnica da abordagem)*.
3. **Caso 3: Documento com Layout Complexo (Fatura de Energia)**
   - Processamento de faturas densas para extração precisa de faturamentos, tributos aninhados e histórico de consumo mensal a partir de tabelas.

## Como Executar a POC

1. Clone o repositório em sua máquina:
   ```bash
   git clone https://github.com/vrsebeatriz/poc_extracao_documentos.git
   cd poc_extracao_documentos
   ```
2. Crie e ative um ambiente virtual:
   ```bash
   python -m venv venv
   source venv/bin/activate  # ou `venv\Scripts\activate` no Windows
   ```
3. Instale as dependências do projeto:
   ```bash
   pip install google-genai pypdf jupyter
   ```
4. Abra o arquivo `poc_extracao_documentos.ipynb` e insira sua chave de API na variável `GEMINI_API_KEY`.
5. No notebook, atualize os caminhos dos arquivos (`PATH_CNH`, `PATH_FATURA`, `PATH_PAPER`) para apontar para os documentos correspondentes na sua máquina local antes de rodar as células de execução.

## Coleta de Métricas

O notebook está instrumentado para coletar e exibir automaticamente as seguintes métricas a cada execução, a fim de balizar a decisão técnica final recomendada no Dossiê:
- Latência total (segundos)
- Tokens de Input processados
- Tokens de Output gerados
- Estimativa de Custo baseada em *pricing* público da API.

---
*Desenvolvido por Ana Beatriz Araújo Silva.*
