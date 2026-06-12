---
title: "Nvidia problem with plymouth. Rectified?"
date: 2010-05-22
forum: The Cafe
---

### Post by praveesh on 2010-05-22
Is the ugly boot loader bug with the proprietary drivers rectified?

---

### Post by yabbadabbadont on 2010-05-22
It's working fine for me, but I'm using the *96 version drivers.  I'm also not using a graphical login manager, just straight to a framebuffer console login.  However, it was also working fine when I was using gdm.

---

### Post by WinterRain on 2010-05-22
It works fine for me after an update.

---

### Post by dtfinch on 2010-05-22
I'm pretty sure it worked on mine (GT 240, nvidia-current), but I disabled it since I prefer to see the boot log.

---

### Post by praveesh on 2010-05-22
I installed updates and installed nvidia driver . The uglyness has gone . But the resolution is still too low .

---

### Post by purelinuxuser on 2010-05-22
> **praveesh said:**
> Is the ugly boot loader bug with the proprietary drivers rectified?

Not out of the box for me, I have a GeForce 310M with the stock Lucid Nvidia 195 drivers installed. :( You can see a bug report here: [https://bugs.launchpad.net/ubuntu/+source/xsplash/+bug/551196](https://bugs.launchpad.net/ubuntu/+source/xsplash/+bug/551196) .

HOWEVER, there is a fix that worked well for me: [http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/](http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/) . :)

---

