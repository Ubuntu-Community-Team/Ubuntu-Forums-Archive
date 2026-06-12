---
title: "Server adding hard drives"
date: 2011-07-15
forum: Server Platforms
---

### Post by xkaliburx on 2011-07-15
[FONT="Verdana"]Have a new clean install of U10.04LTS and have just added 2 SSD drives which I want to setup via raid1.  The drives are lit, and once in /messages shows the following;


[SIZE="1"]kernel: [47335.041553] scsi 2:0:0:0: Direct-Access     SEAGATE  ST9146803SS      FS62 PQ: 0 ANSI: 5
kernel: [47335.042347] scsi 2:0:1:0: Direct-Access     SEAGATE  ST9146803SS      FS62 PQ: 0 ANSI: 5
kernel: [47335.043142] scsi 2:0:2:0: Direct-Access     SEAGATE  ST9146803SS      FS62 PQ: 0 ANSI: 5
kernel: [47335.043936] scsi 2:0:3:0: Direct-Access     SEAGATE  ST9146803SS      FS62 PQ: 0 ANSI: 5
[COLOR="Red"]kernel: [47335.044756] scsi 2:0:4:0: Direct-Access     ATA      INTEL SSDSA2CW12 0302 PQ: 0 ANSI: 5
kernel: [47335.045545] scsi 2:0:5:0: Direct-Access     ATA      INTEL SSDSA2CW12 0302 PQ: 0 ANSI: 5[/SIZE][/COLOR]

So looking above, I can see that the kernel sees them (the red ones), but I can't parition, format, etc. 

I tried *lshw -C disk* and all I see is the primary raid 10;
[SIZE="1"]*-disk                  
       description: SCSI Disk
       product: PERC 6/i
       vendor: DELL
       physical id: 2.0.0
       bus info: scsi@2:2.0.0
       logical name: /dev/sda
       version: 1.22
       serial: 0037d4960668feb11500c9e517b0ad4b
       size: 272GiB (292GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=00047044
[/SIZE]
Now, I tried using the rescan-ssci-bus.sh tool which didn't help as well as reading around, people posting some echo commands like echo "- - -" > /sys/class/scsi_host/host2/scan  but I still dont see the drives to partition.

I've been up a long time through the night with upgrades, so it maybe a case of something really stupid (which I am hoping for), so please give me something else to try and ease my mind ... 

Thanks
[/FONT]

---

### Post by karlson on 2011-07-15
> **xkaliburx said:**
> [FONT="Verdana"]Have a new clean install of U10.04LTS and have just added 2 SSD drives which I want to setup via raid1.  The drives are lit, and once in /messages shows the following;


[SIZE="1"]kernel: [47335.041553] scsi 2:0:0:0: Direct-Access     SEAGATE  ST9146803SS      FS62 PQ: 0 ANSI: 5
kernel: [47335.042347] scsi 2:0:1:0: Direct-Access     SEAGATE  ST9146803SS      FS62 PQ: 0 ANSI: 5
kernel: [47335.043142] scsi 2:0:2:0: Direct-Access     SEAGATE  ST9146803SS      FS62 PQ: 0 ANSI: 5
kernel: [47335.043936] scsi 2:0:3:0: Direct-Access     SEAGATE  ST9146803SS      FS62 PQ: 0 ANSI: 5
[COLOR="Red"]kernel: [47335.044756] scsi 2:0:4:0: Direct-Access     ATA      INTEL SSDSA2CW12 0302 PQ: 0 ANSI: 5
kernel: [47335.045545] scsi 2:0:5:0: Direct-Access     ATA      INTEL SSDSA2CW12 0302 PQ: 0 ANSI: 5[/SIZE][/COLOR]

So looking above, I can see that the kernel sees them (the red ones), but I can't parition, format, etc. 

I tried *lshw -C disk* and all I see is the primary raid 10;
[SIZE="1"]*-disk                  
       description: SCSI Disk
       product: PERC 6/i
       vendor: DELL
       physical id: 2.0.0
       bus info: scsi@2:2.0.0
       logical name: /dev/sda
       version: 1.22
       serial: 0037d4960668feb11500c9e517b0ad4b
       size: 272GiB (292GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=00047044
[/SIZE]
Now, I tried using the rescan-ssci-bus.sh tool which didn't help as well as reading around, people posting some echo commands like echo "- - -" > /sys/class/scsi_host/host2/scan  but I still dont see the drives to partition.

I've been up a long time through the night with upgrades, so it maybe a case of something really stupid (which I am hoping for), so please give me something else to try and ease my mind ... 

Thanks
[/FONT]

What does ```
 fdisk -l 
``` show?

---

### Post by xkaliburx on 2011-07-15
Disk /dev/sda: 292.3 GB, 292326211584 bytes
255 heads, 63 sectors/track, 35539 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00047044

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          32      248832   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2              32       35540   285222913    5  Extended
/dev/sda5              32       35540   285222912   8e  Linux LVM

Disk /dev/sdb: 1023 MB, 1023934464 bytes
64 heads, 32 sectors/track, 976 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x49e2fd2f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               5         900      917504    5  Extended
/dev/sdb4   *           1           4        4080    4  FAT16 <32M
/dev/sdb5               5         254      255984    6  FAT16
/dev/sdb6             255         504      255984    6  FAT16
/dev/sdb7             505         614      112624   fc  VMware VMKCORE
/dev/sdb8             615         900      292848    6  FAT16


Note: sdb2 is a 1G SD card as this was used as an vm ESXi box and I haven't removed the card yet.

---

