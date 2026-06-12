---
title: "Installing ATI Radeon 7000 AGP card"
date: 2013-03-04
forum: Ubuntu Studio
---

### Post by hbnmgr on 2013-03-04
Installing an ATI Radeon 7000 AGP dual monitor (No.109-83100-00) video card in my system with UbuntuStudio v11.10 installed.  Which driver set should I look for to install to make this card work? There seems so many listed in Synaptic Pkg.Mgr.

Any help appreciated.

Thanks!
hbnmgr

---

### Post by jejeman on 2013-03-04
If that is old AGP card, then the radeon driver is for it. It should be already active.
Give us
```
lspci -knn | grep VGA -A 5
```

---

### Post by hbnmgr on 2013-03-04
What is that code for?  I haven't installed the card yet, wanted to know if there are drivers for it in ubuntu. Which Radeon driver is for it? Here is what is listed under one driver set, but not sure which CHIP is on my card???

=================
This package provides the 'radeon' driver for the AMD/ATI cards. The
following chips should be supported: R100, RV100, RS100, RV200, RS200,
RS250, R200, RV250, RV280, RS300, RS350, RS400/RS480, R300, R350, R360,
RV350, RV360, RV370, RV380, RV410, R420, R423/R430, R480/R481,
RV505/RV515/RV516/RV550, R520, RV530/RV560, RV570/R580,
RS600/RS690/RS740, R600, RV610/RV630, RV620/RV635, RV670, RS780/RS880,
RV710/RV730, RV740/RV770/RV790, CEDAR, REDWOOD, JUNIPER, CYPRESS,
HEMLOCK, PALM, SUMO/SUMO2, BARTS, TURKS, CAICOS, CAYMAN, ARUBA.

More information about X.Org can be found at:
<URL:http://www.X.org>

This package is built from the X.org xf86-video-ati driver module.
========================

Any idea which chip is on this card? I've looked with a magnifying glass and can't tell.

Thanks!
hbnmgr

---

### Post by jejeman on 2013-03-04
It is eather R100 or RV100.
Just plug in the card, and the system will figure it out.
There are posibly two drivers for it (which are installed by default): xserver-xorg-video-radeon or xserver-xorg-video-ati.
Just make sure that you have those installed.

---

### Post by hbnmgr on 2013-03-04
Apparently they are installed as Synaptic shows a "green" box and only option is to Remove it.  Will install card and report back.
Thanks!

---

