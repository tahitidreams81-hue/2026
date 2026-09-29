# Hitihaunui — générer l'APK

## Option A — dans le cloud, sans rien installer (recommandé)
1. Créez un dépôt GitHub (gratuit) et envoyez-y le contenu de ce dossier
   (bouton « Add file > Upload files » : glissez tous les fichiers, y compris le dossier `.github`).
2. Onglet **Actions** > « Build APK » > **Run workflow** (il démarre aussi tout seul à l'envoi).
3. Après ~5 min, ouvrez l'exécution terminée > **Artifacts** > téléchargez `Hitihaunui-APK`.
4. Dézippez, copiez `app-debug.apk` sur le téléphone et installez-le
   (autorisez « sources inconnues » si Android le demande).

## Option B — sur votre PC (Node 20+, Java 21, Android Studio/SDK)
    npm install
    npx cap add android
    npx cap sync android
    cd android && ./gradlew assembleDebug
L'APK sort dans `android/app/build/outputs/apk/debug/app-debug.apk`.

## Option C — sans code : pwabuilder.com
Hébergez `www/` (Netlify, GitHub Pages…), collez l'URL sur pwabuilder.com > Android.

## Notes
- Les polices Google et la reconnaissance de texte (Tesseract) se chargent depuis Internet :
  hors connexion, police système + OCR indisponible. Le reste fonctionne hors ligne.
- Cet APK « debug » est installable directement. Pour le Play Store il faudra un APK/AAB signé.
