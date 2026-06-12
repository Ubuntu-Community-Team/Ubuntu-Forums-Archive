---
title: "Ubuntu Server 9.04 won't mount with second SATA disk attached to system?"
date: 2009-07-20
forum: Server Platforms
---

### Post by nerr on 2009-07-20
EDIT:  I meant "boot" in the title versus "mount".  Sorry about that.

Okay, I'm completely stumped.  I have a headless server box with no video out, running Ubuntu Server.  I know that makes the situation more difficult, but perhaps an expert can lend some insight.

The system contains two 1TB disks, and 256MB of built in flash memory.  One of the disks is the system disk, the other is one massive XFS partition that holds backups of the data on the first, and the flash memory is completely blank and now formatted as ext3 for perhaps small archival.  Neither the second disk nor the flash memory is flagged as bootable by a "sudo fdisk -l" command.  I'm completely at a loss for what the system could be doing, but it only happens when the second 1TB disk is attached at boot time.

If it makes a difference, for some reason the machine is shown connecting with 100mbit ethernet, as it begins its boot process, versus 1gbit as it runs on Ubuntu Server.  The actual Ubuntu OS never seems to load, as I don't get any response from OpenSSH, Samba, CUPS, or any other daemons I usually run at boot time.   I have absolutely no idea what this could indicate.

Any help is greatly appreciated.  I'd love to get this worked out, and not have to call somebody at home to remove a disk if I ever need to reboot.  Thanks very much.

---

### Post by swerdna on 2009-07-21
Could this be a scenario: The operating system was loaded when only one sata drive was attached and it was recognised as sda. When a second sata is attachedand you boot, the bios recognises the first disk as sdb, and the booting fails.


You could check by booting off a live cd and running "sudo fdisk -l" for two cases: one drive and then two drives attached

Just a drive by thought :D

---

### Post by nerr on 2009-07-21
Interesting!  I think I've solved the problem actually.  My home server system is an Acer easystore H340, with four hotswap drive bays.   I was using Bay 4 for my OS, since it was the top bay, and Bay 3 for my backups, being the second to top.  Swapping the OS into the bottom bay, Bay 1, and the backup drive into Bay 2 seems to have done the trick as far as the weird booting issues go.

So in otherwords, Ubuntu worked flawlessly.  The end user however?  Not so much.  Thank you very much for your help anyway, swerdna. :)

---

