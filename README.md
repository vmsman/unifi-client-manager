# UniFi Client Reservation Manager

A modern web-based management utility for UniFi Network environments that provides advanced visibility into clients, DHCP reservations, stale devices, and offline systems.

Designed for administrators who need significantly more visibility and cleanup capability than the default UniFi client interface provides.

---

# Features

- Real-time UniFi client inventory
- Online/offline client tracking
- DHCP reservation management
- Toggle fixed IP reservations
- Forget/remove UniFi clients
- Identify stale offline devices
- Identify stale reservations
- Offline aging indicators
- Search and filtering
- Wired/Wi-Fi identification
- Uplink port visibility
- Network/VLAN visibility
- CSV export support
- Keyboard navigation
- Dark modern responsive interface
- Lightweight Node.js + Docker deployment

---

# Screenshots

![UniFi Client Reservation Manager](https://raw.githubusercontent.com/scottibyte/unifi-client-manager/main/screenshots/unifi-client-manager-main.png)

---

# Docker Deployment

## Quick Start

```bash
docker run -d \
  --name unifi-client-manager \
  --restart unless-stopped \
  -p 3000:3000 \
  --env-file .env \
  scottibyte/unifi-client-manager:latest
```

---

# Docker Compose

```yaml
services:
  unifi-client-manager:
    image: scottibyte/unifi-client-manager:latest
    container_name: unifi-client-manager
    restart: unless-stopped

    ports:
      - "3000:3000"

    env_file:
      - .env
```

Start the container:

```bash
docker compose up -d
```

---

# Environment Variables

Create a `.env` file:

```env
UNIFI_BASE_URL=https://192.168.1.1
UNIFI_USERNAME=admin
UNIFI_PASSWORD=password
UNIFI_SITE=default
PORT=3000
POLL_INTERVAL_MS=15000
VERIFY_SSL=false
```

| Variable | Description |
|---|---|
| `UNIFI_BASE_URL` | URL of your UniFi controller or gateway |
| `UNIFI_USERNAME` | UniFi username |
| `UNIFI_PASSWORD` | UniFi password |
| `UNIFI_SITE` | UniFi site name |
| `PORT` | Web UI port |
| `POLL_INTERVAL_MS` | Client refresh interval |
| `VERIFY_SSL` | Verify SSL certificates (`true` or `false`) |

---

# Accessing the Application

Open your browser:

```text
http://YOUR_SERVER_IP:3000
```

---

# API Endpoints

| Endpoint | Purpose |
|---|---|
| `/api/health` | Health status |
| `/api/clients` | Full client list |
| `/api/export/reservations.csv` | Export reservations |
| `/api/debug/raw-clients` | Debug sample clients |

---

# Why This Utility Exists

The default UniFi client interface becomes difficult to manage in larger environments with:

- stale offline clients
- outdated DHCP reservations
- IoT device sprawl
- VLAN-heavy deployments
- hundreds of devices

This utility provides a fast operational view specifically designed for cleanup, auditing, and reservation management.

---

# Security

Credentials are supplied through Docker environment variables and are **not embedded into the container image**.

---

# Recommended Reverse Proxy

This container works well behind:

- NGINX Proxy Manager
- Traefik
- Caddy
- SWAG
- Cloudflare Tunnel

---

# Related Projects

- UniFi Statistics Dashboard
- UniFi Reservation Cleanup Utilities
- ScottiBYTE Incus Dashboard

---

# License

MIT License

---

# Author

ScottiBYTE Enterprise Consulting Services

YouTube:
https://youtube.com/@ScottiBYTE

Discussion Community:
https://discussion.scottibyte.com
