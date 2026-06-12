---
title: "ré-installer ubuntu avec windows 7"
date: 2010-04-18
forum: Tunisia Team
---

### Post by TheWhiteTiger on 2010-04-18
Bonsoir tout le monde,
J'ai un laptop sur lequel j'ai cohabité UBUNTU 9.10 et windows7.
Tout marche bien. :lolflag:
Je veux ré-installer une autre fois UBUNTU en supprimant l'installation existante (de UBUNTU) et la changer avec une autre.
En fait j'ai un projet à faire et j'en ai besoin d'une machine réelle et que le SE UBUNTU soit à ces configurations d'origine.
Donc mon objectif, c'est d'effacer un SE et de le remplacer par un autre sans toucher à windows 7 et sans perdre le boot.
peut être j'aurais l'occasion d'essayer Lucid Lynx aussi \\:D/  	\\:D/

---

### Post by Nizarus on 2010-04-19
il suffit d'installer la nouvelle version de ubuntu dans la même patition du disque que l'ancienne version.
Tu peux commencer par supprimer la partition où ubuntu et déjà installée pour qu'elle devienne vide ensuite lors de l'installation de la nouvelle version tu choisis la partition vide.

---

### Post by Neo31 on 2010-04-19
> **Nizarus said:**
> Tu peux commencer par supprimer la partition où ubuntu et déjà installéey a un petit outil appele gparted dans le live CD ubuntu pour supprimer les partitions ubuntu.
apres c simple, tu fait installer en utilisant l'espace libre ;)

une autre solution, c'est d'utiliser les machines virtuelles pour installer une autre version ubuntu pour ton projet.

---

### Post by TheWhiteTiger on 2010-04-28
@ Nizarus : Merci pour la réponse, en fait je croyais que j'allais perdre le boot, c'est pour cela que j'ai poser la question! :-k 8-[
@ Neo31 : oui, bien-sure je connais bien cet outil, merci, d'ailleurs je l'utilise parfois :)

---

### Post by TheWhiteTiger on 2010-04-28
Je vais en  profiter pour installer le Lucid Lynx \\:D/

---

### Post by Hmammou on 2011-01-24
salut 
il suffit d'installer la nouvelle version de ubuntu dans la même patition du disque que l'ancienne version.
Tu peux commencer par supprimer la partition où ubuntu et déjà installée  pour qu'elle devienne vide ensuite lors de l'installation de la  nouvelle version tu choisis la partition vide.
ensuit booter avec le dvd de windows 7
choisi: réparer l'ordinateur pas installer
choisi maintenant réparation du démarrage et continuer
mais maintenant il n'y a plus ubuntu
comment récupérer ubuntu??
tout simplement un logiciel s'appelle EasyBCD
[ici]("http://www.clubic.com/telecharger-fiche33420-easybcd.html")
comment faire pour récupérer ubuntu avec ça ??
installer ce logiciel dans windows 7 et maintenant tu peut récupérer ubuntu
ouvre le logiciel
choisi le bouton "add new entry"
bon maintenant dans le cadre operating system "windows" "linux" "mac" ...
choisi linux
Type: Grub 2
Name: ubuntu
Driver: --------------

Voila
Windows 7 + ubuntu

---

