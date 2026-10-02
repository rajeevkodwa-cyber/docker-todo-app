# 🐳 Docker Todo App (Flask + PostgreSQL)

A simple Todo List application built with **Flask** and **PostgreSQL**, fully containerized using **Docker** and orchestrated with **Docker Compose**. Deployed on **AWS EC2**.

## 🚀 Tech Stack

- **Backend:** Python (Flask)
- **Database:** PostgreSQL 15
- **Containerization:** Docker, Docker Compose
- **Hosting:** AWS EC2

## 📂 Project Structure

```
docker-todo-app/
├── app.py                 # Flask application
├── requirements.txt       # Python dependencies
├── Dockerfile              # Image build instructions
├── docker-compose.yml      # Multi-container orchestration
├── .gitignore               # Ignored files
└── templates/
    └── index.html            # Frontend template
```

## ✨ Features

- Add and view todo tasks
- Data persists in PostgreSQL using Docker volumes
- Fully isolated multi-container environment (App + DB)
- Health checks to ensure the database is ready before the app starts
- Auto-restart on failure or server reboot

## 🧰 Prerequisites

- [Docker](https://www.docker.com/) installed
- [Docker Compose](https://docs.docker.com/compose/) (bundled with Docker Desktop / `docker compose` plugin on Linux)

## ▶️ How to Run

1. Clone the repository
   ```bash
   git clone https://github.com/rajeevkodwa-cyber/docker-todo-app.git
   cd docker-todo-app
   ```

2. Create a `Dockerfile` and `docker-compose.yml` (see below) if not already present

3. Build and start the containers
   ```bash
   docker compose up -d --build
   ```

4. Open your browser and visit
   ```
   http://localhost:5000
   ```

5. To stop the app
   ```bash
   docker compose down
   ```

## 🏗️ Architecture

```
┌─────────────────┐       ┌──────────────────┐
│   Flask (web)      │ <---> │  PostgreSQL (db)    │
│   Port: 5000          │       │   Port: 5432           │
└─────────────────┘       └──────────────────┘
          |                           |
          └──────── Docker Network ────────┘
                 (created automatically by Compose)
```

- `web` and `db` run as **separate containers**
- They communicate over a Docker-managed internal network
- Database data is persisted using a **named volume** (`pgdata`), so data survives container restarts
- A **health check** ensures Postgres is fully ready before the Flask app starts

## 📖 What I Practiced

- Writing a `Dockerfile` to containerize a Python/Flask app
- Writing a `docker-compose.yml` to manage a multi-container application
- Container-to-container networking (Flask connects to Postgres using the service name `db`)
- Using Docker volumes for persistent database storage
- Adding health checks and `restart: always` for reliability
- Deploying a Dockerized app on an AWS EC2 instance
- Managing AWS Security Groups to allow public access on the required port

## 📌 Future Improvements

- Add delete/update functionality for todos
- Add a frontend framework (React) as a separate container
- Set up a custom domain with HTTPS via Nginx + Let's Encrypt
- Push the image to Docker Hub for faster deployments
- Add a CI/CD pipeline using GitHub Actions

---

### 🔗 Connect with me
Feel free to check out the code and reach out if you have any suggestions!
