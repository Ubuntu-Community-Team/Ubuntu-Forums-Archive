---
title: "Different versions for PC or laptop"
date: 2011-09-08
forum: System76 Support
---

### Post by New76er on 2011-09-08
I could never download a usable CD from my old PC and used my Pangolin to burn a CD and load it on my HP Media Center PC running a 2002 version of XP.  I do not want to have anything more to do with Windows and only have 11.04 installed.  But Natty keeps referring to my PC as a laptop.  Are there different versions for different types of computers?

When I try to enter sudo commands I'm asked for my password but nothing appears when I type.  I was trying find out why my Amped wireless SR300 repeater would not connect (it's the only one that doesn't) by using the trouble shooter.  But I am stopped because I can't enter my password.

Thank you.

****

---

### Post by drewbenn on 2011-09-08
> **New76er said:**
> I do not want to have anything more to do with Windows and only have 11.04 installed.

Hooray! :guitar:

> But Natty keeps referring to my PC as a laptop.  Are there different versions for different types of computers?

No, the difference is in some of the packages that get installed.  For example, you could issue the command ```
dpkg -l | grep laptop
``` and choose to uninstall any that show up, if you really want (if they aren't hurting anything, I might prefer to leave them alone if it were my computer).  I would guess that 'laptop-mode-tools' got installed by mistake, or maybe there is something about your PC that confused the installer into thinking it is a laptop.

> When I try to enter sudo commands I'm asked for my password but nothing appears when I type.  I was trying find out why my Amped wireless SR300 repeater would not connect (it's the only one that doesn't) by using the trouble shooter.  But I am stopped because I can't enter my password.

Don't worry, that's normal!  Your password does not get echoed at all (so someone looking over your shoulder wouldn't be able to learn how many characters are in your password).  Just type in your password and press enter, and you'll be okay.

Since your questions aren't really System76-specific, you might have gotten better and more responses by posting in a general forum; the System76 employees won't really be able to help you here.  Just sayin' ;)

---

### Post by New76er on 2011-09-09
Thank you for your help, sorry to bother.

---

### Post by drewbenn on 2011-09-12
Not a bother at all!!  I was just hoping to provide a friendly pointer to where your questions would be noticed by the most knowledgeable people :)  Hope my answers helped a little.

---

