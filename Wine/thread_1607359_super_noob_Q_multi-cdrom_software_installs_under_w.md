---
title: "super noob Q multi-cdrom software installs under wine"
date: 2010-10-27
forum: Wine
---

### Post by fluxlizard on 2010-10-27
Hello all,

I am trying to install diablo 2 under wine using playonlinux.

The problem- when it asks me to change cds during the install, I do not know the proper way of doing this. Wine does not seem aware of when cd is ejected and new cd put in.

Thank you for your help!

This problem seems so basic, but I haven't been able to turn anything up using search here on the forums or ixquick search. Maybe I am asking it wrong?

---

### Post by fluxlizard on 2010-10-29
Wow- nobody knows how to change the cdrom in wine?

If nobody wants to explain that one to me, does anyone know a good step-by-step guide somewhere on the net that walks me through at least the basics of installing multi-cd software with wine?

---

### Post by fluxlizard on 2010-11-01
O-kaaaaaay not a lot of help on a simple request

I've spent a lot of time trying to find the answer on the forums and google. No luck.

Wine *really* needs a user manual.

A comprehensive one.

Badly.

Lack of support documentation and just plain community support is becoming extremely irritating at this point.

Just in case anyone is actually bothering to read this-

I believe I am one step closer to identifying the root of the problem. 

Ubuntu and wine seem to not assign the cdrom drive to wine. This seems to be further frustrated by the fact that ubuntu seems to not identify the cdrom a path until I put a cd in it. And the fact that winecfg seems to not find the cdrom drive when I use that auto feature.

So I guess here is a simpler question for those expert wine users out there who I guess were stumped by my first simple question. 

Exactly how do I tell wine where my cdrom drive is?

Sorry for the sarcasm- I just find it unbelievable that nobody ever installed software that required multi-cds to install with wine, and am frustrated that nobody cares to help.

---

### Post by Refalm on 2010-11-02
If you want something that works like Daemon Tools, you can install "Furius ISO Mount", which you can find in the Ubuntu Software Centre.

---

### Post by fluxlizard on 2010-11-04
Thanks.

I am actually looking for instructions on how to change an actual real physical cd.

But that is a cool software you brought to my attention.

Installed :popcorn:

---

### Post by Soulcage on 2010-11-04
1. Put disc in tray
2. Open terminal type wine /media/Diablo_II_D1/install.exe (or w/e it is)
3. When you're told to change discs you right click on what is on the desktop and choose eject then put in the 2nd disc and repeat.

If that won't work you can type ```
wine eject D:
```
Hope it works.

---

