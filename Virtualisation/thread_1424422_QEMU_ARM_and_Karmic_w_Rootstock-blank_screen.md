---
title: "QEMU ARM and Karmic w Rootstock-blank screen"
date: 2010-03-07
forum: Virtualisation
---

### Post by domi007 on 2010-03-07
Hello folks,

I have an HTC Kaiser phone, and I am working currently on building a Ubuntu based distro for this phone. I already have a kernel (2.6.25 if I'm right) and I also made an own initrd based on the Android initrd found on XDA-developers forum.
I put together a rootfs with rootstock (nothing special, LXDE and build-essential).

So, I wanted to test my new distro, so I downloaded qemu-system-arm and tried to launch it with this command:
```
sudo qemu-system-arm -cpu arm946 -kernel ./zImage -initrd initrd.gz -sd sd.img
```

I use the arm946 cpu, because this is the only one which works (any other CPU gives me an error like ```
qemu: hardware error: integratorcm_write: Unimplemented offset 0x4000
```).
My problem is that I only get a blank screen, no output (not in the console, not in the black QEMU window) and my CPU usage goes up to 100%.

I tried to use the official kernel with the -cpu cortex-a8 and it worked, because it showed some output (it didn't find the rootfs).

I wonder if anyone has any idea...sorry if I posted in wrong section, I am not sure that this is a QEMU question anymore :oops::oops::oops:

Thank you anyway,
DOMy

---

### Post by Bombenbach on 2010-04-10
Check out this article in our Rhobuntu Wiki
[http://wiki.xda-developers.com/index.php?pagename=RhodiumUbuntu#QEMU](http://wiki.xda-developers.com/index.php?pagename=RhodiumUbuntu#QEMU)

---

