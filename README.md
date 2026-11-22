CYBERGUARD AI

AI-Assisted Security Information and Event Management (SIEM) & Security Operations Center (SOC) Platform

<p align="center">
  <strong>Intelligent Security Monitoring • Threat Detection • Incident Response</strong>
</p>

CYBERGUARD AI is an advanced cybersecurity monitoring and incident response platform designed to help security analysts collect, monitor, investigate, and respond to security events from Linux systems and network environments.

The project combines Python, FastAPI, React, SQLite, Wazuh, Suricata, and optional AI-powered log analysis to provide a centralized security monitoring environment.

It is being developed as a modular cybersecurity project for defensive security research, SOC learning, and practical incident investigation.

1. Project Overview

Modern systems generate large volumes of security logs, making it difficult to identify suspicious activity and investigate potential threats manually.

CYBERGUARD AI aims to simplify this process by providing a centralized dashboard for:

Monitoring system and authentication logs.

Detecting suspicious activities and potential attacks.

Investigating security alerts.

Monitoring file integrity.

Analysing network security events.

Mapping detected threats to MITRE ATT&CK.

Managing security incidents.

Generating security assessment reports.

Supporting investigations with optional AI-assisted analysis.

The platform is designed to support both lightweight lab environments and expanded SOC deployments.

2. Key Features

Module

Description

Security Dashboard

Centralized overview of security events and alerts

Live Log Monitoring

Collects and displays supported system logs

Threat Detection

Rule-based detection of suspicious activities

AI Log Analysis

Optional AI-assisted security event explanations

Incident Management

Track, investigate, and resolve security incidents

Authentication Monitoring

Identify repeated login failures and suspicious authentication activity

File Integrity Monitoring

Detect changes to monitored files using cryptographic hashes

Network Monitoring

Analyse supported network security events

MITRE ATT&CK

Map relevant detections to ATT&CK techniques

Alert Management

Organize, prioritize, and investigate alerts

Security Reports

Export investigation results in supported formats

Wazuh Integration

Connect to Wazuh for centralized endpoint security monitoring

Suricata Integration

Ingest network detection events from Suricata

Feature availability depends on the development stage and configured integrations.

3. Technology Stack

Backend

Python

FastAPI

SQLAlchemy

Pydantic

SQLite

Frontend

React

Vite

Tailwind CSS

Recharts

Lucide Icons

Security Monitoring

Kali Linux

Wazuh

Suricata

Linux system logs

Systemd Journal

AI Integration

Optional Ollama or external AI provider

Rule-based analysis fallback

Development and Deployment

Git and GitHub

Docker and Docker Compose

Nginx

GitHub Actions

4. System Architecture

             CYBERGUARD AI
                   |
          React SOC Dashboard
                   |
             FastAPI Backend
                   |
       +-----------+-----------+
       |           |           |
   Detection    Incident    AI Analysis
    Engine      Management    (Optional)
       |
   Event Processing
       |
   +---+-------------------+
   |           |           |
 Linux Logs   Wazuh     Suricata
   |           |           |
   +-----------+-----------+
               |
          SQLite Database
               |
       Reports and Analytics

The lightweight profile uses local log sources and rule-based detection. An expanded deployment can integrate Wazuh and Suricata as external security monitoring services.

5. Project Structure

CYBERGUARD-AI/
│
├── backend/
│   ├── api/
│   ├── core/
│   ├── database/
│   ├── detection/
│   ├── integrations/
│   ├── reports/
│   └── main.py
│
├── frontend/
│   ├── src/
│   ├── public/
│   └── package.json
│
├── config/
├── data/
├── logs/
├── reports/
├── tests/
│
├── scripts/
│   ├── install.sh
│   ├── start.sh
│   ├── stop.sh
│   └── health-check.sh
│
├── .env.example
├── .gitignore
├── requirements.txt
├── docker-compose.yml
└── README.md

6. System Requirements

Lightweight Development Profile

Suitable for the initial development environment:

Kali Linux or another supported Linux distribution.

4 GB RAM minimum for lightweight development.

Python 3.

Node.js and npm.

Git.

SQLite.

Internet connection for installing dependencies.

The lightweight profile should avoid running the complete Wazuh stack and a local large language model simultaneously on a 4 GB virtual machine.

Expanded SOC Profile

Recommended for the complete monitoring environment:

8 GB RAM minimum target; 16 GB preferred.

2–4 or more CPU cores.

Adequate disk space for logs and event indexing.

Wazuh Manager, Indexer and Dashboard.

Suricata network monitoring where required.

Optional AI inference infrastructure.

Actual resource requirements depend on event volume, retention, enabled integrations, and the number of monitored endpoints.

7. Installation

Step 1: Clone the Repository

git clone https://github.com/SwetaDas555/CYBERGUARD-AI.git
cd CYBERGUARD-AI

Step 2: Install System Dependencies

sudo apt update

sudo apt install -y \
python3 \
python3-pip \
python3-venv \
python3-dev \
git \
curl \
jq \
sqlite3 \
build-essential

Install Node.js and npm using a supported installation method if they are not already available.

Step 3: Create a Python Virtual Environment

python3 -m venv .venv
source .venv/bin/activate

Step 4: Install Backend Dependencies

pip install --upgrade pip
pip install -r requirements.txt

Step 5: Configure Environment Variables

Create a local environment file:

cp .env.example .env

Configure the required application settings. Never commit real passwords, API keys, or other secrets.

Step 6: Start the Backend

uvicorn backend.main:app --reload --host 127.0.0.1 --port 8000

If the application entry point changes during development, use the command documented for that version.

Step 7: Start the Frontend

cd frontend
npm install
npm run dev

Open the frontend URL displayed by Vite in your terminal.

The backend API documentation should be available at:

http://127.0.0.1:8000/docs

8. Security Detection Capabilities

The planned detection engine includes rules for identifying:

Repeated failed SSH authentication attempts.

Potential brute-force activity.

Successful authentication following repeated failures.

Suspicious root authentication.

Unusual privilege escalation.

Changes to monitored system files.

Unexpected file permission changes.

Suspicious network events.

Potential command-and-control indicators from supported telemetry.

Detection results should include timestamps, source information, severity, supporting evidence, and applicable MITRE ATT&CK references.

9. AI-Assisted Security Analysis

The optional AI analysis module is intended to assist security investigations by:

Explaining security alerts in understandable language.

Summarizing related log events.

Highlighting suspicious activity patterns.

Suggesting relevant MITRE ATT&CK techniques.

Providing investigation and remediation recommendations.

Helping analysts prioritize incidents.

AI-generated findings must be treated as recommendations, not verified security evidence. Sensitive logs should not be sent to external AI services without appropriate authorization and privacy controls.

10. Testing

Run backend tests using:

pytest -v

Check the API documentation and test supported endpoints through the local application.

Testing should include:

Authentication and authorization.

Log ingestion.

Detection rule validation.

Incident creation and updates.

File integrity monitoring.

Report generation.

Integration error handling.

AI analysis fallback.

Input validation and security controls.

Only use systems and network environments that you own or are explicitly authorized to monitor.

11. Development Roadmap

Project architecture and initial setup.

FastAPI backend development.

SQLite database integration.

Authentication and role-based access control.

Professional React SOC dashboard.

Security log collection.

Rule-based threat detection.

Authentication monitoring.

File integrity monitoring.

Incident management.

MITRE ATT&CK mapping.

AI-assisted log analysis.

Wazuh integration.

Suricata integration.

Reports and analytics.

Automated testing.

Docker deployment.

Security documentation and GitHub release.

12. Security and Responsible Use

CYBERGUARD AI is intended for defensive security monitoring, cybersecurity education, and authorized security investigations.

Monitor only systems and networks for which you have permission.

Protect authentication credentials and API keys.

Apply least-privilege permissions.

Secure access to logs and investigation evidence.

Validate and sanitize all user-controlled inputs.

Do not execute AI-generated commands automatically.

Preserve investigation evidence and maintain audit records.

Configure TLS and appropriate access controls for production deployments.

13. Project Purpose

This project is being developed as an advanced cybersecurity learning and development project to explore SIEM architecture, SOC operations, log analysis, threat detection, digital investigation, incident response, and AI-assisted security monitoring.

The goal is to build a practical, modular platform that demonstrates how different defensive security technologies can work together in a centralized monitoring environment.

14. Author

Sweta Kumari Das

Cyber Security and Digital Forensics Student

GitHub: @SwetaDas555

15. License

This project is currently under development. A license should be selected and added before public distribution. Until then, do not assume that the repository grants permission to reuse or redistribute its code.

<p align="center">
  <strong>CYBERGUARD AI — Monitor. Detect. Investigate. Respond.</strong>
</p>
