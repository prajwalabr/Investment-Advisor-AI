# Advanced Investment Advisor AI

An advanced multi-agent AI system that acts as a personal investment advisor. It automatically researches company news, retrieves financial data, analyses everything, and delivers actionable investment advice — all powered by GPT-4.1.

## What It Does

Give it a company name and it will:
1. **Search for the latest company news**
2. **Retrieve financial data** (company info & income statements)
3. **Analyse** all the gathered information
4. **Give you investment advice** based on the full analysis

## System Architecture

The system uses **4 specialized AI agents** working in a pipeline:

| Agent | Role | Task | Tool Used |
|-------|------|------|-----------|
| Agent 1 | News Info Explorer | Get company news | `search_tool` |
| Agent 2 | Data Explorer | Get company financials | `get_company_info`, `get_income_statements` |
| Agent 3 | Analyst | Analyse data from Agent 1 & 2 | — |
| Agent 4 | Financial Expert | Deliver investment advice | `get_current_stock_price` |

### Execution Flow
```
Agent 1 ─┐
          ├──► Agent 3 (Analyst) ──► Agent 4 (Advisor) ──► Final Result
Agent 2 ─┘
```
Agent 1 and Agent 2 run **in parallel** to save time, then Agent 3 analyses their combined output, and finally Agent 4 delivers the advice.

### Why Use Agents Instead of a Simple Web Search?
- Web search alone is unreliable and hard to automate
- Agents reduce the risk of hallucination by grounding responses in real data
- Parallel execution makes the system fast and efficient

## Tech Stack

- **Language:** Python
- **LLM:** GPT-4.1 (used across all agents)
- **Framework:** CrewAI
- **API Server:** FastAPI

## Project Structure

```
advanced/
├── agents.py                  # Defines all 4 AI agents
├── tools.py                   # Tools used by agents (search, financials, stock price)
├── tasks.py                   # Tasks assigned to each agent
├── main.py                    # Main entry point
├── api_server.py              # FastAPI server to expose the agent as an API
├── start_server.py            # Script to launch the server
├── example_client.py          # Example of how to call the API
└── minimal_parallel_tutorial.py  # Tutorial demonstrating parallel agent execution
```

## Getting Started

### 1. Clone the repository
```bash
git clone https://github.com/prajwalabr/advanced-investment-advisor.git
cd advanced-investment-advisor
```

### 2. Install dependencies
```bash
pip install -r requirements.txt
```

### 3. Set up your API key
```bash
export OPENAI_API_KEY=your_openai_api_key
```

### 4. Run the agent
```bash
python main.py
```

### 5. Or start the API server
```bash
python start_server.py
```

---

## What I Learned

- How to design and architect a **multi-agent AI system** from scratch
- Why agents are more reliable than direct LLM queries for research tasks
- How to structure agent pipelines with **parallel execution** for efficiency
- How to expose an AI system as a **REST API** using FastAPI

---

## 👤 Author

**prajwalabr** — [github.com/prajwalabr](https://github.com/prajwalabr)
