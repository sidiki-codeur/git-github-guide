# Tutoriel Git et GitHub pour la Gestion de Versions du Code

Ce tutoriel est conçu pour vous aider à utiliser **Git** et **GitHub** afin de gérer efficacement les versions du code durant le projet. Il couvre les bases de Git, les commandes essentielles, et la manière de collaborer via GitHub.

---

## Table des Matières

1. [Introduction à Git et GitHub](#1-introduction-à-git-et-github)
2. [Installation et Configuration Initiale](#2-installation-et-configuration-initiale)
3. [Commandes Git Essentielles](#3-commandes-git-essentielles)
    - [Créer un Dépôt Git](#31-créer-un-dépôt-git)
    - [Cloner un Dépôt Existant](#32-cloner-un-dépôt-existant)
    - [Enregistrer des Changements](#33-enregistrer-des-changements)
    - [Voir l'État du Dépôt](#34-voir-létat-du-dépôt)
    - [Historique des Commits](#35-historique-des-commits)
    - [Gestion des Branches](#36-gestion-des-branches)
4. [Utilisation de GitHub pour la Collaboration](#4-utilisation-de-github-pour-la-collaboration)
    - [Connexion à GitHub](#41-connexion-à-github)
    - [Travailler avec des Remotes](#42-travailler-avec-des-remotes)
    - [Pousser et Récupérer des Changements](#43-pousser-et-récupérer-des-changements)
5. [Gestion des Conflits](#5-gestion-des-conflits)
6. [Bonnes Pratiques](#6-bonnes-pratiques)
7. [Références Rapides des Commandes](#7-références-rapides-des-commandes)
8. [Ressources Supplémentaires](#8-ressources-supplémentaires)

---

## 1. Introduction à Git et GitHub

- **Git** est un système de contrôle de version distribué qui permet de suivre les modifications apportées au code source au fil du temps.
- **GitHub** est une plateforme en ligne qui héberge des dépôts Git et facilite la collaboration entre développeurs.

---

## 2. Installation et Configuration Initiale

### Installation de Git

- **Windows** : Téléchargez Git depuis [git-scm.com](https://git-scm.com/downloads) et installez-le.
- **macOS** : Utilisez Homebrew avec la commande :

  ```bash
  brew install git
  ```

- **Linux** : Installez via le gestionnaire de paquets, par exemple :

  ```bash
  sudo apt-get install git
  ```

### Configuration de Git

Après l'installation, configurez votre nom d'utilisateur et votre adresse e-mail :

```bash
git config --global user.name "Votre Nom"
git config --global user.email "votre.email@example.com"
```

Vérifiez la configuration :

```bash
git config --list
```

---

## 3. Commandes Git Essentielles

### 3.1. Créer un Dépôt Git

Pour initialiser un nouveau dépôt Git dans un répertoire existant :

```bash
cd chemin/vers/votre/projet
git init
```

Cela crée un sous-répertoire caché `.git` qui contient tous les fichiers nécessaires au suivi des versions.

### 3.2. Cloner un Dépôt Existant

Pour cloner un dépôt distant (par exemple depuis GitHub) :

```bash
git clone https://github.com/utilisateur/nom-du-depot.git
```

### 3.3. Enregistrer des Changements

#### Ajouter des Fichiers au Suivi

Pour ajouter un fichier spécifique :

```bash
git add chemin/vers/fichier
```

Pour ajouter tous les fichiers modifiés :

```bash
git add .
```

#### Créer un Commit

Après avoir ajouté les fichiers, enregistrez les changements avec un commit :

```bash
git commit -m "Message décrivant les changements"
```

#### Combinaison des Commandes add et commit

Pour ajouter tous les changements et créer un commit en une seule commande :

```bash
git commit -a -m "Message du commit"
```

> **Remarque** : L'option `-a` ajoute seulement les fichiers déjà suivis par Git.

### 3.4. Voir l'État du Dépôt

Pour voir les fichiers modifiés, ajoutés ou supprimés :

```bash
git status
```

### 3.5. Historique des Commits

Afficher l'historique des commits :

```bash
git log
```

Pour un historique condensé en une ligne par commit :

```bash
git log --oneline
```

### 3.6. Gestion des Branches

#### Créer une Nouvelle Branche

```bash
git branch nom-de-la-branche
```

#### Basculer vers une Branche

```bash
git checkout nom-de-la-branche
```

#### Créer et Basculer vers une Nouvelle Branche en Une Commande

```bash
git checkout -b nom-de-la-branche
```

#### Fusionner une Branche dans la Branche Courante

```bash
git merge nom-de-la-branche
```

#### Supprimer une Branche

```bash
git branch -d nom-de-la-branche
```

---

## 4. Utilisation de GitHub pour la Collaboration

### 4.1. Connexion à GitHub

#### Créer un Compte GitHub

- Rendez-vous sur [github.com](https://github.com) et créez un compte si vous n'en avez pas déjà un.

#### Configurer l'Authentification SSH (Optionnel mais Recommandé)

1. **Générer une Clé SSH** :

   ```bash
   ssh-keygen -t ed25519 -C "votre.email@example.com"
   ```

   Appuyez sur **Entrée** pour accepter l'emplacement par défaut, et éventuellement ajouter une phrase de passe.

2. **Ajouter la Clé SSH à GitHub** :

   - Copiez le contenu de la clé publique :

     ```bash
     cat ~/.ssh/id_ed25519.pub
     ```

   - Sur GitHub, allez dans **Settings > SSH and GPG keys > New SSH key** et collez la clé publique.

### 4.2. Travailler avec des Remotes

#### Vérifier les Remotes

```bash
git remote -v
```

#### Ajouter une Remote

```bash
git remote add origin https://github.com/utilisateur/nom-du-depot.git
```

#### Changer l'URL d'une Remote

```bash
git remote set-url origin nouvelle_url
```

### 4.3. Pousser et Récupérer des Changements

#### Pousser les Changements vers le Dépôt Distant

```bash
git push origin nom-de-la-branche
```

Pour pousser la branche courante et établir une liaison avec la branche distante :

```bash
git push -u origin nom-de-la-branche
```

> **Remarque** : L'option `-u` établit une liaison entre la branche locale et la branche distante.

#### Récupérer les Changements du Dépôt Distant

```bash
git pull origin nom-de-la-branche
```

#### Récupérer sans Fusion Automatique

```bash
git fetch origin
```

Cela télécharge les changements mais ne les fusionne pas. Vous pouvez ensuite fusionner manuellement.

---

## 5. Gestion des Conflits

Un conflit survient lorsque deux modifications incompatibles sont apportées au même morceau de code.

#### Étapes pour Résoudre un Conflit :

1. **Identifier les Fichiers en Conflit** :

   ```bash
   git status
   ```

2. **Ouvrir les Fichiers Concernés** et rechercher les marqueurs de conflit (`<<<<<<<`, `=======`, `>>>>>>>`).

3. **Éditer les Fichiers** pour conserver les changements souhaités.

4. **Ajouter les Fichiers Résolus** :

   ```bash
   git add chemin/vers/fichier
   ```

5. **Créer un Commit de Fusion** :

   ```bash
   git commit -m "Résolution des conflits"
   ```

---

## 6. Bonnes Pratiques

- **Commits Fréquents** : Commitez régulièrement pour enregistrer vos progrès.
- **Messages de Commit Clairs** : Décrivez précisément ce qui a été fait.
- **Utiliser les Branches** : Travaillez sur des branches pour développer des fonctionnalités sans affecter la branche principale (`main` ou `master`).
- **Mettre à Jour Régulièrement** : Avant de commencer à travailler, faites `git pull` pour synchroniser votre dépôt local.
- **Éviter de Commiter des Fichiers Sensibles** : Utilisez `.gitignore` pour exclure les fichiers comme les mots de passe, les clés API, ou les fichiers de configuration locaux.
- **Revue de Code** : Utilisez les Pull Requests sur GitHub pour examiner le code avant de le fusionner dans la branche principale.

---

## 7. Références Rapides des Commandes

### Configuration

- Configurer le nom d'utilisateur :

  ```bash
  git config --global user.name "Votre Nom"
  ```

- Configurer l'e-mail :

  ```bash
  git config --global user.email "votre.email@example.com"
  ```

### Initialisation et Clonage

- Initialiser un dépôt Git :

  ```bash
  git init
  ```

- Cloner un dépôt distant :

  ```bash
  git clone url_du_depot
  ```

### Gestion des Changements

- Vérifier l'état du dépôt :

  ```bash
  git status
  ```

- Ajouter un fichier au suivi :

  ```bash
  git add fichier
  ```

- Ajouter tous les fichiers modifiés :

  ```bash
  git add .
  ```

- Créer un commit :

  ```bash
  git commit -m "Message du commit"
  ```

- Ajouter et commiter en une commande :

  ```bash
  git commit -a -m "Message du commit"
  ```

### Historique et Logs

- Afficher l'historique des commits :

  ```bash
  git log
  ```

- Historique condensé :

  ```bash
  git log --oneline
  ```

- Voir les changements non committés :

  ```bash
  git diff
  ```

- Voir les changements ajoutés mais non committés :

  ```bash
  git diff --staged
  ```

### Branches

- Lister les branches locales :

  ```bash
  git branch
  ```

- Créer une nouvelle branche :

  ```bash
  git branch nom-de-la-branche
  ```

- Basculer vers une branche :

  ```bash
  git checkout nom-de-la-branche
  ```

- Créer et basculer vers une nouvelle branche :

  ```bash
  git checkout -b nom-de-la-branche
  ```

- Fusionner une branche dans la branche courante :

  ```bash
  git merge nom-de-la-branche
  ```

- Supprimer une branche :

  ```bash
  git branch -d nom-de-la-branche
  ```

### Remotes

- Afficher les remotes :

  ```bash
  git remote -v
  ```

- Ajouter une remote :

  ```bash
  git remote add origin url_du_depot
  ```

- Pousser vers la remote :

  ```bash
  git push origin nom-de-la-branche
  ```

- Récupérer et fusionner les changements :

  ```bash
  git pull origin nom-de-la-branche
  ```

- Récupérer les changements sans fusionner :

  ```bash
  git fetch origin
  ```

### Annuler des Changements

- Annuler les modifications locales sur un fichier non committé :

  ```bash
  git checkout -- fichier
  ```

- Retirer un fichier de la zone de staging :

  ```bash
  git reset HEAD fichier
  ```

- Annuler un commit spécifique :

  ```bash
  git revert id_du_commit
  ```

---

## 8. Ressources Supplémentaires

- **Documentation Git** : [https://git-scm.com/doc](https://git-scm.com/doc)
- **Livre Pro Git (gratuit)** : [https://git-scm.com/book/fr/v2](https://git-scm.com/book/fr/v2)
- **Guides GitHub** : [https://guides.github.com](https://guides.github.com)
