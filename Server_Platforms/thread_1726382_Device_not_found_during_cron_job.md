---
title: "Device not found during cron job"
date: 2011-04-11
forum: Server Platforms
---

### Post by holzkatz on 2011-04-11
(ubuntu server 10.4 LTS)

I've got a bash script that performs the backups on our office server. Backups are done to an external usb hard drive that we swap every week. The script works fine from the command line and also runs from cron, however every second day or so it seems I get the same problem: the server reports that it cannot find the device, even though it's plugged in. When I come into the office in the morning and the backup has failed, I just login and run the script and everything is fine - why it finds the device after I login is a mystery to me.

So I'm wondering why the server can't find this usb device every second day at 4 am, but as soon as I log in via ssh it can find it without any problems? Is there some sort of command I can execute that will discover or restart the drive (or something else)? 

NOTE:
I thought it might be that the drive needed to be woken up or something so I tried executing some other commands (blkid, hdparm) to wake it up. No dice.

Error messages:
hdparm -t /dev/sdb1
/dev/sdb1:
 Timing buffered disk reads:  read() failed: Input/output error
BLKFLSBUF failed: No such device

mount /dev/sdb1 /mnt/backup
mount: no such partition found


/var/log/messages
Apr 11 05:02:44 phoenix kernel: [500802.177851] usb 1-1: USB disconnect, address 5
Apr 11 05:02:44 phoenix kernel: [500802.181951] sd 8:0:0:0: [sdb] Unhandled error code
Apr 11 05:02:44 phoenix kernel: [500802.181956] sd 8:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
Apr 11 05:02:44 phoenix kernel: [500802.181961] sd 8:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 3f 00 00 f0 00
Apr 11 05:02:44 phoenix kernel: [500802.187727] __ratelimit: 230 callbacks suppressed
Apr 11 05:02:44 phoenix kernel: [500802.239952] sd 8:0:0:0: [sdb] Unhandled error code
Apr 11 05:02:44 phoenix kernel: [500802.239962] sd 8:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
Apr 11 05:02:44 phoenix kernel: [500802.239962] sd 8:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 01 2f 00 00 f0 00
Apr 11 05:02:51 phoenix kernel: [500809.180035] usb 1-1: new high speed USB device using ehci_hcd and address 6
Apr 11 05:02:51 phoenix kernel: [500809.333705] usb 1-1: configuration #1 chosen from 1 choice
Apr 11 05:02:51 phoenix kernel: [500809.333964] scsi9 : SCSI emulation for USB Mass Storage devices
Apr 11 05:02:56 phoenix kernel: [500814.330647] scsi 9:0:0:0: Direct-Access     WD       3200BMV External 1.75 PQ: 0 ANSI: 4
Apr 11 05:02:56 phoenix kernel: [500814.331084] sd 9:0:0:0: Attached scsi generic sg4 type 0
Apr 11 05:02:56 phoenix kernel: [500814.332008] sd 9:0:0:0: [sdb] 625142448 512-byte logical blocks: (320 GB/298 GiB)
Apr 11 05:02:56 phoenix kernel: [500814.332510] sd 9:0:0:0: [sdb] Write Protect is off
Apr 11 05:02:56 phoenix kernel: [500814.343511]  sdb: sdb1
Apr 11 05:02:56 phoenix kernel: [500814.386431] sd 9:0:0:0: [sdb] Attached SCSI disk


/var/log/kern.log:
Apr 11 05:02:44 phoenix kernel: [500802.177851] usb 1-1: USB disconnect, address 5
Apr 11 05:02:44 phoenix kernel: [500802.181951] sd 8:0:0:0: [sdb] Unhandled error code
Apr 11 05:02:44 phoenix kernel: [500802.181956] sd 8:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
Apr 11 05:02:44 phoenix kernel: [500802.181961] sd 8:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 3f 00 00 f0 00
Apr 11 05:02:44 phoenix kernel: [500802.181972] end_request: I/O error, dev sdb, sector 63
Apr 11 05:02:44 phoenix kernel: [500802.187727] __ratelimit: 230 callbacks suppressed
Apr 11 05:02:44 phoenix kernel: [500802.187732] Buffer I/O error on device sdb1, logical block 0
Apr 11 05:02:44 phoenix kernel: [500802.193572] Buffer I/O error on device sdb1, logical block 1
Apr 11 05:02:44 phoenix kernel: [500802.199219] Buffer I/O error on device sdb1, logical block 2
Apr 11 05:02:44 phoenix kernel: [500802.204743] Buffer I/O error on device sdb1, logical block 3
Apr 11 05:02:44 phoenix kernel: [500802.210253] Buffer I/O error on device sdb1, logical block 4
Apr 11 05:02:44 phoenix kernel: [500802.215629] Buffer I/O error on device sdb1, logical block 5
Apr 11 05:02:44 phoenix kernel: [500802.220871] Buffer I/O error on device sdb1, logical block 6
Apr 11 05:02:44 phoenix kernel: [500802.226133] Buffer I/O error on device sdb1, logical block 7
Apr 11 05:02:44 phoenix kernel: [500802.230986] Buffer I/O error on device sdb1, logical block 8
Apr 11 05:02:44 phoenix kernel: [500802.235465] Buffer I/O error on device sdb1, logical block 9
Apr 11 05:02:44 phoenix kernel: [500802.239952] sd 8:0:0:0: [sdb] Unhandled error code
Apr 11 05:02:44 phoenix kernel: [500802.239962] sd 8:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
Apr 11 05:02:44 phoenix kernel: [500802.239962] sd 8:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 01 2f 00 00 f0 00
Apr 11 05:02:44 phoenix kernel: [500802.239964] end_request: I/O error, dev sdb, sector 303
Apr 11 05:02:51 phoenix kernel: [500809.180035] usb 1-1: new high speed USB device using ehci_hcd and address 6
Apr 11 05:02:51 phoenix kernel: [500809.333705] usb 1-1: configuration #1 chosen from 1 choice
Apr 11 05:02:51 phoenix kernel: [500809.333964] scsi9 : SCSI emulation for USB Mass Storage devices
Apr 11 05:02:51 phoenix kernel: [500809.334094] usb-storage: device found at 6
Apr 11 05:02:51 phoenix kernel: [500809.334095] usb-storage: waiting for device to settle before scanning
Apr 11 05:02:56 phoenix kernel: [500814.330173] usb-storage: device scan complete
Apr 11 05:02:56 phoenix kernel: [500814.330647] scsi 9:0:0:0: Direct-Access     WD       3200BMV External 1.75 PQ: 0 ANSI: 4
Apr 11 05:02:56 phoenix kernel: [500814.331084] sd 9:0:0:0: Attached scsi generic sg4 type 0
Apr 11 05:02:56 phoenix kernel: [500814.332008] sd 9:0:0:0: [sdb] 625142448 512-byte logical blocks: (320 GB/298 GiB)
Apr 11 05:02:56 phoenix kernel: [500814.332510] sd 9:0:0:0: [sdb] Write Protect is off
Apr 11 05:02:56 phoenix kernel: [500814.332513] sd 9:0:0:0: [sdb] Mode Sense: 23 00 00 00
Apr 11 05:02:56 phoenix kernel: [500814.332516] sd 9:0:0:0: [sdb] Assuming drive cache: write through
Apr 11 05:02:56 phoenix kernel: [500814.338754] sd 9:0:0:0: [sdb] Assuming drive cache: write through
Apr 11 05:02:56 phoenix kernel: [500814.343511]  sdb: sdb1
Apr 11 05:02:56 phoenix kernel: [500814.382124] sd 9:0:0:0: [sdb] Assuming drive cache: write through
Apr 11 05:02:56 phoenix kernel: [500814.386431] sd 9:0:0:0: [sdb] Attached SCSI disk

---

