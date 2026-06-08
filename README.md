# Intervimo Docs

Documentation fonctionnelle d'Intervimo construite avec Mintlify.

## Installation

### Prérequis

* Node.js 20+
* npm

Vérifier les versions installées :

```bash
node -v
npm -v
```

## Lancer la preview

Installer les dépendances :

```bash
npm install
```

Lancer la documentation en local :

```bash
mint dev
```

Ouvrir ensuite :

```text
http://localhost:3000
```

La prévisualisation se met à jour automatiquement lors des modifications des fichiers.

## Structure du projet

```text
intervimo-docs/
├── docs.json
├── README.md
├── favicon.svg
├── concepts/
├── locataires/
├── gestionnaires/
├── prestataires/
├── snippets/
│   └── EnCours.mdx
├── images/
└── logo/
```

### Organisation de la documentation

```text
Concepts
├── cycle-de-vie
├── roles-acteurs
├── glossaire
└── prise-en-main

Locataires
├── signaler
└── suivre

Gestionnaires
├── qualifier
├── matchmaking
├── devis
└── planification

Prestataires
├── recevoir-chiffrer
└── executer
```

## Créer une page

Créer un fichier `.mdx` dans le dossier correspondant.

Exemple :

```text
locataires/nouvelle-page.mdx
```

Ajouter le frontmatter :

```mdx
---
title: Nouvelle page
description: Description de la page
---
```

Ajouter ensuite la page dans la navigation du fichier `docs.json`.

Exemple :

```json
{
  "group": "Locataires",
  "pages": [
    "locataires/signaler",
    "locataires/suivre",
    "locataires/nouvelle-page"
  ]
}
```

## Modifier une page

Ouvrir le fichier `.mdx` concerné.

Exemple :

```text
locataires/signaler.mdx
```

Modifier le contenu puis enregistrer.

La prévisualisation Mintlify se met à jour automatiquement.

## Utiliser EnCours

Les pages en cours de rédaction doivent afficher le bandeau WIP.

Importer le composant :

```mdx
import EnCours from "../snippets/EnCours.mdx"

<EnCours />
```

Exemple :

```mdx
---
title: Signaler
description: Documentation en cours de rédaction
---

import EnCours from "../snippets/EnCours.mdx"

<EnCours />
```

Retirer le composant lorsque la page est validée lors de la revue documentaire.

## Ajouter une capture

Déposer l'image dans le dossier :

```text
images/
```

Exemple :

```text
images/locataire-signaler-formulaire.png
```

Insérer ensuite l'image dans une page MDX :

```mdx
![Formulaire de signalement](/images/locataire-signaler-formulaire.png)
```

Vérifier que la capture est lisible avant validation.

## Convention de captures

Toutes les captures d'écran de la documentation doivent respecter les règles suivantes :

### Langue

* Français (FR)

### Thème

* Thème clair

### Taille de fenêtre

* Viewport constant : 1440 px de large

### Recadrage

* Recadrage propre
* Supprimer les zones inutiles
* Mettre en évidence l'action ou l'information documentée

### Stockage

```text
/images
```

### Convention de nommage

Format :

```text
acteur-page-detail.png
```

Exemples :

```text
locataire-signaler-formulaire.png
gestionnaire-devis-validation.png
prestataire-executer-photo-avant.png
```

## Composant réutilisable EnCours

Le composant partagé se trouve dans :

```text
snippets/EnCours.mdx
```

Il affiche le message :

```text
🚧 Documentation en cours de rédaction
```

Toutes les pages stub doivent l'utiliser jusqu'à leur validation.

## Vérification avant livraison

Avant de créer une Pull Request :

* Vérifier que `mint dev` démarre sans erreur.
* Vérifier que toutes les pages sont accessibles depuis la navigation.
* Vérifier que chaque page stub affiche le bandeau WIP.
* Vérifier que les captures respectent la convention de nommage.
* Vérifier que les images sont stockées dans `/images`.
* Vérifier que les liens de navigation correspondent à `docs.json`.

## Ressources utiles

Documentation Mintlify :

* https://mintlify.com/docs

Quickstart :

* https://mintlify.com/docs/quickstart
