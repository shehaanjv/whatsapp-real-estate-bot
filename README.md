# whatsapp/telegram-real-estate-bot
# RealtyBot: AI-Powered Real Estate Lead Generation Agent

* "Transitioned the user interface from WhatsApp (Twilio) to Telegram to leverage its free, developer-friendly API for continuous testing."

An automated, AI-driven Telegram bot designed to act as a virtual property advisor for a premier Mumbai real estate brokerage. This agent converses naturally with prospective clients, qualifies their requirements, and automatically logs structured lead data into an Airtable CRM.

## 🚀 Live Demo
![Demo]([Link to your GIF or video demo here])

## 🏗️ Architecture & Tech Stack
This project uses **n8n** as the central automation engine to orchestrate the flow of data between three main services:
* **User Interface:** Telegram API
* **AI Brain:** OpenAI (GPT-4) via n8n's Advanced AI Agent node
* **Database / CRM:** Airtable

## ✨ Key Features
* **Conversational Qualification:** The bot naturally extracts 5 critical data points from the user: `Name`, `Intent` (Buy/Rent), `Configuration` (e.g., 2 BHK), `Locality` (e.g., Bandra), and `Budget`.
* **Persistent Memory:** Utilizes n8n's Simple Memory node to remember conversation history and context across multiple messages.
* **Autonomous Tool Usage:** Once all required criteria are met, the AI Agent autonomously triggers a database tool to format and push the data.
* **Error Handling:** Fallback responses are configured in case of API or database connection timeouts.

## 🛠️ Setup & Installation

To run this project on your own n8n instance:

### 1. Prerequisites
* An active n8n instance (Cloud or Self-Hosted)
* A Telegram Bot Token (via BotFather)
* An OpenAI API Key
* An Airtable Personal Access Token (with `data.records:read`, `data.records:write`, and `schema.bases:read` scopes)

### 2. Database Setup
Create an Airtable base with a table containing the following exactly named Single Line Text columns:
* `Name` | `Intent` | `Configuration` | `Locality` | `Budget` | `Chat ID`

### 3. Import the Workflow
1. Download the `workflow.json` file from this repository.
2. Open your n8n workspace.
3. Click **Import from File** in the top right corner of the canvas, or simply open the JSON file, copy its contents, and paste (`Ctrl+V` / `Cmd+V`) directly onto the n8n canvas.
4. Add your API credentials to the respective nodes (Telegram Trigger, OpenAI Model, and Airtable Tool).
5. Activate the workflow!

---
