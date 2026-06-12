---
title: "usb drives"
date: 2011-06-03
forum: Server Platforms
---

### Post by mnknight on 2011-06-03
Seems when the Usb Harddrives I have connected to the server goes to sleep, the server decides to relabel the drives upon waking, is this common or is this a bug? see dmesg below:

[ 1274.200035] usb 1-3: reset high speed USB device using ehci_hcd and address 2
[ 6301.647853] usb 1-3: USB disconnect, address 2
[ 6301.812359] sd 6:0:0:0: [sdb] Synchronizing SCSI cache
[ 6301.814554] sd 6:0:0:0: [sdb]  Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[ 6313.510038] usb 1-3: new high speed USB device using ehci_hcd and address 5
[ 6313.664308] scsi9 : usb-storage 1-3:1.0
[ 6314.662112] scsi 9:0:0:0: Direct-Access     Seagate  FreeAgent        0138 PQ: 0 ANSI: 4
[ 6314.662970] sd 9:0:0:0: Attached scsi generic sg2 type 0
[ 6314.665241] sd 9:0:0:0: [sde] 2930277166 512-byte logical blocks: (1.50 TB/1.36 TiB)
[ 6314.665730] sd 9:0:0:0: [sde] Write Protect is off
[ 6314.665740] sd 9:0:0:0: [sde] Mode Sense: 1c 00 00 00
[ 6314.667230] sd 9:0:0:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 6314.688723]  sde: unknown partition table
[ 6314.691242] sd 9:0:0:0: [sde] Attached SCSI disk
[ 6315.054237] EXT3-fs: barriers not enabled
[ 6315.077900] kjournald starting.  Commit interval 5 seconds
[ 6315.080250] EXT3-fs (sde): using internal journal
[ 6315.080259] EXT3-fs (sde): recovery complete
[ 6315.080836] EXT3-fs (sde): mounted filesystem with ordered data mode

any ideas to correct this?

---

### Post by mnknight on 2011-06-04
Seagate Freeagent drives have a power issue which linux can't handle, so the work around is one or two ways :

easy way is to hook usb drive upto a windows machine and use the software provided by seagate to adjust the spin down and sleep modes.

not so easy way is going to terminal and using the sdparm command like this

sudo sdparm --clear STANDBY -6 /dev/sdb

sudo sdparm -a /dev/sdb

the standby should read zero now!

---

