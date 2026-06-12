---
title: "Grub won't start after successful install"
date: 2014-01-18
forum: Server Platforms
---

### Post by jkugler on 2014-01-18
I've googled best I know, and can't find what I'm looking for.

I have a Gigabyte Z87N-WIFI motherboard.  I installed Ubuntu Server 13.10 via a USB key to a software RAID1 pair of drives.  /boot is on a 500MB RAID1 device.

The setup went without a hitch (well, not too big, I had to do the generic initrd instead of targeted due to a bug).  However, when I rebooted, grub won't even start.  I booted up with a rescue mode, mounted the partitions, and ran (this is from memory):

grub-install --directory=/usr/lib/grub/uefi-x86_64 /dev/sda

also tried /dev/sda1, /dev/sdb, /dev/sdb1.  I verified those drives are the system drives, not the USB key.

However, when the system boots, I see a cursor on a black screen. It advances a line or two, but then the system hangs.  When I was reinstalling grub, I enabled the grub startup sound; that doesn't even ring, so it appears that grub is not starting, or hanging very shortly after that.

How can I troubleshoot this?

Thanks!

---

### Post by Bucky Ball on 2014-01-18
*Thread moved to **Server Platforms**.*

---

### Post by oldfred on 2014-01-18
I do not know RAID and there are so many different versions of RAID.

But if RAID you install grub's boot loader to the root of the RAID.
I think only if you have /boot outside of the RAID, then you have a standard install and then install grub to sda, never to a partition unless you have another boot loader.

Also your motherboard is UEFI.
Did you install in UEFI boot mode? Then you need an efi partition which I think has to be outside RAID and usually first partition on drive. And some have had issues getting efi to boot and have to add another grub.cfg in the efi partition with a configfile pointing to grub.cfg in install.

Single entry like this where yours may be md partitions??
       configfile (hd0,gpt8)/boot/grub/grub.cfg


   found that putting grub.cfg into /EFI/ubuntu works, even when grubx64.efi is in /EFI/Boot

   grub doesn't boot with efi and md raid root
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1229738](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1229738)
RAID install with efi, need configfile and grub in efi partition.
[http://ubuntuforums.org/showthread.php?t=2190716](http://ubuntuforums.org/showthread.php?t=2190716)

---

### Post by jkugler on 2014-01-20
Turns out it did need a EFI partition, even though I thought I enabled all needed Legacy settings.  At any rate, I am up and running. Thank you!

---

