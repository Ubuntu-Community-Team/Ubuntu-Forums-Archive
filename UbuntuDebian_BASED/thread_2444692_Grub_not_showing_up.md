---
title: "Grub not showing up"
date: 2020-06-03
forum: Ubuntu/Debian BASED
---

### Post by purplephoenix77 on 2020-06-03
I just installed Elementary OS to an SSD on my laptop. The laptop also  has a hdd with MX Linux. After install I'm unable to dual boot and grub  doesn't show up even when I manually choose the hdd with MX Linux on it in the bios. Edit: I  should add both drivers are encrypted don’t know if that matters or  not. I did update grub in the elementary terminal but that had no  effect. How can I fix the dual booting issue?

---

### Post by ajgreeny on 2020-06-03
Is your machine using UEFI or MBR/BIOS?

For a start let's see the output of ```
sudo fdisk -l
``` from whichever OS you can boot to; the output should be the same whichever you are running.

I suspect you may have one OS installed as UEFI and the other using BIOS so go to **Boot-Repair** in my signature below and follow the instructions there to run the Boot-Info-Script.	 
**Do not run the default repair just yet** but simply copy back here the pastebin link you get which will show us a lot more about your system and should help us figure out what's going on.

---

### Post by purplephoenix77 on 2020-06-03
> **ajgreeny said:**
> Is your machine using UEFI or MBR/BIOS?

For a start let's see the output of ```
sudo fdisk -l
``` from whichever OS you can boot to; the output should be the same whichever you are running.

I suspect you may have one OS installed as UEFI and the other using BIOS so go to **Boot-Repair** in my signature below and follow the instructions there to run the Boot-Info-Script.     
**Do not run the default repair just yet** but simply copy back here the pastebin link you get which will show us a lot more about your system and should help us figure out what's going on.


Thanks. Below is the output of fdisk. At the very bottom is the boot info link. 


Disk /dev/sda: 298.1 GiB, 320072933376 bytes, 625142448 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x47580c9d

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1  *         2048   1050623   1048576   512M 83 Linux
/dev/sda2         1050624 620883967 619833344 295.6G 83 Linux
/dev/sda3       620883968 625078271   4194304     2G 83 Linux


Disk /dev/sdb: 447.1 GiB, 480103981056 bytes, 937703088 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x0314bee6

Device     Boot   Start       End   Sectors   Size Id Type
/dev/sdb1          2048   1499135   1497088   731M 83 Linux
/dev/sdb2       1501182 937701375 936200194 446.4G  5 Extended
/dev/sdb5       1501184 937701375 936200192 446.4G 83 Linux


Disk /dev/mapper/sdb5_crypt: 446.4 GiB, 479332401152 bytes, 936196096 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/mapper/elementary--vg-root: 445.4 GiB, 478272290816 bytes, 934125568 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/mapper/elementary--vg-swap_1: 976 MiB, 1023410176 bytes, 1998848 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes







[http://paste.ubuntu.com/p/Vx3KDknbCN/](http://paste.ubuntu.com/p/Vx3KDknbCN/)

---

### Post by ajgreeny on 2020-06-03
The Boot-Repair output suggests that RAID was detected; do you have a raid system as well as encryption?

If so, I shall have to pull out of further comment as I do not and never have used either RAID or encryption.  Hang around further and hopefully someone else will come along who understands such systems better than I do.

---

### Post by oldfred on 2020-06-03
Does not look like RAID, but just LVM.
RAID would have matching partitions on two drives.

For Boot-Repair to correctly reinstall grub you have to mount LVM and decrypt the encrypted volumes.

Grub does not normally show if it only sees one install. Unless you mount & decrypt second install, grub2's os-prober has to see the second install.

---

### Post by purplephoenix77 on 2020-06-03
> **oldfred said:**
> Does not look like RAID, but just LVM.
RAID would have matching partitions on two drives.

For Boot-Repair to correctly reinstall grub you have to mount LVM and decrypt the encrypted volumes.

Grub does not normally show if it only sees one install. Unless you mount & decrypt second install, grub2's os-prober has to see the second install.

Okay. Thanks. I should've thought of that. I'm still a relative linux newbie. How would I go about correcting grub? I mean  what commands, etc would i need to run.

---

### Post by oldfred on 2020-06-03
Mount the encrypted partitions in the LVM and run Boot-Repair.

I do not know LVM, but have these links which I believe are still good.
Mount LVM - duckhook
[https://ubuntuforums.org/showthread.php?t=2383017&p=13733372#post13733372](https://ubuntuforums.org/showthread.php?t=2383017&p=13733372#post13733372)
[https://unix.stackexchange.com/questions/339011/how-do-i-mount-an-lvm-partition/339621#339621](https://unix.stackexchange.com/questions/339011/how-do-i-mount-an-lvm-partition/339621#339621)
For mounting encrypted see first few lines, you do not need the resize which is rest of post:
[https://askubuntu.com/questions/262211/how-do-i-resize-an-encrypted-lvm-to-install-another-copy-of-ubuntu](https://askubuntu.com/questions/262211/how-do-i-resize-an-encrypted-lvm-to-install-another-copy-of-ubuntu)

---

