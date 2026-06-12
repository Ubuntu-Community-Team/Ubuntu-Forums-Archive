---
title: "DualBooting - Install windows 7 after xubuntu"
date: 2014-04-05
forum: Windows
---

### Post by ihelpyou59 on 2014-04-05
Hello All, Im considering installing windows 7 in addition to xubuntu. I already have on my pc laptopxubuntu 12.04 lts. just want to be able to use win for select apps that don't run well, if at all under wine/virtual box. Are there some fairly simple, straight forward steps I can take for pre and post install so that all is working right when done?


Tai

---

### Post by sikander3786 on 2014-04-05
You didn't provide many details about your partitioning setup so I guess you are able to handle those yourself. Just make sure you install Windows to a primary partition. It won't boot off a logical one.

And once Windows is installed, for setting up dual boot, you will need a Linux, preferably Ubuntu, live CD/USB. Boot Linux from that live medium and follow this:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Just use "Recommended repair" button and you'll be dual-booting.

---

### Post by ihelpyou59 on 2014-04-05
The partitioning setup, it's just the default setup that was created when I had installed xubuntu.

---

### Post by sikander3786 on 2014-04-05
Please post the output of this command for letting us take a look at your partitions:

```
sudo fdisk -l
```

---

### Post by ihelpyou59 on 2014-04-05
here is the output from "sudo fdisk -l"

tai@Waldo:~$ sudo fdisk -l
[sudo] password for tai: 

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000aebe3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   480014335   240006144   83  Linux
/dev/sda2       480016382   488396799     4190209    5  Extended
/dev/sda5       480016384   488396799     4190208   82  Linux swap / Solaris

Disk /dev/sdb: 31.2 GB, 31221153792 bytes
255 heads, 63 sectors/track, 3795 cylinders, total 60978816 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1

---

### Post by ihelpyou59 on 2014-04-05
sorry about repost....didn't realize i didn't copy all txt

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000aebe3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   480014335   240006144   83  Linux
/dev/sda2       480016382   488396799     4190209    5  Extended
/dev/sda5       480016384   488396799     4190208   82  Linux swap / Solaris

Disk /dev/sdb: 31.2 GB, 31221153792 bytes
255 heads, 63 sectors/track, 3795 cylinders, total 60978816 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2    60978815    30489407    b  W95 FAT32

---

### Post by sikander3786 on 2014-04-05
Oops, doesn't sound great. Please post the output of this one also:

```
sudo parted -l
```

I should have already requested this one also.

---

### Post by ihelpyou59 on 2014-04-05
Model: ATA Hitachi HTS54252 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  246GB  246GB   primary   ext4            boot
 2      246GB   250GB  4291MB  extended
 5      246GB   250GB  4291MB  logical   linux-swap(v1)


Model:  USB Flash Memory (scsi)
Disk /dev/sdb: 31.2GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End     Size    Type     File system  Flags
 1      1024B  31.2GB  31.2GB  primary  fat32

---

### Post by ihelpyou59 on 2014-04-05
ok, sorry if something may seem off here.....I currently have a 32GB flash drive connected to the machine in question.

---

### Post by sikander3786 on 2014-04-05
In the current setup, it looks quite difficult to install Windows. You'll need to shrink your Ubuntu partition as there doesn't seem to be any other choice. If it isn't an old install, and you feel easy setting it up again, I would prefer a re-install of Xubuntu also.

I will try to guide you through it. Before that, it would be better to decide if you want to shrink your Ubuntu partition or you want to start fresh?

---

### Post by ihelpyou59 on 2014-04-05
I agree, under any other circumstance, i'd wipe the drive and start with installing windows....but with this system, I had some help in setting up the integrated wifi card, i.e. the broadcom driver, and I don't know where the driver was pulled from due to someone else had located and installed it for me.

---

### Post by ihelpyou59 on 2014-04-05
I have no qualms about trying to run gparted from a live "cd"/usb

---

### Post by sikander3786 on 2014-04-05
Ok then. Boot into a Live USB/CD and use GParted to resize your Ubuntu partition. I would strongly recommend to backup all your important data.

In the space that you free up, create a new Primary partition whatever size you prefer and format it to NTFS.

The ideal scenario for me while dual booting would be:

Partition 1: 40-50 GB, ext4, primary, Xubuntu
Partition 2: 40-50 GB, NTFS, primary, Windows
Partition 3: 120-130 GB, NTFS, logical, For data storage and sharing between Xubuntu and Windows
Partition 4: 4 GB, logical, Linux Swap

If you don't need a shared partition between Xubuntu and Windows, just leave it. I don't know how much data is there in your Xubuntu partition so my table won't be perfect for you although it might give you the basic idea.

Once you install Windows in the newly created partition, you will lose access to Xubuntu. You'll again need the Live USB/CD then. Boot from it and follow "2nd option" from here:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Choose "Recommended repair" and you will be done. On power up, you will see the menu for choosing the OS you want to boot.

---

### Post by oldfred on 2014-04-05
You will also need to move boot flag from sda1 to the new NTFS primary partition, probably sda3. Do not worry about order. Partitions on drives do not have to be in order.
Windows only installs to primary NTFS partitions with the boot flag. Grub does not use boot flag, but Windows has to have one to know which partition to install into and which to boot from.

---

