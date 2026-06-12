---
title: "Problem with Ubuntu Update 20.04"
date: 2020-04-17
forum: Ubuntu Development Version
---

### Post by Herve33700 on 2020-04-17
Hello
when i try to put in oven through the command line my distribution I have an error message:
```
herve@Ubuntu:~$ sudo apt update
[sudo] Mot de passe de herve : 
Atteint :1 http://fr.archive.ubuntu.com/ubuntu focal InRelease
Atteint :2 http://fr.archive.ubuntu.com/ubuntu focal-updates InRelease         
Ign :3 http://dl.google.com/linux/chrome/deb stable InRelease                  
Atteint :4 http://fr.archive.ubuntu.com/ubuntu focal-backports InRelease       
Atteint :5 http://dl.google.com/linux/chrome/deb stable Release                
Atteint :6 http://security.ubuntu.com/ubuntu focal-security InRelease          
Lecture des listes de paquets... Fait               
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
Tous les paquets sont à jour.



```

```
herve@Ubuntu:~$ sudo apt full-upgrade
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
Vous pouvez lancer « apt --fix-broken install » pour corriger ces problèmes.
Les paquets suivants contiennent des dépendances non satisfaites :
 linux-headers-5.4.0-24-generic : Dépend: linux-headers-5.4.0-24 mais il n'est pas installé
E: Dépendances non satisfaites. Essayez « apt --fix-broken install » sans paquet
   (ou indiquez une solution).

```

```
herve@Ubuntu:~$ sudo apt --fix-broken install
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
Correction des dépendances... Fait
Les paquets supplémentaires suivants seront installés : 
  linux-headers-5.4.0-24
Les NOUVEAUX paquets suivants seront installés :
  linux-headers-5.4.0-24
0 mis à jour, 1 nouvellement installés, 0 à enlever et 0 non mis à jour.
103 partiellement installés ou enlevés.
Il est nécessaire de prendre 0 o/11,0 Mo dans les archives.
Après cette opération, 70,7 Mo d'espace disque supplémentaires seront utilisés.
Souhaitez-vous continuer ? [O/n] o
(Lecture de la base de données... 191282 fichiers et répertoires déjà installés.
)
Préparation du dépaquetage de .../linux-headers-5.4.0-24_5.4.0-24.28_all.deb ...
Dépaquetage de linux-headers-5.4.0-24 (5.4.0-24.28) ...
dpkg-deb (sous-processus) : décompression du membre de l'archive : erreur LZMA :
 les données compressées sont corrompues
dpkg-deb: erreur: <decompress> subprocess returned error exit status 2
dpkg: erreur de traitement de l'archive /var/cache/apt/archives/linux-headers-5.
4.0-24_5.4.0-24.28_all.deb (--unpack) :
 impossible de copier les données extraites pour « ./usr/src/linux-headers-5.4.0
-24/drivers/clocksource/Kconfig » vers « /usr/src/linux-headers-5.4.0-24/drivers
/clocksource/Kconfig.dpkg-new » : fin de fichier ou de flux inattendue
Des erreurs ont été rencontrées pendant l'exécution :
 /var/cache/apt/archives/linux-headers-5.4.0-24_5.4.0-24.28_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)




```

Impossible to go further, and impossible to install linux-headers-5.4.0-24
Do you also have this type of problem today?

Thanks

---

### Post by dino99 on 2020-04-17
Hello Hervé

les sources ne sont utiles que pour compiler soit meme des paquets/applications.
Edite le fichier de configuration:

> sudo gedit /etc/apt/sources.list
et copie/colle le contenu en écrasant le précédent contenu:

> deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) focal-updates main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) focal main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) focal universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) focal-updates universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) focal multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) focal-updates multiverse
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) focal partner
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) focal-proposed multiverse universe main restricted

et install synaptic pour une maintenance graphique: > sudo apt-get install synaptic
ensuite installe 'linux-generic' si ce n'est dejà fait.

---

### Post by Herve33700 on 2020-04-17
Bonjour dino99
ok, je pensais qu'en installant directement la version béta on avait un source.list classique.
C'est le source.list qui est officiel pour la version LTS ?
Merci pour ta réponse.


Hello dino99
ok, I thought that by installing the beta version directly we had a classic source.list.
Is the source.list official for the LTS version?
Thank you for your answer.

---

### Post by Herve33700 on 2020-04-17
Bonjour,
merci j'ai recréé mon sources.list en utilisant cette méthode et ça fonctionne:
[https://forum.ubuntu-fr.org/viewtopic.php?pid=21562507#p21562507](https://forum.ubuntu-fr.org/viewtopic.php?pid=21562507#p21562507)

A quoi sert linux-généric ? Et je ne suis pas certain que depuis la dernière version d'Ubuntu synaptic fonctionne, j'avais pas réussi sur le live-usb il y a quelques temps.

---

### Post by dino99 on 2020-04-17
linux-generic est un paquet qui liste les dernières dépendances/versions nécessaires

This package will always depend on the latest complete generic Linux kernel
and headers.

Un usb-live , comme un cdrom, ne peut evidemment pas etre modifié en 'live' sans etre reformaté. Synaptic fonctionne très bien dans l'environnement 'gnome'.

---

### Post by Herve33700 on 2020-04-17
Je viens de l'installer synaptic fonctionne nickel, merci ! linux-generic est installé déjà sur mon PC, merci dino99 pour ton aide !!  J'adore cette communauté Ubuntu ;)

---

