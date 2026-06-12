---
title: "problem to mount VBox Guest additions"
date: 2009-06-02
forum: Virtualisation
---

### Post by debuntu7561 on 2009-06-02
Hi there;

My host system is ubunutu 8.04 dktp. My guset system is ubuntu 9.04 sever.

I can't mount the VBoxGuestAdditions_2.2.0.iso file despite the cd-rom is set to this image.
I've got nothing in /media/cdrom or /media/cdrom0.

thanks for your help
jef

---

### Post by lonerook on 2009-06-15
Did you try to mount it from the guest system as well? As far as I understand, virtualbox simply lets the operating system that a physical cdrom is inserted, but it is not actually mounted (unless some kind of automount is set up inside the guest).

Hence, try the following on your Ubuntu guest system:

  sudo mount /dev/scd0 /media/cdrom

and hopefully you will get the cd mounted in /media/cdrom.

Theoretically, the disk image you also be put in /dev/scx, where x = 1,2,3..., and in that case adjustments have to be done. Try "sudo fdisk -l /dev/scd0" etc to see what is actually in that hardware slot.

---

