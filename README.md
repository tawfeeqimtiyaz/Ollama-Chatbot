Local Ollama Chatbot

A private, offline Q&A chatbot that runs open-source language models on your own computer using Ollama, LangChain and Streamlit. No API key, no account and no usage fees. Your questions never leave your machine.

Features
Runs fully locally with open-source models served by Ollama
No API key or internet connection needed once the models are downloaded
Model selector in the sidebar: mistral, phi3, gemma4 and llama3
Adjustable temperature (0.0 to 1.0) and max tokens (50 to 300) sliders
LangChain chain: ChatPromptTemplate | Ollama | StrOutputParser
Optional LangSmith tracing, enabled only if you add a key
Clean, lightweight web interface built with Streamlit
Supported Models
Model	Best for
mistral	Fast, efficient answers and general chat
phi3	Small and lightweight, runs well on modest hardware
gemma4	Google's open model, a good general-purpose choice
llama3	Strong all-round quality from Meta

To add another model, pull it with Ollama and add its name to the model list in app.py.

Tech Stack
Component	Technology
Model runtime	Ollama
LLM framework	LangChain (langchain-community Ollama integration)
Interface	Streamlit
Configuration	python-dotenv
Language	Python 3.11+
Project Structure
.
├── app.py              # Streamlit app and LangChain chain
├── requirements.txt    # Python dependencies
└── README.md
Prerequisites
Python 3.11 or newer
Ollama installed from ollama.com
Enough free RAM and disk space for the models you choose. Larger models need more memory, and phi3 is the lightest option.
Getting Started
1. Clone the repository
bash
git clone https://github.com/<your-username>/<your-repo-name>.git
cd <your-repo-name>
2. Download the models

Make sure Ollama is running, then pull the models you want:

bash
ollama pull mistral
ollama pull phi3
ollama pull gemma4
ollama pull llama3

Check what is installed with:

bash
ollama list

The names in the sidebar model list in app.py must match the names shown by ollama list.

3. Create and activate a virtual environment
bash
python -m venv venv
# Windows
venv\Scripts\activate
# macOS / Linux
source venv/bin/activate
4. Install dependencies
bash
pip install -r requirements.txt
5. Run the app
bash
streamlit run app.py

Then open http://localhost:8501 in your browser.

Optional: LangSmith Tracing

Tracing is off by default. To turn it on, create a .env file in the project root:

env
LANGCHAIN_API_KEY=your_langsmith_api_key_here

If the key is missing, the app runs normally without tracing. Never commit your .env file.

Usage
Pick a model in the sidebar.
Set the temperature and max tokens. Lower temperature gives focused, consistent answers, and higher gives more varied ones. Max tokens limits the length of the answer.
Type your question in the input box.
Read the answer displayed below.

The first answer from a model can take longer, because Ollama loads the model into memory. Later answers are faster.

Troubleshooting
Connection error or "connection refused": Ollama is not running. Start the Ollama app, or run ollama serve, then try again.
Model not found: pull it first with ollama pull <model-name>, and check the exact name with ollama list.
Slow responses: use a smaller model such as phi3, and close other heavy programs to free up memory.
Deployment Note

This app needs Ollama running on the same machine, so it cannot run on Streamlit Community Cloud, which does not provide Ollama. Run it locally, or host it on your own server or VM where Ollama is installed.

Roadmap
Conversation history and multi-turn memory
Streaming responses
Chat with your own documents
License

Released under the MIT License. See LICENSE for details.
