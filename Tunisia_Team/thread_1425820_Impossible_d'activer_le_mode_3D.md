---
title: "Impossible d'activer le mode 3D"
date: 2010-03-09
forum: Tunisia Team
---

### Post by WMDElite on 2010-03-09
Salut a tous,

Oui, c'est moi encore  , mais cette fois avec une probleme différente.

Quand je tente d'activer, le mode 3D, pour jouer au "jeu d'echecs" (Heh échec!!! :-&)
Et bah,, jai echouer... , et c'est le message que je reçoit :frown::




Il est impossible de jouer en mode 3D à cause des problèmes suivants :
Pas de prise en charge Python OpenGL
Pas de prise en charge Python GTKGLExt

Contactez l'administrateur de votre système pour résoudre ces problèmes. En attendant, vous pouvez toujours jouer aux échecs en mode 2D.

S'il vous palait un peut d'aide [-o<

:popcorn:Merci davance.

---

### Post by Bachstelze on 2010-03-09
Est-ce que tu as de la 3D sur d'autres programmes, par exemple [font=monospace]glxgears[/font]? Si oui, il faut peut-être installer les modules Python qui vont bien

```
sudo apt-get install python-opengl python-gtkglext1
```

---

### Post by WMDElite on 2010-03-09
Salut,

j'ai taper la commade mais il me senmble que je demande l'impossible. 

Le voila ce que le système a effectuer:

[B]Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
Certains paquets ne peuvent être installés. Ceci peut signifier
que vous avez demandé l'impossible, ou bien, si vous utilisez
la distribution unstable, que certains paquets n'ont pas encore
été créés ou ne sont pas sortis d'Incoming.
L'information suivante devrait vous aider à résoudre la situation : 

Les paquets suivants contiennent des dépendances non satisfaites :
  python-opengl: Dépend: freeglut3 mais il n'est pas installable
E: Paquets défectueux


:popcorn:[/B]Merci d'avance  pour l'aide [B].
[/B]

---

### Post by Bachstelze on 2010-03-09
L'enfer des dépendances...

```
sudo apt-get install freeglut3
```

Quelle est l'erreur ?

---

### Post by WMDElite on 2010-03-09
Jai taper lacommade sur Terminal:

[B]
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
[COLOR=Red]Aucune version du paquet freeglut3 n'est disponible[/COLOR], [COLOR=Green]mais il existe dans la base
de données[/COLOR]. Cela signifie en général que [COLOR=Green]le paquet est manquant[/COLOR], [COLOR=Blue]qu'il est devenu obsolète
ou qu'il n'est disponible que sur une autre source[/COLOR]
E: Aucun paquet ne correspond au paquet freeglut3
[/B]
Mon systeme d'exploitation est:
Version 8.4 Ubuntu.

---

### Post by WMDElite on 2010-03-10
Salut encore,
J'ai 2 nouvelle ,une bonne et une mauvaise :

1)La bonne nouvelle

J'ai arriver a installer le paquet "freeglut3" en tapant la commande 

```
sudo apt-get install freeglut3[COLOR=Red]-dev[/COLOR]
```Le resultat est:

[SIZE=1][B]Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
Les paquets suivants ont été installés automatiquement et ne sont plus nécessaires :
  fakeroot linux-headers-2.6.28-11 linux-headers-2.6.28-17
  linux-headers-2.6.28-11-generic dkms linux-headers-2.6.28-17-generic patch
Veuillez utiliser « apt-get autoremove » pour les supprimer.
Les paquets supplémentaires suivants seront installés : 
  freeglut3 libgl1-mesa-dev libglu1-mesa-dev libice-dev libpthread-stubs0
  libpthread-stubs0-dev libsm-dev libx11-dev libxau-dev libxcb1-dev
  libxdmcp-dev libxext-dev libxt-dev mesa-common-dev x11proto-core-dev
  x11proto-input-dev x11proto-kb-dev x11proto-xext-dev xlibmesa-gl-dev
  xtrans-dev
Les NOUVEAUX paquets suivants seront installés :
  freeglut3 freeglut3-dev libgl1-mesa-dev libglu1-mesa-dev libice-dev
  libpthread-stubs0 libpthread-stubs0-dev libsm-dev libx11-dev libxau-dev
  libxcb1-dev libxdmcp-dev libxext-dev libxt-dev mesa-common-dev
  x11proto-core-dev x11proto-input-dev x11proto-kb-dev x11proto-xext-dev
  xlibmesa-gl-dev xtrans-dev
0 mis à jour, 21 nouvellement installés, 0 à enlever et 1 non mis à jour.
Il est nécessaire de prendre 3379ko dans les archives.
Après cette opération, 10,9Mo d'espace disque supplémentaires seront utilisés.
Souhaitez-vous continuer [O/n] ? O
Réception de : 1 [http://tn.archive.ubuntu.com](http://tn.archive.ubuntu.com) jaunty/main x11proto-core-dev 7.0.14-2 [92,4kB]
Réception de : 2 [http://tn.archive.ubuntu.com](http://tn.archive.ubuntu.com) jaunty/main libxau-dev 1:1.0.4-1 [16,3kB]
Réception de : 3 [http://tn.archive.ubuntu.com](http://tn.archive.ubuntu.com) jaunty/main libxdmcp-dev 1:1.0.2-3 [20,0kB]
Réception de : 4 [http://tn.archive.ubuntu.com](http://tn.archive.ubuntu.com) jaunty/main x11proto-input-dev 1.5.0-1ubuntu1 [12,0kB]
Réception de : 5 [http://tn.archive.ubuntu.com](http://tn.archive.ubuntu.com) jaunty/main x11proto-kb-dev 1.0.3-3ubuntu1 [27,4kB]
Réception de : 6 [http://tn.archive.ubuntu.com](http://tn.archive.ubuntu.com) jaunty/main xtrans-dev 1.2.3-1 [65,2kB]
Réception de : 7 [http://tn.archive.ubuntu.com](http://tn.archive.ubuntu.com) jaunty/main libpthread-stubs0 0.1-2 [2812B]
Réception de : 8 [http://tn.archive.ubuntu.com](http://tn.archive.ubuntu.com) jaunty/main libpthread-stubs0-dev 0.1-2 [3090B]
Réception de : 9 [http://tn.archive.ubuntu.com](http://tn.archive.ubuntu.com) jaunty-updates/main libxcb1-dev 1.1.93-0ubuntu3.1 [69,0kB]
Réception de : 10 [http://tn.archive.ubuntu.com](http://tn.archive.ubuntu.com) jaunty/main libx11-dev 2:1.1.99.2-1ubuntu2 [1709kB]
Réception de : 11 [http://tn.archive.ubuntu.com](http://tn.archive.ubuntu.com) jaunty-updates/main mesa-common-dev 7.4-0ubuntu3.2 [202kB]
Réception de : 12 [http://tn.archive.ubuntu.com](http://tn.archive.ubuntu.com) jaunty-updates/main libgl1-mesa-dev 7.4-0ubuntu3.2 [26,6kB]
Réception de : 13 [http://tn.archive.ubuntu.com](http://tn.archive.ubuntu.com) jaunty-updates/main libglu1-mesa-dev 7.4-0ubuntu3.2 [202kB]
Réception de : 14 [http://tn.archive.ubuntu.com](http://tn.archive.ubuntu.com) jaunty/main libice-dev 2:1.0.4-1 [56,0kB]
Réception de : 15 [http://tn.archive.ubuntu.com](http://tn.archive.ubuntu.com) jaunty/main libsm-dev 2:1.1.0-1 [25,1kB]
Réception de : 16 [http://tn.archive.ubuntu.com](http://tn.archive.ubuntu.com) jaunty/main x11proto-xext-dev 7.0.4-1 [42,1kB]
Réception de : 17 [http://tn.archive.ubuntu.com](http://tn.archive.ubuntu.com) jaunty/main libxext-dev 2:1.0.99.1-0ubuntu3 [79,2kB]
Réception de : 18 [http://tn.archive.ubuntu.com](http://tn.archive.ubuntu.com) jaunty/main libxt-dev 1:1.0.5-3ubuntu1 [485kB]
Réception de : 19 [http://tn.archive.ubuntu.com](http://tn.archive.ubuntu.com) jaunty/main freeglut3 2.4.0-6.1ubuntu1 [86,9kB]
Réception de : 20 [http://tn.archive.ubuntu.com](http://tn.archive.ubuntu.com) jaunty/main xlibmesa-gl-dev 1:7.4~5ubuntu18 [962B]
Réception de : 21 [http://tn.archive.ubuntu.com](http://tn.archive.ubuntu.com) jaunty/main freeglut3-dev 2.4.0-6.1ubuntu1 [156kB]
3379ko réceptionnés en 46s (72,1ko/s)                                          
Sélection du paquet x11proto-core-dev précédemment désélectionné.
(Lecture de la base de données... 193903 fichiers et répertoires déjà installés.)
Dépaquetage de x11proto-core-dev (à partir de .../x11proto-core-dev_7.0.14-2_all.deb) ...
Sélection du paquet libxau-dev précédemment désélectionné.
Dépaquetage de libxau-dev (à partir de .../libxau-dev_1%3a1.0.4-1_i386.deb) ...
Sélection du paquet libxdmcp-dev précédemment désélectionné.
Dépaquetage de libxdmcp-dev (à partir de .../libxdmcp-dev_1%3a1.0.2-3_i386.deb) ...
Sélection du paquet x11proto-input-dev précédemment désélectionné.
Dépaquetage de x11proto-input-dev (à partir de .../x11proto-input-dev_1.5.0-1ubuntu1_all.deb) ...
Sélection du paquet x11proto-kb-dev précédemment désélectionné.
Dépaquetage de x11proto-kb-dev (à partir de .../x11proto-kb-dev_1.0.3-3ubuntu1_all.deb) ...
Sélection du paquet xtrans-dev précédemment désélectionné.
Dépaquetage de xtrans-dev (à partir de .../xtrans-dev_1.2.3-1_all.deb) ...
Sélection du paquet libpthread-stubs0 précédemment désélectionné.
Dépaquetage de libpthread-stubs0 (à partir de .../libpthread-stubs0_0.1-2_i386.deb) ...
Sélection du paquet libpthread-stubs0-dev précédemment désélectionné.
Dépaquetage de libpthread-stubs0-dev (à partir de .../libpthread-stubs0-dev_0.1-2_i386.deb) ...
Sélection du paquet libxcb1-dev précédemment désélectionné.
Dépaquetage de libxcb1-dev (à partir de .../libxcb1-dev_1.1.93-0ubuntu3.1_i386.deb) ...
Sélection du paquet libx11-dev précédemment désélectionné.
Dépaquetage de libx11-dev (à partir de .../libx11-dev_2%3a1.1.99.2-1ubuntu2_i386.deb) ...
Sélection du paquet mesa-common-dev précédemment désélectionné.
Dépaquetage de mesa-common-dev (à partir de .../mesa-common-dev_7.4-0ubuntu3.2_all.deb) ...
Sélection du paquet libgl1-mesa-dev précédemment désélectionné.
Dépaquetage de libgl1-mesa-dev (à partir de .../libgl1-mesa-dev_7.4-0ubuntu3.2_all.deb) ...
Sélection du paquet libglu1-mesa-dev précédemment désélectionné.
Dépaquetage de libglu1-mesa-dev (à partir de .../libglu1-mesa-dev_7.4-0ubuntu3.2_i386.deb) ...
Sélection du paquet libice-dev précédemment désélectionné.
Dépaquetage de libice-dev (à partir de .../libice-dev_2%3a1.0.4-1_i386.deb) ...
Sélection du paquet libsm-dev précédemment désélectionné.
Dépaquetage de libsm-dev (à partir de .../libsm-dev_2%3a1.1.0-1_i386.deb) ...
Sélection du paquet x11proto-xext-dev précédemment désélectionné.
Dépaquetage de x11proto-xext-dev (à partir de .../x11proto-xext-dev_7.0.4-1_all.deb) ...
Sélection du paquet libxext-dev précédemment désélectionné.
Dépaquetage de libxext-dev (à partir de .../libxext-dev_2%3a1.0.99.1-0ubuntu3_i386.deb) ...
Sélection du paquet libxt-dev précédemment désélectionné.
Dépaquetage de libxt-dev (à partir de .../libxt-dev_1%3a1.0.5-3ubuntu1_i386.deb) ...
Sélection du paquet freeglut3 précédemment désélectionné.
Dépaquetage de freeglut3 (à partir de .../freeglut3_2.4.0-6.1ubuntu1_i386.deb) ...
Sélection du paquet xlibmesa-gl-dev précédemment désélectionné.
Dépaquetage de xlibmesa-gl-dev (à partir de .../xlibmesa-gl-dev_1%3a7.4~5ubuntu18_all.deb) ...
Sélection du paquet freeglut3-dev précédemment désélectionné.
Dépaquetage de freeglut3-dev (à partir de .../freeglut3-dev_2.4.0-6.1ubuntu1_i386.deb) ...
Traitement des actions différées (« triggers ») pour « man-db »...
Paramétrage de x11proto-core-dev (7.0.14-2) ...
Paramétrage de libxau-dev (1:1.0.4-1) ...
Paramétrage de libxdmcp-dev (1:1.0.2-3) ...
Paramétrage de x11proto-input-dev (1.5.0-1ubuntu1) ...
Paramétrage de x11proto-kb-dev (1.0.3-3ubuntu1) ...
Paramétrage de xtrans-dev (1.2.3-1) ...
Paramétrage de libpthread-stubs0 (0.1-2) ...
Paramétrage de libpthread-stubs0-dev (0.1-2) ...
Paramétrage de libxcb1-dev (1.1.93-0ubuntu3.1) ...
Paramétrage de libx11-dev (2:1.1.99.2-1ubuntu2) ...
Paramétrage de mesa-common-dev (7.4-0ubuntu3.2) ...
Paramétrage de libgl1-mesa-dev (7.4-0ubuntu3.2) ...
Paramétrage de libglu1-mesa-dev (7.4-0ubuntu3.2) ...
Paramétrage de libice-dev (2:1.0.4-1) ...
Paramétrage de libsm-dev (2:1.1.0-1) ...
Paramétrage de x11proto-xext-dev (7.0.4-1) ...
Paramétrage de libxext-dev (2:1.0.99.1-0ubuntu3) ...
Paramétrage de libxt-dev (1:1.0.5-3ubuntu1) ...
Paramétrage de freeglut3 (2.4.0-6.1ubuntu1) ...

Paramétrage de xlibmesa-gl-dev (1:7.4~5ubuntu18) ...
Paramétrage de freeglut3-dev (2.4.0-6.1ubuntu1) ...
Traitement des actions différées (« triggers ») pour « libc6 »...
ldconfig deferred processing now taking place

[/B][/SIZE]Et jai arriver a declancher la commande 

```
apt-get install python-opengl python-gtkglext1
```Le resultat de la commnade:

[B]Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
Les paquets suivants ont été installés automatiquement et ne sont plus nécessaires :
  fakeroot linux-headers-2.6.28-11 linux-headers-2.6.28-17
  linux-headers-2.6.28-11-generic dkms linux-headers-2.6.28-17-generic patch
Veuillez utiliser « apt-get autoremove » pour les supprimer.
Les paquets supplémentaires suivants seront installés : 
  libgtkglext1
Paquets suggérés :
  python-tk python-numpy libgle3
Les NOUVEAUX paquets suivants seront installés :
  libgtkglext1 python-gtkglext1 python-opengl
0 mis à jour, 3 nouvellement installés, 0 à enlever et 1 non mis à jour.
Il est nécessaire de prendre 787ko dans les archives.
Après cette opération, 6668ko d'espace disque supplémentaires seront utilisés.
Souhaitez-vous continuer [O/n] ? o
Réception de : 1 [http://tn.archive.ubuntu.com](http://tn.archive.ubuntu.com) jaunty/universe libgtkglext1 1.2.0-1ubuntu1 [108kB]
Réception de : 2 [http://tn.archive.ubuntu.com](http://tn.archive.ubuntu.com) jaunty/universe python-opengl 3.0.0~b6-3 [535kB]
Réception de : 3 [http://tn.archive.ubuntu.com](http://tn.archive.ubuntu.com) jaunty/universe python-gtkglext1 1.1.0-3.1build1 [144kB]
787ko réceptionnés en 12s (63,7ko/s)                                           
Sélection du paquet libgtkglext1 précédemment désélectionné.
(Lecture de la base de données... 195397 fichiers et répertoires déjà installés.)
Dépaquetage de libgtkglext1 (à partir de .../libgtkglext1_1.2.0-1ubuntu1_i386.deb) ...
Sélection du paquet python-opengl précédemment désélectionné.
Dépaquetage de python-opengl (à partir de .../python-opengl_3.0.0~b6-3_all.deb) ...
Sélection du paquet python-gtkglext1 précédemment désélectionné.
Dépaquetage de python-gtkglext1 (à partir de .../python-gtkglext1_1.1.0-3.1build1_i386.deb) ...
Paramétrage de libgtkglext1 (1.2.0-1ubuntu1) ...

Paramétrage de python-opengl (3.0.0~b6-3) ...

Paramétrage de python-gtkglext1 (1.1.0-3.1build1) ...

Traitement des actions différées (« triggers ») pour « libc6 »...
ldconfig deferred processing now taking place
Traitement des actions différées (« triggers ») pour « python-support »...
[/B]

La mauvaise nouvelle ce que quand j'ai voulu jouer au jeu d'échec , et que j'ai mit l'affichage 3D, il c'est fermer et ne veut plus s'ouvrir. Il y a bien marqué "Lancement du jeu d'échec"  le jeu ne se lance pas.


:popcorn:Merci d'avance pour me repondre.

---

