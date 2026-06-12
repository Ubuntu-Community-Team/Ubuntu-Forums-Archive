---
title: "WoW and Openbox"
date: 2009-01-05
forum: Wine
---

### Post by tpe11etier on 2009-01-05
Hi Folks,

I'm having a mouse issue with openbox when running WoW and was hoping I could get some help.

Prior to running openbox, I was using BTNX with no issue at all.  Openbox is obviously lighter, but I'm having trouble with my side buttons.  They are something like B4 and B5 which is exactly what the middle button left and right are.   So, I'm not able to use all key bindings.

It seems like I could ditch btnx, but I'm not quite sure how to configure the forward/back buttons.

I'm using a logitech G5.

Any help is greatly appreciated.

Thanks

---

### Post by dutchman72 on 2009-01-05
If you look at the website for btnx, they state that the development has halted, and I saw why with the latest kernel patch put out just before Christmas. I run Ubuntu Hoary, and keep up to date with the patches, haven't upgraded to Ibex. And after the patching I saw that with Wow under WINE, all my buttons are now registering correctly, no settings tweaks for a Logitech MX-1000 from before the patching.

Prior to that all the thumb buttons had registered as a mirror for the 2 main buttons and middle mouse, but they now register as buttons 4,5 and 6.

All this means you might be able to remove btnx and have all the buttons register correctly with a full kernel patching to replace it.

---

### Post by tpe11etier on 2009-01-05
Thanks Dutch.

I'm going to try booting right into gnome tonight and see what happens.  I suspect you are right, but I'm thinking Openbox's rc.xml is causing me problems.

I was hoping someone here was running WoW with openbox.  Maybe I could take a look at your rc.xml?

Thanks!

---

