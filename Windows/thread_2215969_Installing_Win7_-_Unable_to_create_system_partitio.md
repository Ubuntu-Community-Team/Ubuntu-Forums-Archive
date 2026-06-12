---
title: "Installing Win7 - Unable to create system partition"
date: 2014-04-09
forum: Windows
---

### Post by Thomas Kenobi on 2014-04-09
Hi, I am trying to install Win7 on my laptop in addition to the Ubuntu installation I am already using and I am getting an error I have never seen before. During Win7 installation, when selecting the partition I have prepared for it I get the error "windows was unable to create a new system partition".

My system's partitions are the following:

- Main SSD
-- /dev/sda1 : ext4 : /
-- /dev/sda2 : ext4 : /home
-- /dev/sda3 : ntfs : <-- this is where I am trying to install windows (~35 GiB)

- On-board SSD
-- /dev/sdb1 : linux-swap
-- /dev/sdb2 : ext4

The windows installer is running off of a bootable USB stick prepared using WinUSB.

I have tried deleting the /dev/sda3 partition from within the windows installer and either recreating it or trying to select the unallocated space to install into, but I keep getting the same error.
In addition I've noticed that inside the installer, /dev/sda1 is marked as a system partition, while the others are marked as primary. Could the issue be that windows can't place the 100MiB system partition it wants to create as the first partition on the disk?

Problem is, this is my main work system so there is only so much experimenting I can do with it. I'm concerned about data corruption in the Ubuntu partitions if I start resizing them to try things out.

Any help is welcome.

PS: I am using the /dev/* names for the partitions even when referring to the win installer for the sake of consistency.

---

### Post by oldfred on 2014-04-09
You are not showing any efi or bios_grub partitions so I assume drive is partitioned with MBR(msdos).
You will also need the boot flag on the NTFS partition. That is how Windows knows which partition to boot, to install boot files into and which partition to repair. Windows will install its boot loader to the drive set as boot in BIOS so make sure it is the same drive. Windows has been known to overwrite a Linux partition on another drive with its 100MB boot partition, But if only the one NTFS it should install just to that partition. Best to have good backups just incase.

Some have reported that even if it has boot flag, you have to use the make active command in Windows which is the same as the boot flag in Linux.

You will need Linux live installer to restore grub boot loader to MBR as there is no way to prevent Windows from installing its boot loader. I would boot Windows just to make sure it works before hand as grub really only boots working Windows.

---

### Post by Thomas Kenobi on 2014-04-10
Thanks for the tips. I managed to fix the original issue by setting the /dev/sda3 partition's boot flag and by removing all partitions from the on-board SSD. For some reason Windows wanted to put the 100MiB system partition it creates on that disk instead of on my main SSD.

---

