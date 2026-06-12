---
title: ".wmv files don't work -_-"
date: 2005-02-27
forum: The Cafe
---

### Post by Rhizome21 on 2005-02-27
I'm on Ubuntu and it seems that everything is working except for .wmv files. Whenever I try to open a video .wmv file it would not run.. all i get is totem player blank and distorted sounds.

I installed Mplayer, but I'm also having trouble running stuff on it. It opens, but whenever i try to play a video on it it would just make the computer freeze :S. I tried running it in terminal but same problem.

help is much appreciated :D

---

### Post by delltony on 2005-02-27
try downloading the w32codec
sudo apt-get install w32codec should do the trick.
Hope this helps.

---

### Post by Uuranor on 2005-02-27
w32codec from multi-verse is little old...
I use a rpm version of the newest one converted to .deb with alien :)

---

### Post by Sir.Real on 2006-07-07
I'm having the exact same problem, even after installing the win32 codecs (both using automatix, and "sudo apt-get install w32codecs". I am a linux noob and i don't know what else to do.

Any other suggestions???

---

### Post by tsb on 2006-07-08
> **Uuranor said:**
> w32codec from multi-verse is little old...
I use a rpm version of the newest one converted to .deb with alien :)

or just d/l the file from the source's website and copy them in the "/usr/lib/win32" directory from "sudo nautilus" in terminal

[http://www1.mplayerhq.hu/MPlayer/releases/codecs/essential-20060611.tar.bz2](http://www1.mplayerhq.hu/MPlayer/releases/codecs/essential-20060611.tar.bz2)

---

### Post by siimo on 2006-07-08
there is an easier way!

grab ubuntu penguin liberation front (PLF) repos into your sources.list from:
[http://doc.ubuntu-fr.org/doc/plf](http://doc.ubuntu-fr.org/doc/plf)

and then leech the w32codecs package from there.  Should work with totem player in Ubuntu.

---

