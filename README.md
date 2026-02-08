# 🏢 SpaceBooker - Plateforme de Réservation d'Espaces

[![Live Demo](https://img.shields.io/badge/demo-live-success)](https://spacebooker.vercel.app)
[![Backend API](https://img.shields.io/badge/API-online-blue)](https://spacebooker-api.onrender.com)
[![License](https://img.shields.io/badge/license-MIT-green)](LICENSE)

> Plateforme web full-stack de réservation d'espaces de travail au Maroc 🇲🇦

![SpaceBooker Homepage](./screenshots/home.png)

---

## 📋 Table des Matières

- [À Propos](#-à-propos)
- [Fonctionnalités](#-fonctionnalités)
- [Technologies](#-technologies)
- [Installation](#-installation)
- [Déploiement](#-déploiement)
- [API Documentation](#-api-documentation)
- [Screenshots](#-screenshots)
- [Contribution](#-contribution)
- [Licence](#-licence)

---

## 🎯 À Propos

**SpaceBooker** est une application web moderne permettant la réservation d'espaces de travail dans les principales villes du Maroc. Elle offre une expérience utilisateur fluide pour rechercher, comparer et réserver des espaces de coworking, salles de réunion, bureaux privés et espaces événementiels.

### Pourquoi SpaceBooker ?

- 🔍 **Recherche avancée** avec filtres multiples
- 💰 **Prix transparents** en Dirhams marocains (MAD)
- 🚀 **Réservation instantanée** avec confirmation en temps réel
- 📊 **Dashboard administrateur** complet
- 📱 **Design responsive** adapté à tous les écrans
- 🔒 **Sécurité renforcée** (JWT, bcrypt, validation)

---

## ✨ Fonctionnalités

### Pour les Utilisateurs

✅ **Authentification sécurisée**
- Inscription et connexion avec JWT
- Hash des mots de passe avec bcrypt
- Gestion de profil

✅ **Recherche d'espaces**
- Recherche textuelle (nom, ville, description)
- Filtres avancés (type, capacité, prix, ville)
- Tri personnalisable
- Pagination des résultats

✅ **Réservation**
- Sélection de dates et heures
- Calcul automatique du prix
- Vérification de disponibilité
- Gestion des réservations (annulation, consultation)

### Pour les Administrateurs

✅ **Gestion des espaces**
- CRUD complet sur les espaces
- Upload d'images (jusqu'à 5)
- Gestion des disponibilités

✅ **Dashboard statistiques**
- Nombre total d'espaces, utilisateurs, réservations
- Revenus totaux en MAD
- Top espaces populaires
- Réservations récentes

---

## 🛠️ Technologies

### Backend

```
Node.js 18+
Express.js 4.18
MongoDB Atlas
Mongoose 8.0
JWT (jsonwebtoken)
bcryptjs
Multer (upload)
express-validator
```

### Frontend

```
React 18
Vite 5.0
TailwindCSS 3.4
React Router DOM 6
Axios
Context API
date-fns
```

### Infrastructure

```
MongoDB Atlas (Database)
Render (Backend hosting)
Vercel (Frontend hosting)
```

---

## 🚀 Installation

### Prérequis

- Node.js v18+
- npm v9+
- MongoDB Atlas account (gratuit)
- Git

### 1. Cloner le Repository

```bash
git clone https://github.com/votre-username/spacebooker.git
cd spacebooker
```

### 2. Backend Setup

```bash
cd spacebooker-backend
npm install

# Créer le fichier .env
cp .env.example .env

# Éditer .env avec vos valeurs:
# - MONGO_URI (MongoDB Atlas connection string)
# - JWT_SECRET (clé secrète forte)
# - FRONTEND_URL (http://localhost:3000)

# Seed la base de données
node config/seed-morocco.js

# Démarrer le serveur
npm run dev
```

Le backend démarre sur **http://localhost:5000**

### 3. Frontend Setup

```bash
cd spacebooker-frontend
npm install

# Le .env.example est déjà configuré pour le développement local
cp .env.example .env

# Démarrer l'application
npm run dev
```

Le frontend démarre sur **http://localhost:3000**

### 4. Comptes de Test

**Admin:**
```
Email: admin@spacebooker.com
Password: Admin123!
```

**Utilisateur:**
```
Email: youssef.alami@email.com
Password: User123!
```

---

## 🌐 Déploiement

### Frontend (Vercel)

[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone?repository-url=https://github.com/votre-username/spacebooker-frontend)

**Variables d'environnement:**
```
VITE_API_URL=https://votre-backend.onrender.com
```

### Backend (Render)

[![Deploy to Render](https://render.com/images/deploy-to-render-button.svg)](https://render.com/deploy)

**Variables d'environnement:**
```
MONGO_URI=mongodb+srv://...
JWT_SECRET=...
FRONTEND_URL=https://votre-app.vercel.app
NODE_ENV=production
```

**Guide complet:** Voir [GUIDE_DEPLOIEMENT.md](./GUIDE_DEPLOIEMENT.md)

---

## 📚 API Documentation

### Base URL

```
Production: https://spacebooker-api.onrender.com/api
Local: http://localhost:5000/api
```

### Endpoints Principaux

#### Authentification
```http
POST   /auth/register          # Inscription
POST   /auth/login             # Connexion
GET    /auth/me                # Profil utilisateur (protégé)
PUT    /auth/profile           # Modifier profil (protégé)
```

#### Espaces
```http
GET    /spaces                 # Liste des espaces
GET    /spaces/:id             # Détail d'un espace
POST   /spaces                 # Créer un espace (admin)
PUT    /spaces/:id             # Modifier un espace (admin)
DELETE /spaces/:id             # Supprimer un espace (admin)
```

#### Réservations
```http
GET    /bookings               # Mes réservations (protégé)
POST   /bookings               # Créer une réservation (protégé)
PUT    /bookings/:id/cancel    # Annuler une réservation (protégé)
```

#### Dashboard
```http
GET    /dashboard/stats        # Statistiques globales (admin)
GET    /dashboard/top-spaces   # Top espaces (admin)
```

**Documentation complète:** Voir [RAPPORT_PROJET.md](./RAPPORT_PROJET.md)

---

## 📸 Screenshots

### Page d'Accueil
![Homepage](./screenshots/home.png)

### Liste des Espaces
![Spaces List](./screenshots/spaces.png)

### Détail & Réservation
![Space Detail](./screenshots/detail.png)

### Dashboard Admin
![Admin Dashboard](./screenshots/dashboard.png)

---

## 📁 Structure du Projet

```
spacebooker/
├── spacebooker-backend/          # Backend API
│   ├── config/                   # Configuration & seed
│   ├── controllers/              # Logique métier
│   ├── middleware/               # Auth, validation, upload
│   ├── models/                   # Modèles Mongoose
│   ├── routes/                   # Routes Express
│   └── server.js                 # Point d'entrée
│
├── spacebooker-frontend/         # Frontend React
│   ├── src/
│   │   ├── components/           # Composants réutilisables
│   │   ├── pages/                # Pages de l'app
│   │   ├── context/              # Context API
│   │   ├── hooks/                # Custom hooks
│   │   └── utils/                # Utilitaires
│   └── index.html                # HTML principal
│
├── DOCUMENTATION_TECHNIQUE.md    # Doc technique complète
├── RAPPORT_PROJET.md             # Rapport final
├── GUIDE_DEPLOIEMENT.md          # Guide de déploiement
└── README.md                     # Ce fichier
```

---

## 🔒 Sécurité

- ✅ **Authentification JWT** avec tokens signés
- ✅ **Hash des mots de passe** avec bcrypt (10 salt rounds)
- ✅ **Validation des entrées** avec express-validator
- ✅ **Protection CORS** configurée
- ✅ **Upload sécurisé** avec Multer (validation MIME)
- ✅ **Sanitization MongoDB** automatique
- ✅ **HTTPS** en production (Render + Vercel)

---

**Fait avec ❤️ 🇲🇦**

