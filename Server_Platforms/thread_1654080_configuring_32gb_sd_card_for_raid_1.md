---
title: "configuring 32gb sd card for raid 1"
date: 2010-12-27
forum: Server Platforms
---

### Post by zander1013 on 2010-12-27
hi,

i am setting up a raid 1 on a netbook with the 30gb internal ssd as the primary drive and the 32gb sd card as the mirror.

i am following the instructions here...
[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

i have several working raid 1 arrays under my belt using usb sticks and want to try something more advanced and practical now.

i have configured the internal ssd with no trouble, however, the 32gb sd card is not showing up in the installer. so i cannot configure it as the mirror.:(

my 2gb sd cards show up when i run the installer why doesn't the 32gb sd card?

if i boot into a session the primary ssd the 32gb card does show up mounted on the desktop. it shown as a dos partition.

please advise.

thank you.

---

### Post by tgalati4 on 2010-12-27
sudo fdisk -l

dmesg | tail

---

### Post by zander1013 on 2010-12-27
> **tgalati4 said:**
> sudo fdisk -l

dmesg | tail


here is the output of those commands...
> af@eartha:~$ sudo fdisk -l
[sudo] password for af: 

Disk /dev/sda: 30.8 GB, 30816608256 bytes
255 heads, 63 sectors/track, 3746 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a2e8c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3587    28806144   83  Linux
/dev/sda2            3587        3747     1285121    5  Extended
/dev/sda5            3587        3747     1285120   82  Linux swap / Solaris

Disk /dev/mmcblk0: 32.3 GB, 32270450688 bytes
83 heads, 63 sectors/track, 12053 cylinders
Units = cylinders of 5229 * 512 = 2677248 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1               2       12054    31510016    b  W95 FAT32

Disk /dev/dm-0: 1315 MB, 1315962880 bytes
255 heads, 63 sectors/track, 159 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x021786db

Disk /dev/dm-0 doesn't contain a valid partition table
af@eartha:~$ 



> af@eartha:~$ dmesg | tail 
[   31.018232] Bluetooth: SCO socket layer initialized
[   31.192123] Bluetooth: RFCOMM TTY layer initialized
[   31.192142] Bluetooth: RFCOMM socket layer initialized
[   31.192150] Bluetooth: RFCOMM ver 1.11
[  101.488137] Skipping EDID probe due to cached edid
[  101.528132] Skipping EDID probe due to cached edid
[  101.568156] Skipping EDID probe due to cached edid
[  101.600157] Skipping EDID probe due to cached edid
[  104.809206] Skipping EDID probe due to cached edid
[  107.148180] Skipping EDID probe due to cached edid
af@eartha:~$ 


---

### Post by tgalati4 on 2010-12-28
Perhaps the mismatch of Cylinder, Heads, Sectors count or the fact that the SD card goes through a kernel module for the SD reader that then mounts it as an mmcblk device instead of an sda device.

You could try to trick the system:

sudo ln -s /dev/mmcblk0 /dev/sdf1

But I would be concerned of the performance mismatch between the SSD and the SD card.  Instead of trying to set up a mirror RAID, write a cronjob that performs an rsync of your data (not the entire disk) and that way you have some protection.  The SD card lacks the wear-leveling that is needed to get significant life out of many read-write-erase cycles that a RAID setup imposes.

So unlike wikipedia, the concept of making a RAID pair out of an SD card and SSD drive sounds better on paper than in operation.

---

### Post by zander1013 on 2010-12-28
thank you tgalati4,

there is wisdom in your comment.

i was unaware the device mismatch would be such a dramatic problem.

in my naive ignorance i might try to setup the sd card in a usb sd card reader and then just stick it in the sd slot on the netbook and see what happens ,,  :-({|=

but your appraisal of the situation leads me to believe that my enthusiasm for a ssd/sd raid is after-all misguided. ;)

thank yo for your help.

you solved the thread. :)

---

### Post by tgalati4 on 2010-12-28
I'm not saying it can't be done.  It's just outside the envelope for how RAID was set up in the first place--a bunch of cheap, identical drives, ganged together to get speed, reliability, or both.  So you could set up RAID with 2 SSD's, but they are expensive and SSD's are fast enough by themselves that they don't need "striping" to get speed.

You could set up RAID with a bunch of SD cards, they are cheap, but the controllers in them are crappy and they wear out quickly with too many writes of small files.  They are fine for storing your holiday pictures, but not a filesystem.

---

