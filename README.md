# LAB 6 — Analyse statique d'APK Android avec MobSF

**Cours : Sécurité des applications mobiles | Plateforme : MLIAEdu**

---

## 📋 Vue d'ensemble

Ce laboratoire permet de découvrir l'analyse statique d'applications Android (APK) à l'aide de **MobSF (Mobile Security Framework)** , un outil open-source d'analyse automatisée de sécurité mobile. L'analyse s'effectue dans un environnement contrôlé (VM Mobexler) et vise à identifier les vulnérabilités potentielles sans exécuter l'application.

### 🎯 Objectifs pédagogiques

| Objectif | Statut |
|----------|--------|
| Comprendre le processus d'analyse statique d'un APK | ✅ |
| Identifier les composants sensibles d'une application Android | ✅ |
| Interpréter un rapport d'analyse de sécurité mobile | ✅ |
| Reconnaître les vulnérabilités courantes dans les applications Android | ✅ |
| Associer les vulnérabilités aux standards OWASP MASVS | ✅ |
| Formuler des recommandations de sécurité pertinentes | ✅ |
| Produire un mini-rapport d'audit professionnel | ✅ |

---

## 🖥️ Environnement technique

| Composant | Version |
|-----------|---------|
| VM | Mobexler |
| OS | Ubuntu (Mobexler) |
| Framework | MobSF |
| APK analysé | `app-debug.apk` |
| Hash SHA-256 | `dd7c1932f506ea626622325fa5a041f4061aa8ff9cbf1454a58cc7f233efc4a6` |
| Package | `ma.ens.myapplication` |
| SDK cible | 36 (Android 16) |
| SDK minimum | 24 (Android 7.0) |

---

## 📊 Résultats de l'analyse

### Score de sécurité
**`58/100`** - Niveau de risque : 🟡 **MOYEN**

### Top 3 vulnérabilités identifiées

| # | Vulnérabilité | Sévérité | Localisation |
|---|---------------|----------|--------------|
| 1 | `android:debuggable=true` | 🔴 ÉLEVÉE | `AndroidManifest.xml` |
| 2 | `minSdkVersion=24` (Android 7.0) | 🔴 ÉLEVÉE | `AndroidManifest.xml` |
| 3 | `android:allowBackup=true` | 🟡 MOYENNE | `AndroidManifest.xml` |

### Points positifs

| Catégorie | Statut |
|-----------|--------|
| Permissions dangereuses | ✅ Aucune |
| Secrets hardcodés | ✅ Aucun |
| Configuration réseau | ✅ Sécurisée |
| URLs sensibles | ✅ Aucune |

---

## 🔧 Démarche d'analyse

### 1. Préparation de l'environnement

bash
mkdir -p ~/apk_analysis/$(date +%Y-%m-%d)
cd ~/apk_analysis/$(date +%Y-%m-%d)
sha256sum app-debug.apk > apk_hash.txt


2. Lancement de MobSF
bash
cd ~/tools/Mobile-Security-Framework-MobSF
./run.sh 127.0.0.1:8000

3. Analyse statique
L'APK a été soumis à MobSF qui a effectué plus de 100 vérifications couvrant :

Analyse du manifeste et des permissions

Configuration réseau

Code analysis (secrets, vulnérabilités)

Analyse des binaires et des ressources

<img width="777" height="365" alt="screeen1" src="https://github.com/user-attachments/assets/08b7cca7-1db6-4c80-ac51-4759b43fe60a" />
<img width="350" height="173" alt="screen2" src="https://github.com/user-attachments/assets/36ec6401-62b2-45c5-b03d-a9c5531b6807" />
<img width="720" height="174" alt="manifest" src="https://github.com/user-attachments/assets/069ff521-d5be-4acc-b941-446f92241bb8" />
<img width="650" height="45" alt="permission" src="https://github.com/user-attachments/assets/faec4980-696d-4efd-9766-0090e3a57d62" />





