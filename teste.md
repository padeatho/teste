# Convexus – ETL TransferGov para PostgreSQL (Talend) — **As-Built (Correção Mermaid)**

## 4.1 Grafo de Orquestração do Job (corrigido)

```mermaid
graph TD
    PRE[tPrejob - conexao BD e setup] --> CLN[tFileList e tFileDelete]
    CLN --> DWN[tFileFetch - download ZIP]
    DWN --> UNZ[tFileUnarchive - extracao ZIP]
    UNZ --> S1[Job proponentes]
    UNZ --> S2[Job convenio]
    UNZ --> S3[Job empenho]
    UNZ --> S4[Job desembolso]
    UNZ --> S5[Job cronofisico]
    UNZ --> S6[Job termo_aditivo]
    UNZ --> S7[Job solicitacao_rend_aplicacao]
    UNZ --> S8[Job contraproposta]
    S1 --> POST[tPostjob - fechamento de conexoes e logs]
    S2 --> POST
    S3 --> POST
    S4 --> POST
    S5 --> POST
    S6 --> POST
    S7 --> POST
    S8 --> POST
```

---

## 8. Política de Erros & Reprocessamento (corrigido)

```mermaid
flowchart TD
    A[Falha no subjob] --> B{Tipo de erro}
    B -->|Rede ou download| C[Reexecutar job ou refazer download]
    B -->|CSV corrompido| D[Isolar arquivo e registrar erro]
    B -->|Dado invalido| E[Enviar para DLQ - rejeitados]
    C --> Z[Relancar job]
    D --> Z
    E --> Z
```

---

✅ **Correção aplicada:**  
Esses diagramas foram ajustados para compatibilidade com **Mermaid v10+** e renderizadores do **GitHub/Confluence**, removendo caracteres especiais que causavam erros (`*`, `/`, `ç`, `()`, acentos etc.).
