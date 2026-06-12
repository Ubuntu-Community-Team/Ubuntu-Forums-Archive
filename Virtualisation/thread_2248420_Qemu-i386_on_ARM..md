---
title: "Qemu-i386 on ARM."
date: 2014-10-14
forum: Virtualisation
---

### Post by hamishmb on 2014-10-14
Hi,

I've been having some issues with qemu, but first here's my setup:

I'm running qemu-i386 on an ARM tablet in an attempt to run wine in user mode.
I know this will probably give me very bad performance, but that's not a problem.
My tablets specs are:

4G storage (allocated to ubuntu 14.04 for ARM) (I'll upgrade this soon to ~12GB with a new sdcard),
1GB ram,
1.0GHz CPU.

It's not great, but it's fast enough for my needs.

So, I downloaded ubuntu 14.04 core for i386, and unpacked it into /usr/i386-ubuntu14.04-gnueabi/, then copied /usr/bin/qemu-i386-static to /usr/i386-ubuntu14.04/gnueabi/usr/bin/.
At this point, I can successfully chroot into my i386 ubuntu installation, and all works fine, and at decent speed.
However, if I try to run an i386 executable with:

qemu-i386 -L /usr/i386-ubuntu14.04-gnueabi/ /usr/i386-ubuntu14.04-gnueabi/bin/bash (or any other i386 executable)

The system maxes the CPU and does absolutely nothing until I kill the process.
I also encountered this in virtualbox on my quad-core system, so it's not about lack of cpu power on my tablet.
Does anyone know what I'm doing wrong?

Thanks in advance,
Hamish

---

### Post by hamishmb on 2014-10-14
Oh, I forgot:

I'm using Linux Deploy for Android to run linux (with LXDE and VNC).
Seeing as I'll have about 12GB of space for Ubuntu, what I can always do is virtualize a full i386 ubuntu installation inside my Linux Deploy installation.
I'm happy to do that if anyone thinks it'll be easier, but my only concern is how well that'll run on a 1GHz CPU with 1GB ram!

Hamish

---

### Post by hamishmb on 2014-10-14
And the answer to that is: very slow indeed.
It took more than 10 minutes to boot the kernel, so that's definetly the end of that idea!

Hamish

---

### Post by hamishmb on 2014-10-26
Okay, I've given up with this because it was too tricky to set it up, so I'll mark it as solved.

---

