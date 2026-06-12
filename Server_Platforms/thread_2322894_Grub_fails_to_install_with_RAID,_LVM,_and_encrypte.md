---
title: "Grub fails to install with RAID, LVM, and encrypted disk with EFI (GPT)"
date: 2016-05-01
forum: Server Platforms
---

### Post by roderick on 2016-05-01
I have been trying to get Ubuntu Server (Xenial) to install with the following setup:

RAID 1 mirror over 2 drives - sda, sdb

I manually create the required partitions (sda1, sdb1) for EFI on both disks (500M) and tag as use for EFI. 

Then I tag the remaining free space as RAID partition (sda2, sdb2) and create the RAID group from these.

In the same manual setup, I create the encrypted volume, followed by the volume group and two logical volumes (one I tag as swap and one as '/').

This all works fine, and the system installs but fails at the grub-installer step. It fails with an error about unable to install grub-dummy.

I have tried dropping to a shell and manually running the grub commands as well as switching to a chroot within the installer. None of these allow me to create a functioning system with this combination of LVM, RAID and encrypted disk using EFI. 

Any solutions? I have tried various tweaks to this and have not been able to make this setup work.

---

### Post by roderick on 2016-05-01
An update:

If I omit creating LVM and do not do full disk encryption (e.g. Just use RAID for swap and '/') and a separate EFI partition, I can get a working system. 

If I omit just the full disk encryption, and keep RAID and LVM, I can get a full working system.

It seems that the installer is getting confused when doing EFI along side an encrypted volume over RAID. 

Hoping someone may have a suggestion.

---

### Post by darkod on 2016-05-01
Did you try separate raid1 /boot partition? Unless I'm wrong encryption needs separate /boot. It needs first to start booting and then ask you for the key. Try separate unencrypted /boot.

---

### Post by roderick on 2016-05-01
Yes, eventually I ended up creating a separate RAID partition for /boot and that allowed me to have the rest of / to be LVM/encrypted/RAID.

I would think this is a case the installer should catch and prevent rather than error/fail. I think Ill reach out to the team and ask.

---

