---
title: "KVM:  grub prompt on VM converted from Parallels Mac."
date: 2013-07-04
forum: Virtualisation
---

### Post by 1clue on 2013-07-04
Hi,

I have an Ubuntu 12.04 server JeOS install which was installed in Mac OS Parallels 5, upgraded to Parallels 8 and then migrated to KVM.

So I converted the disk, opened virt-manager, created a new Linux box with an existing disk, and gave it the disk.  Then I pressed 'run'.

I get the grub prompt.  I don't know a whole lot about grub, I learned lilo and never got the hang of grub.

I booted from the alternate xubuntu image since I already have it on that host.  I tried a rescue, reinstall grub boot loader.  It won't install.

I've verified that the partition containing Linux is /dev/vda1, and I've tried installing the boot loader on /dev/vda and /dev/vda1.

I get "Unable to install GRUB in /dev/vda1.  Executing 'grub-install /dev/vda1 failed.  This is a fatal error."  I get the same thing on any partition I have access to.

Any ideas?

Thanks.

---

### Post by 1clue on 2013-07-04
Solved.  I found a way to convert the image that takes the whole Parallels thing out of the equation.

---

