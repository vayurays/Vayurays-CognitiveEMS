# CognitiveEMS — User Guide

> **Audience:** End users and operators who use CognitiveEMS in a web browser.
> **You do not need to install or configure anything** — your administrator runs the system. This guide explains how to sign in and use each screen.
>
> For installation, building, and configuration, see the **Complete Reference Guide** (`docs/CognitiveEMS-Complete-Reference.md`) and the **Installer guide** (`installer/README.md`).

---

## Table of Contents

1. [What CognitiveEMS Does](#1-what-cognitiveems-does)
2. [Signing In](#2-signing-in)
3. [Forgot / Reset Password](#3-forgot--reset-password)
4. [Getting Around (Layout & Navigation)](#4-getting-around-layout--navigation)
5. [User Roles & What You Can Do](#5-user-roles--what-you-can-do)
6. [First-Run Checklist](#6-first-run-checklist)
7. [Screen-by-Screen Guide](#7-screen-by-screen-guide)
   - [7.1 Dashboard](#71--dashboard)
   - [7.2 My Insights](#72--my-insights)
   - [7.3 Forecast](#73--forecast)
   - [7.4 Optimization](#74--optimization)
   - [7.5 Banking](#75--banking)
   - [7.6 Tariff](#76--tariff)
   - [7.7 Meters](#77--meters)
   - [7.8 SLDC](#78--sldc)
   - [7.9 Data Upload](#79--data-upload)
   - [7.10 Alerts](#710--alerts)
   - [7.11 Integration](#711--integration)
   - [7.12 Users (Admin)](#712--users-admin)
   - [7.13 Settings (Admin)](#713--settings-admin)
8. [Common Tasks (How Do I…?)](#8-common-tasks-how-do-i)
9. [Tips & Troubleshooting](#9-tips--troubleshooting)
10. [Glossary](#10-glossary)

---

## 1. What CognitiveEMS Does

CognitiveEMS is an AI-powered **Energy Management System** for industrial sites. It helps you:

- **Forecast** how much power your facility will need (in 15-minute slots) and how much your solar/wind plants will generate.
- **Optimize** which energy source to use at any moment — Solar, Wind, Battery, Grid, or Open Access — to lower cost.
- **Bank** surplus renewable energy (Open-Access banking) and withdraw it later.
- **Manage tariffs** (Time-of-Day rates) and compare DISCOM vs Open-Access costs.
- **Submit day-ahead schedules** to the SLDC and track deviations.
- **Monitor** live telemetry, alerts, and the health of external integrations.

A green **"Live ●"** indicator in the top bar shows the app is receiving live updates.

---

## 2. Signing In

1. Open the application URL in your browser (ask your administrator; a typical local install is `http://localhost:7072`).
2. Enter your **Username** and **Password**.
3. Click **Sign In**.

**Default administrator account** (created automatically on first install):

| Field | Value |
|---|---|
| Username | `admin` |
| Password | `Admin@123!` |

> Change the default password after first sign-in (an admin can do this from **Users → Reset PW**).

If your credentials are wrong, an error appears under the password box. After signing in you land on the **Dashboard**.

**Staying signed in:** your session is remembered if you refresh the page. The app silently renews your session in the background, so you normally won't be logged out while working. Click **Sign Out** (bottom of the sidebar) to end your session.

---

## 3. Forgot / Reset Password

1. On the sign-in screen, click **Forgot password?**
2. Enter your **email** and click **Send reset link**.
3. If email is configured and your account has that address, you'll receive a message with a reset link.
4. Open the link, choose a **new password** (minimum 8 characters), and confirm.

> If you don't receive an email, ask your administrator — they can reset your password directly from the **Users** screen.

---

## 4. Getting Around (Layout & Navigation)

The screen has three parts:

- **Sidebar (left):** the app logo, your username, and the navigation menu. The active page is highlighted in blue.
- **Top bar:** the title "Cognitive Energy Management" and the **Live ●** connection indicator.
- **Main area:** the content of the selected page.

**Navigation menu:**

| Menu item | What it's for |
|---|---|
| 📊 Dashboard | At-a-glance KPIs, charts, battery, and the latest optimization summary |
| 🔎 My Insights | Where your power came from, consumption patterns, and forecasts |
| 🔮 Forecast | Detailed load and renewable-generation forecasts |
| ⚡ Optimization | Run the dispatch optimizer and review cost savings |
| 🏦 Banking | Inject/withdraw banked energy and view transactions |
| 💰 Tariff | View tariff slots and compare DISCOM vs Open-Access costs |
| 🔌 Meters | Configure meters and their data sources |
| 📅 SLDC | Submit day-ahead schedules and view deviations |
| 📁 Data Upload | Upload consumption, generation, and battery data files |
| 🔔 Alerts | View and acknowledge system alerts (shows an unread count badge) |
| 🔗 Integration | Health of external integrations (weather, SLDC, SCADA, AI) |
| 👥 Users | *(Admin only)* manage users and roles |
| ⚙️ Settings | *(Admin only)* manage application settings and secrets |

The **🔔 Alerts** item shows a red badge with the number of unread alerts.

---

## 5. User Roles & What You Can Do

Every account has a **role**. Your role controls which actions you can take.

| Role | Typical use | Can do |
|---|---|---|
| **Admin** | System owner | Everything, including **Users**, **Settings**, tariff create/edit/delete, meter delete, and AI source configuration |
| **Operator** | Day-to-day operator | View all screens and perform operational actions (run optimization, banking, schedules, uploads, acknowledge alerts) |
| **Viewer** | Read-only / reporting | View dashboards and data |

> If a button is hidden or you see a message like *"Admin role required"*, your role doesn't permit that action. Ask an administrator.

---

## 6. First-Run Checklist

On a brand-new system there is little data yet. To see the app working end-to-end:

1. **Sign in** as `admin`.
2. Go to **⚡ Optimization** and click **📊 Seed 7-day Data**, then **💡 Seed Today** to generate realistic sample input. *(These buttons create demo data so you can explore — your administrator may replace this with real meter data.)*
3. Click **▶ Run Optimization** to compute a dispatch plan.
4. Return to **📊 Dashboard** — KPIs, the source mix, and the optimization summary now show values.
5. *(Optional, Admin)* Configure real meters under **🔌 Meters**, and add secrets (SMTP, weather keys) under **⚙️ Settings**.

---

## 7. Screen-by-Screen Guide

### 7.1 📊 Dashboard

Your home page — a live overview.

**KPI cards (top row):**
- **Est. Cost / Hour** — current estimated cost based on the AI optimization.
- **Savings vs Grid** — how much you're saving per hour vs using the grid only; also shows the recommended source.
- **Banking Balance** — your banked energy (kWh). Turns amber with a warning when it's close to expiry.
- **Active Alerts** — number of unread alerts, with the count of Critical ones.

**Charts:**
- **Energy Source Mix** — how power is currently split across sources.
- **Consumption Forecast** — predicted demand with a confidence band.

**Bottom row:**
- **🔋 Battery** — state of charge (SOC %) with a colored bar (red < 20%, amber < 30%, green otherwise) and the current charge/discharge action.
- **📋 Optimization Summary** — a plain-language summary of the latest dispatch recommendation.

> If you see *"No optimization data yet"*, follow the [First-Run Checklist](#6-first-run-checklist).

---

### 7.2 🔎 My Insights

A user-friendly view of **where your energy comes from** and how you use it.

- **Period buttons** (top-right): **Day / Week / Month** change the time window for all charts.
- **KPI cards:** Total Consumed, Renewable Share, Grid Dependence, and Power Bank (BESS) available energy with SOC and capacity.
- **Where my power came from** — a donut chart of Grid / Solar / Wind / Battery share.
- **Consumption pattern** — a stacked bar chart by hour/day/week.
- **Predicted consumption** — an AI/weather-driven demand forecast.
- **Expected renewable generation** — how much solar and wind your plants are forecast to produce in the next slots.
- **Banked energy (Open-Access)** — banked balance, injected/withdrawn today, and days to expiry.

This screen is **read-only** — it's for understanding, not for making changes.

---

### 7.3 🔮 Forecast

Detailed forecasting for planners.

- **Slots ahead** (top-right): choose how far to forecast — 8, 16, 24, 32, 48, or 96 slots (each slot = 15 minutes; the hours are shown in parentheses).
- **Meta row:** the forecast **Source**, whether it's **cached**, the **model version**, number of slots, and the **peak predicted** load.
- **Load Forecast** chart: the predicted kWh line with a shaded confidence band (upper/lower bound) and a dashed **"Now"** marker.
- **Renewable Generation Forecasts:** per plant, a chart comparing **Raw** predicted output vs **Available (after loss)** output.

If a forecast can't be produced live, the app shows the last cached result (marked **cached**).

---

### 7.4 ⚡ Optimization

Run the dispatch optimizer and review savings.

**Action buttons (top-right):**
- **📊 Seed 7-day Data** — inserts 7 days of realistic simulated history (demo input for the optimizer).
- **💡 Seed Today** — inserts today's simulated consumption, solar, and wind.
- **▶ Run Optimization** — computes the recommended dispatch plan now.

**When a result exists:**
- **Current Source Mix** — pie chart of Solar / Wind / Battery / Grid / Open Access percentages.
- **Dispatch Summary** — recommended source, battery action (and kW), predicted cost, baseline cost, **savings**, and the data source. A plain-language summary appears below.

**Cost Analysis:**
- Switch the period with **7d / 30d / 90d**.
- Shows Total savings, Savings %, Avg daily savings, Actual cost, and Baseline cost.

**Cost History (last 48 slots):** a bar chart comparing Baseline vs Actual cost over recent slots.

> If you see *"No optimization data yet"*, click **Seed 7-day Data → Seed Today → Run Optimization**.

---

### 7.5 🏦 Banking

Manage **Open-Access energy banking** — store surplus renewable energy and withdraw it later.

**Balance summary (top):**
- **Banked Balance** (kWh), **Injected Today**, **Withdrawn Today**, and **Expiry** (date and days left; turns amber/red as expiry nears).

**Inject Units** (store energy):
1. Enter **Units (kWh)**.
2. Enter the **Plant ID** (e.g. `SOLAR-001`).
3. Click **⬆ Inject**.

**Withdraw Units** (use banked energy):
1. Enter **Units (kWh)** and **Plant ID**.
2. Click **⬇ Withdraw**.
   - Withdraw is disabled when your balance is zero (a "No banked units available" note appears).

**Transaction History:** a paged table of every injection, withdrawal, expired units, running balance, banking fee %, plant, and expiry date.

A green/amber/red toast confirms each action or explains any error.

---

### 7.6 💰 Tariff

View Time-of-Day (ToD) tariff slots and compare costs.

**Active Tariff Slots** table: slot name, type (**Peak / Normal / Off-Peak**), time window, DISCOM rate (₹), OA wheeling charge, cross-subsidy surcharge, PPA rate, ToD surcharge, and effective dates.

**Cost Comparison Calculator:**
1. Enter a **Consumption (kWh)** value.
2. The app instantly shows **DISCOM cost**, **Open Access cost**, and your **OA saving** (green when you save, red when OA is more expensive).

**Admin only — managing tariffs:**
- Click **+ New Tariff** to open the form. Fill slot name, type, start/end time, rates and surcharges, and effective-from/-to dates, then click **💾 Save**.
- Use **Edit** / **Delete** in the table to change or deactivate a slot. (Delete deactivates the slot rather than erasing history.)

---

### 7.7 🔌 Meters

Define your meters and where their readings come from. (This is mainly an **Admin/Operator** screen; deleting meters and saving AI config require **Admin**.)

**Meters table:** name, type (Power / Solar / Wind / BESS), data source, data type, tariff, SCADA point, formula, last reading, active state, and per-row actions.

**Create or edit a meter** — click **+ New Meter** (or **Edit**) and fill:
- **Meter Name**, optional **Description**.
- **Meter Type:** Power, Solar, Wind, or BESS.
- **Data Type** (required) and an optional **Tariff**.
- **Interval (seconds)** — how often readings arrive (default 900 = 15 min).
- **Active** checkbox.
- **Data Source** — this changes the rest of the form:

| Source | Meaning | Extra fields |
|---|---|---|
| **Manual** | You upload/post readings yourself | none |
| **VayuRays SCADA** | Live readings from a VayuRays SCADA point | pick a **SCADA Point** (or type the point identifier) |
| **External API** | Pull from a third-party meter API | **API Endpoint** and optional **API Config (JSON)** |
| **Formula (virtual)** | A calculated meter built from other meters | the **Formula Builder** |

**Formula Builder** (for Formula meters): compose an expression by inserting other meters as tokens (e.g. `M1`), numbers, and the operators `+  −  ×  ÷` with parentheses — for example `M1 + 10*M2`, `5*(M1-M2)`, or `M1*10`. The builder validates your expression live and shows a human-readable preview.

**Row actions:**
- **Edit** — change the meter.
- **Sync VayuRays** — (VayuRays meters) pull the latest SCADA readings now; a toast reports how many were saved.
- **Recompute** — (Formula meters) recalculate the virtual meter from its inputs.
- **Delete** — *(Admin)* remove the meter.

**AI Source Configuration** (bottom, save requires **Admin**): map each AI role — **Power, Solar, Wind, BESS** — to a specific meter so forecasts and optimization use your real meters. Leave a role as **None (legacy)** to fall back to the built-in data sources. Click **Save AI Config**.

---

### 7.8 📅 SLDC

Submit **day-ahead** Open-Access schedules to the State Load Dispatch Centre and track how actual draw deviated from plan.

**Submit Day-Ahead Schedule:**
1. Choose a **Schedule date** — must be **tomorrow or later**.
2. *(Optional)* type a value in **Set all hours (kWh)** to fill every hour at once.
3. Adjust any of the **24 hourly blocks** (00:00–01:00 … 23:00–00:00) with the requested Open-Access units.
4. Click **📤 Submit Schedule**. A toast confirms submission.

**Filter bar:** pick a **From** and **To** date to filter the lists below.

**Submitted Schedules** table: date, hour, requested/approved/actual units, **Status** (Submitted / Approved / Rejected / Pending), submission time, and external schedule ID. Use the pager for more rows.

**Deviation Analysis:** when data exists, a chart compares **Scheduled vs Actual** per hour, plus the **deviation %**, with summary totals (total blocks and average deviation).

---

### 7.9 📁 Data Upload

Import meter data from files.

**Upload Meter Data:** three drop zones —
- **Consumption**
- **Generation**
- **Battery**

For each: **drag a file onto the zone** or click it to browse. Accepted formats are **`.xlsx`** and **`.csv`**. A progress bar shows upload status, and a toast confirms success or failure.

> For the exact column layout each file needs, see `docs/Data-Import-Format-Guide.md`.

**Import History:** a live table (refreshes automatically) of recent files with **File**, **Type**, **Status** (Completed / Failed / Processing / Pending), **Records** processed, and the upload time.

---

### 7.10 🔔 Alerts

See and clear system notifications (e.g. low battery, integration failures, deviations).

- **Filter chips:** **All / Unread / Critical / Warning / Info**.
- Each alert shows its **severity** (color-coded: Critical red, Warning amber, Info blue), **type**, **time**, and message. Acknowledged alerts are dimmed and show who acknowledged them.
- **✓ Ack** on an alert marks it read.
- **✓ Acknowledge All** clears every alert at once.

The list refreshes automatically, and the sidebar badge updates to reflect unread alerts.

---

### 7.11 🔗 Integration

Monitor the health of external systems CognitiveEMS talks to (weather providers, SLDC, DISCOM, SFTP, Python AI).

- **Summary row:** counts of **Healthy / Degraded / Unhealthy** integrations.
- **Provider cards:** each shows a **status badge** (Healthy / Degraded / Unhealthy), last success time, consecutive failures, recent call count, and success rate.
- A red warning appears on any provider that has failed 3+ times in a row — that's a cue to check the API key, network, or logs (or tell your administrator).

The page **auto-refreshes every 30 seconds**. *"No integration logs yet"* simply means the background services haven't run yet.

---

### 7.12 👥 Users (Admin)

*Visible to Admins only.* Manage who can sign in and what they can do.

**Users** table: username, full name, email, **role** (editable inline), **status** (Active/Inactive), last login, and actions.

- **+ New User** — enter username, role, email, full name, and an initial **password** (min 8 characters), then **Save**.
- **Edit** — change a user's name, email, or role.
- **Enable / Disable** — toggle whether the account can sign in.
- **Reset PW** — set a new password for the user (min 8 characters) in a popup.
- **Delete** — remove the account.

Change a user's role directly from the **Role** dropdown in their row (Admin / Operator / Viewer).

---

### 7.13 ⚙️ Settings (Admin)

*Visible to Admins only.* Store application settings and secrets such as the **SMTP password** (for password-reset emails) and **weather API keys**.

**All Settings** table: key, value, whether it's a **secret** (🔒), description, and last-updated time.

- **+ Add Setting** — enter a **Key** (e.g. `Email:Password`) and **Value**. Tick **Encrypt value (password/secret)** for sensitive values — secrets are stored encrypted and never shown in plain text.
- **Edit** — update a setting. For secrets, **leave the value blank to keep the current one**; type a new value only to replace it.
- **Delete** — remove a setting.

> Secret values configured here override the matching entries in the server's configuration file, so you can manage credentials without editing files.

---

## 8. Common Tasks (How Do I…?)

| I want to… | Go to | Do this |
|---|---|---|
| See current cost & savings | 📊 Dashboard | Read the KPI cards and Optimization Summary |
| Get a fresh dispatch recommendation | ⚡ Optimization | Click **▶ Run Optimization** |
| Try the app with sample data | ⚡ Optimization | **Seed 7-day Data → Seed Today → Run Optimization** |
| Store surplus renewable energy | 🏦 Banking | Enter units + plant, click **⬆ Inject** |
| Use banked energy | 🏦 Banking | Enter units + plant, click **⬇ Withdraw** |
| Compare grid vs Open-Access cost | 💰 Tariff | Enter kWh in the Cost Comparison Calculator |
| Add a calculated (virtual) meter | 🔌 Meters | **+ New Meter → Data Source: Formula**, build the expression |
| Submit tomorrow's OA schedule | 📅 SLDC | Set hourly blocks, click **📤 Submit Schedule** |
| Import a data file | 📁 Data Upload | Drag a `.csv`/`.xlsx` onto the matching drop zone |
| Clear notifications | 🔔 Alerts | **✓ Ack** one or **✓ Acknowledge All** |
| Add a user *(Admin)* | 👥 Users | **+ New User**, fill the form, **Save** |
| Store an API key / SMTP password *(Admin)* | ⚙️ Settings | **+ Add Setting**, tick **Encrypt value** |

---

## 9. Tips & Troubleshooting

- **"Live ●" is grey/red:** the app isn't receiving live updates. Wait a moment, or refresh — the server may be restarting.
- **A page shows "No … data yet":** there's simply no data for that period. For optimization, use the seed buttons; for forecasts and integrations, data appears after the background services run.
- **A button is missing or says "Admin role required":** your role doesn't allow that action — ask an administrator.
- **Dashboard shows a "Could not load optimization data" banner:** the API may still be starting up; the page auto-refreshes and the banner clears on its own.
- **Upload failed:** check the file is `.csv` or `.xlsx` and matches the format in `docs/Data-Import-Format-Guide.md`.
- **Didn't get a password-reset email:** email may not be configured — ask an admin to reset your password from **Users**.
- **You got logged out:** sign in again. Sessions renew automatically while you work, so this is rare.

---

## 10. Glossary

| Term | Meaning |
|---|---|
| **SOC** | State of Charge — how full the battery is, as a percentage |
| **BESS** | Battery Energy Storage System |
| **ToD** | Time-of-Day — electricity tariffs that change by time block (Peak/Normal/Off-Peak) |
| **DISCOM** | Distribution Company — your normal grid electricity supplier |
| **Open Access (OA)** | Buying power from the open market instead of the DISCOM |
| **Banking** | Storing surplus renewable energy with the grid to withdraw later |
| **SLDC** | State Load Dispatch Centre — approves day-ahead Open-Access schedules |
| **Wheeling charge** | Fee for transmitting Open-Access power over the grid |
| **Deviation** | Difference between the scheduled and actual energy drawn |
| **Slot** | A 15-minute time interval used for forecasting and optimization |
| **Dispatch** | The plan for which energy source to use at a given time |
| **Formula meter** | A virtual meter whose value is calculated from other meters |
| **SCADA** | The plant control system that provides live meter readings (via VayuRays) |

 Cognitive EMS Installer
https://drive.google.com/file/d/1IXFtc26hgzmnuMTMOXoJlS-vfhp2yMuH/view?usp=drive_link

 Vayurays Installer.
https://drive.google.com/file/d/1zpSzZZGY0iZ7VjZZvpDyrMTTlqsH5ylo/view?usp=drive_link
