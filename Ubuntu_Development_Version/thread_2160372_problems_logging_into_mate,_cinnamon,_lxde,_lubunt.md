---
title: "problems logging into mate, cinnamon, lxde, lubuntu"
date: 2013-07-06
forum: Ubuntu Development Version
---

### Post by rburkartjo on 2013-07-06
note after i upgraded to 13.10 i have problems logging into mate, cinnamon, lxde, lubuntu.

---

### Post by BreezyBrooke on 2013-07-06
Ubuntu 13.10 is in the process of transtioning from GTK3.6 to 3.8 so expect a lot of breakage as there are currently mixed libraries. So Desktops that are heavily GTK dependant will most certantly break. Unity just so happens to not be so strict with GTK support and so isn't truely bothered by this.

---

### Post by zika on 2013-07-07
> **rburkartjo said:**
> note after i upgraded to 13.10 i have problems logging into mate, cinnamon, lxde, lubuntu.LightDM was among upgrades?
Did You try GDM, SliM or startx/xinit...?
Order should be reverse, because startx/xinit is always there and other two should be installed...

---

### Post by rburkartjo on 2013-07-07
i found a way to fix. if i log into the default desktop which is unity i then can log out and load any other flavor i have installed. and if i dont log into unity first cant get the others to load.

---

### Post by vinibali on 2013-07-07
i installed the xfce for my ubuntu, after a restart i cant bring it back to life.
i think u should reinstall...

---

