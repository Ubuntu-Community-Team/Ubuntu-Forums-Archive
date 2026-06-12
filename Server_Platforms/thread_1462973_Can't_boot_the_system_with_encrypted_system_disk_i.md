---
title: "Can't boot the system with encrypted system disk if one of mirror disks failed"
date: 2010-04-26
forum: Server Platforms
---

### Post by ivancheng on 2010-04-26
Hi,

Here's the Ubuntu Server v9.10 configuration:

    /boot (/dev/md0) -  EXT4 (RAID 1)
     /              (/dev/md1)  - EXT4 (RAID 1 + LUKS Encrypted)

     Mirrored system disks: /dev/sda /dev/sdb for /dev/md0 & /dev/md1

1. Grub-pc (Grub2) installed and upgrade-from-grub-legacy executed.
2. ubuntu-desktop installed

In normal situation, the system will ask to input the password for the encrypted system disk /dev/md1 first and then boot up the desktop.

The problem is that the system can't boot up successully if one of the mirrored disks failed.   It don't ask to input the password for the encrypted system disk  and just show ubuntu's logo.  After waiting for ~5 mins, the server returned the "initramfs" prompt.

If booting the system to single user mode first, the result is same.  

Does any have solution for fixing it?:confused:

Thanks in advance.

Rgds,
Ivan

---

### Post by ivancheng on 2010-04-26
Here's the output during booting up after disabling the desktop:

Begin: loading essential drivers ....
 :
 :
Done
Begin: Running /scripts/init-premount ...
Done.
Begin: Mounting root file system.. ...
Begin: Running /scripts/local-top ...
... usb 1-6.3: new low speed USB device using ehci_hcd and address 5
... usb 1-6.3: configuration #1 chosen from 1 choice
... input: ... USB mouse ...
... generic-usb 003 .....
Done.

***** After showing above, there is no output and waiting for ~5 mins ****

Here's error messages after 5 mins:

   Check cryptopts=source= bootarg cat /proc/cmdline
   or missing modules, device: cat /proc/modules ls /dev
-r ALERT! /dev/disk/by-uuid/c5005f76-bc94-4601-ab0b-ccdabb04073a does not exist. Dropping to shell!

BusyBOx v1.13.3 (Ubuntu 1:1.13-3-1ubuntu7) built-in shell (ash)
Enter 'help' ...
(initramfs)

---

