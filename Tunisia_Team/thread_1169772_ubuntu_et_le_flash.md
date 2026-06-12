---
title: "ubuntu et le flash"
date: 2009-05-25
forum: Tunisia Team
---

### Post by dark of angel on 2009-05-25
Bonjour à tous

il m'est impossible de visionner les videos sur facebook
en tapant sur la video je recois le message video unavailble video has been removed (sous ubuntu 9.04) pourtant quand j ete sous ubuntu 8.10 ca fonctionne
comment resoudre ce problème pourtant que j ai installe tout les paquets necessaires:
adobe-flashplugin 
 flashplugin-nonfree 
 flashplugin-installer	 
Gnash 
	mozilla-plugin-gnash gnash 	

Merci

---

### Post by MaWaLe on 2009-05-26
Franchement je ne serai trop quoi te dire parce que chez moi sous la 9.04 et même sous la 9.10 ça marche à la perfection avec moins de package que toi

je n'ai installé que les ubuntu resticted extras et le flash plugin pour firefox.

---

### Post by Neo31 on 2009-05-26
> **dark of angel said:**
> adobe-flashplugin 
 flashplugin-nonfree 
 flashplugin-installer     
Gnash 
mozilla-plugin-gnash gnashJe pense qu'il manque un plugin pour le lecteur video, genre xine, mplayer 7aja ki hakka.
A mon avis installe mplayer et son plugin mozilla.
Reposte un message ici quand ca marche :)

---

### Post by Abouyeza on 2009-05-27
[FONT=Times New Roman][SIZE=4]&#1589;&#1576;&#1575;&#1581; &#1575;&#1604;&#1582;&#1610;&#1585;[/SIZE][/FONT]
J'avais le même genre de problème, du moins je crois, résolu grâce au forum de Ubuntu-fr, en faisant la manipulation suivante :

                                 taper dans la console :
 

 - sudo apt-get remove swfdec-mozilla mozilla-plugin-gnash gnash flashplugin-nonfree adobe-flasplugin
 puis :
 - sudo apt-get install adobe-flashplugin
 

 P.S. : Il vaut mieux que le navigateur soit fermé.
 Doc sur : [http://doc.ubuntu-fr.org/flashplayer](http://doc.ubuntu-fr.org/flashplayer)


Bonne chance, et préviens-nous du résultat,
[SIZE=4]&#1605;&#1593; &#1575;&#1604;&#1587;&#1604;&#1575;&#1605;&#1577;[/SIZE]

---

### Post by MaWaLe on 2009-05-28
Au fait le problème est qu'il y a plusieurs lecteurs FALSF installé donc il risque d'avoir une ambiguité surtout à savoir lequel utiliser par défaut.

Donc un choix à faire :
- Utiliser le lecteur Flash d'Adobe qui n'est pas libre et open source, mais compatible avec tous les sites sauf qu'il comporte aussi quelques bugs
- utiliser des lecteurs flash tel que GNASH qui sont open source mais qui ne sont pas compatibles avec tous les sites

---

### Post by dark of angel on 2009-05-28
> **Neo31 said:**
> Je pense qu'il manque un plugin pour le lecteur video, genre xine, mplayer 7aja ki hakka.
A mon avis installe mplayer et son plugin mozilla.
Reposte un message ici quand ca marche :)
mplayer et son plugin mozilla sont installees
et pas de solution encore!

---

### Post by dark of angel on 2009-05-28
> **Abouyeza said:**
> [FONT=Times New Roman][SIZE=4]&#1589;&#1576;&#1575;&#1581; &#1575;&#1604;&#1582;&#1610;&#1585;[/SIZE][/FONT]
J'avais le même genre de problème, du moins je crois, résolu grâce au forum de Ubuntu-fr, en faisant la manipulation suivante :

                                 taper dans la console :
 

 - sudo apt-get remove swfdec-mozilla mozilla-plugin-gnash gnash flashplugin-nonfree adobe-flasplugin
 puis :
 - sudo apt-get install adobe-flashplugin
 

 P.S. : Il vaut mieux que le navigateur soit fermé.
 Doc sur : [http://doc.ubuntu-fr.org/flashplayer](http://doc.ubuntu-fr.org/flashplayer)


Bonne chance, et préviens-nous du résultat,
[SIZE=4]&#1605;&#1593; &#1575;&#1604;&#1587;&#1604;&#1575;&#1605;&#1577;[/SIZE]
merci  ca marche

---

### Post by helmoony on 2009-05-30
Salut les Ubuntwensa

J'ai eu le meme probleme j'ai installer 36 000 plug ins de flash sur mon Ubuntu 9. C'est de la merde. En plus les flash free sont de très mauvaise qualité je préfère et de loin les logiciels propriétaires des fois comme Flash, Acrobat reader et Skype (même si la version est nieille sur linux mais au moins c est compatible avec Windows).


baslamaaaaaaaaaaaaaaa

---

