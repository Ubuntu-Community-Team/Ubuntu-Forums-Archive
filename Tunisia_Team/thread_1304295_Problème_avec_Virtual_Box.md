---
title: "Problème avec Virtual Box"
date: 2009-10-29
forum: Tunisia Team
---

### Post by TheWhiteTiger on 2009-10-29
bonjour tt le monde,

g une machine virtuelle Sun VirtualBox sur mon laptop
version 3.0.8 r53138
sur laquelle j'ai installé un windowsXP sp2, je prblème c que j'ai tout configurer dans les préférences de telle sorte que les ports USB soit fonctionnels, mais là la machine virtuelle les capte, et me les présente "grisés" (non cliquables) , donc j'arrive pas à les utiliser, pourtant elle capte les noms des périphériques branchés sur les USB.
Pouvez vous m'aidez SVP
Mon SE est un UBUNTU 9.04 
merci ;)

---

### Post by Neo31 on 2009-10-29
Salut TheWhiteTiger,
Ce probleme est un bug dans VirtualBox pas dans Ubuntu, J'ai eux le meme probleme sur un autre SE Linux. Je posterai une reponse plus detaillée quand je me rappel des etapes que j'ai fait sur mon SE.

---

### Post by Neo31 on 2009-10-29
OK voila la procedure a faire pour activer l'USB sur VirtualBox :

1. Edition du fichier /etc/rc.sysinit
2. Edition du fichier /etc/udev/rules.d/10-vboxdrv.rules
3. Redemarrer
4. Si ca ne marche pas encore. Installation de VirtualBox Guest Additions


**Etape 1**

1.1
Ouvrir le terminal (CLI : Command Line Interface)

1.2
Executer la commande
```
gedit /etc/rc.sysinit
```1.3
Changer le bloc de code
```
if [ ! -d /proc/bus/usb ]; then
        modprobe usbcore >/dev/null 2>&1 && mount -n -t usbfs /proc/bus/usb /proc/bus/usb
else
       mount -n -t usbfs /proc/bus/usb /proc/bus/usb
fi
```en
```
if [ ! -d /proc/bus/usb ]; then
        modprobe usbcore >/dev/null 2>&1 && mount -n -t usbfs /proc/bus/usb /proc/bus/usb
else
#       mount -n -t usbfs /proc/bus/usb /proc/bus/usb
        mount -t usbfs -o remount,devgid=$(awk -F: '/^vboxusers:/{print $3}' /etc/group),devmode=664 /proc/bus/usb /proc/bus/usb
fi
```1.4
Enregistrer et fermer


**Etape 2**

2.1
Ouvrir le terminal

2.2
Executer la commande
```
gedit /etc/udev/rules.d/10-vboxdrv.rules
```2.3
Changer la ligne
```
KERNEL=="vboxdrv", NAME="vboxdrv", OWNER="root", GROUP="root", MODE="0600"
```en
```
KERNEL=="vboxdrv", NAME="vboxdrv", OWNER="root", GROUP="root", MODE="0660"
```2.4
Enregistrer et fermer


**Etape 3**

3.1
C'est difficile a faire, j'ai oublier comment redemarrer le PC :p


**Etape 4**

4.1
Demarrer VirtualBox

4.2
Demarrer la machine virtuelle

4.3
Se connecter a une session Administrateur de la machine virtuelle Windows

4.4
clic sur l'option "Install guest additions" dans le menu Devices
ou appui sur <HOST>+D (host est le bouton CTRL droit par defaut)


**Voila**

On attend une confirmation que c'est bien passer.
bonne chance.

---

### Post by omrisaber on 2009-10-30
Assalamu alaikom

La version qui se trouve dans les repositoires de ubuntu par défaut c la version OSE (open source) celle-ci ne supporte pas les USB (grisé pour dire que l'autre version closed source l'aye!)

donc tu devrais passer pour la version Closed Source.
Voila la différence entre les 2 : [http://www.virtualbox.org/wiki/Editions](http://www.virtualbox.org/wiki/Editions)

Pour télécharger : [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by Neo31 on 2009-10-30
Oui c'est vrai omrisaber,
J'ai supposer qu'il dispose de la version closed parce qu'il n'as pas mentionner que c'est une version VirtualBox-OSE. mais mm sur la version closed y a un bug pr les USB.
Il peut suivre la demarche que j'ai ecrit pour resoudre le probleme de l'USB avec la closed source :)

---

### Post by TheWhiteTiger on 2009-11-01
Merci Neo31 pour ta coopération, je vien du suivre les étapes que tu ma présenté, mais le bizarre c que je n'aini dans les fichiers rc.sysinit ni 10-vboxdrv.rules les lignes que t'as présenté! de tte façon j'ai essayé de mettre les ligne que t'as mis, mais sans vain!!
:(

concernant la version que j'ai installé omrisaber, c le même lien que tu m'as présenté! c la version même que j'utilise sur ma machine, c pas à partir du ripositoire UBUNTU mé à partir du site de virtual box : [http://download.virtualbox.org/virtualbox/3.0.10/virtualbox-3.0_3.0.10-54097_Ubuntu_jaunty_i386.deb](http://download.virtualbox.org/virtualbox/3.0.10/virtualbox-3.0_3.0.10-54097_Ubuntu_jaunty_i386.deb)

donc, encore, mon problème n'est pas résolu :(

---

### Post by Neo31 on 2009-11-01
TheWhiteTiger
essaye d'ajouter ton compte utilisateur au groupe vboxusers
si tu trouve pas le compte cree le.
je ss pas sure si ca marche mais tu perdera rien de l'essayer.
je ferai une petite recherche kan j'aurai un peut de temps et je te notifira si j'aurai qq chose d'interessant. utilise google english c tres puissant.
bonne chance

---

### Post by RachedTN on 2009-11-03
> **TheWhiteTiger said:**
> bonjour tt le monde,

g une machine virtuelle Sun VirtualBox sur mon laptop
version 3.0.8 r53138
sur laquelle j'ai installé un windowsXP sp2, je prblème c que j'ai tout configurer dans les préférences de telle sorte que les ports USB soit fonctionnels, mais là la machine virtuelle les capte, et me les présente "grisés" (non cliquables) , donc j'arrive pas à les utiliser, pourtant elle capte les noms des périphériques branchés sur les USB.
Pouvez vous m'aidez SVP
Mon SE est un UBUNTU 9.04 
merci ;)

Bonjour

Je pense que vous n'avez pas les droits d'accès nécessaires, donc voilà ce que vous devez faire :
1- Allez à : Système -> Administration -> Utilisateurs et groupes
2- cliquez sur déverrouiller ensuite entrez votre mot de passe.
3-cliquez sur : gérer les groupes
4-défilez en bas et sélectionnez vboxusers ensuite cliquez sur propriétés
5-Mettez 128 ou 127 dans ID de groupe
6-Cochez Tous les membres de groupes (Vous pouvez les cocher tous ou bien en choisir un ou deux selon le besoin)
7- Cliquez sur valider ensuite fermer
8-Redémarrer votre ordinateur

Et voilà, comme par magie ce n'est plus encore grisé :)
Enjoy-it

---

### Post by TheWhiteTiger on 2009-11-05
Salut RachedTN, comment cava?
bon, merci pour l'intervention, mais je te met informé que j'ai déjà essayé cette idée!!
le problème persiste encore, même après l'avoir réessayer après ton intervention! ;(
Aidez moi, j'arrive pas à trouver la solution!!

---

### Post by TheWhiteTiger on 2009-11-06
Salut les amis, bonne nouvelle :D
Je viens de mettre à jour mon SE hier soir de Ubuntu 9.04 à 9.10, et là la surprise! en démarrant le virtualBox, il m'a demander de télécharger la nouvelle version du logiciel :
virtualbox-3.0_3.0.10-54097_Ubuntu_jaunty_i386.deb
le lien [http://dlc-cdn-rd.sun.com/c1/virtualbox/3.0.10/virtualbox-3.0_3.0.10-54097_Ubuntu_jaunty_i386.deb?e=1257463064&h=ab10ac1ff95a62d327ec21f2b1dc9cd3](http://dlc-cdn-rd.sun.com/c1/virtualbox/3.0.10/virtualbox-3.0_3.0.10-54097_Ubuntu_jaunty_i386.deb?e=1257463064&h=ab10ac1ff95a62d327ec21f2b1dc9cd3)

cette nouvelle version, marche bien sous Ubuntu 9.10 et les USB sont reconnus et fonctionnels aussi :D

Donc, avis à tous ceux qui ont le même problème que moi, le remède est dans l'installation de la nouvelle version du logiciel ;-)
merci mes amis!!
enjoy it everybody! :lolflag:

---

### Post by Neo31 on 2009-11-06
Congratulations :)

---

