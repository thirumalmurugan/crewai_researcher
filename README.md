# CrewaiResearcher Crew

Welcome to the CrewaiResearcher Crew project, powered by [crewAI](https://crewai.com). This project demonstrates a multi-agent AI system designed to conduct deep research and generate comprehensive reports automatically.

## Project Overview

This system utilizes two specialized AI agents to collaborate on a given topic:
1.  **Research**: Finds relevant and cutting-edge information.
2.  **Report**: Compiles findings into a structured, easy-to-read document.

By default, the crew is configured to research "Open source AI agent frameworks", but this can be easily customized.

## Project Structure

The project is organized as follows:

- **`src/crewai_researcher/main.py`**: The entry point. Sets up inputs (topic, date) and kicks off the crew execution.
- **`src/crewai_researcher/crew.py`**: Defines the `CrewaiResearcher` class, configuring the agents and tasks using decorators.
- **`src/crewai_researcher/config/agents.yaml`**: YAML file defining the agents' roles, goals, and backstories.
- **`src/crewai_researcher/config/tasks.yaml`**: YAML file defining the specific tasks and expected outputs.
- **`.env`**: Configuration file for environment variables (API keys).

## Agents

The crew consists of two intelligent agents:

### 1. Senior Data Researcher (`researcher`)
- **Role**: {topic} Senior Data Researcher
- **Goal**: Uncover cutting-edge developments in {topic}
- **Backstory**: A seasoned researcher known for finding the most relevant information and presenting it clearly.
- **Tools**: Uses `SerperDevTool` to search the internet for real-time information.

### 2. Reporting Analyst (`reporting_analyst`)
- **Role**: {topic} Reporting Analyst
- **Goal**: Create detailed reports based on {topic} data analysis and research findings
- **Backstory**: A meticulous analyst who turns complex data into clear, actionable reports.

## Tasks

### 1. Research Task
- **Goal**: Conduct thorough research on the topic.
- **Output**: A list of 10 bullet points with the most relevant information.

### 2. Reporting Task
- **Goal**: Expand the researched topics into full sections.
- **Output**: A fully fledged markdown report (`report.md`) containing detailed sections on the findings.

## Installation

This project uses [UV](https://docs.astral.sh/uv/) for fast and reliable dependency management.

1.  **Install `uv`** (if needed):
    ```bash
    pip install uv
    ```

2.  **Install Project Dependencies**:
    Navigate to the project root and run:
    ```bash
    crewai install
    ```

3.  **Configure Environment**:
    Create a `.env` file in the root directory and add your API keys:
    ```text
    OPENAI_API_KEY=your_openai_api_key
    SERPER_API_KEY=your_serper_api_key
    ```
    *Note: `SERPER_API_KEY` is required for the Internet search capability.*

## Running the Project

To start the crew and generate a report:

```bash
crewai run
```

### Expected Output
After running the command, you will see the agents collaborating in the console. Once finished, a file named **`report.md`** will be created in the root directory containing the final research report.

## Customization

You can customize the research topic by modifying `src/crewai_researcher/main.py`:

```python
def run():
    inputs = {
        'topic': 'Your Custom Topic Here',
        'current_year': str(datetime.now().year)
    }
    CrewaiResearcher().crew().kickoff(inputs=inputs)
```

## Support

- [crewAI Documentation](https://docs.crewai.com)
- [crewAI GitHub](https://github.com/joaomdmoura/crewai)
- [crewAI Discord](https://discord.com/invite/X4JWnZnxPb)
