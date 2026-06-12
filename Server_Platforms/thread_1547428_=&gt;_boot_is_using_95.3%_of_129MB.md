---
title: "=&gt; /boot is using 95.3% of 129MB"
date: 2010-08-06
forum: Server Platforms
---

### Post by waloshin on 2010-08-06
=> /boot is using 95.3% of 129MB Size 129.12 MB / Free 113 kB

So why is it using so much?

And how can I increase the size?

Ubuntu 10.04 lts server 64 bit.

---

### Post by CharlesA on 2010-08-06
Old kernels.

You can remove the ones you don't use anymore.

---

### Post by ian dobson on 2010-08-07
Hi,

just do a dpkg -l | grep linux to see which kernels are installed and just remove the old/unnecessary ones.

Regards
Ian Dobson

---

### Post by oldfred on 2010-08-07
Older command line instructions that still will work.

[http://www.go2linux.org/clean-linux-kernel-images-grub-menu](http://www.go2linux.org/clean-linux-kernel-images-grub-menu)

---

