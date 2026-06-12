---
title: "Problème avec ubuntu: je n'arrive plus à voir les partitions C et D de mon disque"
date: 2008-12-23
forum: Tunisia Team
---

### Post by Salma43 on 2008-12-23
Salem,
je suis une nouvelle utilisatrice de ubuntu.
Quand je l'ai installé çà marche très bien.
Mais depuis ke j'ai supprimé kk programmes et kk dossiers des partitions C et D depuis le système windows je n'arrive plus à voir mes deux partitions.
En fait les dossiers s'affichent mais sont vides alors ke depuis windows ils sont très bien remplis avec mes dossiers.
Autre chose avec skype je n'arrive plus à communiquer avec un appel téléphonique. Problème avec le périphérique de lecture audio.
Merci de me répondre!

---

### Post by 007up on 2008-12-23
aller à Application-> ajouter/supprimer
dans la zonne dérolante afficher choisie d'afficher toutes les application disponibles
puis taper ntfs 
dans les résultats un cocher "outil de configuration NTFS" puis apliquer les changement
après l'installation du programme 
aller à Application -> outil systeme -> outil de configuration NTFS

nommer chaque partition et appliquer les modifications.

---

### Post by Salma43 on 2008-12-24
Merci bp,

le problème est résolu.

Reste le problème de son avec skype car je n'arrive plus à faire des appels depuis ubuntu: problème avec le périphérique de lecture audio.

Merci pour votre aide!

---

### Post by freeh_ on 2009-03-20
> **Salma43 said:**
> Merci bp,

le problème est résolu.

Reste le problème de son avec skype car je n'arrive plus à faire des appels depuis ubuntu: problème avec le périphérique de lecture audio.

Merci pour votre aide!

Essaye de boidouiller un peu la configuration du son entrant/sortant, moi c'est comme sa que sa marche. Sinon branche ton casque ou ton téléphone ensuite redémarre skype pour qu'il auto-detect le périphérique.

---

### Post by TheWhiteTiger on 2009-03-24
le problème c que sa crée un conflit sur l'allocation de la ressource de sortie audio si Skype et une autre application (lecteur de musique ou de vidéo) sont lancés.
Même dans la configuration du son de Skype, on peut trouver un conflit si tu laisse le paramétrage par défaut.
Il faut changer les canaux d'entrée et de sortie pour ne pas allouer la même ressources deux fois.;) , essaie et j'espère que sa va marcher.:D

---

