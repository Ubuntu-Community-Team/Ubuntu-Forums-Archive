---
title: "Boot encrypted system from USB memory stick"
date: 2012-05-30
forum: Security
---

### Post by narcisgarcia on 2012-05-30
I've tried to install an Ubuntu 12.04 to an encrypted partition (LUKS created with the same CD alternate installer) using part of a blank hard disk, but setting up an Ext4 partition in an USB memory stick to have the /boot unencrypted as required for GRUB, and to avoid having this unencrypted part in the hard disk.

The installation process completes successfully (root filesystem in /dev/sda1 encrypted and GRUB installs to /dev/sdb =usb).
Then I boot from USB stick, GRUB runs but Linux kernel freezes.

I've also tested to copy the boot partition (/dev/sdb1) to the hard disk (as /dev/sda2) and to boot from USB with [SuperGrubDisk]("http://www.supergrubdisk.org/"). sda2 with GRUB and Linux is perfectly detected, and can jump to that GRUB in the hard disk, but next, when try to boot Linux it freezes (no kind of keyboard response).

My questions:

A) Could I enable some LUKS support to GRUB2 and then no need to have Linux kernel out of encryption?

B) Is there any way to have the /boot part in a removable device?

C) Could a Live-CD do this job?

Note: For the moment I see that in Ubuntu 12.04 GRUB comes with a "crypto" module in /usr/lib/grub/i386-pc but not the "luks" module to manage the password prompt.

---

