---
title: "Nouveau driver beats nVidia driver in 2D performances"
date: 2007-07-13
forum: The Cafe
---

### Post by BrokeBody on 2007-07-13
The test was made with [GtkPerf](http://gtkperf.sourceforge.net/).

Results:

Nouveau: 24.86 sec
NV: 40.78 sec

wich means progress of 64% in comparement with nv driver. This is a limited 2D test and it doesn't include 3D capabilities, but it certainly points that Nouveau project is on the right way. Most of you probably know that Canonical is giving help and support to this project. More info on [Nouveau web site](http://nouveau.freedesktop.org/wiki/).

---

### Post by Ex-Cyber on 2007-07-13
> **BrokeBody said:**
> Nouveau: 24.86 sec
NV: 40.78 sec[/url].
Isn't "nv" the X.Org driver for NVidia chipsets? Are you talking about nVidia's proprietary drivers, or the one integrated into X.Org?

---

### Post by jiminycricket on 2007-07-13
> **Ex-Cyber said:**
> Isn't "nv" the X.Org driver for NVidia chipsets? Are you talking about nVidia's proprietary drivers, or the one integrated into X.Org?

Yes it's nv compared to Nouveau that they're talking about.

nv is the nVidia open source (but obfuscated) 2d driver
nvidia is the nVidia closed source 3d driver

Still, the fact that open source beats proprietary (or effectively proprietary as nv is) is something important to note.  nVidia's 3d driver still has many annoying bugs that open source will fix.

---

### Post by bread eyes on 2007-07-13
It doesn't really concern me but that's nice.

---

### Post by PatrickMay16 on 2007-07-13
> **bread eyes said:**
> It doesn't really concern me but that's nice.

If it doesn't concern you then why even spend the time to reply?

---

### Post by ~LoKe on 2007-07-13
Not really sure if this even means anything.  Once we start getting into 3D I'll be more inclined to look into it.

I hope it all goes well.

---

### Post by steven8 on 2007-07-14
I think it sounds most promising, and I have great faith in the Nouveau devs.  Great work!!!

---

### Post by bread eyes on 2007-07-14
> **PatrickMay16 said:**
> If it doesn't concern you then why even spend the time to reply?

boredom

---

### Post by fyllekajan on 2007-07-14
Isn't the title misleading? I want all the performance I can get out of my hardware. So I use the nvidia proprietary driver (but then again I also want 3D capabilities). It's nice to see open source alternatives in development though.

---

### Post by Ex-Cyber on 2007-07-14
One [post](http://linuxupdate.blogspot.com/2007/07/nouveau-driver-2d-performance-exceeds.html) reporting these results was updated with a comparison of nv to nvidia, but it's not on the same hardware as the nv vs. nouveau test. It's hard to draw a specific conclusion from this test since it introduces so many variables. There are still questions of configuration, but overall I'd say it looks good.

---

### Post by slimdog360 on 2007-07-14
they didn't even work for me, they even crashed kdm.

---

