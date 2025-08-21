# Análise de Controle de Qualidade de Dados Meteorológicos (Projeto SONDA/INPE)

Este repositório contém um script em Python (`qcd_tutorial.py`) projetado para realizar uma análise de controle de qualidade (CQ) em dados meteorológicos do projeto SONDA, mantido pelo Instituto Nacional de Pesquisas Espaciais (INPE).

O script serve como um tutorial completo, demonstrando como automatizar o processo de download, descompactação, processamento e análise de dados, focando especificamente no formato de arquivos CSV para dados e CSV para flags de qualidade (DQC - *Data Quality Control*).

## 🎯 Objetivo do Projeto

O objetivo principal é avaliar a consistência e a qualidade dos dados de variáveis meteorológicas (pressão, radiação, velocidade do vento e temperatura) através da interpretação dos flags de qualidade atribuídos pelo sistema de validação do INPE. O processo permite identificar dados suspeitos, faltantes ou de boa qualidade, gerando visualizações e um relatório consolidado.

## ✨ Funcionalidades

- **Download e Extração Automáticos:** Baixa um arquivo de dados mensal (`.7z`) diretamente do servidor do INPE e o descompacta.
- **Leitura e Junção de Dados:** Processa pares de arquivos `.csv` (dados) e `_DQC.csv` (qualidade), unindo-os em um único DataFrame.
- **Processamento de Flags:** Interpreta os flags de qualidade de 3 dígitos do INPE, extraindo o dígito final que representa o status consolidado.
- **Análise Quantitativa:** Calcula a distribuição percentual dos flags de qualidade (0, 2, 5, 9) para cada variável.
- **Análise Visual:** Gera séries temporais para cada variável, colorindo os pontos de dados de acordo com seu flag de qualidade, facilitando a identificação de anomalias.
- **Geração de Relatório:** Exporta os resultados para um arquivo Excel (`.xlsx`) contendo um resumo estatístico e uma lista detalhada de todos os registros marcados como "suspeitos".

## 🚀 Como Usar

Este script foi desenvolvido para ser executado em um ambiente como o **Google Colab**, que facilita a instalação de dependências e a manipulação de arquivos.

### Pré-requisitos

- **Dependências de Sistema:** O script requer `wget` e `p7zip`, que são instalados automaticamente em ambientes baseados em Debian (como o Colab) pelo próprio script.
- **Bibliotecas Python:** As seguintes bibliotecas são necessárias:
  - `pandas`
  - `matplotlib`
  - `seaborn`
  - `numpy`

Você pode instalar todas com o pip:
```bash
pip install pandas matplotlib seaborn numpy
```

### Execução

1.  **Abra no Google Colab:** Faça o upload do arquivo `qcd_tutorial.py` (ou a versão `.ipynb`) para o Google Colab.
2.  **Execute as Células:** Execute o código sequencialmente. O script é auto-contido e realizará todas as etapas automaticamente.
3.  **Altere a Fonte de Dados (Opcional):** Para analisar um período diferente, simplesmente altere a variável `url` no "Passo 2" do script para o link do arquivo `.7z` desejado.
4.  **Acesse o Relatório:** Ao final da execução, um arquivo `.xlsx` (ex: `Relatorio_Qualidade_SMS_201904.xlsx`) será gerado. Você poderá baixá-lo no painel de arquivos do Colab.

## 📈 Estrutura do Relatório de Saída

O arquivo Excel gerado contém duas planilhas:

1.  **Resumo da Qualidade:** Uma tabela que mostra a distribuição percentual de cada flag de qualidade para as variáveis analisadas.
2.  **Dados Suspeitos (Flag 2):** Uma lista completa de todos os registros que foram marcados com o flag "2" (dado suspeito), permitindo uma investigação mais aprofundada.
