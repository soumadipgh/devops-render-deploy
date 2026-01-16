# DevOps Internship Task – BaronTechLab

This project is part of a DevOps practical assessment. The goal is to demonstrate containerization, CI/CD, reverse proxy configuration, and cloud deployment using a Django REST Framework application.

---

## 📌 Project Overview

The project is a simple Django REST API with one endpoint:

Endpoint:
/api/hello/

Functionality:
Returns a message stored in the database.

---

## 🧰 Tech Stack

- Django 5.x
- Django REST Framework
- SQLite
- Docker & Docker Compose
- Nginx (Reverse Proxy)
- GitHub Actions (CI/CD)
- Render (Cloud Deployment)

---

## 🏗 Architecture Overview

Client (Browser)
↓
Nginx (Docker Container)
↓
Gunicorn (Docker Container)
↓
Django REST API

- Nginx handles incoming requests and serves static files  
- Gunicorn runs the Django application  
- Docker Compose manages multi-container setup  
- GitHub Actions runs CI pipeline  
- Render hosts the deployed Docker app

---

## ▶️ How to Run Locally (Without Docker)

```bash
python -m venv venv
venv\Scripts\activate     # Windows

pip install -r requirements.txt
Create a  .env file:
SECRET_KEY=your-secret-key
DEBUG=True
Run migrations and start server:
python manage.py migrate
python manage.py runserver
Open:
http://127.0.0.1:8000/api/hello/

🐳 Run with Docker

Build and start containers:

docker compose up --build

Open in browser:

http://localhost/api/hello/

🔄 CI/CD Pipeline (GitHub Actions)

CI pipeline runs automatically on every push to main branch.

Pipeline steps:

Install dependencies

Run flake8 linting

Run Django tests

Build Docker image

Workflow file:
.github/workflows/deploy.yml

☁️ Deployment

The project is deployed using Render with Docker.

Environment variables used in production:

SECRET_KEY

DEBUG=False

https://devops-intern-task-86yy.onrender.com