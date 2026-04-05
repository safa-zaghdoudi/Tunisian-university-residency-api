# 🏠 Tunisian University Residency API

A RESTful API for managing university residencies in Tunisia, built with **Flask (Python)**, **MongoDB Atlas**, and a **Next.js** frontend. This project streamlines the student housing application process — from browsing residencies to submitting applications and tracking their status.

> 📚 Academic Project — Tunis Business School, University of Tunis | 2024–2025  
> Supervised by: Mr. Montassar Ben Messaoud

---

## 📋 Table of Contents

- [About the Project](#about-the-project)
- [Tech Stack](#tech-stack)
- [Features](#features)
- [Project Structure](#project-structure)
- [API Endpoints](#api-endpoints)
- [Database Design](#database-design)
- [Security](#security)
- [Getting Started](#getting-started)
- [Testing](#testing)
- [Future Enhancements](#future-enhancements)

---

## 📌 About the Project

Traditional student housing management in Tunisia relies on semi-automated, paper-based processes that often lead to:
- Long processing times
- Poor communication between students and administrators
- Favoritism in room assignments

This project addresses these issues by providing a **centralized, automated platform** for both students and administrators to manage university residency applications efficiently and fairly.

---

## 🛠 Tech Stack

| Layer | Technology |
|-------|-----------|
| Backend | Python, Flask |
| Database | MongoDB Atlas (Cloud) |
| Frontend | Next.js, TypeScript, Tailwind CSS |
| Authentication | JWT (JSON Web Tokens) |
| Password Security | bcrypt |
| API Testing | Insomnia |

---

## ✨ Features

### For Students
- Browse available university residencies and their details
- Submit housing applications with preferences (e.g., preferred roommate, medical status)
- Track application status in real time
- Leave reviews and ratings for residencies

### For Administrators
- Full CRUD management of residencies, blocks, and rooms
- View and manage all student applications
- Access student reviews

---

## 📁 Project Structure

```
WebProject_Backend/
├── resources/
│   ├── auth.py          # Registration, login, JWT handling
│   └── residency.py     # RESTful endpoints for residencies & applications
├── models/
│   └── residency.py     # Database interaction functions
├── app.py               # App entry point — Flask setup, CORS, blueprints
├── db.py                # MongoDB connection initialization
├── requirements.txt     # Python dependencies
└── .flaskenv            # Flask environment configuration
```

---

## 🔗 API Endpoints

### Authentication

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/auth/register` | Register a new user (admin or student) |
| POST | `/auth/login` | Login and receive a JWT token |
| POST | `/auth/logout` | Logout and invalidate the JWT token |

### Administrator Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/residencies` | Fetch all residencies |
| GET | `/residency/<id>` | Get residency details |
| POST | `/residencies` | Create a new residency |
| PUT | `/residency/<id>` | Update a residency |
| DELETE | `/residency/<id>` | Delete a residency |
| GET | `/<residency_id>/blocks` | Fetch all blocks in a residency |
| POST | `/<residency_id>/blocks` | Create a new block |
| PUT | `/blocks/<id>` | Update a block |
| DELETE | `/blocks/<id>` | Delete a block |
| GET | `/<block_id>/rooms` | Fetch all rooms in a block |
| POST | `/<block_id>/rooms` | Create a new room |
| PUT | `/rooms/<id>` | Update a room |
| DELETE | `/rooms/<id>` | Delete a room |
| GET | `/applications` | Fetch all student applications |
| GET | `/reviews` | Fetch all student reviews |

### Student Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/residencies` | Browse all residencies |
| GET | `/residencies/<id>` | View residency details |
| POST | `/applications` | Submit a housing application |
| DELETE | `/applications/<id>` | Delete an application |
| POST | `/reviews` | Submit a review |
| DELETE | `/reviews/<id>` | Delete a review |

---

## 🗄 Database Design

The database includes the following models:

- **User** — base model with `user_id`, `username`, `password`
- **Admin** — extends User with `first_name`, `last_name`
- **Student** — extends User with `first_name`, `last_name`, `year_of_study`, `university`
- **Residency** — name, type, city, address, telephone, transportation
- **Block** — linked to a residency; contains `block_name`, `number_of_floors`, `total_rooms`
- **Room** — linked to a block; contains `floor`, `room_number`, `capacity`, `is_available`
- **Application** — links a student to a residency with preferences and status
- **Review** — links a student to a residency with a rating and text

---

## 🔒 Security

- **Password Hashing** — bcrypt ensures passwords are never stored in plain text
- **JWT Authentication** — tokens expire after 1 hour; protected routes use a `token_required` decorator
- **Input Validation** — prevents malformed requests and injection attacks
- **CORS Configuration** — restricts cross-origin requests to trusted domains
- **Virtual Environment** — isolated Python dependencies for consistent builds

---

## 🚀 Getting Started

### Prerequisites
- Python 3.8+
- MongoDB Atlas account
- Node.js (for the frontend)

### Backend Setup

```bash
# Clone the repository
git clone https://github.com/your-username/tunisian-university-residency-api.git
cd tunisian-university-residency-api

# Create and activate a virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Set up your environment variables in .flaskenv
FLASK_APP=app.py
FLASK_ENV=development
MONGO_URI=your_mongodb_atlas_connection_string
JWT_SECRET_KEY=your_secret_key

# Run the app
flask run
```

### Frontend Setup

```bash
cd frontend
npm install
npm run dev
```

---

## 🧪 Testing

API endpoints were tested using **Insomnia**, covering:
- Valid and invalid inputs
- Authentication flows
- CRUD operations for all resources
- Edge cases and error handling

---

## 🔮 Future Enhancements

- **Web scraping** to automate residency data collection
- **University database integration** for more precise room assignments
- **Online document uploads** to replace paper-based submissions
- **Google OAuth** for simplified student login
- **Arabic language support** for a broader user base
- **AI-powered room assignment** based on student preferences and fairness metrics

---

## 👩‍💻 Author

**Safa Zaghdoudi**  
Tunis Business School — University of Tunis  
Academic Year 2024–2025
