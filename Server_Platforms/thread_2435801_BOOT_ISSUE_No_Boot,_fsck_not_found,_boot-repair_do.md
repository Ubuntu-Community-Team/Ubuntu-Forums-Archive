---
title: "BOOT ISSUE: No Boot, fsck not found, boot-repair doesn't work"
date: 2020-01-26
forum: Server Platforms
---

### Post by JusticeEmpire on 2020-01-26
Hi All,

You may be able to see from a few of my other threads, but I had started to build a server for small business use (18.04 on HP MicroServer Box). After it being shelved for a little while, I went back to trying to get it setup and running, but soon discovered a problem....... it doesn't boot properly anymore. I'm suspecting this to be down to lack of maintenance and a power cut.

If i let it run, I end up at a busybox prompt. 

I've googled and tried to fix from there, but 'fsck' or 'e2fsck' isn't found. I've managed to load grub, but various attempts from there did nothing. I tried a live usb, with boot repair installed. but a multitude of error messages e.g. system in legacy boot, run from uefi..... hindered any progress there. The only useful piece of information i could deduce was that my 250GB SSD (where OS should be) came up as an unknown file system, which i assume means that it's not mounted anymore.

I will keep having an attempt at trying to fix it, obviously an OS reinstall is an option but the last option, but I thought I'd post on here and ask if anyone can see something obvious?

Many thanks in advance

---

### Post by oldfred on 2020-01-26
If you can run Boot-Repair, post the link it gives for the Summary Report.

If at a grub prompt, you cannot run most commands, just a few boot related.
You would have to mount partition(s) and run e2fsck from there.

Use Ubuntu live installer, not Boot-Repair ISO. And if install is UEFI, be sure to boot live installer in UEFI boot mode, or you do get a lot complaints unless you want to convert from UEFI to old BIOS.

---

### Post by JusticeEmpire on 2020-03-03
OK, I've spent some time on this trying to get it sorted, and still not having much luck, although I do think I'm starting to narrow down the fault/s. I can't login via SSH at the moment, so copy/pasting information is a tad difficult.

 I've tried using boot-repair, but it's not made any difference. When I had enough of it, I attempted to reinstall the OS, using the LVM partitions already there, and even though I got an 'installation successful' message, I'm still stuck in a boot loop. When I'm at the install screen, I get various options when to select an installation disk....
[U]
Available devices:[/U]
[vg (existing), LVM Volume Group, 7.2T
 MBData existing, already formatted as ext4, not mounted, 2.0T
 free space 5.2T ]
[ubuntu-vg (existing), LVM Volume Group, 222.5G
 ubuntu-lv existing, already formatted as ext4, not mounted, 4.0G
 free space 218.5G]
[220GB SSD Drive, local disk, 223.5G
 partition 1, existing, already formatted as ext4, not mounted
 free space 1.0M]

_Used devices:_ 

Lists 2 x software raid 1, 220GB and 4 x 2T drives.


This leads me to thinking that the reason the system isn't booting properly, is that the drives/partitions aren't mounted? When I have been trying to work out the issue, I've been concentrating on trying to edit /etc/fstab, but I'm still at the same problem. 

The other point that totally confuses me, is what mount points to use as the OS is installed on LVM. I'm aware that /dev/mapper and sys-link play a role, but I'm not sure where.

---

