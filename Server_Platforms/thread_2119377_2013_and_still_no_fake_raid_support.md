---
title: "2013 and still no fake raid support?"
date: 2013-02-23
forum: Server Platforms
---

### Post by pneumatic on 2013-02-23
Every time that the point of the onboard SATA RAID is brought up, the pedantic masses indicate that this method is low performance.

What they don't bring up is that it is a very cost-effective method for creating a durable boot disk for a server that does not require huge disk performance.

Why do I have to buy a $250 raid card to get a durable boot disk?  Why can't I install grub on an mdadm raid?

Really?

---

### Post by darkod on 2013-02-23
What is durable boot disk exactly?

You don't need any raid card to use mdadm SW raid. In fact it is not supposed to work with disks passing through HW raid card.

What do you mean you can't install grub on mdadm? I have it running in my living room right now.

---

### Post by rubylaser on 2013-02-23
I'm not what this is all about.  mdadm is easy to setup and boot from.  It also requires no special hardware.  If you are talking about using the fakeraid built into many motherboards, that is also supported, but then you are hardware dependent. In most cases mdadm is a better solution than fakeraid.

---

### Post by pneumatic on 2013-02-24
A durable boot disk is a raid that will survive a single disk failure.

Someone show me a step-by-step that works as follows:

1) Create a bootable 2 disk mdadm raid1 with grub.
2) Boot the system.
3) Pull one disk.
4) Reboot system.
5) Insert disconnected disk.
6) After resync, pull other disk.
7) Reboot system.
8) Replace disconnected disk with new item.

This can't work with linux without lots of trickery (you can install grub on a per-disk basis and then raid the partitions but this requires lots of installation fiasco and you still need to intervene in the BIOS to select the secondary drive if the primary is flapping).

I can do this on Windows without a real hardware RAID controller.  I can't do this on linux because the kernel devs don't like the performance implications of fake raid.

This pains me.

---

### Post by darkod on 2013-02-24
The steps are just like you described it. There is one important moment during setting up the array, it will ask you if you want it to boot degraded. If you say No, it will not boot with only one disk. It will wait for operator action.
If you say Yes it will boot.

The grub2 by default will install on both disks MBRs, but in case it fails simply double check and install it by hand. After that pull one disk and boot with only one disk to check if it works.

There is no trickery involved.

---

