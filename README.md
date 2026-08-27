# Stylus Mini-Apps on Arbitrum · Final Report

Milestone 4 of [WakeUp Labs](https://wup.ar)' grant under **Developer Tooling on Arbitrum One and Stylus 3.0**: [Validating Stylus in Production: Open-Source Mini-Apps on Arbitrum Mainnet](https://questbook.app/dashboard/?proposalId=68fac3fe96f32ac6ce9a3522&grantId=67d802bd46da2f90cc3267b0&chainId=10).

The grant asked for three production Mini-Apps in Stylus, then a closing write-up. This repo is that write-up. It is not another app. It is the measured record of what shipped, what broke, and what we would tell the Stylus / Arbitrum team next.

**[Read the full report (PDF)](docs/informe-final-stylus.pdf)**

## What this report is

Questbook Milestone 4 asked for:

- a summary of insights across all three Mini-Apps
- qualitative findings on Stylus performance, integration patterns, and mainnet-readiness

The PDF covers architecture and on-chain status for each app, then the cross-cutting findings: the one-fragment mainnet WASM gate, size levers, activation cost, gas, `eth_estimateGas` under-reporting Stylus→EVM calls, Permit2 / ERC-1271, Lemon `callSmartContract`, verification of `-Zbuild-std` builds, and the missing fork-testing story. Every figure traces to a source document. Nothing here is estimated.

## The three Mini-Apps

The original backlog named a Tamagotchi-style game, an ERC-4626 vault router, and a DEX aggregator. What shipped, in the order of the public series:

| | Mini-App | What it is | Where |
| --- | --- | --- | --- |
| 1 | **BananitaSwap** | USDC↔token swap through Camelot V3 and Uniswap V3. Stylus router plus adapters, hosted in Lemon. | [Part 1](https://wup.ar/blog/building-production-applications-arbitrum-stylus-part-1-dex-aggregation) |
| 2 | **CoinFlip** | Asynchronous randomness pattern: Stylus core, Chainlink VRF v2.5, locked-liability accounting, permissionless refund. | [Repo](https://github.com/wakeuplabs/ArbitrumMiniApp-2-verifiable-randomness) · [Part 2](https://wup.ar/blog/production-patterns-arbitrum-stylus-part-2-verifiable-randomness) |
| 3 | **Vaulty** | USDC yield aggregator. One deposit splits across Aave, Morpho, Fluid, and Euler (the production shortlist; Beefy did not ship). | [Repo](https://github.com/wakeuplabs/ArbitrumMiniApp-3-Vaulty) · [Part 3](https://wup.ar/blog/production-patterns-arbitrum-stylus-part-3-vault-aggregation) |

BananitaSwap and Vaulty are live on Arbitrum One. CoinFlip is live on Arbitrum Sepolia; the Arbitrum One deploy was deferred by client decision. Addresses, sizes, and receipts are in the PDF.

## Grant shape

Four milestones, same deliverable shape on the first three (mainnet Mini-App, listing, public repo, video set, blog post), then this report:

1. Mini-App #1
2. Mini-App #2
3. Mini-App #3
4. Final report (this repo)

Program: [Developer Tooling on Arbitrum One and Stylus 3.0](https://questbook.app/dashboard/?proposalId=68fac3fe96f32ac6ce9a3522&grantId=67d802bd46da2f90cc3267b0&chainId=10) on Questbook.
