---
title: "installation de firefox 3.5"
date: 2009-09-20
forum: Tunisia Team
---

### Post by A-random on 2009-09-20
Bounjour à tous je trouve un grand probleme dans l'installation de la nouvelle firefox.
j'ai télechargé le fichier firefox-3.5.3.tar.bz2 depuis le site de mozilla.
j'ai décomprssé le package et ensuite j'ai utilusé 
./configure
make
make install
et le resultat 
bash: ./configure: Aucun fichier ou dossier de ce type
make: *** Pas de cibles spécifiées et aucun makefile n'a été trouvé. Arrêt.
make: *** Pas de règle pour fabriquer la cible « install ». Arrêt.

je fais quoi maintenant?? merci d'avance

---

### Post by alaya.zied on 2009-09-21
Bonjour,
j'ai déjà fait le test chez moi, et la version qui va s'installé ne s'appelle pas Firefox mais Shiretoko (peut être pour éviter un conflit de nom).
Voici ce que j'ai fait:

Activé le dépôt Universe, puis installez le paquet firefox-3.5.

Pour activer le dépôt universe il suffit d'aller dans Système->Administration->Source de mise à jour, cocher le dépôt.

Pour installer firefox 3.5 (code name Shiretoko): sudo apt-get install firefox-3.5

Source: [http://doc.ubuntu-fr.org/firefox](http://doc.ubuntu-fr.org/firefox)

---

### Post by A-random on 2009-09-21
> **alaya.zied said:**
> Bonjour,
j'ai déjà fait le test chez moi, et la version qui va s'installé ne s'appelle pas Firefox mais Shiretoko (peut être pour éviter un conflit de nom).
Voici ce que j'ai fait:

Activé le dépôt Universe, puis installez le paquet firefox-3.5.

Pour activer le dépôt universe il suffit d'aller dans Système->Administration->Source de mise à jour, cocher le dépôt.

Pour installer firefox 3.5 (code name Shiretoko): sudo apt-get install firefox-3.5

Source: [http://doc.ubuntu-fr.org/firefox](http://doc.ubuntu-fr.org/firefox)
merci beacoup.
c'est resolu

---

### Post by RachedTN on 2009-09-23
Il y'a encore plus simple
Allez dans : Applications -> Ajouter supprimer
Choisir : Toutes les applications disponibles 
ensuite tapez : shiretoko
Cochez la case correspondante et cliquez sur Appliquer et le tour est joué.
Rq : lors du premier lancement de Firefox 3.5, ça va prendra un peu de temps car il fera la mise à jour de la version 3.5.1 beta à la version 3.5.2 stable.
Enjoy it :)

---

