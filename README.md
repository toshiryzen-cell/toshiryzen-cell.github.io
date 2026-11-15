# Pages publiques pour l'app TikTok

TikTok exige 3 adresses https : CGU, politique de confidentialité, page de retour (Redirect URI).
Ce dossier les contient, à héberger gratuitement sur GitHub Pages.

| Fichier | Adresse une fois en ligne | Champ TikTok |
|---|---|---|
| `terms.html` | `https://<pseudo>.github.io/terms.html` | Terms of Service URL |
| `privacy.html` | `https://<pseudo>.github.io/privacy.html` | Privacy Policy URL |
| `tiktok-callback/index.html` | `https://<pseudo>.github.io/tiktok-callback/` | Redirect URI |
| `index.html` | `https://<pseudo>.github.io/` | Website URL |

La page de retour n'envoie rien à personne : elle affiche l'adresse du navigateur avec un bouton « Copier ».
Aucun cookie, aucun traceur, aucun script externe.

## 1. Compléter

Dans `terms.html` et `privacy.html`, remplace :
- `[YOUR NAME]` par ton nom ou ton pseudo de créateur ;
- `[YOUR CONTACT EMAIL]` par une adresse de contact (une adresse dédiée suffit).

## 2. Mettre en ligne (5 min)

1. Sur https://github.com/new, crée un dépôt **public** nommé exactement `<pseudo>.github.io` (ton pseudo GitHub).
2. **Add file → Upload files** : glisse le **contenu** de ce dossier (pas le dossier lui-même), y compris le dossier `tiktok-callback`. Puis **Commit changes**.
3. **Settings → Pages** : Source = *Deploy from a branch*, branche `main`, dossier `/ (root)`.
4. Attends 1 à 2 minutes et ouvre `https://<pseudo>.github.io/terms.html`.

## 3. Brancher

Dans le portail TikTok, colle les adresses du tableau. Dans `.env` :

```
TIKTOK_REDIRECT_URI=https://<pseudo>.github.io/tiktok-callback/
```

L'adresse doit être **identique** des deux côtés, barre `/` finale comprise.
Puis `docker compose up -d worker` et `python -m app.cli tiktok-auth url` (voir docs/RUNBOOK.md).
