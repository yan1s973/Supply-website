# Backend- Guide simple

## 1) Le but du projet 
Ce dépôt contient:
- Un serveur Node.js / Express
- Une API pour 3 familles de produits: caméras, peluches, meubles
- Un front statique dans `public/` (pages HTML, CSS, JS)

Le serveur sert:
- Le front (pages)
- Les médias (`/images`, `/videos`)
- Les routes API (`/api/cameras`, `/api/teddies`, `/api/furniture`)

## 2) Prérequis
- le Node.js doit etre installé
- une Connexion Internet (si tu utilises MongoDB Atlas)

## 3) Installation
Depuis la racine du projet:

```bash
npm install
```

## 4) Variables d'environnement
Un fichier d'exemple existe: `.env.example`.

Créer un fichier `.env` à la racine avec au minimum:

```env
PORT=3000
MONGODB_URI=mongodb+srv://<user>:<password>@<cluster>/<database>?retryWrites=true

SMTP_HOST=smtp.office365.com
SMTP_PORT=587
SMTP_SECURE=false
SMTP_USER=...
SMTP_PASS=...
MAIL_FROM=...
ORDER_NOTIFICATION_EMAIL=...
```

Important:
- Ne pas versionner de vrais identifiants (mot de passe SMTP, accès DB).
- Si des secrets réels ont été exposés, il faut les régénérer.

## 5) comment  lancer le projet
Il n'y a pas de script `start` dans `package.json`.

le démarrage se fais avec la commande :

```bash
node server.js
```

Message attendu au démarrage:

```text
Listening on port 3000
```

## 6) Accès local
Une fois lancé:
- Site: `http://localhost:3000`
- Page d'accueil directe: `http://localhost:3000/index.html`

## 7) API disponible
### Cameras
- `GET /api/cameras`
- `GET /api/cameras/:id`
- `POST /api/cameras/order`

### Teddies
- `GET /api/teddies`
- `GET /api/teddies/:id`
- `POST /api/teddies/order`

### Furniture
- `GET /api/furniture`
- `GET /api/furniture/:id`
- `POST /api/furniture/order`

## 8) Ce qu'on a fait ensemble dans cette session
1. Vérification de `package.json`:
   - Aucun script `start` présent.
2. Lancement manuel du serveur:
   - Commande utilisée: `node server.js`.
3. Résultat confirmé:
   - Le serveur écoute sur le port 3000.
4. Incident observé:
   - Échec de connexion MongoDB Atlas (`ECONNREFUSED` DNS SRV sur le cluster).
5. Conséquence:
   - Le serveur web démarre, mais l'accès à la base distante échoue tant que la résolution DNS / accès réseau Atlas n'est pas rétabli.

## 9) Dépannage rapide MongoDB Atlas
Si tu vois "Unable to connect to MongoDB Atlas":
- Vérifier la valeur de `MONGODB_URI` dans `.env`
- Vérifier user/password/database dans l'URI
- Vérifier que l'IP est autorisée dans MongoDB Atlas Network Access
- Vérifier la connectivité DNS (résolution SRV) depuis ton réseau
- Vérifier pare-feu / proxy / VPN de la machine

## 10) Amélioration conseillée (optionnelle)
Ajouter des scripts npm dans `package.json` pour simplifier:

```json
{
  "scripts": {
    "start": "node server.js",
    "dev": "node server.js"
  }
}
```

Ensuite, lancement possible avec:

```bash
npm start
```
## (Petit bonus)

- L'animation de txt au lancement c'est fais grace au logiciel After Effect et a été implémenté au front 

- Aussi pour des raisons inconnus le formulaire n'est plus fonctionnel j'ai donc repris des anciens formulaires de commmandes pour prouver sa fonctionnalité (oui meme si il n'est pas fonctionnel)

