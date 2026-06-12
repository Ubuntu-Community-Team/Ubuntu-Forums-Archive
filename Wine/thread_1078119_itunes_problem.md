---
title: "itunes problem"
date: 2009-02-23
forum: Wine
---

### Post by pi.theta on 2009-02-23
i have ubuntu 8.10 - 64 bit installed on core 2 duo intel processor
am having trouble installing itunes through wine

itunes v6- starts install, ends with quicktime error code 1607

itunes v7 & v8 - when trying to install nothing happens

also entries are created for both itunes & quicktime in the wine add/remove soft, and files are also copied in drive_c when installing itunes v6 but proper un-install doesn't take place

---

### Post by cogadh on 2009-02-23
Almost all versions of iTunes barely work in the default Wine:
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=1347](http://appdb.winehq.org/objectManager.php?sClass=application&iId=1347)

You can patch and compile a custom version of Wine that supposedly works, but you might be better off looking for a Linux native app, like Amarok, to replace iTunes.

---

### Post by jocheem67 on 2009-02-23
Is there a reason for you to hang on to iTunes?

---

### Post by pi.theta on 2009-02-23
i tried the installing the custom version but gt into some problem that i couldn't identify.

as for running itunes, i have been using banshee since the past month but tag editing is very tedious in banshee. thats why i wanted to run itunes on ubuntu. i would be grateful if u could suggest an alternative for itunes as far as tag editing is concerned

---

### Post by Traygon on 2009-02-23
Songbird is a cool media application that takes the look of iTunes and builds upon mozilla, it is still in early release, in later releases they will have better mp3 player and iPod support, worth a look:

[http://getsongbird.com](http://getsongbird.com)

---

### Post by Gandolf9517 on 2009-05-01
I still want itunes, because of the music store, app store, and the iphone ringtones support, and the software update. I want to be able to use my future iphone with itunes. Banshee works for any ipod except the touch and iphone, because of the software updates and the lack of the app store, I know that you can use the app store on either, but I feel better using it on the computer

---

### Post by tacantara on 2009-05-01
If you really want iTunes, the only way you're going to get it is to either set up your system as as dual-boot (Linux/Windows) or install a virtual machine program like Sun VirtualBox, and run Windows on the virtual drive.  I chose the latter option, and it works for me.  As large as the Wine apps database is, my experience with it is that the database is mostly games and graphics programs.  They claim to have some success with iTunes, but only with some considerable tweaking.

---

