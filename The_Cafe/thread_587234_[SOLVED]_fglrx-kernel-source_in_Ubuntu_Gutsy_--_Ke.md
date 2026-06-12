---
title: "[SOLVED] fglrx-kernel-source in Ubuntu Gutsy -- Kernel Problems"
date: 2007-10-22
forum: The Cafe
---

### Post by master_kernel on 2007-10-22
I am compiling the 2.6.23.1 kernel and whenever it does compile, I run into two problems.

One, the fglrx module (in ubuntu gutsy) does not compile (exits with an error, I saw something about the new API in 2.6.23, don't know if this has anything to do with it)

Two, I have no sound when I reboot into the new kernel. No devices are found.

Any help is appreciated!



master_kernel

---

### Post by barbro on 2007-10-22
Hello!
I have compiled 2.6.23.1 but now i have huge problems getting my Nvidia (8800GTS) card working under XGL + compiz after installing the 100.14.19 by running the nvidia installer. It is fine running with AIGLX but when i to run XGL with compiz i get the white cube. XGL + compiz work like a charm before installing 2.6.23.1..

How do i fix this white cube bug?

---

### Post by plun on 2007-10-24
> **master_kernel said:**
> I am compiling the 2.6.23.1 kernel and whenever it does compile, I run into two problems.

One, the fglrx module (in ubuntu gutsy) does not compile (exits with an error, I saw something about the new API in 2.6.23, don't know if this has anything to do with it)
l

Within this thread there is patch for 2.6.23
[http://www.phoronix.com/forums/showthread.php?p=16228#post16228](http://www.phoronix.com/forums/showthread.php?p=16228#post16228)

EDIT more about latest driver
[http://www.phoronix.com/scan.php?page=article&item=887&num=1](http://www.phoronix.com/scan.php?page=article&item=887&num=1)

-------
barbro: i believe this is a bug with xserver-xgl, uninstall that package and just use XGL.  It was broken a month ago (also AIGLX)

I also got the "infamous" white cube with xserver-xgl installed.and nVidias driver

.

---

### Post by master_kernel on 2007-10-29
I fixed both problems. The sound issue was caused because I didn't enable the Azalia HD Intel audio support under ALSA. The fglrx problem was fixed after applying 3 patches that I uploaded to the KernelCheck pool repository in patches/fglrx.

Hope this helps someone else!

master_kernel

---

