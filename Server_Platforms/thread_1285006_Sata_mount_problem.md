---
title: "Sata mount problem"
date: 2009-10-07
forum: Server Platforms
---

### Post by SteZZz on 2009-10-07
After a server crash I put livecd in the system and backuped my files to an external drive.
I reinstalled my server with ubuntu server 9.04 32bits edition.
Now the problem is that i can mount my 2 * 200GB SATA , IDE harddisk with ubuntu installation, and external harddisk. I can't mount my 2 * 320GB SATA disks. I disabled all the RAID in the bios and controller before i installed the server.

What i think maby sounds strange, but when i boot from the livecd i can access and mount my 320gb drives.
Inside my server installation i can't

maby it's usefull for me to post here some info of the system.

```
$ ls -la /dev/disk/by-id | sort
drwxr-xr-x 2 root root 640 2009-10-07 17:03 .
drwxr-xr-x 6 root root 120 2009-10-07 17:03 ..
lrwxrwxrwx 1 root root  10 2009-10-07 17:03 ata-WDC_WD2000JD-00GBB0_WD-WMAEP3020089-part1 -> ../../sda1
lrwxrwxrwx 1 root root  10 2009-10-07 17:03 ata-WDC_WD2000JD-00GBB0_WD-WMAEP3020089-part5 -> ../../sda5
lrwxrwxrwx 1 root root  10 2009-10-07 17:03 ata-WDC_WD2000JD-55HBB0_WD-WCALL1411237-part1 -> ../../sdb1
lrwxrwxrwx 1 root root  10 2009-10-07 17:03 ata-WDC_WD2000JD-55HBB0_WD-WCALL1411237-part5 -> ../../sdb5
lrwxrwxrwx 1 root root  10 2009-10-07 17:03 ata-WDC_WD800JB-00ETA0_WD-WMAHL2786815-part1 -> ../../sde1
lrwxrwxrwx 1 root root  10 2009-10-07 17:03 ata-WDC_WD800JB-00ETA0_WD-WMAHL2786815-part2 -> ../../sde2
lrwxrwxrwx 1 root root  10 2009-10-07 17:03 ata-WDC_WD800JB-00ETA0_WD-WMAHL2786815-part5 -> ../../sde5
lrwxrwxrwx 1 root root  10 2009-10-07 17:03 scsi-SATA_WDC_WD2000JD-00WD-WMAEP3020089-part1 -> ../../sda1
lrwxrwxrwx 1 root root  10 2009-10-07 17:03 scsi-SATA_WDC_WD2000JD-00WD-WMAEP3020089-part5 -> ../../sda5
lrwxrwxrwx 1 root root  10 2009-10-07 17:03 scsi-SATA_WDC_WD2000JD-55_WD-WCALL1411237-part1 -> ../../sdb1
lrwxrwxrwx 1 root root  10 2009-10-07 17:03 scsi-SATA_WDC_WD2000JD-55_WD-WCALL1411237-part5 -> ../../sdb5
lrwxrwxrwx 1 root root  10 2009-10-07 17:03 scsi-SATA_WDC_WD800JB-00EWD-WMAHL2786815-part1 -> ../../sde1
lrwxrwxrwx 1 root root  10 2009-10-07 17:03 scsi-SATA_WDC_WD800JB-00EWD-WMAHL2786815-part2 -> ../../sde2
lrwxrwxrwx 1 root root  10 2009-10-07 17:03 scsi-SATA_WDC_WD800JB-00EWD-WMAHL2786815-part5 -> ../../sde5
lrwxrwxrwx 1 root root  10 2009-10-07 17:03 usb-Maxtor_3200_2CAHTP1P-0:0-part1 -> ../../sdf1
lrwxrwxrwx 1 root root  27 2009-10-07 17:03 dm-name-via_bgbcbidfie -> ../../mapper/via_bgbcbidfie
lrwxrwxrwx 1 root root  27 2009-10-07 17:03 dm-uuid-DMRAID-via_bgbcbidfie -> ../../mapper/via_bgbcbidfie
lrwxrwxrwx 1 root root  28 2009-10-07 17:03 dm-name-via_bgbcbidfie5 -> ../../mapper/via_bgbcbidfie5
lrwxrwxrwx 1 root root  28 2009-10-07 17:03 dm-uuid-DMRAID-via_bgbcbidfie5 -> ../../mapper/via_bgbcbidfie5
lrwxrwxrwx 1 root root   9 2009-10-07 17:03 ata-WDC_WD2000JD-00GBB0_WD-WMAEP3020089 -> ../../sda
lrwxrwxrwx 1 root root   9 2009-10-07 17:03 ata-WDC_WD2000JD-55HBB0_WD-WCALL1411237 -> ../../sdb
lrwxrwxrwx 1 root root   9 2009-10-07 17:03 ata-WDC_WD3200JD-00KLB0_WD-WCAMR1623857 -> ../../sdc
lrwxrwxrwx 1 root root   9 2009-10-07 17:03 ata-WDC_WD3200JD-00KLB0_WD-WCAMR1624830 -> ../../sdd
lrwxrwxrwx 1 root root   9 2009-10-07 17:03 ata-WDC_WD800JB-00ETA0_WD-WMAHL2786815 -> ../../sde
lrwxrwxrwx 1 root root   9 2009-10-07 17:03 scsi-SATA_WDC_WD2000JD-00WD-WMAEP3020089 -> ../../sda
lrwxrwxrwx 1 root root   9 2009-10-07 17:03 scsi-SATA_WDC_WD2000JD-55_WD-WCALL1411237 -> ../../sdb
lrwxrwxrwx 1 root root   9 2009-10-07 17:03 scsi-SATA_WDC_WD3200JD-00_WD-WCAMR1623857 -> ../../sdc
lrwxrwxrwx 1 root root   9 2009-10-07 17:03 scsi-SATA_WDC_WD3200JD-00_WD-WCAMR1624830 -> ../../sdd
lrwxrwxrwx 1 root root   9 2009-10-07 17:03 scsi-SATA_WDC_WD800JB-00EWD-WMAHL2786815 -> ../../sde
lrwxrwxrwx 1 root root   9 2009-10-07 17:03 usb-Maxtor_3200_2CAHTP1P-0:0 -> ../../sdf
total 0
``````
$ sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00020a0c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24321   195358401    5  Extended
/dev/sda5               1       24321   195358369+  83  Linux

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000f33d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       24321   195358401    5  Extended
/dev/sdb5               1       24321   195358369+  83  Linux

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c4295

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       38913   312568641   83  Linux

Disk /dev/sdd: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00025111

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       38913   312568641    5  Extended
/dev/sdd5               1       38913   312568609+  83  Linux

Disk /dev/sde: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0abb0aba

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1        9379    75336786   83  Linux
/dev/sde2            9380        9729     2811375    5  Extended
/dev/sde5            9380        9729     2811343+  82  Linux swap / Solaris

Disk /dev/sdf: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd41375ff

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1       60801   488384001    7  HPFS/NTFS

``````

$ sudo mount /dev/sdc1 /mnt/usenet
mount: special device /dev/sdc1 does not exist
$ sudo mount /dev/sdd5 /mnt/usenet
mount: special device /dev/sdd5 does not exist

$ sudo mount /dev/sdc /mnt/usenet
mount: unknown filesystem type 'via_raid_member'
$ sudo mount /dev/sdd /mnt/usenet
mount: unknown filesystem type 'via_raid_member'

```

```

ls /dev/sd*
/dev/sda  /dev/sda1  /dev/sda5  /dev/sdb  /dev/sdb1  /dev/sdb5  /dev/sdc  /dev/sdd  /dev/sde  /dev/sde1  /dev/sde2  /dev/sde5  /dev/sdf  /dev/sdf1

```

Well i hope somebody can help me with the strange problem.
Thanks in Advance!

---

### Post by Vegan on 2009-10-07
Mixing EIDE with SATA will be problematic, use one kind or the other. This is due to the way the BIOS remaps disks.

---

### Post by SteZZz on 2009-10-07
hmm why should this make my disk no be mountable. and in the past this all worked just fine...

---

### Post by SteZZz on 2009-10-07
EIDE you mean External IDE other said usb drive?
well i got the usb drive disconnected @ start, but because i needed to backup the files from the harddrives, i used the livecd and pluged in the usb drive.
so the problem wass there before i connected the drive.

---

### Post by tamashumi on 2010-01-21
I have exactly the same problem although slight different config.

Anyone solved it already? Please...

---

### Post by cariboo on 2010-01-21
Make sure all the drives are detected in the bios. I have a mix of 2 pata drives, 2 sata drives and 1 esata drives in my server. it took a little bit of fiddling to get the correct boot order, but everything works as it should.

---

