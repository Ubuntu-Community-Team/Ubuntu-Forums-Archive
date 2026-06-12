---
title: "Ubuntu Server 10:04 won't recognise external drive."
date: 2011-01-26
forum: Server Platforms
---

### Post by Wildscot on 2011-01-26
I'm having problems getting an external USB hard drive (250GB, NTFS) to be recognised by Ubuntu 10.04 Server. 
If I attach it to my Debian desktop (CrunchBang) it's just fine.

I've even formatted the drive (again NTFS) with gParted. I've also run ntfsfix with it attached to my desktop, no errors.

I've installed usbmount on the server, no difference.

Here's what I've tried to date, after attaching the drive to the running system and rebooting the system with the drive attached.


```
sudo fdisk -l
```It doesn't show up.
```
df -l
```It doesn't show up.
```
cat /proc/scsi/scsi
```
Attached devices:
Host: scsi0 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: ST310014A        Rev: 3.09
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi0 Channel: 00 Id: 01 Lun: 00
  Vendor: ATA      Model: ST3160812A       Rev: 3.AA
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi1 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: WDC WD3200JB-00K Rev: 08.0
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi1 Channel: 00 Id: 01 Lun: 00
  Vendor: ATA      Model: Maxtor 6Y080L0   Rev: YAR4
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi2 Channel: 00 Id: 00 Lun: 00
  Vendor: Seagate  Model: FreeAgentDesktop Rev: 100D
  Type:   Direct-Access                    ANSI  SCSI revision: 02

There it is, FreeAgentDesktop.

```
lsusb
```
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 000: ID 0bc2:3000 Seagate RSS LLC 
Bus 001 Device 002: ID 0bc2:3000 Seagate RSS LLC 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

There it is, twice though?

```
ls /dev/sd*
```
/dev/sda  /dev/sda1  /dev/sda2  /dev/sdb  /dev/sdb1  /dev/sdc  /dev/sdc1  /dev/sdd  /dev/sdd1  /dev/sde

It's /dev/sde but without a partition if I'm understanding this correctly


```
dmesg | less
```
Pages and pages of errors repeating very similar to this.

[  193.788926] sd 2:0:0:0: [sde] Unhandled error code
[  193.788936] sd 2:0:0:0: [sde] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  193.788944] sd 2:0:0:0: [sde] CDB: Read(10): 28 00 00 00 01 08 00 00 08 00
[  193.788964] end_request: I/O error, dev sde, sector 264
[  193.799682] Buffer I/O error on device sde, logical block 33
[  193.924092] usb 1-4: reset high speed USB device using ehci_hcd and address 2
[  194.188103] usb 1-4: reset high speed USB device using ehci_hcd and address 2
[  194.452096] usb 1-4: reset high speed USB device using ehci_hcd and address 2
[  194.720085] usb 1-4: reset high speed USB device using ehci_hcd and address 2
[  194.988110] usb 1-4: reset high speed USB device using ehci_hcd and address 2
[  195.252097] usb 1-4: reset high speed USB device using ehci_hcd and address 2
[  195.397161] sd 2:0:0:0: [sde] Unhandled error code

So we have a problem, but what is this telling me? 
And why does it mount without issue on a Debian desktop system, pass (ntfstools) ntfsfix without error etc.

Anyone have any ideas what's going on here, as you can tell I've tried everything I can think of :confused:

---

### Post by Wildscot on 2011-01-26
OK, isn't it amazing how often after hours of searching, when you've tried everything you can think of, gone mental, tried everything again, then posted to the forums that you mysteriously work it out.

It turns out that it was a hardware issue. The machine in question is a frankenserver built from an old Compaq SFF desktop, hacked to bits and built into a living room unit. The USB ports on the back come from a riser that connects to the mother board through a PCI slot. It was one of those that wouldn't recognise the drive.

5 minutes with my hand jammed down the side of it to plug the cable into one of the USB ports on the front that comes directly off the motherboard and it showed up straight away. 8-[

---

