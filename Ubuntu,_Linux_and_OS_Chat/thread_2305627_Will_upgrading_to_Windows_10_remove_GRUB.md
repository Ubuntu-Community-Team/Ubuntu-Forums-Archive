---
title: "Will upgrading to Windows 10 remove GRUB?"
date: 2015-12-07
forum: Ubuntu, Linux and OS Chat
---

### Post by help_me2 on 2015-12-07
I got a notification that my win 10 upgrade is available. I have a feeling I will have to reinstall grub after upgrading. Correct?

---

### Post by oldfred on 2015-12-07
UEFI or BIOS?
As with any major upgrade, you should have good backups.

And if BIOS and Ubuntu is in a Linux partition, backup partition table also. Windows is known to forget to write a Linux logical partition back to partition table. Data is still there, just entry in partition table is missing.

       Backup partition table structure to text file & save to external device.
sudo sfdisk -d /dev/sda > PTsda.txt

If UEFI, ubuntu entry is still there, Windows just makes the Windows entry first in UEFI boot order.

---

### Post by help_me2 on 2015-12-07
It was one of the first laptops to have uefi (2011) but has bios also, letting the user choose which one to use. I chose bios. I believe I could use a bootable ubuntu thumbdrive and use the Boot Repair program, right?

---

### Post by oldfred on 2015-12-07
Boot-Repair is pretty easy to use.
You can just use command line to restore grub to MBR with BIOS boot, but I like Boot-Repair just because of its Summary Report if issue is more than just a simple reinstall of grub.

But Boot-Repair will not restore a missing partition. Either testdisk, parted rescue or your own backup. And easiest to use your own backup.

---

