---
title: "Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)"
date: 2013-04-12
forum: Ubuntu Development Version
---

### Post by ksousa on 2013-04-12
There is any problem with bcmwl-kernel-source 6.20.155.1 and/or ubuntu raring beta with kernel 3.8.0-17 generic.
My wifi is instaled but can't connect (i'm working with ethernet lan) allways trying the connection but nothing.
There is any fix (i "googled" but no solution).
Can anybody help.
So sorry for my bad english
Thanks

---

### Post by fr2632 on 2013-04-12
> **ksousa said:**
> There is any problem with bcmwl-kernel-source 6.20.155.1 and/or ubuntu raring beta with kernel 3.8.0-17 generic.
My wifi is instaled but can't connect (i'm working with ethernet lan) allways trying the connection but nothing.
There is any fix (i "googled" but no solution).
Can anybody help.
So sorry for my bad english
Thanks

Take a look here and let me know if you get fixed:
[http://www.thelinuxguy.nl/how-tos/broadcom-wireless-networking-adapter-is-not-recognised-by-linux-how-to-fix-it/](http://www.thelinuxguy.nl/how-tos/broadcom-wireless-networking-adapter-is-not-recognised-by-linux-how-to-fix-it/)

---

### Post by ksousa on 2013-04-13
First thanks for your help (people like you is one the reason i choose ubuntu for my unique SO)
I tried all the fixes in the link but the problem persist.
I wait for new upgrades for this version.
Thanks again for your time.

---

### Post by dandroid13 on 2013-04-23
Same here, using bcmwl version 6.20.155.1+bdcom-0ubuntu6 it won't connect at all, but if I install the version for Quantal, it works fine.

---

### Post by sdowney717 on 2013-04-24
this worked for mine

```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
```

---

### Post by dandroid13 on 2013-04-24
> **sdowney717 said:**
> this worked for mine

```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
```
It works! But now my bluetooth mouse lags when downloading anything and the cooler fan is noisier.

---

