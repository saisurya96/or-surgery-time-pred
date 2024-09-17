# SQL Agent and SQL Chain with OpenAI LLM

This repository demonstrates how to create a SQL Agent and a SQL Query Chain using the LangChain framework integrated with OpenAI's language models. These tools enable natural language interaction with a PostgreSQL database.

## Overview

The project consists of two main components:

1. **SQL Agent**: An agent designed to interact with a SQL database by generating and executing SQL queries based on natural language inputs.
2. **SQL Query Chain**: A chain that allows for querying a SQL database, which can be extended and customized for specific use cases.

## Setup

### Prerequisites

- Python 3.7 or higher
- PostgreSQL database (e.g., Chinook)
- OpenAI API key

### Installation

1. Clone the repository:
    ```bash
    git clone https://github.com/yourusername/txt2sql-bot.git
    cd sql-agent-langchain
    ```
2. Set up environment variables:
    - Create a `.env` file in the root directory of the project.
    - Add your OpenAI API key and PostgreSQL connection details:
      ```
      OPENAI_API_KEY=your_openai_api_key
      POSTGRES_USERNAME=your_postgres_username
      POSTGRES_PASSWORD=your_postgres_password
      POSTGRES_HOST=localhost
      POSTGRES_PORT=5432
      POSTGRES_DATABASE=chinook
      ```

## Usage

### SQL Agent

The SQL Agent can interpret natural language queries and generate SQL commands to interact with your database.

```python
from langchain_community.agent_toolkits import create_sql_agent
from langchain_openai import ChatOpenAI
```
# Initialize OpenAI LLM
llm = ChatOpenAI(api_key=openai_api_key, temperature=0, model='gpt-4o-mini')

# Create SQL Agent
sql_agent = create_sql_agent(llm=llm, db=sql_database, verbose=True, top_k=None)

# Example query
response = sql_agent.invoke({"input": "What are the total monthly sales?"})
print(response)

### SQL Query Chain

The SQL Query Chain enables more complex operations by chaining different tasks.

```python
from langchain.chains import create_sql_query_chain

# Create SQL Query Chain
chain = create_sql_query_chain(llm, db)
```
# Example query
```python
response = chain.invoke({"question": "How many employees are there?"})
print(response)
```
# Customization
You can customize the prompts and behavior of the agent and chain by modifying the prefix and suffix templates or by extending the chains with additional tasks.
