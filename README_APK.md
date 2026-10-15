# Stream TV — projet APK Android (français)

Ce dossier contient un projet Android Studio **complet et prêt à compiler** qui
embarque votre application IPTV (`app/src/main/assets/www/index.html` + lecteurs
HLS/DASH en local) dans une vraie application Android.

**Pourquoi une APK règle vos problèmes :** dedans, la page tourne avec les
pouvoirs d'une appli native — trafic HTTP autorisé, pas de CORS, pas de
blocage de contenu mixte, IP résidentielle directe. Votre serveur Xtream en
`http://` fonctionnera comme dans vos autres applis.

## Méthode 1 : compilation automatique gratuite (recommandée, sans rien installer)

1. Créez un compte sur https://github.com (gratuit).
2. Créez un dépôt **public** nommé par ex. `stream-tv` (bouton « New », cochez
   « Add a README file » pour que le dépôt ne soit pas vide).
3. Dans le dépôt : **Add file → Upload files**, envoyez-y **tout le contenu de
   ce dossier `apk/`** (gardez l'arborescence : `app/`, etc.) **plus le dossier
   `.github/`** fourni à côté dans le zip (indispensable : c'est lui qui lance
   la compilation auto).
4. Onglet **Actions** → cliquez **« I understand my workflows, go ahead and
   enable them »** si demandé → la compilation « Build APK » démarre seule
   (5 à 10 minutes, relancez-la via « Run workflow » si besoin).
5. Une fois terminé (coche verte) : cliquez sur le run → section **Artifacts** →
   téléchargez **stream-tv-apk** → copiez le fichier `app-debug.apk` sur votre
   téléphone / boîtier TV → installez (autoriser « sources inconnues »).

## Méthode 2 : Android Studio (si vous avez un PC)

1. Installez Android Studio, ouvrez ce dossier `apk/`, laissez Gradle se
   synchroniser, puis **Run** sur un téléphone branché en USB (débogage USB)
   ou **Build → Build APK**.

## Mettre à jour l'appli dans l'APK

La page est embarquée : après chaque modification du générateur, recopiez le
nouveau `index.html` vers `app/src/main/assets/www/index.html` (en remplaçant
les 2 lignes CDN `jsdelivr` par `libs/hls.min.js` et `libs/dash.all.min.js`),
recommitez, et relancez le workflow pour une APK fraîche.

## Personnaliser

- Nom affiché : `android:label` dans `app/src/main/AndroidManifest.xml`.
- Identifiant : `applicationId` dans `app/build.gradle` (doit rester unique).
