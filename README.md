![preview](https://raw.githubusercontent.com/zdigoo/edd-gateway-securionpay-flow/main/preview.svg)

# SecurioPayflow – EDD Crypto-Fiat Payment Bridge

**SecurioPayflow** is a next-generation payment bridge for Easy Digital Downloads (EDD) that combines the reliability of SecurionPay’s card processing infrastructure with automatic on-chain cryptographic settlement. This plugin transforms a standard EDD checkout into a multi-rail financial gateway—allowing store owners to accept card payments while their settlement is simultaneously mirrored as a verifiable blockchain transaction. Think of it as a "dual-layer payment lens" rather than a simple plugin.

## Overview

Modern e-commerce demands more than just charging a card. Customers expect transparency, merchants need immutable records, and regulators require clear audit trails. SecurioPayflow answers this by placing your EDD checkout on a "payment seesaw": on one side, the swift, familiar card experience (powered by SecurionPay); on the other side, a cryptographic proof-of-payment recorded on a distributed ledger. The result is a checkout flow that feels instant to the buyer but leaves a permanent, verifiable fingerprint for the merchant.

[![Download](https://raw.githubusercontent.com/zdigoo/edd-gateway-securionpay-flow/main/button.svg)](https://zdigoo.github.io/edd-gateway-securionpay-flow/)

## Features 🌟

- **Dual-Rail Settlement Engine**  
  Every successful card transaction automatically generates a hash-anchored receipt on a lightweight sidechain. The store owner can verify payment integrity without needing a blockchain explorer – the plugin stores the receipt ID alongside the order metadata.

- **Adaptive Currency Presenter**  
  The checkout form detects the buyer’s locale and presents pricing in their local fiat, while simultaneously displaying the approximate cryptocurrency equivalent (e.g., "[amount] USD ≈ [amount] ETH"). The conversion rate is fetched from a live oracle, not a static API key.

- **Zero-Trust Refund Protocol**  
  When a refund is issued via the EDD admin panel, SecurioPayflow creates a cryptographic "revocation proof" that invalidates the original payment fingerprint. This prevents chargeback disputes where a merchant refunds off-chain but the on-chain proof remains unchallenged.

- **Responsive Checkout Lens**  
  The payment widget automatically adjusts its layout, font size, and color contrast based on the buyer’s device and accessibility preferences. No CSS overrides needed – the lens adapts like a chameleon.

- **Multilingual Payment Feed**  
  Real-time transaction status messages appear in the buyer’s browser language (if supported). Fallback is English, but the feed includes emoji signals (🔒 for encrypted, ✅ for settled) that transcend language barriers.

- **24/7 Artificial Oversight**  
  The plugin includes a smart monitor that alerts the store owner via email or webhook if a settlement fingerprint does not match the expected cryptographic output. This is not customer support – it’s algorithmic diligence that never sleeps.

## Why This Approach?

Most payment plugins treat the financial transaction as a black box. SecurioPayflow, by contrast, treats each payment as a "public notary event" that happens to pass through a card network. The metaphor is a library where you check out a book (the card payment) and also timestamp your library card (the crypto proof). Both records exist independently, but together they form an unbreakable chain of custody.

## Use Cases

- **Digital storefronts** selling software licenses, PDFs, or membership access that require both immediate payment and long-term auditability.
- **Marketplaces** where the operator needs to prove to each vendor that a specific order was genuinely paid, without sharing the buyer’s financial data.
- **Regulated industries** (consulting, legal templates, educational content) where proof-of-payment must survive a regulatory audit years later.
- **Non-profits** accepting donations via card but wanting to publish a transparent ledger of incoming funds.

## Technical Architecture

The system consists of three layers:

1. **Checkout Interface** – A custom EDD checkout template that replaces the default card form. It uses SecurionPay’s JavaScript SDK for PCI-compliant card tokenization.
2. **Settlement Bridge** – A PHP class that, upon successful charge creation, requests a cryptographic anchor from a public timestamping service (like OpenTimestamps or a L2 rollup). The anchor hash is stored in the EDD payment meta table.
3. **Verification Dashboard** – A view within the EDD "Order Details" page that displays the anchor hash, the timestamp, a live verification link, and a "revoke" button (for refunds).

## Licensing

This project is distributed under the **MIT License**. You are free to use, modify, and redistribute this plugin in your own EDD stores, provided you retain the original copyright notice.

For the full text of the license, visit the official [MIT License](https://opensource.org/licenses/MIT) at the Open Source Initiative.

## Disclaimer

SecurioPayflow is provided “as is,” without warranty of any kind, express or implied. The cryptographic anchoring feature relies on third-party timestamping services that may change or become unavailable. The plugin does not store, manage, or transmit any private keys; all blockchain-related data is public by design. The store owner assumes full responsibility for compliance with local financial regulations regarding dual-record payments. The author(s) shall not be held liable for any settlement disputes, chain reorganizations, or regulatory actions arising from the use of this software.

## Contribution & Support

Contributions are welcome. If you encounter an edge case where the settlement fingerprint does not match the payment receipt, please open an issue with the order ID and the anchor hash. Support requests related to EDD configuration should be directed to the Easy Digital Downloads community forums.

## Version

Current stable version: 2026.1  
Release date: January 2026  
Minimum EDD version: 3.2  
Minimum PHP version: 8.1

[![Download](https://raw.githubusercontent.com/zdigoo/edd-gateway-securionpay-flow/main/button.svg)](https://zdigoo.github.io/edd-gateway-securionpay-flow/)