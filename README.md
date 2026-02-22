# TDSE-04-RAG

Introduction to Creating RAGs (Retrieval-Augmented Generators) with Gemini

## Description

This project is part of the TDSE-04 lab, designed to introduce students to the fundamental concepts and practical implementation of Retrieval-Augmented Generators (RAGs) using Google's Gemini and the LangChain framework. The RAG system combines a vector database (Pinecone) with large language models to enhance responses with contextual information retrieved from a knowledge base.

The project demonstrates how to:
- Load and process documents using LangChain
- Create vector embeddings using HuggingFace
- Store and retrieve embeddings using Pinecone vector database
- Build a RAG pipeline that augments LLM responses with retrieved context using Gemini

## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes.

### Prerequisites

What things you need to install the software and how to install them:

- Python 3.12+
- Google AI API Key (for Gemini)
- Pinecone API Key

### Installing

A step by step series of examples that tell you how to get a development env running:

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd TDSE-04-RAG
   ```

2. **Create a virtual environment (optional but recommended)**
   ```bash
   python -m venv .venv
   source .venv/bin/activate
   ```

3. **Install the dependencies**
   ```bash
   pip install -U langchain langchain-google-genai langchain-pinecone pinecone-client langchain-huggingface sentence-transformers
   ```

4. **Configure environment variables**
   
   Copy the `.env.example` file to `.env` and fill in your API keys:
   ```bash
   cp .env.example .env
   ```
   
   Edit `.env` with your credentials:
   ```
   GOOGLE_API_KEY=your_google_api_key_here
   PINECONE_API_KEY=your_pinecone_api_key_here
   PINECONE_INDEX=your_index_name
   ```

5. **Set up Pinecone**
   
   - Create an account at [Pinecone](https://www.pinecone.io/)
   - Create a new index with the following settings:
     - Dimension: 384 (for all-MiniLM-L6-v2)
     - Metric: cosine
   - Note your index name and use it in the `.env` file

## Running the Project

### Using Jupyter Notebook

Open the Jupyter notebook and run the cells sequentially:

```bash
jupyter notebook langchainRAG.ipynb
```

### Project Structure

The notebook contains the following sections:
1. **Installation**: Install required packages
2. **Environment Setup**: Configure API keys
3. **Document Loading**: Load documents using LangChain document loaders
4. **Text Splitting**: Split documents into chunks for embedding
5. **Embedding Creation**: Create vector embeddings using HuggingFace
6. **Vector Store**: Store embeddings in Pinecone
7. **Retrieval**: Implement retrieval-augmented generation
8. **Q&A Chain**: Build the RAG pipeline

## Architecture

The RAG system consists of the following components:

```
┌─────────────┐     ┌─────────────────┐     ┌──────────────┐
│  Documents  │────>│   Text Splitter │────>│  Embeddings  │
└─────────────┘     └─────────────────┘     └──────────────┘
                                                  │
                                                  v
┌─────────────┐     ┌─────────────────┐     ┌──────────────┐
│  User Query │────>│   Retrieval     │<────│  Pinecone    │
└─────────────┘     └─────────────────┘     │  Vector Store│
                     │                       └──────────────┘
                     v
              ┌─────────────┐     ┌──────────────┐
              │    LLM      │<────│   Context    │
              │  (Gemini)   │     │  (Retrieved) │
              └─────────────┘     └──────────────┘
```

## Built With

- [LangChain](https://www.langchain.com/) - Framework for building LLM applications
- [Google Gemini](https://gemini.google.com/) - LLM model
- [HuggingFace](https://huggingface.co/) - Embedding models
- [Pinecone](https://www.pinecone.io/) - Vector database for embeddings
- [Jupyter](https://jupyter.org/) - Interactive computing environment

## Assessment Criteria

- Completeness of code and adherence to the tutorials
- Clarity and detail of the README documentation
- Proper GitHub repository organization and presentation

## Authors

- **Tulio Riaño Sánchez** -

See also the list of [contributors](https://github.com/your-repo/contributors) who participated in this project.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments

- LangChain documentation and tutorials
- Google for providing the Gemini LLM
- HuggingFace for providing the embedding models
- Pinecone for the vector database infrastructure
