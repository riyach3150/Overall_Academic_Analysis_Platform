# 🎓 Overall Academic Analysis (OAA)

### An AI-Powered Student Performance, Analytics & Talent Management Platform

OAA (Overall Academic Analysis) is a full-stack academic analytics platform designed to provide a comprehensive view of student performance beyond traditional grades and attendance.

It brings together academic results, technical skills, project contributions, behavioural records, and AI-powered performance insights into a unified platform.

The system provides dedicated dashboards for students and institutional administrators, enabling data-driven academic monitoring, performance evaluation, student rankings, and talent identification.

---

## 📌 Table of Contents

- [Overview](#-overview)
- [Problem Statement](#-problem-statement)
- [Project Objectives](#-project-objectives)
- [Key Features](#-key-features)
- [User Roles](#-user-roles)
- [OAA Scoring System](#-oaa-scoring-system)
- [AI-Powered Prediction Engine](#-ai-powered-prediction-engine)
- [System Architecture](#-system-architecture)
- [Technology Stack](#-technology-stack)
- [Project Structure](#-project-structure)
- [Database Design](#-database-design)
- [API Endpoints](#-api-endpoints)
- [Installation and Setup](#-installation-and-setup)
- [Environment Variables](#-environment-variables)
- [Running the Application](#-running-the-application)
- [Future Enhancements](#-future-enhancements)
- [Privacy and Security](#-privacy-and-security)
- [Contributing](#-contributing)

---

## 🚀 Overview

Traditional academic evaluation systems primarily focus on examination marks, grades, and attendance. However, these metrics alone cannot represent a student's overall capabilities.

A student may have excellent academic performance but limited practical experience, while another may demonstrate strong technical skills, projects, and problem-solving abilities.

**Overall Academic Analysis (OAA)** addresses this gap by introducing a multidimensional student evaluation framework.

The platform combines:

- Academic performance and examination results.
- Technical skills and proficiency levels.
- Project development and practical contributions.
- Behavioural and disciplinary records.
- AI-assisted academic risk prediction.
- Student rankings and class-level analytics.

The goal is to create a unified academic ecosystem that helps institutions identify student strengths, recognize improvement areas, and support better academic decision-making.

## 🎯 Problem Statement

Educational institutions often face several challenges:

1. **Fragmented Student Information:** Academic marks, attendance, skills, and project records are maintained across different systems.
2. **Limited Performance Evaluation:** Traditional grading systems do not adequately measure practical skills and project contributions.
3. **Lack of Predictive Insights:** Identifying students who may be at risk of academic underperformance often requires manual analysis.
4. **Inefficient Talent Identification:** Finding students based on their combined academic and technical capabilities can be difficult.
5. **Manual Administrative Work:** Importing student information and monitoring performance across multiple classes can consume significant time.

OAA aims to address these challenges through centralized data management, analytical scoring, automated reporting, and AI-assisted insights.

## 🎯 Project Objectives

- Develop a centralized platform for student academic information.
- Evaluate students using academic, technical, project, and behavioural indicators.
- Generate composite OAA scores and student rankings.
- Provide interactive dashboards for different institutional roles.
- Analyze class-level academic performance.
- Support spreadsheet and transcript-based student data ingestion.
- Identify potential academic risk using machine learning.
- Encourage project development and technical skill tracking.

---

## ✨ Key Features

### 1. Student Dashboard

A dedicated workspace that allows students to monitor their academic progress and overall performance.

- Personal academic overview.
- Examination marks and subject-wise performance.
- Attendance tracking.
- OAA score and ranking information.
- Technical skill portfolio.
- Project showcase.
- Student profile management.

### 2. Administration Dashboard

A centralized interface for institutional administrators to manage and monitor student information.

- Student management and records.
- Academic performance monitoring.
- Attendance analytics.
- Marks management.
- Student leaderboard.
- Class potential analysis.
- AI-powered academic insights.
- Report generation.
- Administrative settings.

### 3. Academic Analytics

Provides analytical views of student and institutional performance.

- Overall academic performance.
- Subject-wise analysis.
- Attendance trends.
- Student performance comparisons.
- Class-level insights.
- Visual analytics and charts.

### 4. AI-Powered Academic Risk Prediction

An integrated Python-based machine learning microservice that analyzes student performance indicators.

It considers:

- Average academic marks.
- Attendance rate.
- Marks performance trend.
- Number of weak subjects.
- Consecutive absence indicators.

The prediction service generates risk classifications, confidence information, feature importance, and actionable academic suggestions.

### 5. Student Data Ingestion

Reduces manual administrative work by supporting structured student data extraction.

**Excel / CSV Ingestion**

- Upload spreadsheet records.
- Automatically map common student information fields.
- Identify subject-wise marks.
- Normalize extracted records before confirmation.

**PDF Transcript Ingestion**

- Extract text from PDF transcripts.
- Process academic information.
- Support structured student record extraction.
- Provide a fallback parsing mechanism when AI-based extraction is unavailable.

### 6. OAA Composite Scoring

Evaluates students using multiple performance indicators.

The scoring engine considers academic performance, technical skills, project scores, and behavioural records to calculate a composite score.

### 7. Class Potential Analysis

Provides a class-level academic performance indicator to help administrators understand overall cohort performance.

### 8. Student Communication and Moderation

Includes project-oriented peer communication functionality.

- Chat room management.
- Peer messaging.
- Message moderation status.
- Flagged message monitoring.
- Administrative review of moderation alerts.

### 9. Disciplinary Management

Maintains behavioural and disciplinary records through a dedicated administrative module.

- Incident recording.
- Red Dot tracking.
- Behavioural score integration.
- Administrative monitoring.

### 10. Reports and Data Visualization

- Academic performance visualizations.
- Attendance analytics.
- Student ranking reports.
- Downloadable PDF reports.

---

## 👥 User Roles

The platform supports role-based access through authentication and authorization controls.

| Role          | Primary Responsibilities                                                          |
| ------------- | --------------------------------------------------------------------------------- |
| Student       | View personal academic records, attendance, marks, profile, skills and projects.  |
| Teacher       | Manage assigned academic records and participate in student monitoring workflows. |
| Administrator | Manage student information, analytics, reports and administrative operations.     |
| Principal     | Access institutional monitoring and administrative functionality.                 |

---

## 🧮 OAA Scoring System

One of the core components of the platform is the OAA Composite Scoring Engine.

Unlike conventional academic evaluation systems, OAA considers multiple dimensions of student performance.

### Current implemented scoring model

The scoring engine uses the following calculation:

**OAA Score = Academic Score + Skills Score + Project Score + Behaviour Score**

| Performance Component   | Maximum Points |
| ----------------------- | -------------: |
| Academic Performance    |             40 |
| Technical Skills        |             30 |
| Project Contributions   |             20 |
| Behavioural Performance |             10 |
| **Total**               |        **100** |

### Component calculations

**1. Academic Score**

Academic marks are normalized to a maximum of 40 points.

Academic Score = (Average Marks / Average Maximum Marks) × 40

**2. Skills Score**

Technical skill proficiency is converted into points:

- Beginner: 2 points
- Intermediate: 4 points
- Advanced: 6 points

The total skills score is capped at 30 points.

**3. Project Score**

The average project evaluation score is considered, capped at 20 points.

**4. Behaviour Score**

The behavioural score is calculated using disciplinary records.

Behaviour Score = max(0, 10 − (Red Dot Count × 2))

The resulting score is capped between 0 and 10.

The final OAA score is calculated on a scale of 100.

### Class Potential

The platform also implements a Class Potential calculation:

CP = (μ / Mmax) × 100

Where:

- μ represents the average marks of the class.
- Mmax represents the normalized maximum benchmark.

This provides an overview of class-level academic performance.

---

## 🤖 AI-Powered Prediction Engine

OAA integrates a separate Python-based AI microservice built using FastAPI and Scikit-learn.

### Machine Learning Model

The prediction service uses a Random Forest Classifier to identify potential academic underperformance.

### Input Features

| Feature             | Description                              |
| ------------------- | ---------------------------------------- |
| Average Marks       | Overall academic performance             |
| Attendance Rate     | Student attendance percentage            |
| Marks Trend         | Recent academic performance change       |
| Weak Subjects Count | Number of subjects requiring improvement |
| Absent Streak       | Consecutive absence indicator            |

### Prediction Outputs

The service provides:

- Academic risk classification.
- Risk probability score.
- Prediction confidence.
- Feature importance values.
- Personalized academic suggestions.

### AI Service Endpoints

| Method | Endpoint             | Purpose                                  |
| ------ | -------------------- | ---------------------------------------- |
| GET    | `/health`            | Check service health                     |
| POST   | `/predict`           | Generate academic risk predictions       |
| POST   | `/train`             | Retrain the prediction model             |
| POST   | `/ingest/excel`      | Process Excel or CSV records             |
| POST   | `/ingest/transcript` | Extract information from PDF transcripts |

The AI service can also generate personalized suggestions using Google Cloud Vertex AI when properly configured. Rule-based recommendations provide a fallback.

**Note:** The predictions are decision-support indicators and should not replace professional academic evaluation.

---

## 🏗️ System Architecture

OAA follows a modular architecture with a Next.js web application, a relational database layer, and a separate Python AI microservice.

```text
                 STUDENTS / ADMINISTRATORS
                           |
                           v
                NEXT.JS WEB APPLICATION
                 React + TypeScript
                           |
                           v
                   APPLICATION APIs
                  Next.js API Routes
                           |
              +------------+------------+
              |                         |
              v                         v
        DATABASE LAYER            AI MICROSERVICE
        Drizzle ORM                FastAPI
        Turso / libSQL             Python
              |                         |
              v                         v
        STUDENT DATA             SCikit-learn
        MARKS / ATTENDANCE        Random Forest
        SKILLS / PROJECTS         PREDICTIONS
        OAA SCORES                INSIGHTS
              |                         |
              +------------+------------+
                           |
                           v
                 ANALYTICS & DASHBOARDS
```

### Architecture Components

- **Frontend Layer:** Provides the student and administrative interfaces.
- **Application Layer:** Handles authentication, API requests, business logic, and access control.
- **Database Layer:** Stores academic, attendance, skill, project, and platform records.
- **AI Layer:** Processes student performance indicators and generates prediction results.
- **Analytics Layer:** Presents scores, rankings, reports, and performance trends.

---

## 🛠️ Technology Stack

### Frontend

- Next.js 14
- React 18
- TypeScript
- Tailwind CSS
- Framer Motion
- Recharts
- Lucide React
- Zustand

### Backend

- Next.js API Routes
- Node.js
- Auth.js / NextAuth
- Drizzle ORM
- Zod
- bcryptjs

### Database

- Turso
- libSQL
- SQLite-compatible relational database
- Drizzle ORM

### Artificial Intelligence and Machine Learning

- Python
- FastAPI
- Scikit-learn
- Random Forest Classifier
- Pandas
- NumPy
- Joblib
- Google Cloud Vertex AI integration

### Data Processing and Reporting

- XLSX
- PyPDF
- jsPDF
- jsPDF AutoTable

### Development Tools

- Visual Studio Code
- Git
- GitHub
- Docker

---

## 📂 Project Structure

```text
OAA/
│
├── ai-service/
│   ├── main.py
│   ├── model.pkl
│   ├── Dockerfile
│   ├── requirements.txt
│   ├── models/
│   │   ├── predictor.py
│   │   └── train_ssynthetic.py
│   └── routes/
│       ├── predict.py
│       ├── train.py
│       └── ingest.py
│
├── app/
│   ├── (auth)/
│   │   ├── login/
│   │   └── register/
│   ├── api/
│   │   ├── admin/
│   │   ├── ai/
│   │   ├── analytics/
│   │   ├── attendance/
│   │   ├── auth/
│   │   ├── chat/
│   │   ├── discipline/
│   │   ├── marks/
│   │   ├── oaa/
│   │   ├── projects/
│   │   ├── skills/
│   │   └── students/
│   └── dashboard/
│       ├── admin/
│       └── student/
│
├── components/
├── design-system/
├── drizzle/
├── hooks/
├── lib/
│   ├── db/
│   ├── scoring/
│   └── api/
│
├── public/
├── scripts/
├── types/
│
├── .env.local.example
├── .gitignore
├── auth.ts
├── auth.config.ts
├── drizzle.config.ts
├── middleware.ts
├── next.config.js
├── package.json
├── package-lock.json
├── tailwind.config.ts
└── tsconfig.json
```

---

## 🗄️ Database Design

The application uses Drizzle ORM with a Turso/libSQL database.

The current database schema includes the following major entities:

| Table             | Purpose                          |
| ----------------- | -------------------------------- |
| users             | Authentication and user roles    |
| students          | Student profiles                 |
| schools           | Institutional information        |
| marks             | Examination marks                |
| attendance        | Attendance records               |
| skills            | Technical skills and proficiency |
| projects          | Student project information      |
| oaa_scores        | Composite performance scores     |
| red_dots          | Disciplinary records             |
| ai_predictions    | AI prediction results            |
| chat_rooms        | Peer communication rooms         |
| peer_messages     | Chat messages                    |
| moderation_alerts | Flagged message records          |
| sessions          | Authentication sessions          |

---

## 🔌 API Endpoints

The Next.js application exposes REST API routes for the platform's main operations.

| API Route                         | Purpose                     |
| --------------------------------- | --------------------------- |
| `/api/students`                   | Student record management   |
| `/api/marks`                      | Academic marks management   |
| `/api/attendance`                 | Attendance management       |
| `/api/skills`                     | Technical skill management  |
| `/api/projects`                   | Project management          |
| `/api/discipline`                 | Disciplinary records        |
| `/api/analytics/overview`         | Overall analytics           |
| `/api/analytics/subject`          | Subject analytics           |
| `/api/analytics/attendance-trend` | Attendance trends           |
| `/api/oaa/score/[studentId]`      | Individual OAA score        |
| `/api/oaa/leaderboard`            | Student leaderboard         |
| `/api/oaa/class-potential`        | Class potential calculation |
| `/api/ai/predict`                 | AI prediction integration   |
| `/api/chat/messages`              | Peer messaging              |
| `/api/chat/rooms`                 | Chat room management        |
| `/api/chat/moderate`              | Message moderation          |

Additional routes are available for authentication, administrative ingestion, and score recalculation.

---

## ⚙️ Installation and Setup

Follow these steps to run OAA locally.

### Prerequisites

Install the following:

- Node.js 18.17 or later
- npm
- Python 3.10 or 3.11 (for the AI microservice)
- Git
- A Turso/libSQL database for persistent database functionality

### 1. Clone the Repository

```bash
git clone https://github.com/YOUR_USERNAME/overall-academic-analysis.git

cd overall-academic-analysis
```

### 2. Install Dependencies

```bash
npm install
```

### 3. Configure Environment Variables

Create a local environment file:

```bash
cp .env.local.example .env.local
```

On Windows, you can also manually copy `.env.local.example` and rename the copy to `.env.local`.

Add your own database credentials, authentication secret, and other required configuration values.

Refer to the [Environment Variables](#-environment-variables) section.

### 4. Run Database Migrations

```bash
npm run db:migrate
```

This applies the SQL migration files from the `drizzle/` directory when a Turso database URL is configured.

### 5. Start the Next.js Application

```bash
npm run dev
```

Open:

[http://localhost:3000](http://localhost:3000)

### 6. Set Up the AI Microservice (Optional)

Navigate to the AI service:

```bash
cd ai-service
```

Create a Python virtual environment:

```bash
python -m venv venv
```

Activate it on Windows:

```bash
venv\Scripts\activate
```

Install the dependencies:

```bash
pip install -r requirements.txt
```

Start the FastAPI service:

```bash
uvicorn main:app --host 0.0.0.0 --port 7860 --reload
```

The service will be available at:

[http://localhost:7860](http://localhost:7860)

Interactive API documentation:

[http://localhost:7860/docs](http://localhost:7860/docs)

---

## 🔐 Environment Variables

Create a `.env.local` file in the project root.

| Variable               | Description                   |
| ---------------------- | ----------------------------- |
| `TURSO_DATABASE_URL`   | Turso database connection URL |
| `TURSO_AUTH_TOKEN`     | Turso authentication token    |
| `AUTH_SECRET`          | Auth.js authentication secret |
| `AUTH_URL`             | Application base URL          |
| `AUTH_GOOGLE_ID`       | Google OAuth client ID        |
| `AUTH_GOOGLE_SECRET`   | Google OAuth client secret    |
| `AI_SERVICE_URL`       | Deployed AI microservice URL  |
| `NEXT_PUBLIC_APP_NAME` | Public application name       |

Example configuration:

```env
TURSO_DATABASE_URL=libsql://your-database.turso.io
TURSO_AUTH_TOKEN=your-token

AUTH_SECRET=your-generated-secret
AUTH_URL=http://localhost:3000

AUTH_GOOGLE_ID=your-google-client-id
AUTH_GOOGLE_SECRET=your-google-client-secret

AI_SERVICE_URL=http://localhost:7860
NEXT_PUBLIC_APP_NAME=OAA
```

Never commit your `.env.local` file, API keys, passwords, or database credentials to GitHub.

---

## ▶️ Running the Application

### Frontend

```bash
npm run dev
```

### Production Build

```bash
npm run build
```

### Production Server

```bash
npm run start
```

### Database Commands

```bash
npm run db:generate
npm run db:push
npm run db:migrate
npm run db:studio
```

**Important:** The optional `npm run db:seed` script clears existing application records before inserting demo data. Use it only with a disposable development database, never with production or personal data.

---

## 🔮 Future Enhancements

The following are potential improvements for future development:

- Advanced academic performance forecasting.
- More comprehensive student skill assessment.
- Integration with GitHub APIs for verified project contributions.
- Automated resume and portfolio generation.
- Advanced NLP-based communication moderation.
- Improved class and institutional benchmarking.
- Automated academic intervention recommendations.
- Enhanced privacy controls and consent management.
- Production deployment with monitoring and scalability improvements.
- Comprehensive automated testing and model evaluation.

---

## 🔒 Privacy and Security

OAA is designed around role-based access and controlled academic data management.

Important considerations include:

- Authentication and role-based authorization.
- Secure password hashing.
- Environment-based secret management.
- Controlled access to student records.
- Review workflows for flagged communication.
- Protection of sensitive student information.

Before production deployment, additional security testing, access-control validation, privacy reviews, and institutional compliance checks are necessary.

---

## 🤝 Contributing

Contributions, suggestions, and improvements are welcome.

1. Fork the repository.
2. Create a new feature branch.
3. Implement your changes.
4. Test your changes locally.
5. Commit your updates.
6. Submit a pull request.

```bash
git checkout -b feature/your-feature-name

git add .

git commit -m "Add: your feature description"

git push origin feature/your-feature-name
```

---

## 📄 Project Documentation

The repository includes an enterprise architecture blueprint describing the platform's product vision, scoring framework, data governance principles, and proposed system architecture.

Refer to:

`Overall_Academic_Analysis_OAA_Enterprise_Blueprint.pdf`

---

## ⭐ Project Vision

**Beyond Grades. Beyond Rankings. A Complete View of Student Potential.**

OAA aims to transform traditional academic evaluation into a comprehensive, data-driven approach that recognizes academic excellence, technical capabilities, practical contributions, and continuous student development.

---

*Built with a focus on Full-Stack Development, Artificial Intelligence, Machine Learning, and Academic Analytics.*
