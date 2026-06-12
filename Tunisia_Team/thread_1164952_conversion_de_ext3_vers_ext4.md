---
title: "conversion de ext3 vers ext4"
date: 2009-05-20
forum: Tunisia Team
---

### Post by dark of angel on 2009-05-20
ubuntu 9.04 donne le choix de mettre le system de fichier ext4(au moment de l installation) au lieu de ext3 
et ces benifisses(ext4) sont:
# Un support de volume allant jusqu&#8217;à 16 EB (exabytes, ou exaoctet, ce qui représente 1 024 pétaoctets ou 1 152 921 504 606 846 976 octets)
# L&#8217;ajout de la date de suppression (dtime) et de la date de création (crtime)
# Le support de la nanoseconde dans l&#8217;enregistrement des dates
# Support des dates jusqu&#8217;au 25 avril 2514 (préparez vous pour le bug d&#8217;avril 2514 !!)
# Le nombre maximum de fichiers est passé à 4 milliards 
# Et le nombre de sous-répertoires possibles est passé de 32 000 à 64 000
# Le support de gros fichiers jusqu&#8217;à 16 TB
et...
+ un gain de temps de démarrage arrive a20% par rapport au matériel( corriger moi s'il ya des fautes)
mais le problème est de faire la convertion de system ext3 vers ext4 sous ubuntu 9.04 en conservant le travail
< jai pas voulu faire  cette convertion qu a apres  la confirmition des utilisateurs de ext4 >
et merci

---

### Post by MaWaLe on 2009-05-21
Personnellement je suis bel et bien sous EXT4 depuis un bon bout de temps déjà et je confirme l'amélioration nette des performances. De même je confirme aussi que ce système de fichier peut être déclaré stable pour les systèmes non-critiques (bien qu'il est toujours conseillé de l'éviter en milieu de production).

Par contre, je doute que passer son système de fichier vers EXT4 ne peut sef aire que par formattage donc ce qui implique impérativment la perte de données du disque à convertir.

---

### Post by Nizarus on 2009-05-22
Bonjour,
Il est possible de passer d'un système de fichiers en ext3 vers un système de fichiers en ext4 sans formater.
J'ai déjà fait l'opération dans jaunty mais mon système a planté après quelques jours d'utilisation. Apparemment c'est un bug connu et beaucoup d'utilisateurs de jaunty on eu ce problème.
Donc ce qui est recommandé pour l'instant c'est de faire un formatage plustôts qu'une conversion.

---

### Post by MaWaLe on 2009-05-22
Ce qui revient à dire : il n'est pas possible de passer de EXT3 vers EXT4 sans formatter :p

Je crois que j'ai déjà vu ça quelque part :d

---

### Post by dark of angel on 2009-05-23
j ai passe de system de fichier ext3 vers ext4 sous ubuntu 9.04 sans formater l ordinateur  et apres 3 jours d utilisation j ai pas des bugs mais  et on va voir ce qui se passe

---

