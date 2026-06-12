---
title: "lecture des radios en net"
date: 2009-05-16
forum: Tunisia Team
---

### Post by dark of angel on 2009-05-16
en ouvrant mosaïque pour l ecouter sur le net et en cherchant le greffon
et apres le recherche du greffon ce message apparait 
"Aucun paquet n’a été trouvé avec les greffons requis.
Les greffons requis sont*:

Source protocole MMS (Microsoft Media Server)"
ce problem je me souvient et tres vite corriger sous ubuntu 8.10 et le greffon est b1 trouver mais cette fois je ne sais pas pourquoi avec 9.04 jai un tel message pareil

---

### Post by omrisaber on 2009-05-16
> **dark of angel said:**
> 
et apres le recherche du greffon ce message apparait 
"Aucun paquet n’a été trouvé avec les greffons requis.
Les greffons requis sont*:


Essayer d'installer le paquet "mplayer for Firefox" (je me souviens pas exactement du nom, tu peux chercher en ouvrant synaptic et en tapant "mplayer" dans la zone de recherche)

---

### Post by omrisaber on 2009-05-16
en fait le paquet est "**[COLOR="DarkRed"]mozilla-mplayer[/COLOR]**" ;)

---

### Post by MaWaLe on 2009-05-18
Il suffit d'utiliser RythmBox
Et en plus tu peux enregistrer la radio  de façon de la retrouver la procahine fois en ouvrant rythmbox.
Personnellement je trouve que c'est meilleur que d'écouter Mosaique avec le navigateur.

---

### Post by RachedTN on 2009-05-18
> **MaWaLe said:**
> Il suffit d'utiliser RythmBox
Et en plus tu peux enregistrer la radio  de façon de la retrouver la procahine fois en ouvrant rythmbox.
Personnellement je trouve que c'est meilleur que d'écouter Mosaique avec le navigateur.

Tu peux aussi enregistrer des videos/audios avec rythmbox :)

---

### Post by gnom2009 on 2009-06-04
salut mawel 5ouya
je suis un etudient de l enig de gabes 
j m appel Ghanem si tu me souvient
je un prob rahou el radio jawhara w mosaique ma yemcouch 3al ubuntu
je telecharger firefox-mediaplayer w  RythmBox
w 9a3ed nafs el message
merci de m aider
a bientot

---

### Post by MaWaLe on 2009-06-05
> **gnom2009 said:**
> salut mawel 5ouya
je suis un etudient de l enig de gabes 
j m appel Ghanem si tu me souvient
je un prob rahou el radio jawhara w mosaique ma yemcouch 3al ubuntu
je telecharger firefox-mediaplayer w  RythmBox
w 9a3ed nafs el message
merci de m aider
a bientot

Si tu nous donnais plus de détails sur ton problème parce que pour moi, Mosaique fonctionne à la perfection et je t'assure que c'est sur Ubuntu :)

---

### Post by omrisaber on 2009-06-05
> **gnom2009 said:**
> salut mawel 5ouya
je suis un etudient de l enig de gabes 
j m appel Ghanem si tu me souvient
je un prob rahou el radio jawhara w mosaique ma yemcouch 3al ubuntu
je telecharger firefox-mediaplayer w  RythmBox
w 9a3ed nafs el message
merci de m aider
a bientot

Je t'assure que ça marche parfaitement !
Ci-joint screenshot de mon pc, (Rythmbox en lecture du radio mosaïque)

PS: je n'écoute pas mosaique radio, mais c'est juste pour essayer si ça marche bien chez moi rn utlisant ubuntu !

[ATTACH]116516[/ATTACH]

---

### Post by helmoony on 2009-06-05
Si tu as Ubuntu 8 passe au 9 et normalement il n'y aura plus de problemes

---

### Post by MaWaLe on 2009-06-07
Il suffit de lancer Rythbox
d'aller sur les Radios
Cliquer avec le bouton Droit et cliquer sur ajouter une nouvelle radio

dans le champs qui va apparaitre il suffit de coller cette adresse telle qu'elle est sans rien changer :
[mms://stream.mosaiquefm.net/mosaique64k]("mms://stream.mosaiquefm.net/mosaique64k")

ensuite il suffit de doube cliquer sur la radion qui vient d'apparaitre dans la liste et le tour est joué ;)

---

### Post by Poyntz on 2009-06-07
> **RachedTN said:**
> Tu peux aussi enregistrer des videos/audios avec rythmbox :)

Tu peut le faire aussi avec mplayer :P

---

### Post by gnom2009 on 2009-06-12
merciiiiiiiii mes amis
bon travail je suis fière de vous;)

---

### Post by hafedh on 2009-07-02
> **MaWaLe said:**
> Il suffit de lancer Rythbox
d'aller sur les Radios
Cliquer avec le bouton Droit et cliquer sur ajouter une nouvelle radio

dans le champs qui va apparaitre il suffit de coller cette adresse telle qu'elle est sans rien changer :
[mms://stream.mosaiquefm.net/mosaique64k]("mms://stream.mosaiquefm.net/mosaique64k")

ensuite il suffit de doube cliquer sur la radion qui vient d'apparaitre dans la liste et le tour est joué ;)

salut;j'ai bien lu ton message j'ai bien essayé d'écouter radio mosaique mais quand meme je n'ai pas réussi.je suis nouveau sur ubuntu et j'ai déja installé la  derniere version 9.04

---

### Post by MaWaLe on 2009-07-03
> **hafedh said:**
> salut;j'ai bien lu ton message j'ai bien essayé d'écouter radio mosaique mais quand meme je n'ai pas réussi.je suis nouveau sur ubuntu et j'ai déja installé la  derniere version 9.04

Hafedh
après avoir installé ton Ubuntu, tape cette commande dans une console :

sudo apt-get install ubuntu-restricted-extras

Le système te demandera de taper ton mot de passe pour vérifier que tu es la bonne personne (disposant des droits sudoer)

Ensuite, lance Rythmbox, dans la section Radio, fait un clic droit, ajouter nouvelle radio et colle le lien que j'ai déjà fourni (il faut faire attention de le coller tel qu'il est sans espace additionnel ou autre).
[mms://stream.mosaiquefm.net/mosaique64k]("mms://stream.mosaiquefm.net/mosaique64k")

L'imposition d'installer les ubuntu restricted extras avant d'ajouter cette radio est du fait que le flux de streaming de MosaiqueFM est un flux mms (donc propriétaire Micro**ft :)

---

