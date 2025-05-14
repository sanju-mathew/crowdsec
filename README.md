# 🛡️ Integrating CrowdSec with Docker and Traefik in a Homelab

📖 **Read the full blog post here:** [https://homelab.sanjuprojects.uk/crowdsec-and-docker/](https://homelab.sanjuprojects.uk/crowdsec-and-docker/)

## 🔍 Overview

This guide outlines how to integrate **CrowdSec**, an open-source intrusion prevention system, with **Docker** and **Traefik** to enhance the security of self-hosted services in a homelab.

### Why CrowdSec?
- **Behavioral Detection**: Identifies suspicious behavior through log analysis.
- **Community Defense**: Shares and receives threat data globally.
- **Open-Source**: Transparent, extendable, and free.
- **Docker-Friendly**: Easily deployable via containers.

## 🔄 Integration with Traefik

CrowdSec analyzes logs and identifies malicious IPs, but it needs a "bouncer" to enforce bans. The `fbonalair/traefik-crowdsec-bouncer` Docker image serves this role by integrating with Traefik to block those IPs in real time.

## 🛠️ Key Integration Points

- CrowdSec reads logs (e.g., from Traefik) to detect brute-force, DDoS, and other attacks.
- The Traefik bouncer receives decision data from CrowdSec and blocks offending IPs dynamically.
- Logs should be mounted read-only to the CrowdSec container.
- Use `.env` or Docker secrets to manage sensitive variables like the API key.
- Place containers on a common external Docker network (e.g., `proxy`) for communication.

## 🔐 Security Best Practices

- Use `no-new-privileges:true` to prevent privilege escalation in containers.
- Mount only necessary log files with read-only permissions.
- Keep API keys and secrets out of version control using environment variables or secrets management.
- Regularly update your images to receive upstream security patches.

## 📂 Reference

- Blog Post: [https://homelab.sanjuprojects.uk/crowdsec-and-docker/](https://homelab.sanjuprojects.uk/crowdsec-and-docker/)

---
