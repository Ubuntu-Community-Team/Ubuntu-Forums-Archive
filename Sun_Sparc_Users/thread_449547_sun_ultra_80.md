---
title: "sun ultra 80"
date: 2007-05-20
forum: Sun Sparc Users
---

### Post by didijeeeke on 2007-05-20
Hey i bought myself a sun ultra 80 workstation 

a 30 kg big case lol :)

4 cpu 450 mgz 
2gb ram

But my problem is i bought this system second hand and it boots into solaris and asks a password (wish i don't know).

So i tried to install the ubuntu sparc server but it wont boot of the cdrom...

I don't know how to get into the bios please help.

---

### Post by mahy on 2007-05-20
You should've asked in the Sun SPARC section of this forum. Anyway, make sure you download the correct CD, i.e. the version for SPARC, not common Intel-based computers. This is it: [http://releases.ubuntu.com/7.04/ubuntu-7.04-server-sparc.iso](http://releases.ubuntu.com/7.04/ubuntu-7.04-server-sparc.iso)

Burn it,  power up the computer, put it into the CD drive and press Stop+A as soon as the screen comes to life. Then type "boot cdrom" and press Enter. That's it.

---

### Post by didijeeeke on 2007-05-20
thanks,

this system keeps suprizing me lol

but now i have this other problem the setup does not have my keyboard type
sun type 6

only 4 and 5 when i select one of those lot's of important keys like up down don't work
and i can't use a other keyboard the sun uses a weird connector

---

### Post by netztier on 2007-05-21
> **didijeeeke said:**
> thanks,

this system keeps suprizing me lol

but now i have this other problem the setup does not have my keyboard type
sun type 6

only 4 and 5 when i select one of those lot's of important keys like up down don't work
and i can't use a other keyboard the sun uses a weird connector

With Linux 2.6 kernels, you have to choose **pc104/105** as keyboard layout, *not* sun type4 or type 5. Weird, but correct. And answered many times in this forum which - wouldn't you believe it - actually *does* have a search function.

best regards

Marc

---

