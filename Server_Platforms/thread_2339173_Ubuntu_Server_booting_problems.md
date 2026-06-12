---
title: "Ubuntu Server booting problems"
date: 2016-10-05
forum: Server Platforms
---

### Post by jplr8922 on 2016-10-05
Summary : 
After a 'successful' installation of Ubuntu server 16.04, GRUB will not load unless the proper hard drive is explicitly choosen in the BIOS boot option list

Story : 
After 1yr+ of using an old ubuntu desktop as a headless home server (installing Samba, Plex & all trough SSH), I invested my money into two 3TB hard drives in order to install a fresh Ubuntu Server 16.04 on a RAID1 setting. I simply put the two new drives the PC, went trough the installation, and created my RAID1 as intended in the process. When I finally rebooted my PC (making sure that my new drives had the priority in the BIOS boot order list), it booted in my old GRUB menu with the Ubuntu desktop... hm. I then rebooted, I asked my bios to explicitly boot into one of my two new drives (with the boot device selection), and then I was able to acces my new Ubuntu Server OS trough a new GRUB menu, showing my old UbuntuDesktop as an option. Physically removing my old UbuntuDesktop drive gives me a boot failure, UbuntuServer just will not load. The BIOS will simply not boot to ubuntu server by default ; I'm now stuck with two invalid GRUB instances... THE END.

My next option is to try to reinstall UbuntuServer without the old drive plugged in the setup tonight... But some of you might have better ideas!

Thanks,

---

### Post by darkod on 2016-10-05
No need to reinstall. When you can boot the server OS (with the desktop HDD connected), you can install grub on any disk from the booted server OS. But I think you might have another issue.

With 3TB disks the partition table is probably gpt, not the older msdos type. But grub2 can't install on the MBR of gpt disks unless it has one small 1MiB partition on the disk with no filesystem on it. I think this is why grub2 is actually on your desktop HDD and it doesn't boot without it.

Boot the server OS and post the output of:
```
sudo parted -l
```

---

### Post by jplr8922 on 2016-10-05
@Darkod : 

Thanks for the reply. 

1) I cannot give you the output yet (still at work), but I can tell you that the new drives are gpt and the old drive is msdos
2) Note that both OS seems to have their own working GRUB2, but only one is accessed by the default BIOS boot sequence. 

I will give you more info soon!

---

### Post by jplr8922 on 2016-10-06
Sorry for the delay! I had a work emergency...

Here is the output : 

```

Model: ATA WDC WD30EFRX-68E (scsi)
Disk /dev/sda: 3001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  10.5MB  9437kB                     bios_grub
 3      10.5MB  8000MB  7989MB                     raid
 2      8000MB  3001GB  2993GB                     boot, esp


Model: ATA WDC WD30EFRX-68E (scsi)
Disk /dev/sdb: 3001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  10.5MB  9437kB                     bios_grub
 3      10.5MB  8000MB  7989MB                     raid
 2      8000MB  3001GB  2993GB                     boot, esp


Model: Linux Software RAID Array (md)
Disk /dev/md0: 7985MB
Sector size (logical/physical): 512B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system     Flags
 1      0.00B  7985MB  7985MB  linux-swap(v1)


Model: Linux Software RAID Array (md)
Disk /dev/md1: 2992GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system  Flags
 1      0.00B  2992GB  2992GB  ext4


Model: JetFlash TS8GJFV10 (scsi)
Disk /dev/sdg: 8254MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  8253MB  8252MB  primary  ext4



```

Thanks for any advice!

---

