---
title: "Safely unplug disk with ZFS pool on it"
date: 2021-01-06
forum: Server Platforms
---

### Post by andrum99 on 2021-01-06
What is the correct way to prepare a USB drive containing a ZFS pool for safe removal? If I simply export the pool, then unplug the two USB drives (it's a mirrored pool), I get errors in the log:

> [116444.704978] usb 2-2.1: USB disconnect, device number 8[116444.720237] sd 3:0:0:0: [sdd] Synchronizing SCSI cache
[116444.971741] sd 3:0:0:0: [sdd] Synchronize Cache(10) failed: Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[116445.664967] usb 2-2.2: USB disconnect, device number 7
[116445.667584] sd 2:0:0:0: [sdc] Synchronizing SCSI cache
[116445.923761] sd 2:0:0:0: [sdc] Synchronize Cache(10) failed: Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK

I've tried installing udisks2, then running `udisksctl power-off -b /dev/sdc` but I still get the errors. As far as I know there is no problem with the data on the disk - I've done multiple scrubs and no errors are ever reported - but the error messages make me a bit nervous.

---

### Post by TheFu on 2021-01-06
Does powering down the system, then removing the HDD, not work?

---

