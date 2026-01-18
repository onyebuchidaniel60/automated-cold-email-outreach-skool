# Automated Skool Cold Email Outreach Workflow

This n8n workflow automates the process of finding potential leads on Skool and initiating personalized email outreach. It integrates web scraping, data management in Google Sheets, and automated email delivery.

## 🚀 Features

- **Automated Scraping:** Uses the **Apify Skool Email Scraper** to find leads based on specific keywords or discovery URLs.
- **Lead Management:** Automatically appends lead information including Account URL, Email, Biography, and outreach status to a **Google Sheet**.
- **Personalized Outreach:** Sends tailored cold emails regarding health and energy optimization.
- **Rate Limiting:** Includes a **Wait node** (150-second delay) between emails to protect sender reputation and prevent spam flagging.
- **Batch Processing:** Processes leads in batches of 15 to ensure stable execution.

## 🛠️ Prerequisites

To use this workflow, you will need:
- An **n8n** instance.
- **Apify API Key** (with access to the `scraper-mind/skool-email-scraper` actor).
- **Google Sheets OAuth2** credentials.
- **SMTP Credentials** for the sending email account (`lucas@cg.coachclub.site`).

## ⚙️ How It Works

1.  **Trigger:** The workflow is triggered via a **Webhook** receiving `skoolKeywords`.
2.  **Scrape:** The **Apify node** executes a search on Skool for users matching the keywords, specifically looking for `@gmail.com` addresses.
3.  **Data Logging:** For every lead found, the workflow appends the details to the "Reply data outreach 2" Google Sheet.
4.  **Email Generation:** The workflow sets a personalized subject line ("About your energy and health") and body text.
5.  **Delivery:** Emails are sent via SMTP, with a CC to a backup address (`primaldragos@gmail.com`) for tracking.
6.  **Loop & Wait:** The workflow waits for 150 seconds before looping back to the next lead in the batch.

## 📦 Installation

1. Download the `automated personalized cold email outreach skool (2).json` file.
2. Open your n8n dashboard and click on **Import from File**.
3. Configure the following credentials:
   - **Apify API**
   - **Google Sheets OAuth2 API**
   - **SMTP**
4. Update the **Google Sheet ID** in the "Add data to skool sheet" node to match your own spreadsheet.
