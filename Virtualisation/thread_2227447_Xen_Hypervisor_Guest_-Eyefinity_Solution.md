---
title: "Xen Hypervisor Guest -Eyefinity Solution"
date: 2014-06-02
forum: Virtualisation
---

### Post by tuxinteger on 2014-06-02
Please see this thread for the working method for Win7 guest for multiple monitor display under AMD Eyefinity and Xen.

[http://ubuntuforums.org/showthread.php?t=2219436&p=13000378#post13000378](http://ubuntuforums.org/showthread.php?t=2219436&p=13000378#post13000378)

Extract :

 Eyefinity Install without the Catalyst full install ,the way around  the BSOD CCC Install - (1) Extract driver package as per Step (5) prior  ,go to the extracted package
    OUTDIR/Packages/Apps/CCC2. (2) Install the ccc-mom-installproxy.msi  manually . (3) Go to the same CCC2 directory -Install  ccc-core-static.msi.
    You should now have the Catalyst Control Centre avaialble ,go to preferences and set to advanced to Setup Multiple Monitors.
   
This was the only way to get multiple monitors working on the Xen W7 guest ,works great.

---

