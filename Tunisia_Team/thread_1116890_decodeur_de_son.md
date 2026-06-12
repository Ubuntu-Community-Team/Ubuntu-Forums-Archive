---
title: "decodeur de son"
date: 2009-04-05
forum: Tunisia Team
---

### Post by dark of angel on 2009-04-05
st a tous ,
est ce quel qu un peut m expliquer pourquoi   le meme type de 2 fichier (mp3) l un peut le decode et l autre ne peut pas 
et aussi la solution pour decoder (wmal) 
est ce que je peut installer avec wine un décodeur (windows approprie )
j utilise (vlc, lectur rythmbox)

---

### Post by alaya.zied on 2009-04-06
tu a installé les gstreamers ?

---

### Post by MaWaLe on 2009-04-06
Il aurait suffit d'installer le package : Ubuntu restricted extras
ce package comporte des décodeurs ainsi que le javadonc une fois installé il résoud la majorité des problèmes.

---

### Post by dark of angel on 2009-04-06
> **alaya.zied said:**
> tu a installé les gstreamers ?

oui il est installe, mais il ne peut pas decoder certain les fichier

---

### Post by dark of angel on 2009-04-06
> **MaWaLe said:**
> Il aurait suffit d'installer le package : Ubuntu restricted extras
ce package comporte des décodeurs ainsi que le javadonc une fois installé il résoud la majorité des problèmes.
8 il est installer mais incapable de decoder plusieurs fichier

---

### Post by Nizarus on 2009-04-07
Dark regarde ce billet il pourra peut être t'aider : 
[http://nizaurs.blogspot.com/2009/02/ubuntu-et-les-fichiers-multimedias.html](http://nizaurs.blogspot.com/2009/02/ubuntu-et-les-fichiers-multimedias.html)

---

### Post by RachedTN on 2009-04-07
Les codecs binaires Win32 sont des filtres propriétaires de compression/décompression de flux audio et vidéo 32 bits utilisés par les outils multimédia sous Microsoft® Windows®
Comment les installer ?

Vous pouvez installer ces codecs par paquets, à l'aide de votre gestionnaire de paquets logiciels (méthode recommandée), ou bien manuellement, si vous ne désirez pas ajouter de nouvelles sources de paquets à votre système.

Par paquet

   1.
      Il vous faut premièrement modifier vos sources de mises à jour pour y ajouter le dépôt Medibuntu.
   2.
      Ensuite, installez le paquet correspondant à votre architecture :
          *
            pour Ubuntu Intrepid : non-free-codecs
          *
            pour Ubuntu pour systèmes 32 bits (la plupart des ordinateurs) : w32codecs
          *
            pour Ubuntu pour systèmes 64 bits : w64codecs

Il faut que tu visite ce lien : [http://doc.ubuntu-fr.org/w32codecs]("http://doc.ubuntu-fr.org/w32codecs") pour comprendre comment vous allez faire l'installation.

---

