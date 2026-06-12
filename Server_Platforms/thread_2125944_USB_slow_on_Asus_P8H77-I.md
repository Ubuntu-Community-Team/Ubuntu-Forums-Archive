---
title: "USB slow on Asus P8H77-I"
date: 2013-03-15
forum: Server Platforms
---

### Post by glypto on 2013-03-15
Hi,
I'm running Ubuntu Server (64bit) on Asus P8H77-I motherboard (OS installed on WD Caviar green HDD). Everything works fine except for the USB ports - transfer speeds are very low - I only get about 1.7 MB/s via USB 2.0 ports and 2.8 MB/s via USB 3.0 port. This seems wrong to me. Am I missing driver or something?  
USB drive is WD Passport USB 3.0 portable drive with NTFS filesystem.

---

### Post by glypto on 2013-03-16
I forgot to say the same USB drive works well on other computer - my laptop with Ubuntu Desktop 12.04. So I guess this has something to do with combination Ubuntu + P8H77-I. Any idea what diagnostic/troubleshooting can I use?

This is what I get in syslog when USB drive is connected:

```

Mar 16 07:52:33 hroch kernel: [ 4283.100755] usb 4-3: new SuperSpeed USB device number 2 using xhci_hcd
Mar 16 07:52:33 hroch kernel: [ 4283.117632] usb 4-3: New USB device found, idVendor=1058, idProduct=0730
Mar 16 07:52:33 hroch kernel: [ 4283.117636] usb 4-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Mar 16 07:52:33 hroch kernel: [ 4283.117639] usb 4-3: Product: My Passport 0730
Mar 16 07:52:33 hroch kernel: [ 4283.117641] usb 4-3: Manufacturer: Western Digital
Mar 16 07:52:33 hroch kernel: [ 4283.117643] usb 4-3: SerialNumber: 575839314339303030313037
Mar 16 07:52:33 hroch kernel: [ 4283.154358] usbcore: registered new interface driver uas
Mar 16 07:52:33 hroch kernel: [ 4283.165981] Initializing USB Mass Storage driver...
Mar 16 07:52:33 hroch kernel: [ 4283.166220] scsi6 : usb-storage 4-3:1.0
Mar 16 07:52:33 hroch kernel: [ 4283.166313] usbcore: registered new interface driver usb-storage
Mar 16 07:52:33 hroch kernel: [ 4283.166315] USB Mass Storage support registered.
Mar 16 07:52:35 hroch kernel: [ 4285.059145] scsi 6:0:0:0: Direct-Access     WD       My Passport 0730 1016 PQ: 0 ANSI: 6
Mar 16 07:52:35 hroch kernel: [ 4285.059500] scsi 6:0:0:1: Enclosure         WD       SES Device       1016 PQ: 0 ANSI: 6
Mar 16 07:52:35 hroch kernel: [ 4285.060413] sd 6:0:0:0: Attached scsi generic sg2 type 0
Mar 16 07:52:35 hroch kernel: [ 4285.060620] scsi 6:0:0:1: Attached scsi generic sg3 type 13
Mar 16 07:52:42 hroch kernel: [ 4291.795859] sd 6:0:0:0: [sdc] 1953458176 512-byte logical blocks: (1.00 TB/931 GiB)
Mar 16 07:52:42 hroch kernel: [ 4291.796035] sd 6:0:0:0: [sdc] Write Protect is off
Mar 16 07:52:42 hroch kernel: [ 4291.796039] sd 6:0:0:0: [sdc] Mode Sense: 47 00 10 08
Mar 16 07:52:42 hroch kernel: [ 4291.796191] sd 6:0:0:0: [sdc] No Caching mode page present
Mar 16 07:52:42 hroch kernel: [ 4291.796243] sd 6:0:0:0: [sdc] Assuming drive cache: write through
Mar 16 07:52:42 hroch kernel: [ 4291.797004] sd 6:0:0:0: [sdc] No Caching mode page present
Mar 16 07:52:42 hroch kernel: [ 4291.797058] sd 6:0:0:0: [sdc] Assuming drive cache: write through
Mar 16 07:52:42 hroch kernel: [ 4291.822375]  sdc: sdc1
Mar 16 07:52:42 hroch kernel: [ 4291.823129] sd 6:0:0:0: [sdc] No Caching mode page present
Mar 16 07:52:42 hroch kernel: [ 4291.823182] sd 6:0:0:0: [sdc] Assuming drive cache: write through
Mar 16 07:52:42 hroch kernel: [ 4291.823234] sd 6:0:0:0: [sdc] Attached SCSI disk
Mar 16 07:52:42 hroch ata_id[1658]: HDIO_GET_IDENTITY failed for '/dev/sdc': Invalid argument
Mar 16 07:52:42 hroch kernel: [ 4291.902198] ses 6:0:0:1: Attached Enclosure device
Mar 16 07:52:42 hroch usbmount[1667]: /dev/sdc does not contain a filesystem or disklabel
Mar 16 07:52:42 hroch usbmount[1690]: executing command: mount -tntfs -osync,noexec,nodev,noatime,nodiratime /dev/sdc1 /media/usb0
Mar 16 07:52:43 hroch ntfs-3g[1717]: Version 2012.1.15AR.1 external FUSE 28
Mar 16 07:52:43 hroch ntfs-3g[1717]: Mounted /dev/sdc1 (Read-Write, label "WD Passport", NTFS 3.1)
Mar 16 07:52:43 hroch ntfs-3g[1717]: Cmdline options: rw,noexec,nodev,sync,noatime,nodiratime
Mar 16 07:52:43 hroch ntfs-3g[1717]: Mount options: rw,noexec,nodev,sync,nodiratime,allow_other,nonempty,noatime,fsname=/dev/sdc1,blkdev,blksize=4096
Mar 16 07:52:43 hroch ntfs-3g[1717]: Ownership and permissions disabled, configuration type 7
Mar 16 07:52:43 hroch usbmount[1690]: executing command: run-parts /etc/usbmount/mount.d

```

---

### Post by glypto on 2013-03-16
OK, so I have just booted my server to Ubuntu Desktop (from USB stick) and I get much better USB transfer speeds. 
Tu summarize:

Ubuntu Server:     1.7 MB/sec (USB 2.0);   2.8 MB/sec (USB 3.0)
Ubuntu Desktop:  55.o MB/sec (USB 2.0); 78.0 MB/sec (USB 3.0)

Anybody has any idea what's missing in my Ubuntu Server install?

Thanks in advance

---

### Post by glypto on 2013-03-16
Hmm, seems I have found the solution:
I was using "sync" option when mounting USB drive (usbmount is used to automatically mount usb drive). After "sync" option was removed, transfer speed are much better (70 - 80 MB/sec )
I should spend more time trying to find solution before posting next time ;)

---

