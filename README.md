# Tomix Web — Official Website & Licensing Server

Official website and backend licensing service for [Tomix](https://github.com/rub1-618/Tomix---AI-voice-Assistant) — a personal AI voice assistant with a cyberpunk aesthetic.

---

## What's Here

| Part | Description |
|------|-------------|
| **Landing page** | Download, screenshots, features overview |
| **Profile page** | User registration, login, license key display |
| **Community page** | Plugin showcase and submission |
| **FastAPI backend** | User auth, license validation, plugin management |

---

## Tech Stack

**Backend:** Python · FastAPI · SQLAlchemy · SQLite · Passlib (bcrypt)  
**Frontend:** Vanilla HTML/CSS/JS · Canvas API · Intersection Observer  
**Hosting:** Raspberry Pi 3B+ · nginx · uvicorn · systemd

---

## API

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/register` | Create account + receive free license key |
| POST | `/login` | Authenticate; returns plan & license key |
| GET | `/validate?key=&hwid=` | Validate license + bind hardware ID |
| GET | `/plugins` | List verified community plugins |
| POST | `/plugins` | Submit a plugin for review |

---

## Running Locally

```bash
pip install fastapi sqlalchemy "passlib[bcrypt]" uvicorn
uvicorn main:app --reload
```

Database (`tomix.db`) is created automatically on first run.

---

## Deployment

Files are served from `/home/alan/site/` on the Pi:
- **nginx** — static files (HTML/CSS/JS/images)
- **uvicorn** on port 8000 — FastAPI backend
- **systemd** service name: `tomix`

---

## Related

- [Tomix Desktop App](https://github.com/rub1-618/Tomix---AI-voice-Assistant) — the voice assistant itself (Python + Rust + Flet)
