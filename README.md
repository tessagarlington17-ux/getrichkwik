# 📊 Financial Intelligence Dashboard

A research-backed personal financial analysis dashboard built for Monarch Money users. Password-protected, deployable to Railway in minutes.

## Features

- **5 Analysis Sections**: Overview, Net Worth, Budget, Health Score, Framework
- **🔐 Password Protection**: Session-based authentication
- **📊 6 Interactive Charts**: Line, bar, donut, radar visualizations
- **💡 AI Insights**: Automatic recommendations based on your data
- **✏️ Editable Data**: Click "Edit Data" to update any value
- **📱 Responsive**: Works on desktop and mobile
- **🔥 FIRE Analysis**: Financial independence projections
- **Health Score**: 6-dimension composite scoring (0–100)

## Quick Start (Railway)

### 1. Deploy to Railway

```bash
# Option A: Deploy via GitHub
# Fork this repo → Railway → New Project → Deploy from GitHub

# Option B: Deploy via Railway CLI
npm install -g @railway/cli
railway login
railway init
railway up
```

### 2. Set Environment Variables in Railway Dashboard

Navigate to your Railway project → Variables tab, then add:

```
DASHBOARD_PASSWORD=YourSecurePassword123!
SESSION_SECRET=a-long-random-string-change-this-now
```

**⚠️ IMPORTANT**: Change both of these before deploying!

### 3. Access Your Dashboard

Once deployed, Railway will give you a URL like:
`https://financial-dashboard-production.up.railway.app`

- Visit the URL → you'll see the login page
- Enter your `DASHBOARD_PASSWORD`
- Access your full dashboard

## Local Development

```bash
# Install dependencies
npm install

# Create .env file and update with your password
cp .env .env.local

# Run locally
npm start
# → Open http://localhost:3000
```

## Updating Your Data

1. Click **"✎ Edit Data"** in the top right of the Overview
2. Click any dollar value to edit it (mirrors your Monarch Money data)
3. Click **"✓ Save Changes"** — data persists in browser localStorage

For full accounts:
- Go to **Net Worth** section → edit Assets and Liabilities tables
- Go to **Budget** section → spending categories auto-calculate

## Dashboard Sections

| Section | What it shows |
|---------|---------------|
| **Overview** | KPIs, income/expense trend, spending donut, key insights |
| **Net Worth** | 12-month trend, asset allocation, assets/liabilities tables, milestone tracker |
| **Budget** | 50/30/20 analysis, category breakdown, 10-year savings projection |
| **Health Score** | Overall score (0–100), 6-dimension radar chart, dimension deep-dives |
| **Framework** | Research methodology, academic references, analysis approach |

## Analysis Framework

This dashboard implements 8 research-backed financial frameworks:

1. **50/30/20 Budget Rule** — Warren & Tyagi
2. **PAW/UAW Net Worth Model** — Stanley & Danko
3. **Safe Withdrawal Rate (4% Rule)** — Bengen (1994)
4. **CFPB DTI Thresholds** — Consumer Financial Protection Bureau
5. **3–6 Month Emergency Fund** — FINRA guidelines
6. **Index Fund Strategy** — Bogle
7. **Behavioral Finance Nudges** — Thaler & Sunstein
8. **Composite Health Scoring** — Custom weighted model

## Security

- Passwords stored as bcrypt hashes (never in plaintext)
- Session cookies with httpOnly flag
- 24-hour session expiry
- Change `SESSION_SECRET` to a long random string in production

## Tech Stack

- **Backend**: Node.js + Express
- **Auth**: express-session + bcryptjs
- **Charts**: Chart.js 4.4
- **Fonts**: Playfair Display + DM Mono (Google Fonts)
- **Deployment**: Railway

## Customization

To update spending categories, edit the `data.spending` array in `public/index.html`:
```js
{ category: 'Housing', amount: 1800, color: '#c9a84c', type: 'need' }
```

Types: `'need'` or `'want'` — drives 50/30/20 classification.
