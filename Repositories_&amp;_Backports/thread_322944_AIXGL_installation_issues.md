---
title: "AIXGL installation issues"
date: 2006-12-21
forum: Repositories &amp; Backports
---

### Post by Arcet on 2006-12-21
Hi, 
yesterday i messed up my system while installing AIXGL on a fresh dapper install.
My graphics controller is a intel 82845G running with the i810 driver (direct rendering is on)
I used this guide: [https://help.ubuntu.com/community/CompositeManager/AIGLXOnDapper]("https://help.ubuntu.com/community/CompositeManager/AIGLXOnDapper")

At some point in this guide, i was told to install the package: linux-dri-modules-`uname -r`

uname -r gives the following output: 2.6.15-27-386
this package could not be found. I checked synaptic and could only find 2.6.15-23-386 to 2.6.15-26-386. So i installed 2.6.15-26-386. When i rebooted my system (hoping that AIXGL would start), the screen turned blank, no response what so ever.

Today I reinstalled dapper 6.06, and now my question is: which package should I install? and what could have gone wrong?

Regards, arcey

---

### Post by Arcet on 2006-12-21
I already found the correct package for my kernell on this repository:

deb [http://gandalfn.club.fr/ubuntu](http://gandalfn.club.fr/ubuntu) dapper .

---

