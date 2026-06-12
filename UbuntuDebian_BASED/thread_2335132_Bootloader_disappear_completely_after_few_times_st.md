---
title: "Bootloader disappear completely after few times starting up the computer."
date: 2016-08-25
forum: Ubuntu/Debian BASED
---

### Post by Hendrik_Van_Marcke on 2016-08-25
Good day and hi there,

This is about installing and use a dual boot with Windows 8.1 and CubLinux on a laptop.
My laptop is equipped with an SSD cache chip 32GB (not a SSD drive for clarity).
Currently, installed on HDD 500GB Windows 8.1.
Strange things happen here...
 
Before we can install CubLinux on this laptop we we go into the live environment.
There we can see the 500 GB HDD with GParted, so we can make partitions for Cublinux and Swap space.
But then when we try to install somethings weird happens.
 
The installer doesn't see the HDD so we can't install CubLinux.

So we began to search in Google and found something.

Before we get to install CubLinux we go into the live environment and we uninstall dmraid in synaptic.
That way we can see now the HDD in the installer and we are able to install CubLinux.

So far so good...

We have a dual boot and we are able to start Windows 8.1 or CubLinux.
But then...
After a few times starting up the bootloader is vanished... we can not starting up Windows 8.1 or CubLinux, neither is bootable

Now my question is how to resolve this?

---

### Post by oldfred on 2016-08-25
Do not know anything about CubLinux, but from Ubuntu live installer you can run this report. If your installer is also a live installer it may work from that. It mostly is just running standard Linux tools all in one larger report.
Do not run any fixes until someone has reviewed report.

 May be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by Hendrik_Van_Marcke on 2016-08-26
Hi there,
 I would like first to make something clear.
Windows 8.1 is installed on a hard disk with MBR partition layout so no UEFI.
Unfortunately I now have formatted the HDD and reinstall Windows 8.1.
 Now I dare not install CubLinux for fear that it still happens to me again.

---

### Post by yancek on 2016-08-26
If you want to try CubLinux, you could read the link below which explains creating the bootable usb and the installation process in a video at the bottom of the page.  It is for windows 10 dual boot but I expect windows 8.1 would be similar.  Never used either myself so I don't know how well it will work.

   [https://www.watchmetech.com/dual-boot-cub-linux-windows-10-chromixium/](https://www.watchmetech.com/dual-boot-cub-linux-windows-10-chromixium/)

---

### Post by Hendrik_Van_Marcke on 2016-08-26
I will again ask my question in a different way

there is no UEFI, there is no EFI, there is just the old way partitions are made in MBR

So Windows 8.1 is installed on an MBR partitiontable

Now i like to install CubLinux in dual boot, but when we go in live modus we don't see the drive in the installer

What sould we do to make the drive (where also Windows 8.1 is installed on) visible?

---

### Post by oldfred on 2016-08-26
Is Windows fast start on? Which really is just old fashioned hibernation? And Windows updates may turn it back on, or reinstall a Windows boot loader.

If MBR, have you used all 4 primary partitions?

When you have CubLinux installed the Summary Report from Boot-Repair would have given all sorts of details.
If just Windows now, post this:
sudo parted -l

---

### Post by Hendrik_Van_Marcke on 2016-08-26
Here is the result of sudo parted -l

There are two USB sticks in use, one whith CubLinux on it (8GB)and one i have used to copy the outcome from the terminal on a text file (1GB).


```
Model: ATA ST500LM021-1KJ15 (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End    Size    Type      File system  Flags
 1      1049kB  368MB  367MB   primary   ntfs         boot
 2      368MB   203GB  203GB   primary   ntfs
 3      203GB   500GB  297GB   extended               lba
 5      203GB   278GB  74,9GB  logical   ntfs
 6      278GB   500GB  222GB   logical   ntfs


Model:   (scsi)
Disk /dev/sdc: 8103MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  8103MB  8102MB  primary  fat32        boot, lba


Model: JetFlash TS1GJFV30 (scsi)
Disk /dev/sdd: 1017MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  1017MB  1016MB  primary  ntfs


Error: /dev/zram0: unrecognised disk label                                

Error: /dev/zram1: unrecognised disk label                                

Error: /dev/zram2: unrecognised disk label                                

Error: /dev/zram3: unrecognised disk label                                

cub@CubLinux:~$
```

---

### Post by Hendrik_Van_Marcke on 2016-08-26
Partition number 5 is a data (NTFS) whith movies on it
Partition number 6 is also a data (NTFS) whith my music on it

---

### Post by oldfred on 2016-08-26
You have one primary partition left.
Normal Linux installs want two partitions at minimum or / (root) & swap.
But both can be logicals inside the extended or you could have one / as primary and make swap logical, depending on which NTFS partitions you decide to resize.

Only use Windows own tools to resize NTFS partitions and reboot immediately so it can run chkdsk to repair partition.
Make sure Windows fast start is off. Windows may turn it on after major updates. 

So with a BIOS install you can only boot working Windows from grub. Or it cannot need chkdsk nor be hibernated. You then may need either Windows repair disk or Ubuntu live disk to use as repair tools to reset if you reboot and Windows is hibernated or needs chkdsk.

---

### Post by yancek on 2016-08-26
There is no unallocated space on the drive on which you can install CubLinux which is the basic problem.
500GB disk, partitions 1 and 2 are about 203GB, the Extended partition (3) is 297GB and contains partition 5 and 6.  Add that up and you get 500GB leaving no place on which to install CubLinux or anything else for that matter.

If you install CubLinux on an ntfs partition, it will of course overwrite data on that partition.  Also, CubLinux like any Linux, needs a Linux filesystem to actually work so even if you had an empty ntfs partition or one which you would not mind overwriting, you would have to change the filesystem type and format it for Linux which would also destroy the data.

You need to shrink one of the windows partitions to make room (unallocated space) on which to install CubLinux.  I would use a windows tool such as Disk Management to do it and run Disk Defragmenter first and run chkdsk at least once after making the change.

Which partition you shrink is up to you, probably use the one with the least data in it.  We can't tell from the information you have posted and obviously the partitions you created earlier on which to install CubLinux no longer exist so you will have to do that again.

---

