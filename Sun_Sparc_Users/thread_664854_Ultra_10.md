---
title: "Ultra 10"
date: 2008-01-11
forum: Sun Sparc Users
---

### Post by Polakias on 2008-01-11
I have an Ultra 10 from Sun Microsystems. May ask, the Ubuntu Server can be set up on this? I have to set up solaris, but i would like to try ubuntu!

---

### Post by zanderred on 2008-01-11
Hi, yeh the disk is at [http://cdimage.ubuntu.com/ubuntu-server/dapper/daily/current/](http://cdimage.ubuntu.com/ubuntu-server/dapper/daily/current/) good luck

---

### Post by arfonzo on 2008-01-25
Hi,

I've recently installed from a nightly sparc .iso, it works!

Arfonzo

---

### Post by TehCamel on 2008-01-26
yep - i installed the Server version of 7.10 (I think.. may have been 6.10) recently.
Went straight through, detects everything, and Just Works.

There's a few posts on this forum that should help you if you want a graphical interface too.

---

### Post by arfonzo on 2008-01-26
... I should also mention that I installed ubuntu-server **without local keyboard, mouse and monitor, completely via serial console**. Yes, it all worked (practically) perfectly. Beware the SILO installation limitations (must be within first GB of the first physical disk, being the proper FS type too... do a quick google search to get more details about the SILO bug with certain PROMs, which I believe affects the Ultra 10).

If you're attempting headless install as I described above, you will need a null modem cable to connect your terminal to the Ultra 10. Save yourself the extra cost and upkeep of a monitor!

Good luck!
Arfonzo

---

### Post by BullyCaSa on 2008-02-12
> **arfonzo said:**
> ... I should also mention that I installed ubuntu-server **without local keyboard, mouse and monitor, completely via serial console**. Yes, it all worked (practically) perfectly. Beware the SILO installation limitations (must be within first GB of the first physical disk, being the proper FS type too... do a quick google search to get more details about the SILO bug with certain PROMs, which I believe affects the Ultra 10).

If you're attempting headless install as I described above, you will need a null modem cable to connect your terminal to the Ultra 10. Save yourself the extra cost and upkeep of a monitor!

Good luck!
Arfonzo

Yup, I did the same headless install on my ultra 5/10. I had the latest PROMs so no worries there, and everything went smoothly. Very stable, and has been running for almost 6 months now.

Brian.
Sun Ultra 5/10:  [http://thandi.dyndns.org/](http://thandi.dyndns.org/)

---

