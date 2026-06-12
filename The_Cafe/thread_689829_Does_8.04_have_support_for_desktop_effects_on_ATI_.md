---
title: "Does 8.04 have support for desktop effects on ATI GPU?"
date: 2008-02-06
forum: The Cafe
---

### Post by kool_kat_os on 2008-02-06
Does the 8.04 release have support for desktop effects for the ATI graphic cards....like the ATI Mobility Radeon X700?

---

### Post by Vitamin-Carrot on 2008-02-06
Wouldnt the question be "Will" it have support for desktop effects on ATI

You could Download the alpha and find out that way if you have a spare machine or some extra space.

---

### Post by klange on 2008-02-06
8.04 is currently running on a fairly recent commit of the Git master of Compiz-Fusion. I'm not entirely sure of the status of ATI cards that were previously blacklisted, but I believe the x700 works (Though it may require some setup) - don't quote me on that, I really have no idea. Aside from that, XGL may be needed to get the proper behavior while using frglx.

---

### Post by igknighted on 2008-02-06
All Ubuntu releases should run desktop effects out of the box on that card, the radeon open source driver supports that chipset.  Also, the support for your card has nothing to do with Ubuntu, rather it depends on what drivers ATI releases.

---

### Post by macogw on 2008-02-07
> **igknighted said:**
> All Ubuntu releases should run desktop effects out of the box on that card, the radeon open source driver supports that chipset.  Also, the support for your card has nothing to do with Ubuntu, rather it depends on what drivers ATI releases.

I thought the X... cards were fglrx-only?  This laptop has a Radeon 9600 which I know has open source driver support.  I'm pretty sure the last OpenGL 3D compatible ATI card on open source drivers was the 9250.  The X-series is new, isn't it?

---

### Post by forrestcupp on 2008-02-07
> **macogw said:**
> I thought the X... cards were fglrx-only?  This laptop has a Radeon 9600 which I know has open source driver support.  I'm pretty sure the last OpenGL 3D compatible ATI card on open source drivers was the 9250.  The X-series is new, isn't it?

The HD series is the new series.  I used to have an X800 and that was the cutoff.  I was able to use the open source drivers, but not all of the OpenGL extensions worked, so some opengl apps crashed.  I think anything before X800 works.  I now, unfortunately, have an HD 2600, and the current ATI fglrx drivers are crap if you have any desire to use desktop effects.

---

### Post by Furiattl on 2008-03-19
> **kool_kat_os said:**
> Does the 8.04 release have support for desktop effects for the ATI graphic cards....like the ATI Mobility Radeon X700?

I'm using 8.04 and Radeon 9250 and all desktop effects working fine on the open source ati driver.

---

