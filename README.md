# Ecampus_Unicaen Automator

Ce projet permet d'automatiser l'accès et la connexion automatique à la plateforme Ecampus de l'Université de Caen à l'aide d'un script Python / Selenium. Il gère l'ensemble du parcours d'authentification CAS, y compris la saisie des identifiants et la validation à double facteur (grille de sécurité).

## 📋 Prérequis et Configuration

Pour utiliser le script ou l'exécutable généré, assurez-vous d'avoir renseigné vos identifiants dans le dictionnaire du script :

1. **Identifiant CAS** (nom d'utilisateur).
2. **Mot de passe**.
3. **Clés de la grille de sécurité** (dictionnaire rempli avec vos codes de grille 2FA).

> 💡 **Note :** Google Chrome doit être installé sur votre machine pour que l'automatisation Selenium puisse piloter le navigateur.

---

## 💻 Installation de Python et des Dépendances (Linux, Windows)

Si vous souhaitez exécuter le projet à partir du code source ou le recompiler vous-même :

### 🐧 Sous Linux (Ubuntu / Debian)

1. Mettez à jour les paquets et installez Python, `pip` et l'environnement virtuel :

   ```bash
   sudo apt update
   sudo apt install python3 python3-pip python3-venv
   ```

2. Créez et activez un environnement virtuel :

   ```bash
   python3 -m venv .venv
   source .venv/bin/activate
   ```

3. Installez les dépendances du projet :

   ```bash
   pip install selenium webdriver-manager requests pyinstaller
   ```

### 🪟 Sous Windows

1. Téléchargez et installez **Python** depuis le site officiel : [python.org](https://www.python.org/downloads/).
   > ⚠️ Assurez-vous de bien cocher la case **"Add Python to PATH"** lors de l'installation.

2. Ouvrez l'invite de commandes (`cmd`) ou PowerShell et créez un environnement virtuel :

   ```cmd
   python -m venv .venv
   .venv\Scripts\activate
   ```

3. Installez les dépendances :

   ```cmd
   pip install selenium webdriver-manager requests pyinstaller
   ```

---

## 🛠️ Démarche de Création de l'Exécutable (Compilation)

Pour générer un fichier exécutable autonome à partir de votre script Python :

1. Activez votre environnement virtuel.
2. Lancez la commande PyInstaller :

   ```bash
   pyinstaller --onefile --noconsole --collect-all selenium main.py
   ```

**Explication des options :**
* `--onefile` : Regroupe le script et toutes ses dépendances dans un seul fichier autonome (situé dans le dossier `dist/`).
* `--noconsole` : Empêche l'ouverture d'une fenêtre de terminal en arrière-plan.
* `--collect-all selenium` : Embarque l'intégralité des sous-modules de Selenium nécessaires au runtime.

---

## 🖥️ Création du Raccourci Bureau (`.desktop`) sous Linux

Pour pouvoir exécuter la connexion automatique d'un simple double-clic depuis votre bureau sous Linux :

1. Créez un fichier `.desktop` sur votre bureau :

   ```bash
   nano ~/Bureau/Ecampus_Unicaen.desktop
   ```

2. Ajoutez la configuration suivante (remplacez `/chemin/absolu/vers/votre/projet` par le chemin réel sur votre machine) :

   ```ini
   [Desktop Entry]
   Version=1.0
   Type=Application
   Name=Ecampus Unicaen
   Comment=Lancement et connexion automatique à Ecampus
   Exec=/chemin/absolu/vers/votre/projet/dist/ecampus
   Path=/chemin/absolu/vers/votre/projet/dist
   Icon=utilities-terminal
   Terminal=false
   StartupNotify=true
   ```

3. Rendez le fichier exécutable :

   ```bash
   chmod +x ~/Bureau/Ecampus_Unicaen.desktop
   ```

4. **Activation graphique :** Sur votre bureau Linux, faites un **clic droit** sur l'icône du raccourci et sélectionnez **« Autoriser le lancement »** (*Allow Launching*).
