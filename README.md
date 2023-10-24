# Prompt engineering examples for FOSS4GNA 2023 

Running an Large Language Model locally let's you play with the latest models! Learn by doing.

## Hardware Prerequisites

- OS – recent version of macOS, or Linux
- Storage – minimum 50 Gb free
- Memory – minimum 8 Gb, 16 Gb or more ideal

## Minimum Software Installation for macOS and Linux

We will use Ollama, an application for running Large Language Models locally. Download and install Ollama: https://ollama.ai/download

1. Open a terminal and start ollama. 

```
ollama serve
```

2. Check to see if it is installed: 

```
ollama –version
```

Pull a LLM: 

```
ollama pull orca-mini
```

Start ollama: 

```
ollama run orca-mini
```

## Minimum Software Installation for Windows

Ollama is currently not available for Windows. However, a Docker image is available, and requires installing Docker.

1. Install Docker. https://docs.docker.com/desktop/install/windows-install/
2. Open a Powershell window as Administrator
3. Pull the ollama container image from Docker Hub. Copy and paste this command in the Powershell window.

```
docker pull ollama/ollama
```

4. Start the ollama container. Copy and paste this command in the Powershell window.

```
docker run -d -v ollama:/root/.ollama -p 11434:11434 --name ollama ollama/ollama
```

5. To run a model locally, copy and paste this command in the Powershell window.

```
docker exec -it ollama ollama run orca-mini
```

## Optional Configuration

If you are familiar with Python, using a Jupyter notebook provides an option to save your work and extending the capability of a LLM. We will use Anaconda Distribution,

1. Download anaconda: https://www.anaconda.com/download
2. Install anaconda: https://docs.anaconda.com/free/anaconda/install/index.html
3. We will use Anaconda Navigator: https://docs.anaconda.com/free/anaconda/getting-started/#navigator-tutorials
4. Open Anaconda Navigator https://docs.anaconda.com/free/navigator/getting-started/#starting-navigator
5. In Navigator, launch JupyterLab. It will open a page in a browser.
6. In the Jupyter page choose `New` **>** `Python3` (ipykernel)
7. In the first cell, paste the following to install langchain, then choose Run.

```
conda install langchain -c conda-forge
```

8. Add a new cell and paste the following

```
from langchain.llms import Ollama
from langchain.callbacks.manager import CallbackManager
from langchain.callbacks.streaming_stdout import StreamingStdOutCallbackHandler                                  
llm = Ollama(model="orca-mini", 
             callback_manager = CallbackManager([StreamingStdOutCallbackHandler()]))

llm("Why is the sky blue?")
```

## Prompt Engineering Resources

- [DAIR.AI Prompt Engineering Guide](https://www.promptingguide.ai/)

- [Anthropics Introduction to Prompt Design](https://docs.anthropic.com/claude/docs/introduction-to-prompt-design)

- [AI21 Prompt Engineering](https://docs.ai21.com/docs/prompt-engineering)

- [SageMaker Documentation – Prompt Engineering for FMs](https://docs.aws.amazon.com/sagemaker/latest/dg/jumpstart-foundation-models-customize-prompt-engineering.html)

- [Amazon Bedrock Workshop](https://github.com/aws-samples/amazon-bedrock-workshop/)

- [Amazon Bedrock Prompting samples](https://github.com/aws-samples/amazon-bedrock-prompting)

- [Prompt Engineering Playground with SageMaker](https://github.com/aws-samples/prompt-engineering-playground-with-sagemaker)

# Try it out

Open the notebooks.

- [Prompt Engineering Mapping Example](./mapping-example.ipynb)
- [A RAG example with live data](./RAG%20-%20inciweb.ipynb)

