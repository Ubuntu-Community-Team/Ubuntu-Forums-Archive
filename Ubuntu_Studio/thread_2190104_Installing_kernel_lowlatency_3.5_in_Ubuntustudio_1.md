---
title: "Installing kernel lowlatency 3.5 in Ubuntustudio 12.04"
date: 2013-11-25
forum: Ubuntu Studio
---

### Post by puppett on 2013-11-25
I've been banging my head looking for a  solution for all the week long, and this means the solution is so simple I can't see it or there is no solution at all.

I'm using Precise at the moment, and I don't feel like upgrading because I really want to work with a LTS distro. However my m-audio fast track ultra gives too many xruns and seems like this problem has been solved with the latest lowlatency kernels, starting from the 3.5.

Is there any way to upgrade the kernel without  compiling it? Actually I tried to compile and patch but it didn't work.

Thanks for your help!

---

### Post by puppett on 2013-11-26
This page helps compiling and installing an rt kernel. (3.8, but it's the same for my purpose)

[http://linuxaudio.it/index.php/Latenza](http://linuxaudio.it/index.php/Latenza)

It works, but we have to change this link

[https://www.kernel.org/pub/linux/kernel/projects/rt/3.8/patch-3.8.4-rt2.patch.bz2](https://www.kernel.org/pub/linux/kernel/projects/rt/3.8/patch-3.8.4-rt2.patch.bz2)

with this
[https://www.kernel.org/pub/linux/kernel/projects/rt/3.8/older/patch-3.8.4-rt2.patch.bz2](https://www.kernel.org/pub/linux/kernel/projects/rt/3.8/older/patch-3.8.4-rt2.patch.bz2)

unless we want to install a newer kernel.

No problems, it works fine and I have no xruns at all (HURRAY!!!) but actually the GUI is slowed down (I'm using XCFE). When I move windows the movement looks weak... but I'm pretty sure this is due to the fact that this is actually a REALTIME, not a LOWLATENCY kernel. In fact it can't install ATI proprietary driver.

---

### Post by su:bhatta on 2013-11-26
I have a RT kernel on my Debian Wheezy Machine, 3.2 if I am not mistaken, but it supports both ATI proprietory drivers and I use it with Gnome, still there is no problems of weak movement of windows.

You can add the testing Jessie backports in repos & could give a try to install the 3.8RT from there.

---

