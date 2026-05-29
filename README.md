#  AI News Bot — n8n Workflow

This workflow automatically scrapes AI-related news from **sonxeber.az** and publishes them to a Telegram channel on a schedule.

---

##  What does it do?

###  Pipeline 1 — News Scraping (Every day at 09:00)
- Extracts title, link, and photo URL
- Saves to Google Sheets with status `Gozlemede` (avoids duplicates)

###  Pipeline 2 — News Publishing (Every 2 hours, 09:00–21:00)
- Reads pending news from Google Sheets (status: `Gozlemede`)
- Picks **1 news item** per run
- Sends **photo + text** to Telegram channel
- Updates status to `Paylasildi` in Google Sheets

###  Pipeline 3 — Daily Report (Every day at 21:00)
- Collects all news published that day
- Sends a daily summary to Telegram

---

##  Services Used

| Service | Purpose |
|---|---|
| Google Sheets | News database & status tracking |
| Telegram Bot | Channel publishing & daily report |
| n8n | Workflow automation |

---

##  Files

| File | Description |
|---|---|
| `ai_news_agent.json` | n8n workflow export file |

---

##  How to Import into n8n

1. Open n8n
2. Go to **Workflows** from the left menu
3. Click **Import** in the top right
4. Select the `ai_news_agent.json` file
5. Add your own credentials (Google Sheets, Telegram)

---

##  Requirements

- n8n (cloud or self-hosted)
- Google Sheets OAuth2 connection
- Telegram Bot token

