---
title: "How to test new touchpad driver"
date: 2012-09-16
forum: Ubuntu Dev Link Forum
---

### Post by Beacon11 on 2012-09-16
Hello all.

I obtained the kernel source because I wanted to experiment with the driver for my touchpad. The kernel is currently building with the default parameters.

My question is this: I would like to make some changes to the touchpad driver, but I'm not sure how to test it without messing up my actual install. I don't want to replace the driver that's being used right now, I just want to test this one.

I don't believe the default build will create modules for the mouse driver-- should I build them as modules?

I'm a tad out of my depth and could use some help here. Thanks!

---

### Post by Beacon11 on 2012-09-16
Okay so it looks like it DID build the mouse drivers as modules-- I must have been mistaken. I have a psmouse.ko which is what I want. I know from an lsmod that psmouse is currently loaded. Is it safe to simply rmmod psmouse and insmod my new one? I'm a bit nervous. I would appreciate some advice!

Thank you.

---

### Post by Beacon11 on 2012-09-16
Success! I decided to bite the bullet. Run ```
rmmod psmouse
``` and the mouse stops working . Run ```
insmod <local>/psmouse.ko
``` and the mouse starts working again. ```
rmmod psmouse && modprobe psmouse
``` will put the system's module back in. This isn't so hard!

---

