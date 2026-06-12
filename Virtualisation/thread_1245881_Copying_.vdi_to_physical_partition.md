---
title: "Copying .vdi to physical partition?"
date: 2009-08-21
forum: Virtualisation
---

### Post by c-shadow on 2009-08-21
Virtualbox 3.0.4, Ubuntu 8.10 host, running 9.10 alpha 4 as guest.
I'd like to try 9.10 on the real system, have a couple of partitions to use. Is there any way to transfer the existing 9.10 system from inside the Vbox to one of physical disks?
I already set up users, installed the programs i need, and set up the system the way i like it in vbox.
I was thinking something like this:
- create image (partimage or something) from 9.10 in vbox, or just tar the whole / partition
- transfer it out of vbox and untar to existing partition.
- modify my existing GRUB loader and add entry for 9.10
- modify fstab on 9.10 to correctly mount other disks
- sync the needed stuff from my current /home (firefox, thunderbird profiles,...)
- boot karmic and set up hardware (nvidia, wireless,...)
Is there anything I forgot?

---

