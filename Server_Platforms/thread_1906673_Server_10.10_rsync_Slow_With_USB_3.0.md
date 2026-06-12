---
title: "Server 10.10 rsync Slow With USB 3.0"
date: 2012-01-09
forum: Server Platforms
---

### Post by Catalyph on 2012-01-09
I have an rsync job backing up a lot of large video files to a USB 3.0 external Drive

rsync -ru --stats --progress /Video/ /media/Backup

When doing this it indicates a transfer speed of 13.5 MB/s

this is Very slow for a USB 3.0 external drive

doing 
hdparm -Tt /dev/sdd1
Timing cached reads:   1748 MB in  2.00 seconds = 873.28 MB/sec
Timing buffered disk reads: 352 MB in  3.00 seconds = 117.20 MB/sec

sudo fdisk -lu
Disk /dev/sdd: 2000.4 GB, 2000398931968 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029164 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbaaa46ce

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              63  3907024127  1953512032+   7  HPFS/NTFS/exFAT

sudo lsusb

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 14cd:8168 Super Top 
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 009 Device 002: ID 0bc2:3332 Seagate RSS LLC


sudo df -hT
/dev/sdd1  fuseblk    1.9T  207G  1.7T  12% /media/Backup


Is it just Rsync is slow.

I did a cp for a 1.2gb file and that took 1:06 which is about 16MB/sec But with USB 3.0 I should be getting 60+ MB/sec



####################

My boot up with USB connected :
Jan  9 16:04:31 BlazenNas kernel: [    0.000000] DMI: Gigabyte Technology Co., Ltd. GA-E350N-USB3/GA-E350N-USB3, BIOS F1 01/10/2011
Jan  9 16:04:31 BlazenNas kernel: [    0.832735] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Jan  9 16:04:31 BlazenNas kernel: [    0.832864] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
Jan  9 16:04:31 BlazenNas kernel: [    0.844044] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
Jan  9 16:04:31 BlazenNas kernel: [    0.844308] hub 1-0:1.0: USB hub found
Jan  9 16:04:31 BlazenNas kernel: [    0.844538] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
Jan  9 16:04:31 BlazenNas kernel: [    0.856034] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
Jan  9 16:04:31 BlazenNas kernel: [    0.856279] hub 2-0:1.0: USB hub found
Jan  9 16:04:31 BlazenNas kernel: [    0.856517] ehci_hcd 0000:00:16.2: new USB bus registered, assigned bus number 3
Jan  9 16:04:31 BlazenNas kernel: [    0.868035] ehci_hcd 0000:00:16.2: USB 2.0 started, EHCI 1.00
Jan  9 16:04:31 BlazenNas kernel: [    0.868261] hub 3-0:1.0: USB hub found
Jan  9 16:04:31 BlazenNas kernel: [    0.868386] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Jan  9 16:04:31 BlazenNas kernel: [    0.868536] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 4
Jan  9 16:04:31 BlazenNas kernel: [    0.928175] hub 4-0:1.0: USB hub found
Jan  9 16:04:31 BlazenNas kernel: [    0.928392] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
Jan  9 16:04:31 BlazenNas kernel: [    0.988181] hub 5-0:1.0: USB hub found
Jan  9 16:04:31 BlazenNas kernel: [    0.988404] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 6
Jan  9 16:04:31 BlazenNas kernel: [    1.048172] hub 6-0:1.0: USB hub found
Jan  9 16:04:31 BlazenNas kernel: [    1.048373] ohci_hcd 0000:00:16.0: new USB bus registered, assigned bus number 7
Jan  9 16:04:31 BlazenNas kernel: [    1.108169] hub 7-0:1.0: USB hub found
Jan  9 16:04:31 BlazenNas kernel: [    1.108300] uhci_hcd: USB Universal Host Controller Interface driver
Jan  9 16:04:31 BlazenNas kernel: [    1.168051] usb 2-2: new high speed USB device number 2 using ehci_hcd
Jan  9 16:04:31 BlazenNas kernel: [    1.645338] xhci_hcd 0000:03:00.0: new USB bus registered, assigned bus number 8
Jan  9 16:04:31 BlazenNas kernel: [    1.769414] hub 8-0:1.0: USB hub found
Jan  9 16:04:31 BlazenNas kernel: [    1.769604] xhci_hcd 0000:03:00.0: new USB bus registered, assigned bus number 9
Jan  9 16:04:31 BlazenNas kernel: [    1.772568] hub 9-0:1.0: USB hub found
Jan  9 16:04:31 BlazenNas kernel: [    2.080062] usb 8-1: new high speed USB device number 2 using xhci_hcd
Jan  9 16:04:31 BlazenNas kernel: [    2.092247] Initializing USB Mass Storage driver...
Jan  9 16:04:31 BlazenNas kernel: [    2.102568] USB Mass Storage support registered.
Jan  9 16:04:31 BlazenNas kernel: [    3.101180] scsi 6:0:0:0: Direct-Access     USB Mass  Storage Device       PQ: 0 ANSI: 0 CCS
Jan  9 16:04:34 BlazenNas kernel: [   10.556241] usb 8-1: USB disconnect, device number 2
Jan  9 16:04:34 BlazenNas kernel: [   10.808338] usb 9-1: new SuperSpeed USB device number 2 using xhci_hcd

---

### Post by Catalyph on 2012-01-10
Nobody knows? this is a pain.

It is faster for me to connect the USB drive to a Networked Windows Machine and copy the files over at 80MB/sec

---

