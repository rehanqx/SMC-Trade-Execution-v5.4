# ⚡ Smart Money Concepts V5.4 — Trade Execution Engine (OMS / EMS)

![Pine Script Version](https://img.shields.io/badge/Pine_Script-v6-blue?style=for-the-badge&logo=tradingview)
![TradingView](https://img.shields.io/badge/TradingView-Indicator-00897B?style=for-the-badge&logo=tradingview)
![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)

An institutional-grade **Smart Money Concepts (SMC) Order Management System (OMS) & Execution Management System (EMS) Engine** written in **Pine Script v6** for TradingView.

V5.4 acts as the live execution bridge for the SMC ecosystem. It receives approved trade allocations from the V5.3 Position Sizing Engine and processes them through an OMS/EMS pipeline—enforcing real-time spread filters, slippage guards, latency health monitoring, and multi-channel routing (*MT5 EA Bridge, FIX Gateway, TradingView Webhook*).

---

## 🔥 Key Features

* **📡 OMS Multi-Channel Routing:** Connects validated setups to institutional execution gateways (`MT5 EA Bridge`, `FIX Gateway`, `TradingView Webhook`).
* **🛡️ EMS Spread & Slippage Protection:** Automatically blocks execution or issues warnings when live spread (`max_allowed_spread`) or slippage (`max_allowed_slippage`) exceeds configured thresholds.
* **⚡ Round-Trip Latency & Execution Quality Index:** Tracks simulated execution latency (in milliseconds) and calculates a comprehensive 0–100 Execution Quality Index (*Prime Execution, High Quality, Acceptable, Degraded, Failed*).
* **🔄 Execution Lifecycle Management:** Manages live trade fills through a 5-stage fill tracking state machine:
  `IDLE ➔ SUBMITTED ➔ FULL_FILL ➔ REJECTED ➔ CANCELLED`
* **📊 Master Execution Dashboard:** Real-time on-chart HUD displaying EMS fill statuses, routing channels, round-trip latency, active spread measurements, and order fill statistics.
* **🔌 Open Output API:** Standardized variable exports (`export_ExecutionID`, `export_OrderStatus`, `export_FillPrice`, `export_FillQuantity`, `export_ExecutionQuality`) engineered specifically for **Trade Management (V5.5)**, **Exit Management (V5.6)**, and **MT5 EA Bridge Integration**.

---

## 📊 Dashboard Overview

The built-in master execution HUD displays critical operational parameters:

| Metric | Description |
| :--- | :--- |
| **EMS Fill Status** | Live order fill state (*FULL_FILL, PENDING, REJECTED*) |
| **Execution Quality Score**| Multi-factor rating (0–100) combining spread, slippage, and latency |
| **OMS Routing Channel** | Active output channel (*MT5 EA Bridge, FIX Gateway, Webhook*) |
| **Execution Policy Mode**| Active execution policy (*Immediate, Delayed, Conditional*) |
| **Round-Trip Latency** | Simulated latency in milliseconds vs. `max_latency_ms` threshold |
| **Realtime Market Spread** | Live spread tracking in pips vs. `max_allowed_spread` limit |
| **Execution Slippage** | Real-time slippage measurement in pips |

---

## 🛠️ Configuration & Settings

### 1. OMS Order Management Settings
* `Execution Routing Channel` *(Default: MT5 EA Bridge)*: Target destination for order execution.
* `Execution Policy` *(Default: Immediate)*: Order submission mode (*Immediate, Delayed, Conditional*).
* `Default Order Type` *(Default: Market Order)*: Order structure selection (*Market, Limit, Stop*).

### 2. EMS Slippage & Spread Protection
* `Max Allowed Spread (Pips)` *(Default: 2.0 Pips)*: Maximum spread threshold before blocking orders.
* `Max Allowed Slippage (Pips)` *(Default: 1.5 Pips)*: Maximum tolerated execution slippage.
* `Max Latency Threshold (MS)` *(Default: 300 ms)*: Maximum acceptable execution delay.

### 3. Visual & Display Standards
* Toggles for On-Chart Execution Status Labels and the Master Execution Dashboard.
* Color coding for fill states: **FULL FILL** (Green), **WARNING** (Orange), and **REJECTED / BLOCKED** (Red).

---

## 💻 Installation & Usage

1. Open **[TradingView](https://www.tradingview.com)**.
2. Open the **Pine Editor** tab at the bottom of your workspace.
3. Create a new script, clear the default template, and paste the code from `SMC_Execution_Engine_v5_4.pine`.
4. Click **Save** and then select **Add to Chart**.

---

## ⚡ Real-Time Alerts Included

Includes native TradingView alert conditions for automated execution and webhook bots:
* ⚡ **Order Filled:** Fires immediately when an order is successfully executed.
* ⚠️ **Spread Limit Blocked:** Fires when live market spread exceeds safety limits.
* ⚠️ **Slippage Limit Exceeded:** Fires when execution slippage surpasses tolerance levels.


---

## 📜 License

This project is open-source and released under the [MIT License](LICENSE).
