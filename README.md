<div align="center">
  <h1>Ephemeral</h1>
  
  <p>
    <strong>A decentralized, stateless, and end-to-end encrypted peer-to-peer communication protocol.</strong>
  </p>
  
  <p>
    <a href="https://zrnge.github.io/p2p-chat"><img src="https://img.shields.io/badge/Live_Environment-zrnge.github.io-blue?style=for-the-badge&logo=github" alt="Live Demo"></a>
    <img src="https://img.shields.io/badge/Cryptography-AES--GCM%20%7C%20ECDH-green?style=for-the-badge&logo=lock" alt="Cryptography">
    <img src="https://img.shields.io/badge/Transport-WebRTC-orange?style=for-the-badge&logo=webrtc" alt="WebRTC">
    <a href="LICENSE"><img src="https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge" alt="License: MIT"></a>
  </p>
</div>

## 🌐 Overview

Ephemeral is an industry-grade, serverless communication platform designed with absolute privacy and anonymity as its core tenets. Operating entirely within the client's browser, Ephemeral leverages WebRTC Data Channels to establish direct, peer-to-peer (P2P) connections. 

By eliminating centralized infrastructure, Ephemeral ensures that no intermediate servers ever process, log, or route your communications.

Built by **Zrnge**.

## 🛡️ Privacy vs. Anonymity

Traditional messaging applications rely on centralized servers that inherently track metadata, IP addresses, and user behavior. Ephemeral is built differently to provide **100% Privacy**:

- **Absolute Statelessness**: There are no databases, no user accounts, and no authentication logs. Your identity does not exist on our system.
- **Zero Metadata Retention**: Because the connection is purely P2P, there is no central server routing your messages. We cannot see who you are talking to, when you are talking, or how much data you are sending.
- **Total Ephemerality**: Conversations exist exclusively in volatile memory (RAM). The moment the application is closed or the session is terminated, the cryptographic keys are destroyed, and the conversation ceases to exist permanently.
- **Decentralized Signaling**: Initial Session Description Protocol (SDP) payloads are exchanged completely out-of-band (via QR code or manual copy-paste), ensuring that the initial handshake cannot be intercepted by a centralized signaling server.

> [!WARNING]
> **Anonymity Notice & IP Leakage**
> While Ephemeral guarantees 100% **privacy** (no one can decrypt your messages), it does NOT guarantee 100% **anonymity**. Because WebRTC establishes a direct Peer-to-Peer connection, **your public IP address is exposed to the person you are chatting with**. 
> 
> If strict anonymity from your peer is required, it is highly recommended to route your traffic through a **VPN** or the **Tor Network** before establishing the connection.

## 🔐 Cryptographic Architecture

Ephemeral employs military-grade cryptography to secure the P2P transport layer against eavesdropping and Man-In-The-Middle (MITM) attacks.

- **Key Exchange**: Elliptic Curve Diffie-Hellman (ECDH) over the NIST P-256 curve is used to securely negotiate a shared secret between peers.
- **Key Derivation**: The negotiated secret is processed via HMAC-based Extract-and-Expand Key Derivation Function (HKDF) utilizing SHA-256 to generate the session key.
- **Authenticated Encryption**: All payloads (text and files) are encrypted using AES-256-GCM. A fresh, cryptographically secure 12-byte Initialization Vector (IV) is generated for every transmission.
- **Forward Secrecy**: Keys are generated locally per session and never touch persistent storage.
- **Out-of-Band Authentication**: The protocol provides a visual "Safety Number" fingerprint (derived from the public keys) to mutually authenticate the connection and prevent active interception.

## ✨ Technical Features

- **Direct P2P Architecture**: True zero-trust, serverless infrastructure.
- **Encrypted File Transfer**: Seamlessly transmit files up to 250KB over the encrypted tunnel.
- **Strict Payload Validation**: Automated mitigation against DOM-based Cross-Site Scripting (XSS) and protocol injection vectors via rigorous Data URI filtering.
- **Responsive UI/UX**: A state-of-the-art glassmorphic interface optimized for both desktop and mobile environments.
- **Offline Resilience**: Capable of operating entirely over local network signaling without external dependencies.

## 🚀 Deployment & Usage

### Local Environment
To audit or run the environment locally:
```bash
git clone https://github.com/zrnge/p2p-chat.git
cd p2p-chat
npx http-server -p 8080
```

### Connection Flow
1. **Initialize**: The Host initiates a session, generating a localized SDP offer encoded as a QR payload.
2. **Scan**: The Peer scans the QR code (or processes the text payload), generating an SDP answer.
3. **Acknowledge**: The Host scans the resulting answer.
4. **Establish**: The WebRTC tunnel is authenticated and the encrypted channel opens.

## ⚖️ Legal & Liability Disclaimer

This software is provided "as is", without warranty of any kind, express or implied, including but not limited to the warranties of merchantability, fitness for a particular purpose, and non-infringement. In no event shall the authors or copyright holders (Zrnge) be liable for any claim, damages, or other liability, whether in an action of contract, tort, or otherwise, arising from, out of, or in connection with the software or the use or other dealings in the software. Users are solely responsible for ensuring their communications comply with applicable local laws and regulations.

---
<div align="center">
  <p>Built with ❤️ by <strong>Zrnge</strong></p>
  <p>
    <a href="https://github.com/zrnge/p2p-chat">Repository</a> • 
    <a href="https://zrnge.github.io/p2p-chat">Live Environment</a>
  </p>
</div>
