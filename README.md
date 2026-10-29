# QuickCash Zimbabwe Loans — starter website

This is a starter project, not a published or production-approved lending platform. It includes a mobile-friendly loan application page, a Cloudflare Pages Function that validates and stores applications in D1, optional Telegram notifications, and a basic read-only admin page.

## Included files
- `index.html`, `styles.css`, `app.js` — public application website
- `functions/api/apply.js` — validates and saves applications, then optionally sends a Telegram message
- `admin.html`, `functions/api/admin.js` — basic password-protected, read-only application list
- `schema.sql` — database schema

## Before launch
1. Confirm the lender's legal/business identity, address/contact details, licensing or registration requirements, loan terms, interest/fees, complaints process, privacy notice, and data retention rules. Do not publish until these are accurate.
2. Deploy this project to Cloudflare Pages with Functions enabled.
3. Create a Cloudflare D1 database and execute `schema.sql` in it.
4. Bind the D1 database to the Pages project with binding name `DB`.
5. Set these server-side environment variables in Pages settings (never in browser JavaScript):
   - `TELEGRAM_BOT_TOKEN` — your bot token
   - `TELEGRAM_CHAT_ID` — your private numeric chat ID
   - `ADMIN_PASSWORD` — a strong, unique password
6. Set secrets as encrypted/secret variables where the platform offers that option. Never commit tokens or passwords into this project.
7. Test with dummy information, verify Telegram delivery and admin access, and review security before accepting real applications.

## Telegram private chat setup
- Open your bot in Telegram and press Start, then send a message.
- Use Telegram's official Bot API `getUpdates` method privately to locate the numeric `message.chat.id`.
- Never share your bot token in a chat, screenshot, URL, repository, or frontend code.
- If the bot does not send a message, check the Pages function logs and confirm the bot has been started by the receiving account.

## Admin
After deployment, open `/admin.html`. Enter the `ADMIN_PASSWORD` value to load the latest 500 applications. This is a minimal starter dashboard; it is not a substitute for a security review or a mature authentication system. Do not reuse a personal password.

## Data protection
The form does not collect national ID, passwords, mobile-money PINs, OTPs, or identity-document images. The notification includes the applicant's name, phone, requested amount, employment, income, preferred term, timestamp, and a reference. Make sure the privacy notice and consent are appropriate for your jurisdiction before using the site with real people.

## Not included
- No live hosting/deployment has been performed.
- No custom domain has been purchased.
- No loan approval or repayment calculation engine.
- No claim of affiliation with EcoCash or any other financial provider.
