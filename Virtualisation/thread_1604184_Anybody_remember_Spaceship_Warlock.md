---
title: "Anybody remember Spaceship Warlock?"
date: 2010-10-23
forum: Virtualisation
---

### Post by Cadeyrn on 2010-10-23
I still have the disc and I wanted to play for nostalgia. What's the best way to emulate a color Apple II with CD and graphical capabilities under x64 Linux?

---

### Post by BouldRake on 2010-10-23
KEGS.  It's not in the repo, but you can grab it from Sourceforge - [http://kegs.sourceforge.net/](http://kegs.sourceforge.net/)

---

### Post by Cadeyrn on 2010-10-23
Aww, I have to compile it. Oh well, let's try this thing out!

EDIT: Reading the features in the readme... These guys really outdid themselves! The last time I searched for an Apple II emu, I found all the best ones that WEREN'T this one. Sadly, all the other best ones either don't run properly on Linux or Mac OS X (they needed an old Mac), or they simply weren't built to do color.

EDIT2: Ehm, after going through the readmes and trying to compile, KEGS seems to only support x32 Linux. Should I mod it to do x64 or make a virtual box?

---

### Post by BouldRake on 2010-10-23
Sorry, it was months ago I installed it, I forgot what a pain it was.

Here is the solution I used for help installing it on 64 bit:

[http://newsgroups.derkeiler.com/Archive/Comp/comp.emulators.apple2/2009-08/msg00018.html](http://newsgroups.derkeiler.com/Archive/Comp/comp.emulators.apple2/2009-08/msg00018.html)

---

### Post by Cadeyrn on 2010-10-23
...Or I could just make a x32 virtual Ubuntu box. Thanks for the help, though! I'll see if this link is easier.

EDIT: Yeah, it is. I just had to change a single line of code.

---

### Post by Cadeyrn on 2010-10-24
Alright, all I need now is an HD image. The readme says I can type "./to_pro -16384 <filename>" to make it an image, but there is no "to_pro" file for me. only a to_pro.c, which gives errors, probably because it isn't compiled. You run kegs, right? You probably have an HD image you can send me? I can't find one through Google, and I have no idea how to make one from scratch (I don't want to have to partition an HD and make an image of that, plus it wouldn't even be the right filesystem if I did).

---

### Post by Cadeyrn on 2010-11-13
Hello?

---

