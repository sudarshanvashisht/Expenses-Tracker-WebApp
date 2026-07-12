# 🐳 Dockerized Expenses Tracker (Spring Boot + MySQL)

![Docker](https://img.shields.io/badge/docker-%230db7ed.svg?style=for-the-badge&logo=docker&logoColor=white)
![Java](https://img.shields.io/badge/java-%23ED8B00.svg?style=for-the-badge&logo=openjdk&logoColor=white)
![Spring Boot](https://img.shields.io/badge/spring%20boot-%236DB33F.svg?style=for-the-badge&logo=springboot&logoColor=white)
![MySQL](https://img.shields.io/badge/mysql-%2300f.svg?style=for-the-badge&logo=mysql&logoColor=white)

## 📌 Project Overview
This repository demonstrates the containerization of a monolithic Java Spring Boot application utilizing a MySQL database backend. 

**Infrastructure & DevOps Implementation:**
While the base Spring Boot application code was originally authored by [Mohamed ElSawy (mohamed0sawy)](https://github.com/mohamed0sawy/Expenses-Tracker-WebApp), my technical focus for this repository was exclusively on the **containerization, orchestration, and database networking**. I reverse-engineered the application's environment requirements to build a highly optimized, production-ready Docker deployment.

## 🏗️ Architecture & DevOps Features
* **Multi-Stage Dockerfile:** Engineered a two-stage build process. Stage 1 utilizes Maven to compile the application and run dependencies, while Stage 2 strips out the build tools and runs the resulting `.jar` file on a lightweight `eclipse-temurin:17-jre-alpine` image to drastically reduce container size and attack surface.
* **Race Condition Mitigation:** Implemented precise `healthcheck` and `depends_on` protocols within `docker-compose.yml` to ensure the Java application waits in a pending state until the MySQL database is fully initialized and actively accepting connections.
* **Modern JDBC Security:** Handled MySQL 8.x+ `caching_sha2_password` security protocols by configuring specific public key retrieval flags within the isolated Docker bridge network.
* **Volume Persistence:** Configured host-mapped Docker volumes to ensure the `expenses_tracker` database survives container restarts and teardowns.

## 🚀 Local Setup & Installation

### Prerequisites
* Docker & Docker Compose installed.
* Git.

### Deployment

**1. Clone the repository:**
```bash
git clone [https://github.com/sudarshanvashisht/Expenses-Tracker-WebApp.git](https://github.com/sudarshanvashisht/Expenses-Tracker-WebApp.git)
cd Expenses-Tracker-WebApp
2. Spin up the environment:

Bash
docker compose up -d --build
3. Access the application:
Navigate to http://localhost:8080 in your web browser.

4. Shut down the environment safely:

Bash
docker compose down
👨‍💻 About the Developer
Sudarshan Vashisht

Developer focused on software infrastructure, deployment architecture, and backend operations.
## License
This project is licensed under the MIT License.
