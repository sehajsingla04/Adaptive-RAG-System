# Adaptive Retrieval System

An advanced Retrieval-Augmented Generation (RAG) framework that improves answer quality through retrieval evaluation, query refinement, and dynamic web augmentation.

This project demonstrates the evolution of a RAG pipeline from basic document retrieval to an adaptive system capable of detecting weak retrieval results, refining search queries, incorporating external knowledge, and generating grounded responses.

---

## Project Overview

Traditional RAG systems assume that retrieved documents are always relevant. In practice, retrieval quality can vary significantly, leading to incomplete or incorrect answers.

This project addresses that challenge by introducing a corrective retrieval workflow that evaluates retrieved context before answer generation.

The system:

- Retrieves relevant information from local PDF documents.
- Evaluates retrieval quality using an LLM-based relevance scorer.
- Classifies retrieval quality into multiple decision states.
- Dynamically rewrites weak queries.
- Augments local knowledge with real-time web search.
- Filters noisy context before generation.
- Produces grounded responses using only verified context.

---

## Key Features

### Intelligent Retrieval Evaluation

Retrieved chunks are scored for relevance before answer generation.

### Adaptive Routing

The system dynamically selects one of three retrieval strategies:

| Verdict | Action |
| --- | --- |
| CORRECT | Use local knowledge base only |
| INCORRECT | Rewrite query and use web search |
| AMBIGUOUS | Combine local retrieval with web search |

### Query Rewriting

Weak or unclear questions are automatically transformed into optimized search queries.

### Hybrid Knowledge Sources

Combines:

- Local PDF knowledge base
- Vector search retrieval
- Real-time web search

### Context Refinement

Context is filtered at sentence level to remove irrelevant information before generation.

### Grounded Answer Generation

Responses are generated strictly from validated context to reduce hallucinations.

---

## System Architecture

```text
User Question
      |
      v
Document Retrieval (FAISS)
      |
      v
Retrieval Evaluation
      |
 +----+----+
 |    |    |
 v    v    v
Correct Ambiguous Incorrect
 |      |       |
 |      |       +----> Query Rewrite
 |      |                 |
 |      |                 v
 |      |           Web Search
 |      |
 |      +-----------------+
 |                        |
 v                        v
 Local Context + Web Context
              |
              v
       Context Refinement
              |
              v
      Answer Generation
              |
              v
        Final Response
```

---

## Project Evolution

The repository documents the progressive development of the system through six stages.

| Notebook | Focus |
| --- | --- |
| 01_Basic_RAG | Basic retrieval and generation |
| 02_Retrieval_Refinement | Improved retrieval quality |
| 03_Retrieval_Evaluator | LLM-based relevance scoring |
| 04_Web_Search_Refinement | External knowledge integration |
| 05_Adaptive_RAG_Final | Complete corrective workflow |


---

## Technology Stack

### LLMs

- GPT-4o Mini
- OpenAI Embeddings

### Retrieval

- FAISS Vector Store
- LangChain Retrieval Pipeline

### Document Processing

- PyPDFLoader
- RecursiveCharacterTextSplitter

### Search Augmentation

- Tavily Search API

### Development Environment

- Python
- Jupyter Notebook

---

## Project Structure

```text
adaptive-rag-system/
|
+-- notebooks/
|   +-- 01_Basic_RAG.ipynb
|   +-- 02_Retrieval_Refinement.ipynb
|   +-- 03_Retrieval_Evaluator.ipynb
|   +-- 04_Web_Search_Refinement.ipynb
|   +-- 05_Adaptive_RAG_Final.ipynb
|
+-- documents/
|   # Not included in repository (due to size constraints)
|
+-- requirements.txt
+-- README.md
```

---



