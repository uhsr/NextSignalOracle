# NextSignalOracle: Decentralized Crypto Price Alerts for Automated Trading

NextSignalOracle is a decentralized system designed to provide low-latency crypto price alerts, enabling automated trading strategies. It achieves this by aggregating on-chain price data from multiple decentralized exchanges (DEXs) and using smart contracts to trigger webhook notifications when predefined price thresholds are breached. This system offers a trustless and highly reliable alternative to centralized price alert services, minimizing reliance on single points of failure and maximizing transparency. By leveraging the power of the blockchain, NextSignalOracle ensures that price data is tamper-proof and auditable, providing users with confidence in the integrity of the alerts they receive.

The core of NextSignalOracle lies in its smart contract architecture. These contracts continuously monitor the aggregated price feeds and compare them against user-defined price levels. When a price breach occurs, the smart contract initiates a pre-configured webhook, sending a notification to a designated endpoint. This allows traders to react instantly to market movements, executing buy or sell orders through automated trading bots. The system supports various price conditions, including above, below, and within a range, giving users granular control over their alert parameters. Furthermore, the platform is designed to be modular and extensible, allowing for the integration of new DEXs and notification channels in the future.

This repository contains the complete source code for the NextSignalOracle system, including the smart contracts, data aggregation scripts, and API endpoints for managing price alerts. We aim to provide a robust and user-friendly solution for developers and traders who want to leverage decentralized price data for automated trading strategies. The code is written in TypeScript and Solidity, ensuring type safety and maintainability. By open-sourcing this project, we hope to foster collaboration and innovation within the decentralized finance (DeFi) community, contributing to the development of more efficient and transparent trading systems.

## Key Features

*   **Decentralized Price Aggregation:** Aggregates price data from multiple on-chain DEXs, mitigating the risk of price manipulation and ensuring accurate price representation. Data is fetched using custom TypeScript scripts that interact directly with DEX APIs.
*   **Smart Contract-Triggered Webhooks:** Utilizes Solidity smart contracts to monitor price feeds and automatically trigger webhook notifications when specified price thresholds are met. The smart contract logic includes error handling and gas optimization techniques to ensure reliable and cost-effective operation.
*   **Low-Latency Alerts:** Designed for minimal delay between price breach and notification, crucial for time-sensitive trading strategies. Achieved through optimized smart contract execution and efficient webhook delivery mechanisms.
*   **Configurable Price Conditions:** Supports a range of price conditions, including above, below, and within a range, providing flexibility for various trading strategies. These conditions are defined as parameters within the smart contract.
*   **Webhook Management API:** Includes a REST API for creating, managing, and deleting price alerts. The API is built using Node.js and Express, providing a simple and intuitive interface for interacting with the system.
*   **Auditable and Transparent:** All transactions and price data are recorded on the blockchain, providing a fully auditable and transparent record of price alerts.
*   **Modular and Extensible Architecture:** Designed for easy integration of new DEXs and notification channels, allowing for future expansion and customization. New data sources can be added by implementing a standard interface.

## Technology Stack

*   **TypeScript:** Used for developing the data aggregation scripts, API endpoints, and general application logic, providing type safety and improved code maintainability.
*   **Solidity:** The programming language for the smart contracts that monitor price feeds and trigger webhook notifications.
*   **Node.js:** A JavaScript runtime environment used for building the API endpoints and managing the overall system.
*   **Express:** A Node.js web application framework used for building the REST API.
*   **Web3.js/Ethers.js:** JavaScript libraries for interacting with the Ethereum blockchain.
*   **Hardhat/Truffle:** Development frameworks for compiling, testing, and deploying Solidity smart contracts.
*   **Ganache:** A personal blockchain for Ethereum development.

## Installation

1.  **Clone the repository:**
    `git clone https://github.com/uhsr/NextSignalOracle.git`
    `cd NextSignalOracle`

2.  **Install dependencies:**
    `npm install`

3.  **Install Hardhat (if not already installed):**
    `npm install --save-dev hardhat`

4.  **Compile smart contracts:**
    `npx hardhat compile`

5.  **Deploy smart contracts:**
    First, configure your environment variables (see Configuration section). Then, deploy the smart contracts using Hardhat:
    `npx hardhat deploy --network <network-name>` (e.g., `npx hardhat deploy --network rinkeby`)

6.  **Set up the API:**
    Navigate to the API directory and install dependencies:
    `cd api`
    `npm install`

## Configuration

The following environment variables need to be configured for the system to function correctly:

*   `PRIVATE_KEY`: The private key of the Ethereum account used for deploying contracts and triggering webhooks.
*   `INFURA_API_KEY`: Your Infura API key for connecting to the Ethereum network.
*   `ALCHEMY_API_KEY`: Your Alchemy API key (alternative to Infura).
*   `NETWORK`: The Ethereum network to connect to (e.g., "mainnet", "rinkeby", "goerli").
*   `CONTRACT_ADDRESS`: The address of the deployed smart contract.
*   `WEBHOOK_URL`: The URL of the endpoint to receive webhook notifications.

These variables should be stored in a `.env` file in the root directory and the `api` directory. Example `.env` content:

PRIVATE_KEY="0x"
INFURA_API_KEY="your_infura_api_key"
NETWORK="rinkeby"
CONTRACT_ADDRESS="0x"
WEBHOOK_URL="https://your-webhook-endpoint.com"

## Usage

1.  **Deploy the smart contract:** Deploy the compiled smart contract to your desired Ethereum network using Hardhat or Truffle. Note the contract address.

2.  **Configure the API:** Set the environment variables in the `api/.env` file. Ensure that the `CONTRACT_ADDRESS` matches the deployed smart contract address.

3.  **Run the API server:**
    `cd api`
    `npm start`

4.  **Interact with the API:** The API provides endpoints for creating, reading, updating, and deleting price alerts. Example API endpoint using `curl`:

    Create a new price alert:
    `curl -X POST -H "Content-Type: application/json" -d '{"pair": "ETH/USD", "threshold": 2000, "condition": "above"}' http://localhost:3000/alerts`

    API documentation (Swagger/OpenAPI) will be provided separately detailing all available endpoints and request/response formats.

## Contributing

We welcome contributions to NextSignalOracle! Please follow these guidelines:

1.  Fork the repository.
2.  Create a new branch for your feature or bug fix.
3.  Write clear, concise, and well-documented code.
4.  Submit a pull request with a detailed description of your changes.
5.  Ensure that all tests pass before submitting the pull request.

## License

This project is licensed under the MIT License. See the [LICENSE](https://github.com/uhsr/NextSignalOracle/blob/main/LICENSE) file for details.

## Acknowledgements

We would like to thank the open-source community for providing the tools and libraries that made this project possible.