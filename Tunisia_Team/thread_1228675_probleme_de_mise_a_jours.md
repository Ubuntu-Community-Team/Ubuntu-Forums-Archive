---
title: "probleme de mise a jours"
date: 2009-08-01
forum: Tunisia Team
---

### Post by dark of angel on 2009-08-01
sous la version ubuntu9.04  lorsque je  fais la mise a jours
le téléchargement de ces   mises a jours subissent  une interruption en affichant ce message:
[I]E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.[/b][/color][/I]
et merci pour les futurs réponse

---

### Post by Goldenscorp on 2009-08-02
salut dark of angel
Il suffit de faire ce qui est dis dans ce même message d'erreur c'est à dire taper:


           sudo dpkg --configure -a


   *Cela devrait résoudre le problème.

   * Si ça ne marche toujours pas faites:


           sudo apt-get install -f

 
   * Si ça ne marche toujours pas (encore ... cas rare):

 
           sudo dpkg -P --force-all --configure -a


et bonne chance

---

### Post by MaWaLe on 2009-08-03
Très bonne réponse Goldenscorp et ça résoudra Impérativement le problème

juste pour expliquer : ce problème est le résultat d'une mise à jour cassée. Ceci peut être du à :
- Mise à jour précédente incomplète (partielle)
- Désinstallation d'une dépendance d'un logiciel suite à une autre désinstallation
- Mise à jour supprimant un ancien package pour le remplacer avec un nouveau alors que cet ancien package cosntitue une dépendance (exp : installer FireFTP avec Firefox bloque FireGPG : conflit de version de bibliothèque)

Bonne continuation.

---

### Post by Goldenscorp on 2009-08-10
Merci pour explication MaWaLe

---

### Post by hafedh on 2009-08-31
je viens de recevoir ce message;je suis sous ubuntu 9.04.en duel boot avec windows xp. que dois-je faire?est ce que cette erreur peut influencer la stabilité de mon ordinateur:

Un problème insoluble est survenu pendant l'initialisation des informations du paquet.

Veuillez signaler ce bogue du paquet «*update-manager*» en y joignant le message d'erreur suivant*:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/ftp.crihan.fr_ubuntu_dists_jaunty_main_binary-i386_Packages, E:Les listes de paquets ou le fichier «*status*» ne peuvent être analysés ou lus.'

---

### Post by Nizarus on 2009-08-31
@hafedh : essaye ces commandes :

sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update

---

### Post by alaya.zied on 2009-09-02
Merci Nizar pour la solution.
Moi aussi je viens d'avoir le même problème que Hafedh ce matin :p

---

### Post by hafedh on 2009-09-06
merci nizar,tout va bien maintenant!

---

### Post by largo69 on 2012-08-12
E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/fr.archive.ubuntu.com_ubuntu_dists_precise_universe_i18n_Translation-fr%5fFR, E:Les listes de paquets ou le fichier «*status*» ne peuvent être analysés ou lus.


Voila le message que j'ai lorsque je veux faire une mise à jour ou installer un logiciel sous lubuntu

merci pour votre aide

---

### Post by MaWaLe on 2012-08-13
Dans un terminal (ligne de commandes) taper les commandes suivantes dans l'ordre :
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
sudo apt-get upgrade

---

