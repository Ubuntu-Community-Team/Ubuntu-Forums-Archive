---
title: "(SOLVED)new bcmwl-kernel-source for v3.10.X"
date: 2013-06-18
forum: Ubuntu Development Version
---

### Post by tstc on 2013-06-18
Built. but didn't work 4 me.  YMMV

Tom

[https://launchpad.net/ubuntu/+source/bcmwl/6.30.223.30+bdcom-0ubuntu2/+build/4724924](https://launchpad.net/ubuntu/+source/bcmwl/6.30.223.30+bdcom-0ubuntu2/+build/4724924)

if YMDV report bugs here: [https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/1192314](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/1192314)

(Solved) Reinstalled Saucy and [bcmwl/6.30.223.30+bdcom-0ubuntu2]("https://launchpad.net/ubuntu/+source/bcmwl/6.30.223.30+bdcom-0ubuntu2/+build/4724924") and voila! Problem was that I had some lingering stuff from a b43 module that I had been using as a backup. So far, so good!:guitar:

---

### Post by matt_symes on 2013-06-18
Hi

> **tstc said:**
> Built. but didn't work 4 me.  YMMV

Tom

[https://launchpad.net/ubuntu/+source/bcmwl/6.30.223.30+bdcom-0ubuntu2/+build/4724924](https://launchpad.net/ubuntu/+source/bcmwl/6.30.223.30+bdcom-0ubuntu2/+build/4724924)

if YMDV report bugs here: [https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/1192314](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/1192314)

Thanks for posting this.

My mileage did vary and, hopefully, this will be more stable than 6.30.223.20 was under 3.9.x, as i kept randomly losing connectivity.

As i've just installed it, time will tell.

Kind regards

---

### Post by dino99 on 2013-06-18
kernel 3.10.x should not be installed , as some new dkms are needed and still not available (should land in a few days, so better to wait).

---

### Post by matt_symes on 2013-06-19
Hi

> **dino99 said:**
> kernel 3.10.x should not be installed , as some new dkms are needed and still not available (should land in a few days, so better to wait).

I want the 3.10.rcX kernels early because of the btrfs updates to it.

So far the wl driver works for me.

Kind regards

---

