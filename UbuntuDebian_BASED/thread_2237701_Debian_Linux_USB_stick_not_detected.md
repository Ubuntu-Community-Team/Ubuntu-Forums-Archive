---
title: "Debian Linux USB stick not detected"
date: 2014-08-03
forum: Ubuntu/Debian BASED
---

### Post by Guyofdoom42 on 2014-08-03
My friend has Debian linux, and it won't detect his USB drive. At all. It's like it isn't even there. We tried all the USB ports, and still nothing.

HALP!

---

### Post by coffeecat on 2014-08-03
*Thread moved to **Other Operating Systems and Projects**.*

---

### Post by cariboo on 2014-08-05
Do you get any indication from dmesg when you insert the device? the output should look similar to this:

```
[52529.831635] usb 4-2: new high-speed USB device number 2 using xhci_hcd
[52530.047919] usb 4-2: New USB device found, idVendor=0781, idProduct=5535
[52530.047926] usb 4-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[52530.047931] usb 4-2: Product: Ultra Backup
[52530.047935] usb 4-2: Manufacturer: SanDisk
[52530.047938] usb 4-2: SerialNumber: 43175113E6533D6A
[52530.103826] usb-storage 4-2:1.0: USB Mass Storage device detected
[52530.104579] scsi4 : usb-storage 4-2:1.0
[52530.104667] usbcore: registered new interface driver usb-storage
[52530.107884] usbcore: registered new interface driver uas
[52531.102713] scsi 4:0:0:0: Direct-Access     SanDisk  Ultra Backup     8.32 PQ: 0 ANSI: 0 CCS
[52531.103331] sd 4:0:0:0: Attached scsi generic sg3 type 0
[52531.103428] sd 4:0:0:0: [sdc] 15745023 512-byte logical blocks: (8.06 GB/7.50 GiB)
[52531.103568] sd 4:0:0:0: [sdc] Write Protect is off
[52531.103572] sd 4:0:0:0: [sdc] Mode Sense: 45 00 00 08
[52531.103712] sd 4:0:0:0: [sdc] No Caching mode page found
[52531.103715] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[52531.107366]  sdc: sdc1
[52531.108836] sd 4:0:0:0: [sdc] Attached SCSI removable disk
```

---

