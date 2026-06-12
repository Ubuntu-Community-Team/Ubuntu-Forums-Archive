---
title: "[Request] KGuitar"
date: 2005-06-29
forum: Ubuntu Backports
---

### Post by Quest-Master on 2005-06-29
[http://kguitar.sf.net](http://kguitar.sf.net)

This is pretty much a must-have for me now as I've begun playing guitar, and this app. is like a godsend and would avoid many reboots I make back into Windows for PowerTab and Guitar Pro 4.

Thanks guys.

---

### Post by Quest-Master on 2005-06-30
Just a friendly bump. :)

---

### Post by Knome_fan on 2005-07-01
Hi, thanks for pointing out this great app. I didn't know it was still actively developed.

I think the problem is that kguitar isn't even in breezy as far as I can tell and looking around the net I didn't find a debian package either, so there isn't a big chance of seeing a backport.

However, the good thing is that compiling from source works on hoary without a problem. (Note: I do have a lot of -dev packages already installed, so the only package it complained about was libtse3-dev, which it needs to use midi).

So unless someone comes up with a better solution, I'd suggest to jump right in and compile the app yourself.

Finally, you need to have midi running on your system in order for kguitar to be able to play sound.
Following this howto this should be no problem:
[http://www.ubuntuforums.org/showthread.php?t=30963](http://www.ubuntuforums.org/showthread.php?t=30963)

Have fun!

---

### Post by Quest-Master on 2005-07-01
My ./configure works perfectly fine.. I reach this during make.

> In file included from kguitar_part.cpp:9:
tabsong.h:6:19: qlist.h: No such file or directory
In file included from kguitar_part.cpp:18:
convertxml.h:6:21: qvector.h: No such file or directory
In file included from kguitar_part.cpp:18:
convertxml.h:85: error: 'QVector' is used as a type, but is not defined as a
   type.
make[3]: *** [kguitar_part.lo] Error 1
make[3]: Leaving directory `/home/qmaster/builds/kguitar-0.5/kguitar'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/qmaster/builds/kguitar-0.5/kguitar'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/qmaster/builds/kguitar-0.5'
make: *** [all] Error 2


---

### Post by Knome_fan on 2005-07-02
Hm, just a guess, but IIRC I ran configure with --prefix=/usr. Maybe give it a try and see if the problem goes away.

---

### Post by Quest-Master on 2005-07-02
Nope, same problem.

---

### Post by Knome_fan on 2005-07-03
Ok, I did a little googleing and according to a french ubuntu forum you need libqt3-compat. (I think the package is called libqt3-compat-headers)
[http://forum.ubuntu-fr.org/viewtopic.php?pid=46783](http://forum.ubuntu-fr.org/viewtopic.php?pid=46783)

Disclaimer, my french is terrible, but I think that's what it boils down to.

---

### Post by adriantry on 2005-07-03
I found a deb file at the bottom of this page:
[http://kguitartmp.sourceforge.net/telechargement.html](http://kguitartmp.sourceforge.net/telechargement.html)

I installed it with sudo dpkg -i kguitar_0.0.2-1_i386.deb and everything seemed to go OK.

---

