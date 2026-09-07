# Site vitrine — SDLEP

Site de présentation de la **Sous-direction de la Lutte contre les Épidémies et les
Pandémies** (SDLEP), Ministère de la Santé Publique, République du Cameroun. Site
statique en une page (`index.html`), sans dépendance de build — prêt à déployer tel
quel sur Netlify.

## Contenu

- **Page d'accès** : identifiant/mot de passe avant d'entrer sur le site
- **Hero animé** : ondes de pulsation façon surveillance/radar
- **Mission** : les 8 missions de la SDLEP (Article 56 du décret n° 2013/093)
- **Organisation** : organigramme (SDLEP → 2 services → 4 bureaux, Articles 56-58)
- **Nos outils** : 3 cartes avec lien vers chaque tableau de bord de surveillance

## ⚠️ À faire avant mise en production

1. **Changer les identifiants de connexion.** Ouvrez `index.html`, cherchez
   `SITE_CREDENTIALS` (dans la balise `<script>` en bas de page) et remplacez
   `username`/`password` par les vrais identifiants souhaités.

   **Important : ceci n'est pas une vraie sécurité.** Le mot de passe est visible
   en clair dans le code source de la page (n'importe qui peut l'ouvrir avec
   "Afficher le code source" ou les outils de développement du navigateur). C'est
   un simple filtre qui décourage l'accès direct, pas une protection réelle.
   Pour une vraie authentification, deux options plus robustes :
   - **Netlify Identity** (gratuit, gestion d'utilisateurs côté Netlify)
   - **Password Protection** intégrée de Netlify (offre payante, protège la page
     entière avant même qu'elle ne soit chargée)

2. **Confirmer le lien du tableau de bord Choléra.** Le texte transmis contenait
   une incohérence : le texte affiché du lien pointait vers
   `dashboard-cholera.netlify.app` mais l'adresse réelle du lien était identique
   à celle de la surveillance événementielle (`dashboard-sbc.netlify.app`). En
   attendant confirmation, le site utilise `dashboard-sbc.netlify.app` pour les
   deux cartes, avec un avertissement visible sur la carte Choléra. Cherchez
   `Lien à confirmer` dans `index.html` (2 occurrences) pour corriger.

## Déploiement sur Netlify

1. Poussez ce dépôt sur `github.com/polyglotte03/site-web-sdlep` (déjà fait si vous
   utilisez l'archive fournie)
2. Sur [app.netlify.com](https://app.netlify.com) → **Add new site → Import an
   existing project** → sélectionnez ce dépôt
3. Netlify détecte `netlify.toml` automatiquement (aucune commande de build,
   publication du dossier racine)
4. Déployez

Chaque `git push` sur `main` redéploie automatiquement le site.

## Modifier le contenu

Tout est dans `index.html` (HTML, CSS et JavaScript dans un seul fichier, pas de
dépendances externes à part les polices Google Fonts). Les sections sont
commentées (`<!-- ============ NOM ============ -->`) pour s'y retrouver
facilement.
