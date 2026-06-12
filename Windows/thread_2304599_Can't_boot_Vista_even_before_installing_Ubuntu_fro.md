---
title: "Can't boot Vista even before installing Ubuntu from USB"
date: 2015-11-28
forum: Windows
---

### Post by jens15 on 2015-11-28
Hi all,
I tried to dual boot Ubuntu 14.04 next to my already existing Windows Vista. When installing, I clicked on 'Something else' to manually edit the partitions for Ubuntu. The devices displayed were
```
/dev/sda
  /dev/sda 1    ntfs   250000 MB windows boot loader
```
However, I could not change the size of sda1 to create other partitions for Ubuntu.

Thus I returned to the previous selection page, and I selected the option 'Use LVM with the new Ubuntu installation', but I didn't see it was a selection of 'Erase disk and install Ubuntu'. When I clicked on Install Now a popup screen was shown with the changes of the partitions the system was going to make. I declined that to go back to the 'Something else' intallation, but now it shows different devices:

```
 /dev/mapper/ubuntu-vg-root
  /dev/mapper/ubuntu-vg-root
/dev/mapper/ubuntu-vg-swap_1
  /dev/mapper/ubuntu-vg-swap_1
/dev/sda
  /dev/sda1    ntfs    unknown
  /dev/sda5             unknown

```

The boot loader of windows vista is gone, and indeed, I cannot start windows. Can anyone help me to repair the windows loader? The things I tried:

- Boot-Repair, but the repair option isn't available. This is what I get: [http://paste.ubuntu.com/13541072/](http://paste.ubuntu.com/13541072/) Indeed Windows is installed on sda1
- sudo os-prober and OS-Uninstaller both do not find Windows vista.
- I don't have a windows boot cd :(
- I didn't risk to make changes in GParted

Thanks in advance!

---

### Post by mikewhatever on 2015-11-28
So, you need to search how to repair Vista's bootloader, or ask on a Windows support forum. As you can imagine, the Instalation & Upgrades section here is for Ubuntu support, and has nothing to do with Windows.

---

### Post by jens15 on 2015-11-28
I'm not looking for Windows support. I've managed to get a DVD copy of Vista but couldn't boot it as I'm unable to find the partition C:\ . And as Ubuntu says there is indeed a partition ([http://paste.ubuntu.com/13541072/](http://paste.ubuntu.com/13541072/)) available for Vista (sda1), I thought I'd ask this question on an Ubuntu forum because I don't understand what the paste file means... I'm just worried my whole hard disk was automatically partitioned by Ubuntu and I lost all my other data. Any ideas?

---

### Post by yancek on 2015-11-28
Your post shows LVM partitioning so I expect you will have to modify the partition table.  If you have a vista Installation DVD, you should be able to do that with it with a 'Repair' option on the DVD.  The boot repair output, the very first line, tell you you there is no bootloader code in the MBR.  Without that, nothing will boot.  The boot repair shows a Linux partition (sda5) but nothing on it and your windows partition (sda1) shows a windows filesystem but does not show the boot files ordinarily seen there.  There are specific commands you need to run from the windows DVD from the repair option.  You might try a search for repairing mbr on vista.  I doubt the boot repair software will be able to do it on a proprietary vista system.

If the windows DVD fails, your best option will then will be to use some software on the Ubuntu installation medium such as testdisk to recover files.  You would need to download it to your Ubuntu medium. 

It's too late now, but the time to post here was when you tried to shrink the single windows partition so someone could have instructed you on the process.  Good luck.

---

### Post by Bucky Ball on 2015-11-28
*Thread moved to **Windows**.*

[QUOTE=jens15]Can anyone help me to repair the windows loader?[/QUOTE]

For future reference, you should only use Windows software to resize Windows OS and recovery partitions. Use Ubuntu software for Linux partitions.

I'd start from scratch. If you need to, try and retrieve any lost data with Windows specific software or with [testdisk]("http://www.cgsecurity.org/wiki/TestDisk") or [photorec]("http://www.cgsecurity.org/wiki/PhotoRec") then install from the Vista DVD. Once you have that up and stable, install Ubuntu. Good luck. :)

---

