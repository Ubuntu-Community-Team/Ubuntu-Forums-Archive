---
title: "Plus besoin d'utiliser Windows (ou presque)"
date: 2008-06-08
forum: Tunisia Team
---

### Post by hazelnuts84 on 2008-06-08
Bonjour tout le monde

La seule raison pour laquelle j'ai gardé Windows c'était MSN (aMSN et GAIM c'est pas le top)

Là j'ai réussi à l'installer avec Wine.

D'après tous les tests que j'ai fait il n'y a pour le moment que la version 7.0 qui fonctionne

Tout d'abord il faut installer wine :

```
sudo apt-get install wine
```


*Télécharger  msn 7.0 [COLOR="Red"][http://download.microsoft.com/download/9/7/6/976085f9-d0f8-4d96-9208-fc1b461cd3d7/Install_MSN_Messenger.exe]("http://download.microsoft.com/download/9/7/6/976085f9-d0f8-4d96-9208-fc1b461cd3d7/Install_MSN_Messenger.exe")[/COLOR]


*Executer Install_MSN_Messenger.exe (ne pas lancer msn immédiatement)

* Aler a applications > Wine > configure Wine

*cliquer sur ajouter une application et seléctionner msmsgs.exe (Program files/Msn messenger/...)

*Choisir Windows 2000 comme version de windows. (toujours dans l'onglet application)

*appliquer les changements (il ya un bug : il ne garde pas les modification si on ne clique pas sur appliquer)

*aller dans l'onglet bibliothèque et ajouter les DLL's suivants:

-      riched20
-      riched32

*Appliquer

[IMG]http://farm4.static.flickr.com/3060/2567830757_2c2952f61f.jpg[/IMG]
[IMG]http://farm4.static.flickr.com/3166/2567830133_1f33639c3b.jpg[/IMG]

*Maintenat choisir applications > wine > programmes > msn 7.0


* Le tour est joué : malla jaww

[IMG]http://farm4.static.flickr.com/3066/2561620990_706d29e75e_b.jpg[/IMG]

Screenshot (désolé pour les fleurs c'est l'ordinateur à ma copine:) )


L'équipe de wineHQ.org est entrain de travailler sur  un patch pour faire fonctionner Windows Live Messenger


Je le posterais dès qu'il sera dispo


PS : c'est le premier tuto sur ubuntu-tn, j'éspère que tout le monde s'y mette et donne un peu de son temps libre.
THX

---

### Post by R@fik on 2008-06-08
Et bien merci !

J'allais justement essayer d'installer msn après update de wine vers 1rc4


PS : Es tu inscrit sur la mailing list de notre équipe ?

---

### Post by hazelnuts84 on 2008-06-08
c'est déjà fait
THX

:)

---

### Post by R@fik on 2008-06-09
Yeah cool

Mais là j'ai appliqué ton tuto et j'ai un petit problème.

Msn Démarre normalement, j'ai la liste de contacts "sans les noms"; juste les icones.
Quand je double clique sur l'un, je reçois une erreur "We were unable to start a conversation with xxxxxx. You may want to try again"

J'ai wine 1.0rc4 sous hardy

Merci.

---

### Post by hazelnuts84 on 2008-06-09
> **R@fik said:**
> Yeah cool

Mais là j'ai appliqué ton tuto et j'ai un petit problème.

Msn Démarre normalement, j'ai la liste de contacts "sans les noms"; juste les icones.
Quand je double clique sur l'un, je reçois une erreur "We were unable to start a conversation with xxxxxx. You may want to try again"

J'ai wine 1.0rc4 sous hardy

Merci.

comme jte l'ai dit il faut faire une émulation en win 2000 et ajouter les bibliothèques DLL riched20 et riched32



ça m'est arriver et avec cette petite bidoulle ça a fonctionné

Bon courage :D

---

### Post by R@fik on 2008-06-10
C'est bien ce que j'ai fait :/
Tu as la même version de wine que moi ?

---

### Post by hazelnuts84 on 2008-06-10
> **R@fik said:**
> C'est bien ce que j'ai fait :/
Tu as la même version de wine que moi ?


J'utilise la 1.0 RC4

J'ai ajouter des snapshots comme ça tu peux voir ce que j'ai fait exactement

Il faut s'assurer que le msmsgs.exe (à ne pas confondre avec msnmsgr.exe) est en mode emulation win 200 (il faut l'ajouter dans la liste des applications c:/programp files/...../msmsgs.exe")

---

