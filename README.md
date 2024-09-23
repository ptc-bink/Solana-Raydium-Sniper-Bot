# Solana Raydium Sniper Bot

This **Solana Raydium Sniper Bot** is designed to listen for new Raydium USDC or SOL liquidity pools and automatically buy tokens for a fixed amount in USDC or SOL. Thanks to its speed, the bot often executes trades before tokens are available on the Raydium UI for swapping. While this version is free, it can still generate consistent profits—potentially several hundred dollars per day—depending on market conditions and RPC node performance.

> **Note**: Keep in mind that gas fees are paid in SOL, so even for test runs, it’s recommended to maintain enough SOL in your wallet. A suggested configuration is 0.9 SOL for gas fees and 0.1 WSOL for trading.

For more features or to access a premium version, feel free to reach out via the Telegram link at the bottom of this document.

### Key Features:
- **WSOL Sniping**: Automatically purchase new tokens using WSOL.
- **Auto-Sell**: Automatically sell tokens after purchasing.
- **Take Profit (TP) / Stop Loss (SL)**: Automatically sell based on profit/loss thresholds.
- **Minimum Liquidity Check**: Buy tokens only if they meet minimum liquidity requirements.
- **Burn/Lock Checks**: Ensure the token's liquidity is not burned or locked.
- **Renounce Check**: Buy tokens only if mint authority has been renounced.
- **Fast Buy**: Prioritize speed in purchasing new tokens.

---

## Setup Instructions

### 1. Download the Repository
Clone the repository to your local machine or download the ZIP file:
```bash
git clone https://github.com/AhmedRabby2002/Solana-Raydium-Sniper-Bot.git
```
Alternatively, click the green **Code** button on GitHub and select **Download ZIP**.

### 2. Install Node.js
Ensure you have [Node.js](https://nodejs.org/en) installed on your system.

### 3. SOL/WSOL Setup
Convert some SOL into WSOL for trading. Even during testing, ensure you have sufficient SOL for transaction fees. A good starting ratio is 10 SOL to 1 WSOL, with `QUOTE_AMOUNT=0.1`.

- Use **Jupiter Wrap** to convert SOL to WSOL: [Jupiter Wrap](https://jup.ag)

### 4. Configure the Bot
- Open the `.env.copy` file and update the values, then remove `.copy` from the file name.
- Key configurations:
  - `PRIVATE_KEY`: Your wallet’s private key.
  - `RPC_ENDPOINT`: Your HTTP RPC endpoint.
  - `RPC_WEBSOCKET_ENDPOINT`: Your WebSocket RPC endpoint.
  - `QUOTE_MINT`: Use WSOL by default for trades.
  - `QUOTE_AMOUNT`: Set the amount for purchasing new tokens.
  - `COMMITMENT_LEVEL`: Leave as is for most use cases.
  - `CHECK_IF_IS_BURNED` & `CHECK_IF_IS_LOCKED`: Ensure the liquidity pool is not burned or locked.
  - `MIN_POOL_SIZE`: Define a minimum liquidity size to filter out low-liquidity pools.
  - `TAKE_PROFIT`: Percentage profit at which tokens should be sold (default: 50%).
  - `STOP_LOSS`: Percentage loss at which tokens should be sold (default: 30%).

Refer to the `.env` file for detailed instructions.

---

## Installation

1. Install the required dependencies:
```bash
npm install
```

2. Run the bot:
```bash
npm run start
```

---

## Auto-Sell Feature

By default, the bot will automatically sell tokens after purchase. You can adjust the following settings:

- **AUTO_SELL**: Set to `false` to disable auto-sell.
- **MAX_SELL_RETRIES**: Define the number of attempts for selling.
- **AUTO_SELL_DELAY**: Set the delay (in milliseconds) before attempting to sell.

> **Note**: If `AUTO_SELL_DELAY` is set to 0, the bot will attempt to sell the token immediately after purchase. There is no guarantee the token will be sold at a profit or sold at all.

---

## Snipe List Configuration

By default, the bot buys any token with a newly created liquidity pool. If you want to target specific tokens, use the snipe list feature:

1. Set `USE_SNIPE_LIST` to `true`.
2. Add the mint addresses of the tokens you want to buy in the `snipe-list.txt` file (one per line).

The bot will buy only tokens listed in the file. You can update the list in real-time; the bot checks for new tokens at intervals defined by `SNIPE_LIST_REFRESH_INTERVAL`.

---

## Common Issues & Fixes

- **Empty Transactions**: If you notice empty transactions on SolScan, try changing the `COMMITMENT_LEVEL` to `finalized`.
  
- **Unsupported RPC Node**: If you encounter a `410 Gone` error, your RPC node doesn't support the required methods. Try using alternatives like [Shyft](https://shyft.network), [Helius](https://www.helius.dev/), or [Quicknode](https://www.quicknode.com/).

- **Missing Token Account**: If your wallet doesn’t have a WSOL account, swap some SOL for WSOL via a decentralized exchange (DEX).

---

## Contact & Support

If you encounter any issues not covered here, please open a new issue on this GitHub repository.

- **Discord**: `@ptcbink`

---

## Disclaimer

> **Important**: Use this bot at your own risk. The developer is not responsible for any losses incurred.

---

This version enhances clarity, adds structure to sections, and improves overall readability while maintaining the original information.
