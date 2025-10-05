$JFREE — Variant B (extra Coin spawns 1200ms → 700ms min) + Leaderboard fix
--------------------------------------------------------------------------
Run:
  npm install
  npm start
Open:
  http://localhost:3000

Notes:
- Put your song into assets/theme.mp3 (no autoplay). Volume slider + mute in header.
- 30-day reset uses America/Los_Angeles (Portland). Override TIME_ZONE if needed.
- Leaderboard fix: after the FIRST game (even with score 0), your username appears in the table.

=== Telegram Auth Setup ===
1) Create a Telegram Bot and get its token. Set env var TELEGRAM_BOT_TOKEN to that value.
2) Set data-telegram-login in index.html widget to your bot's username (currently JfreeAuthBot).
3) On Render, add environment variables:
   - TELEGRAM_BOT_TOKEN=<your_bot_token>
   - TIME_ZONE=America/Los_Angeles
4) Start command: node server.js
5) The game requires Telegram login; "Start" button is disabled until login is completed.
6) Leaderboard automatically resets every 30 days when the first write/read happens after the window expires.


Local config (optional):
- Create a file named config.json next to server.js with:
  {
    "TELEGRAM_BOT_TOKEN": "123456:ABC-DEF...",
    "TIME_ZONE": "America/Los_Angeles"
  }
- The server will read this if the corresponding environment variables are not set.

Where to put the Telegram token:
- EITHER set the environment variable TELEGRAM_BOT_TOKEN
- OR put it in config.json as shown above
- On Render: use the Environment tab → add TELEGRAM_BOT_TOKEN (and optional TIME_ZONE)
