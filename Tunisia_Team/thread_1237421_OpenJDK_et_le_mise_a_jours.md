---
title: "OpenJDK et le mise a jours?"
date: 2009-08-11
forum: Tunisia Team
---

### Post by dark of angel on 2009-08-11
lors de telechargement de ces paquets liéé au OpenLDK une fenetre s'ouvre en ecrivant ce message
E: Impossible de verrouiller /var/cache/apt/archives/lock - open (11 Ressource temporairement non disponible)
E: Impossible de verrouiller le répertoire de téléchargement

---

### Post by MaWaLe on 2009-08-12
Ce message n'est pas en relation avec la mise à jour de OpenJDK
Ce message apparait quand deux instances de gestionnaires de paquets (apt, synaptic, aptitude, dpkg ou le gestionnaire de mise à jours) sont lancés simultanément.

Donc ce qu'il faut vérifier :
- si tu as un autre logiciel de gestion de package qui est lancé il faut le fermer parce qu'une fois lancé, ce logiciel "verrouille" le répertoire de cache de apt pour y lire les packages déjà installer et y télécharger les nouvelles versions.
L'objectif d'une telle manoeuvre est d'assurer l'homogénéité du répertoire en question pour éviter tout éventuel conflit entre deux mise à jour concuirrente.

Une fois ce deuxième gestionnaire de packages fermé, tu peux relancer ta mise à jour qui se déroulera sans problème.

Il est à noter pour certains développeurs, qu'il vaut mieux (malheureusement) ne pas utiliser la version OpenJDK (qui n'est pas très conseillé avec les IDE tel que NetBeans mais d'avoir recours au SDK complet de JDK et ce par souci de compatibilité et de disponibilité de bibliothèques.
Donc Penser à la configuration alternative de Java pour cet usage.

---

