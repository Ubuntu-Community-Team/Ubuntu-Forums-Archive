---
title: "Encrypted USB volume not usable on 32-bit machine"
date: 2015-10-16
forum: Security
---

### Post by mid-day on 2015-10-16
Hullo.  On 64-bit laptop 14.04  I encrypted the volume and it works, but it's not readable on my 32-bit 10.04 laptop. On the Lucid, entering the passphrase produces an error message which I could use some help with using...here is the response from dmesg:
```

[ 1504.836115] usb 1-4: new high speed USB device using ehci_hcd and address 5
[ 1504.969622] usb 1-4: configuration #1 chosen from 1 choice
[ 1505.023469] Initializing USB Mass Storage driver...
[ 1505.023680] scsi2 : SCSI emulation for USB Mass Storage devices
[ 1505.024215] usbcore: registered new interface driver usb-storage
[ 1505.024220] USB Mass Storage support registered.
[ 1505.026855] usb-storage: device found at 5
[ 1505.026859] usb-storage: waiting for device to settle before scanning
[ 1510.024710] usb-storage: device scan complete
[ 1510.025283] scsi 2:0:0:0: Direct-Access     Seagate  Portable         0130 PQ: 0 ANSI: 4
[ 1510.026534] sd 2:0:0:0: Attached scsi generic sg2 type 0
[ 1510.028051] sd 2:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[ 1510.030841] sd 2:0:0:0: [sdb] Write Protect is off
[ 1510.030849] sd 2:0:0:0: [sdb] Mode Sense: 2f 08 00 00
[ 1510.030854] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 1510.032871] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 1510.032880]  sdb: sdb1
[ 1510.102970] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 1510.102980] sd 2:0:0:0: [sdb] Attached SCSI disk
[ 1536.238577] device-mapper: table: 252:0: crypt: Invalid IV mode
[ 1536.238582] device-mapper: ioctl: error adding target to table
[ 3178.877005] usb 1-4: USB disconnect, address 5
[ 3309.000140] usb 1-4: new high speed USB device using ehci_hcd and address 6
[ 3309.133723] usb 1-4: configuration #1 chosen from 1 choice
[ 3309.134745] scsi3 : SCSI emulation for USB Mass Storage devices
[ 3309.135049] usb-storage: device found at 6
[ 3309.135053] usb-storage: waiting for device to settle before scanning
[ 3314.132544] usb-storage: device scan complete
[ 3314.133141] scsi 3:0:0:0: Direct-Access     Seagate  Portable         0130 PQ: 0 ANSI: 4
[ 3314.134244] sd 3:0:0:0: Attached scsi generic sg2 type 0
[ 3314.135467] sd 3:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[ 3314.139342] sd 3:0:0:0: [sdb] Write Protect is off
[ 3314.139350] sd 3:0:0:0: [sdb] Mode Sense: 2f 08 00 00
[ 3314.139356] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[ 3314.142201] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[ 3314.142209]  sdb: sdb1
[ 3314.211936] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[ 3314.211946] sd 3:0:0:0: [sdb] Attached SCSI disk
[ 3341.902903] device-mapper: table: 252:0: crypt: Invalid IV mode
[ 3341.902910] device-mapper: ioctl: error adding target to table

```

---

### Post by TheFu on 2015-10-16
Support for 10.04 desktop ended in 2013. Well passed time to migrate to a supported release.
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

Plus, encryption has changed slightly the last 5 yrs. After your laptop runs 14.04, reading the encrypted volume should be possible.

---

### Post by mid-day on 2015-10-16
Thanks

---

