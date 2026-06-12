---
title: "Mouse freezes"
date: 2009-11-19
forum: System76 Support
---

### Post by GeneSalamin on 2009-11-19
I'm having a problem with a non-S76 computer.  It's a ZaReason Atom desktop with Intel graphics that has been upgraded to Karmic.  When I'm logged in as myself, the main user, there is no problem.  But when I log in as another user, if I position the mouse cursor over one of the icons on the top bar, the mouse freezes.  When I manage to start an application, if I position the mouse cursor over a button, the mouse freezes, and if I'm in a type-in box, the keyboard also freezes.  Someone suggested typing Alt-F1 to get a terminal, but that doesn't work; the keyboard is frozen along with the mouse.  The mouse and keyboard are USB devices.  If I log out, then log back in as myself, there is no problem.  These freezes began following the upgrade to Karmic.  I've recovered by powering off and back on.  Can someone offer some help?

---

### Post by thomasaaron on 2009-11-20
**HOLY MACKERAL!**
Do you know how much guts it takes to post a ZaReason support request on the System76 forums? :lolflag:
I would never want to face off with you in [the Octagon]("http://www.ufc.com/")! 

Anyway, it's probably just a bad upgrade. There've been a lot of grub problems problems in the 9.04 -> 9.10 upgrade process.

Try running...

sudo apt-get install grub-pc

...and then rebooting. That *may* help. If not, you may want to just do a fresh install.

---

