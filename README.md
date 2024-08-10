# BabbleBot

## Description
**BabbleBot** is a chatbot project that utilizes open-source Large Language Models (LLMs) to deliver human-like conversational capabilities. The project leverages the Hugging Face Transformers library and implements Facebook's BlenderBot model to understand and generate responses that mimic natural human conversation. The chatbot is designed to manage ongoing dialogues with context awareness, making it a robust and responsive tool for basic conversational AI applications.

## Features
- **Hugging Face Transformers Integration**: Utilizes the powerful Transformer models to process and generate text.
- **BlenderBot Model**: Implements Facebook’s BlenderBot for efficient, open-source conversational AI.
- **Context-Aware Conversations**: Maintains conversation history to provide contextually relevant responses.
- **Tokenization and Input Processing**: Handles natural language inputs by tokenizing and preparing them for model processing.
- **Response Generation**: Generates human-like responses based on the conversation context.
- **Conversation History Management**: Keeps track of dialogue history to ensure coherent interactions over time.

## Installation

### Prerequisites
- Python 3.7 or higher
- pip (Python package installer)

### Steps
1. **Clone the Repository:**
   ```bash
   git clone https://github.com/your-username/BabbleBot.git
   cd BabbleBot

2. Create a Virtual Environment (Optional but recommended):

        python -m venv env
        source env/bin/activate  # On Windows use `env\Scripts\activate`

3. Install Required Libraries:

    Install the necessary Python packages including Hugging Face’s Transformers library:

        pip install -r requirements.txt

4.  Download and Initialize the Model:
        In your script, initialize BlenderBot along with its tokenizer:

            from transformers import BlenderbotTokenizer, BlenderbotForConditionalGeneration

            model_name = "facebook/blenderbot-400M-distill"
            tokenizer = BlenderbotTokenizer.from_pretrained(model_name)
            model = BlenderbotForConditionalGeneration.from_pretrained(model_name)


## Usage

Once the environment is set up, you can start interacting with BabbleBot:

1. Run the Script:

    Start the chatbot by running the main script:

        python main.py

2. Interact with BabbleBot:

    Type in your inputs, and the chatbot will generate responses based on the current conversation context.

## Example Code
Here’s a snippet that demonstrates how the conversation management and response generation work:


    def generate_response(input_text, chat_history=[]):
        inputs = tokenizer([input_text] + chat_history, return_tensors='pt', truncation=True, padding=True)
        outputs = model.generate(**inputs)
        response = tokenizer.decode(outputs[0], skip_special_tokens=True)
        chat_history.append(response)
        return response, chat_history

        # Example usage
        user_input = "Hello, how are you?"
        response, chat_history = generate_response(user_input)
        print("BabbleBot:", response)

This function takes the user input, processes it through the model, and returns a contextually relevant response while updating the chat history.

## Limitations
While BabbleBot is capable of managing basic conversations, it may still have limitations in understanding complex queries or maintaining long-term context over extended dialogues. It is intended as a demonstration of integrating AI models into user-friendly applications.

## License
This project is licensed under the MIT License. See the LICENSE file for more information.

