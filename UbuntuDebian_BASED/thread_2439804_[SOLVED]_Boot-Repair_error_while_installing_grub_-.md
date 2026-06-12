---
title: "[SOLVED] Boot-Repair error while installing grub - Dual boot setup"
date: 2020-04-01
forum: Ubuntu/Debian BASED
---

### Post by erind on 2020-04-01
Hi all,
After I restored linux mint 19.3 using fsarchiver on the linux  partition of a dual-boot setup, I ran Boot-Repair to re-install grub,  however I encountered a few errors shown below. Note that before  restoring the Mint OS, I re-partitioned my disk (removed one redundant  partition) using Gparted.
What was supposed a routine work has turned into a few hours job  without any result so far, and I've tried a few methods reading other  posts in this forum or elsewhere. Any ideas what else can I try?

My pastebin link with Boot-repair info is: [http://paste.ubuntu.com/p/RH7t8BR7tW/](http://paste.ubuntu.com/p/RH7t8BR7tW/)

And the errors after running the Boot-repair commands are:

```
Sourcing file `/etc/default/grub.d/60_mint-theme.cfg'
[B]Generating grub configuration file ...
/usr/bin/grub-mkrelpath: error: failed to get canonical path of `/boot/grub/fonts/UbuntuMono16.pf2'.[/B]
Found linux image: /boot/vmlinuz-5.3.0-45-generic

========

Sourcing file `/etc/default/grub.d/60_mint-theme.cfg'
Generating grub configuration file ...
[B]/usr/sbin/grub-probe: error: failed to get canonical path of `/boot/grub/fonts/UbuntuMono16.pf2'.
No path or device is specified.[/B]
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
[B]dpkg: error processing package grub-pc (--configure):
 installed grub-pc package post-installation script subprocess returned error exit status 64
dpkg: dependency problems prevent configuration of grub-gfxpayload-lists:
 grub-gfxpayload-lists depends on grub-pc (>= 1.99~20101210-1ubuntu2); however:
  Package grub-pc is not configured yet.[/B]

dpkg: error processing package grub-gfxpayload-lists (--configure):
 dependency problems - leaving unconfigured
[B]Errors were encountered while processing:
 grub-pc
 grub-gfxpayload-lists[/B]
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

P.S. I posted before this problem in a different forum too, because I need to fix it as soon as I can. Thanks.

---

### Post by howefield on 2020-04-01
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by erind on 2020-04-03
I solved it by manually installing GRUB:

```

sudo mount /dev/sdb8 /mnt
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt$i; done
sudo chroot /mnt
grub-install /dev/sdb
update-grub
exit
for i in /sys /proc /dev/pts /dev; do sudo umount /mnt$i; done
sudo umount /mnt

```

---

### Post by yancek on 2020-04-03
Thanks for posting your solution.  It is a standard method in some situations.  Your initial post indicates you restored a "partition" so in order to boot it you would need to have reinstalled Grub as you did or update grub from the other OS if is a Linux OS and uses Grub.  Otherwise, the bootloader would have no way of knowing there was another OS to boot.

---

### Post by erind on 2020-04-04
> **yancek said:**
> Thanks for posting your solution.  It is a standard method in some situations.  Your initial post indicates you restored a "partition" so in order to boot it you would need to have reinstalled Grub as you did or update grub from the other OS if is a Linux OS and uses Grub.  Otherwise, the bootloader would have no way of knowing there was another OS to boot.

Exatcly, I needed to re-install Grub, but this time something happened and Boot-Repair got choked on that, but manually worked fine. Something good to know for the future. 

Glad to help!

---

