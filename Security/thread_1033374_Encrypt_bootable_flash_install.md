---
title: "Encrypt bootable flash install?"
date: 2009-01-07
forum: Security
---

### Post by Gitanes on 2009-01-07
I'm wondering if anyone knows whether it's possible to encrypt (with native encryption) a bootable thumb drive install of Ubuntu?

---

### Post by hyper_ch on 2009-01-07
you can encrypt anything but /boot

---

### Post by Gitanes on 2009-01-07
> **hyper_ch said:**
> you can encrypt anything but /boot

Yes, I understand that with regards to installing it on a normal HDD but is it possible with an install encrypted on a thumb drive?  The [tweaks]("http://www.pendrivelinux.com/live-ubuntu-810-usb-persistent-install-windows/#more-630") that I've used to install Ubuntu (from pendrivelinux.com) to my thumb drive doesn't even go through a normal setup procedure (e.g, asking you to make partitions, etc) as one would encounter installing Ubuntu to an HDD from the installation disk. If I'm not mistaken the only time one has the option to create an encrypted install of Ubuntu is during the normal setup, i.e., installing from the installation disk to a HDD.

---

### Post by hyper_ch on 2009-01-07
it is possible... it's just a "block" like a partition that is scrambled and inside you have the real data... if you can partition it and if the kernel has the according modules you can use luks/dm-crypt there also.

---

