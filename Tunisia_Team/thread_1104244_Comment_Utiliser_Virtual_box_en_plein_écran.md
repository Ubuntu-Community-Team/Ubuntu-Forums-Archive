---
title: "Comment Utiliser Virtual box en plein écran ?"
date: 2009-03-23
forum: Tunisia Team
---

### Post by promes_tn on 2009-03-23
J'ai insallé virtual box pour pouvoir utiliser windows xp sous ubuntu, mais lors de l'ouverture, la fenêtre n'est pas affichèe en plein écran (même en utilsant ctrl+F). 
 
[IMG]http://nsa06.casimages.com/img/2009/03/23/090323071527396701.png[/IMG]

alors j'ai essayé de procéder come suit:

[IMG]http://nsa06.casimages.com/img/2009/03/23/090323072054253048.png[/IMG]

mais ce message est apparu:
[IMG]http://nsa06.casimages.com/img/2009/03/23/090323072345703077.png[/IMG]

alors j'ai téléchargé manuellement le fichier iso et j'ai essayé de la déplacer dans le répertoire indiqué dans le message mais:

[IMG]http://nsa06.casimages.com/img/2009/03/23/090323072631359251.png[/IMG]


[IMG]http://nsa06.casimages.com/img/2009/03/23/09032307293864554.png[/IMG]

 je n'ai qu'un seul utilisateur et qu'un seul administrateur, comment faire pour résoudre ce problème ?  J'ai essayé le bouton "skip" mais ça ne fait rien.


Si vous avez des idées (ful screen en virtual box)veuillez m'éclairer ... :(
et merci d'avance pour toutes vos réponses. :D

---

### Post by MaWaLe on 2009-03-24
Bonjour
au fait le problème c'est que tu as téléchargé une version "éclatée" de vBox. C'est à dire l'installable d'un côté et les additions clients de l'autre.

Personnellement ce que je te conseille, c'est de désinstaller la version actuelle que tu as de vBox.

Tu peux copier le fichier .vdi que tu as actuellement pour ne pas perdre l'installation que tu as effectué de ta VM Windows.

Ensuite, tu peux télécharger la version officielle et complète de VirtualBox à partir de ce site en choisissant la version de ton Ubuntu :
[http://www.virtualbox.org/wiki/Linux_Downloads]("http://www.virtualbox.org/wiki/Linux_Downloads")
et après tu réinstalles ta vBox, tu replaces ton fichier .vdi et tu l'attache à la VM que tu vas créer avec ta VirtualBox fraichement installé.

Il y a aussi la méthode d'ajout des dépôts pour Ubuntu qui est conseillée pour ceux qui veulent toujours profiter des dernières mises à jours de VirtualBox au fur et à mesure de leur "release". Cette méthode est indiqué sur la même page indiquée par le lien ci-dessus.

---

### Post by omrisaber on 2009-03-25
assalamu alaikom..

promes_tn, pour le problème de l'erruer lors du copiage de l'image iso demandée, tu dois le faire à partir de la ligne de commande avec le prefixe "[COLOR="Sienna"]**sudo**[/COLOR]"
la commande va devoir ressembler à celle-ci:
> sudo cp /chemin/ton_fichier_iso.iso /chemin destination
le système te demande ton mot de passe, tu n'as qu'à le fournir c tout.

PS: "sudo" permet de te ceder les privilèges d'un root :)

---

