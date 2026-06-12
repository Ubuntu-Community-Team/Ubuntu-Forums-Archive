---
title: "démarrer sa machine virtuel automatiquement"
date: 2010-03-05
forum: Tunisia Team
---

### Post by ismailakira on 2010-03-05
je veux savoir c'est comment ouvrir automatiquement ma machine  virtuelle sans manipulation de la part de l'utilisateur après le  démarrage de la machine hôte .

---

### Post by Neo31 on 2010-03-05
Salut,
tu peut utiliser le binaire VBoxVRDP avec le parametre -startvm pour demarrer une machine virtuelle en ligne de commande.
Voila, c'est le bout de fil a tenir pour commencer ton propre hack, apres tu peut creer un service pour demarrer cette machine avec le systeme ou mettre la ligne dans le fichier rc.local (fichier a verifier) tout simplement.
donc la ligne de commande sera : VBoxVRDP -startvm "HelloWorld"
Comme on a deja dit aujourd'hui, la plupart des problemes ont deja ete posés. donc apres moin de 2 minutes de googling voila la source ou j'ai trouver cette petite info (a verifier toujours les binaires deja existants sur votre OS et ses options et parametres)
[http://ubuntuforums.org/showthread.php?t=701735](http://ubuntuforums.org/showthread.php?t=701735)

---

### Post by alaya.zied on 2010-03-06
Très bien dis Néo.
Oui, en fait si tu a une machine que tu a appelé XP dans virtualBox, il suffit d'ouvrir la console et de taper:
# VBoxManage startvm XP

maintenant si tu veux que ce soit un démarrage automatique, il suffit d'ajouter la commande dans le fichier .bashrc qui se trouve dans ton répertoire home.

---

