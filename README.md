# Convert code from Python to C#

This repository contains a Python-based application that leverages Large Language Models (LLMs) to automatically convert Python code snippets into highly optimized C# code. The application is designed to help developers quickly and efficiently re-implement performance-critical Python algorithms in C#.

## Features

- **LLM-Powered Conversion**: The application uses various LLMs (including GPT, Claude, Gemini, and CodeQwen) to perform code conversion.
- **Performance Optimization**: The LLMs are instructed to prioritize generating C# code that is not only functionally identical to the Python source but also optimized for the fastest possible execution time.
- **Gradio User Interface**: A simple, intuitive web-based interface built with the `Gradio` library allows users to input Python code, select an LLM, and view the converted C# code and its execution output.
- **Top-Level C# Code Generation**: The converted C# code is written in a .csx script format, eliminating the need for a `Main` method and allowing for easy execution with `dotnet-script`.
- **Side-by-Side Comparison**: The application provides a way to run both the original Python code and the converted C# code, displaying their outputs and execution times for direct comparison.

## How It Works

The core of the application is a Python script that:

1.  **Loads API Keys**: Retrieves API keys for various LLMs from a `.env` file.
2.  **Defines Prompts**: Creates system and user messages to instruct the LLMs on the conversion task, emphasizing identical output and performance optimization.
3.  **Streams Responses**: Uses the streaming capabilities of the LLM APIs to provide real-time updates as the C# code is being generated.
4.  **Executes Code**: Uses `subprocess` to run the generated C# code with `dotnet-script`, allowing for a direct performance benchmark against the original Python code.

## Requirements

- Python 3.7+
- A `.env` file with your API keys for the desired LLMs (e.g., `OPENAI_API_KEY`, `ANTHROPIC_API_KEY`, `GOOGLE_API_KEY`, `HF_TOKEN`).
- `dotnet-script` installed on your system to execute the C# code.
- Required Python packages (install with `pip`):
    ```bash
    pip install openai anthropic google-generativeai gradio python-dotenv huggingface-hub transformers
    ```

## Usage

1.  **Clone the repository**:
    ```bash
    git clone https://github.com/novaisDiogo/python-to-csharp-converter.git
    cd python-to-csharp-converter
    ```
2.  **Set up your `.env` file**:
    Create a `.env` file in the root directory and add your API keys.
    ```
    OPENAI_API_KEY=YOUR_OPENAI_KEY
    ANTHROPIC_API_KEY=YOUR_ANTHROPIC_KEY
    GOOGLE_API_KEY=YOUR_GOOGLE_API_KEY
    HF_TOKEN=YOUR_HUGGINGFACE_TOKEN
    ```
3.  **Run the application**:
    ```bash
    jupyter-lab
    ```
    Open the Jupyter Notebook and run all the cells. This will launch the Gradio web interface.
4.  **Convert code**:
    In the Gradio interface, paste your Python code, select an LLM, and click "Convert code". You can then run both the Python and C# code to compare the results.
