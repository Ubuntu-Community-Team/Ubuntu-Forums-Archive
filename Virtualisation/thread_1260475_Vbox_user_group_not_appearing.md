---
title: "Vbox user group not appearing"
date: 2009-09-07
forum: Virtualisation
---

### Post by FatalChaos on 2009-09-07
I was trying to add myself to the vbox user group so I could use usb devices, but the vbox user group isn't there. Anyone know what's going on? 

Ubuntu version: 9.10 Karmic 
Guest OS: Windows Xp

---

### Post by dk06 on 2009-09-08
[http://www.howtoforge.com/virtualbox_ubuntu](http://www.howtoforge.com/virtualbox_ubuntu)

Are you sure it installed properly & have you accepted the EULA?

---

### Post by FatalChaos on 2009-09-08
Problem Solved: Manually added self to user group via sudo usermod -G vboxusers -a username. Vbox users still doesn't appear in the users and groups gui, but w/e.

---

