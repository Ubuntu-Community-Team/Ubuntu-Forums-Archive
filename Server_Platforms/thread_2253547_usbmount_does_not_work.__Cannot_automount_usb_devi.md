---
title: "usbmount does not work.  Cannot automount usb device"
date: 2014-11-20
forum: Server Platforms
---

### Post by bnebb42 on 2014-11-20
I've been trying for two days to get a usb drive (both flash and external hdd) mounted to Server 14.04.  I've installed usbmount per several posts I've found in this and other forums.  All lsusb shows are the root hubs, no inserted devices.  Fdisk only shows the internal hard drive.  usbmount creates the 8 default subdirectories in the /media directory but when a usb device is plugged in, no action.  Checking the system log only shows discovery of the usb root hubs at boot.  The flash drives are fat32 and are found without issue on a linux desktop and on a windows box.  The server? No.  And I had the same problem on 12.04 server.  Never resolved that one either.

I am using the 64 bit server.  This one is on a Dell chassis, the 12.04 was on an HP chassis.  Everything but the USB seems to work.  It appears that something is missing that udev does not detect the insertion of any usb drive.

Can someone help?

---

### Post by nerdtron on 2014-11-20
I'm a bit confused from your title.
Is the problem automounting the USB or you can't even manually mount the USB?

---

### Post by Jonathan L on 2014-11-20
Hi bnebb42

You'll have to find out why the USB device isn't being noticed before addressing the mounting issue.

When you put the USB device in, you should see entries in syslog.  A server without automounting (32-bit, 12.04) shows:
```
Nov 20 21:44:35 rhino kernel: [4069461.788052] usb 1-2: new high-speed USB device number 4 using ehci_hcd
Nov 20 21:44:35 rhino kernel: [4069461.923298] usb 1-2: New USB device found, idVendor=0930, idProduct=6544
Nov 20 21:44:35 rhino kernel: [4069461.923308] usb 1-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Nov 20 21:44:35 rhino kernel: [4069461.923315] usb 1-2: Product: DataTraveler 2.0
Nov 20 21:44:35 rhino kernel: [4069461.923320] usb 1-2: Manufacturer: Kingston
Nov 20 21:44:35 rhino kernel: [4069461.923326] usb 1-2: SerialNumber: C86000BDBE4ECE90426472691
Nov 20 21:44:35 rhino kernel: [4069462.021520] Initializing USB Mass Storage driver...
Nov 20 21:44:35 rhino kernel: [4069462.022031] scsi6 : usb-storage 1-2:1.0
Nov 20 21:44:35 rhino kernel: [4069462.022326] usbcore: registered new interface driver usb-storage
Nov 20 21:44:35 rhino kernel: [4069462.022333] USB Mass Storage support registered.
Nov 20 21:44:35 rhino kernel: [4069462.029126] usbcore: registered new interface driver uas
Nov 20 21:44:36 rhino kernel: [4069463.038038] scsi 6:0:0:0: Direct-Access     Kingston DataTraveler 2.0 1.00 PQ: 0 ANSI: 4
Nov 20 21:44:36 rhino kernel: [4069463.040527] sd 6:0:0:0: Attached scsi generic sg1 type 0
Nov 20 21:44:36 rhino kernel: [4069463.043049] sd 6:0:0:0: [sdb] 15148608 512-byte logical blocks: (7.75 GB/7.22 GiB)
Nov 20 21:44:36 rhino kernel: [4069463.044675] sd 6:0:0:0: [sdb] Write Protect is off
Nov 20 21:44:36 rhino kernel: [4069463.044693] sd 6:0:0:0: [sdb] Mode Sense: 45 00 00 00
Nov 20 21:44:36 rhino kernel: [4069463.045645] sd 6:0:0:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Nov 20 21:44:36 rhino kernel: [4069463.051475]  sdb: sdb1
Nov 20 21:44:36 rhino kernel: [4069463.054603] sd 6:0:0:0: [sdb] Attached SCSI removable disk
```

Afterwards, lsusb will show the new device; manual mounting should work; and I'd guess the automounting.

Is it possible there's something wrong with the USB sockets?

Hope that's helpful,
Jonathan.

---

### Post by lukeiamyourfather on 2014-11-21
If lsusb isn't showing the devices then it's possible there's a hardware issue with the USB ports because the devices should show up regardless of whether they get mounted or not. The most common issue I've seen is current overload. If there are other devices plugged into the USB ports trying removing them, especially high current devices (backlit keyboard, phone or tablet, bus powered external drives, wireless adapters, etc.).

---

