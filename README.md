# Ollama VT-100

A terminal-based chat client for Ollama, meticulously optimized for 80x24 VT-100 and CRT displays. This is a niche tool for the retro-computing enthusiast who wants to chat with modern AI on vintage hardware.


## What It Is

This program is a pure, text-only Go application that connects to an Ollama server. Its primary features are:

* **Retro-Optimized:** All AI responses are sanitized to pure ASCII and formatted to fit a 76-column wide, 21-line high viewport. This ensures clean text wrapping and readability on a standard 80x24 screen, complete with a built-in pager for long responses.
* **Interactive Session Setup:** On startup, the client guides you through:
    1.  **Agent Selection:** Choose a "personality" or system prompt for the AI.
    2.  **Model Selection:** Lists and lets you pick from all available models on your Ollama server.
    3.  **Parameter Tuning:** Set the `temperature` and `context window` for your session.
* **Simple & Focused:** No complex UI, just a classic prompt-and-response chat loop.

## How to Use

1.  **Configure:** Create your `config.json` file and (optionally) add your own `.agent` files (see **Configuration** below).
2.  **Run:** Execute the program:
    ```bash
    # If you have Go installed
    go run main.go
    
    # Or, if you've built the binary
    ./ollama-vt100-linux
    ```
3.  **Follow the Prompts:**
    * Select your desired agent.
    * Select the model you wish to use.
    * Set the temperature and context window (or just press Enter to accept the defaults).
4.  **Chat:**
    * Type your message at the `>` prompt and press Enter.
    * Type `/quit` or `/exit` to end the session.
  
### 2. Agents (Optional)

"Agents" are simply **plain text files** that provide the **system prompt** for your chat session. This sets the personality and instructions for the AI.

* **Location:** All agent files must be placed in the `agents/` directory.
* **File Extension:** Files **must** use the `.agent` extension (e.g., `researcher.agent`).

The program will read all `.agent` files in this directory and present them as a list for you to choose from at startup.

#### Example: `agents/researcher.agent`

To create an agent, just create a new plain text file in the `agents/` directory. For example:

```bash
# Create the file
touch agents/researcher.agent

# Add your plain text system prompt to the file
echo "You are a research agent. Be precise in all of your work, and explain your thought process as you talk." > agents/researcher.agent


## Building from Source

To build your own binary from the source code, run:

```bash
go build -o ollama-vt100 .


## Configuration

Before you can run the client, you must configure it.

### 1. config.json (Required)

This file tells the client where to find your Ollama server. It must be in the same directory as the executable.

Create a file named `config.json` with the following content:

```json
{
  "ollama_url": "[http://127.0.0.1:11434](http://127.0.0.1:11434)"
}

