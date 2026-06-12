---
title: "Ubuntu 17.10 does not detect flash drive."
date: 2017-06-07
forum: Ubuntu Development Version
---

### Post by Hewjr100 on 2017-06-07
Just noticed today that flash drives are not detected.  This is a fresh install of Ubuntu 17.10 daily 6/06/17 with gnome as default.  Anyone else have this problem?

Henry.

---

### Post by oldfred on 2017-06-07
Someone posted this:
 Some HP will not boot a flash drive that is gpt partitioned. Some only boot from the USB2 port not USB3 ports.
[http://ubuntuforums.org/showthread.php?t=2213631&p=13468260#post13468260](http://ubuntuforums.org/showthread.php?t=2213631&p=13468260#post13468260) 

But often you have to go into UEFI/BIOS and turn on settings to allow USB particularly if UEFI Secure Boot is on. As flash drive boot would not be secure.
And some found things start working if they update UEFI/BIOS to newest version from vendor. And some fixes are not in list of things they report they are fixing.

---

### Post by Hewjr100 on 2017-06-07
Not using EUFI flash drive detected in all previous versions of Ubuntu.

Henry.

---

### Post by Hewjr100 on 2017-06-07
One thing I forgot to say.  2 flash drive are FAT32 and 1 is NTFS.  None of them are being detected.  None of them are GPT

---

### Post by cariboo on 2017-06-08
Could you plug in one of your flash drives, and show us what dmesg says. One my system it looks like this:

```
[ 1237.294689] sd 5:0:0:0: Attached scsi generic sg4 type 0
[ 1237.295943] sd 5:0:0:0: [sdd] 15625216 512-byte logical blocks: (8.00 GB/7.45 GiB)
[ 1237.297640] sd 5:0:0:0: [sdd] Write Protect is off
[ 1237.297644] sd 5:0:0:0: [sdd] Mode Sense: 03 00 00 00
[ 1237.298640] sd 5:0:0:0: [sdd] No Caching mode page found
[ 1237.298648] sd 5:0:0:0: [sdd] Assuming drive cache: write through
[ 1237.306921]  sdd: sdd1 sdd2
[ 1237.311753] sd 5:0:0:0: [sdd] Attached SCSI removable disk
[ 1237.730222] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 1237.732593] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 1237.733968] ISO 9660 Extensions: RRIP_1991A
```

I started with Ubuntu-Gnome 17.04, then upgraded to Artful, and checking for updates at least twice a day.

---

### Post by ventrical on 2017-06-08
Works fine here from an earlier fresh install of 17.10.

```

[  789.160023] usb 1-1: new high-speed USB device number 2 using ehci-pci
[  789.337572] usb 1-1: New USB device found, idVendor=048d, idProduct=1177
[  789.337575] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  789.337577] usb 1-1: Product: USB Mass Storage Device
[  789.337578] usb 1-1: Manufacturer: Generic
[  789.516991] usb-storage 1-1:1.0: USB Mass Storage device detected
[  789.517096] scsi host8: usb-storage 1-1:1.0
[  789.517172] usbcore: registered new interface driver usb-storage
[  789.534305] usbcore: registered new interface driver uas
[  790.899832] scsi 8:0:0:0: Direct-Access     Generic  USB Flash Disk   0.00 PQ: 0 ANSI: 6
[  790.901638] sd 8:0:0:0: Attached scsi generic sg1 type 0
[  790.902583] sd 8:0:0:0: [sdb] 31459328 512-byte logical blocks: (16.1 GB/15.0 GiB)
[  790.904456] sd 8:0:0:0: [sdb] Write Protect is off
[  790.904458] sd 8:0:0:0: [sdb] Mode Sense: 23 00 00 00
[  790.905437] sd 8:0:0:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  790.911198]  sdb: sdb1
[  790.914688] sd 8:0:0:0: [sdb] Attached SCSI removable disk

```

---

### Post by rrnbtter on 2017-06-08
Greetings,
I presume the OP is saying that his already installed OS is not loading flash drives. I just noticed this morning that my USB2 DatastickPro will load from my USB3 port but not from my USB2 port. Since the USB3 is faster even on older flash drives I have used USB3 by default and just found this problem. 

Regarding installing from USB, my wife and I have two different releases of the same Lenovo Laptop. I changed the CMOS on my system to boot USB but upon reboot the "boot USB" is reset back to default "no boot USB". I set the CMOS on my wife's system to boot USB and it retains that settings. So it seems that booting from USB options will be different from one system to another.

---

### Post by #&amp;thj^% on 2017-06-08
> **rrnbtter said:**
> Greetings,
I presume the OP is saying that his already installed OS is not loading flash drives. I just noticed this morning that my USB2 DatastickPro will load from my USB3 port but not from my USB2 port. Since the USB3 is faster even on older flash drives I have used USB3 by default and just found this problem. 

Regarding installing from USB, my wife and I have two different releases of the same Lenovo Laptop. I changed the CMOS on my system to boot USB but upon reboot the "boot USB" is reset back to default "no boot USB". I set the CMOS on my wife's system to boot USB and it retains that settings. So it seems that booting from USB options will be different from one system to another.
Thanks for pointing this out ;)...and just to add to it I have 2 My Book USB Dives That normally
have no issues when both are plugged in and show on older versions 16.04, but with 17.10 it will drop one if both are plugged in. (Tested with all kernels)
And troubles with my USB keyboard with certain usage stops interacting fully in All Browsers.
In both sessions Gnome && Wayland.

---

