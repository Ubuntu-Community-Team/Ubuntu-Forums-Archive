---
title: "HDD via USB 1.1.  became even slower"
date: 2010-03-11
forum: The Cafe
---

### Post by auvinen on 2010-03-11
After it took me 11 hours to tar 15gb of data on my USB disk, I decided to try to figure out what is the bottleneck. I am not very knowledgeable in file systems, USB HDs, etc... So I decided to try and ask here.

Here's the deal:
 - The machine I use has only USB 1.1. I use a USB HDD enclosure for back-up.
 - I used to back up things onto a 40gb Seagate ST340810A. 14gb tarred in 3h.
 - Changed the disk to a 80gb one by WD and tar of 15gb took over 11 hours.
 
Now a thing came to my mind: maybe 'time' is slowing things down? I used time to calculate the 11h... So the command was something like 'time tar blabla..."

Below is some info about the disks.

_Old disk (ST340810A) info_
Capacity:  			 			40.8 GB
Speed:  			5400 rpm
Average Read Time: 			8.9 ms
Cylinders: 			1023
Heads: 			256
Sectors: 			63

_New disk ( Barracuda 7200.7 ST380011A) info_
 
Capacity: 80.0gb
Speed: 7200rpm
Average Read Time: 8.5ms
Cylinders: 1023
Heads: 256
Sectors: 63
[U]
Bonnie++ benchmark results on the 80gb drive:[/U]

```
Version 1.03c       ------Sequential Output------ --Sequential Input- --Random-
                    -Per Chr- --Block-- -Rewrite- -Per Chr- --Block-- --Seeks--
Machine        Size K/sec %CP K/sec %CP K/sec %CP K/sec %CP K/sec %CP  /sec %CP
fancy          360M   386   3   386   0   153   0   235   0   254   0   5.3   0
                    ------Sequential Create------ --------Random Create--------
                    -Create-- --Read--- -Delete-- -Create-- --Read--- -Delete--
              files  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP
                 16   471  93 +++++ +++ +++++ +++   734  99 +++++ +++  2633  99
```

[U]
'hwinfo' about the new 80gb disk:[/U]

```
37: SCSI 200.0: 10600 Disk
  [Created at block.243]
  UDI: /org/freedesktop/Hal/devices/storage_serial_ST_ST380011A_0000000000000062W_0_0
  Unique ID: cLrx.yBL3HJZEQBA
  Parent ID: sRsQ.M6dR1NkQHEE
  SysFS ID: /class/block/sdb
  SysFS BusID: 2:0:0:0
  SysFS Device Link: /devices/pci0000:00/0000:00:04.2/usb1/1-2/1-2:1.0/host2/target2:0:0/2:0:0:0
  Hardware Class: disk
  Model: "ST380011A"
  Vendor: usb 0x13fd "ST"
  Device: usb 0x1040 "ST380011A"
  Revision: "1.06"
  Serial ID: "0000000000000062W"
  Driver: "usb-storage", "sd"
  Driver Modules: "usb_storage"
  Device File: /dev/sdb (/dev/sg1)
  Device Number: block 8:16-8:31 (char 21:1)
  Features: Hotpluggable
  Geometry (Logical): CHS 9729/255/63
  Size: 156301488 sectors a 512 bytes
  Speed: 12 Mbps
  Module Alias: "usb:v13FDp1040d0106dc00dsc00dp00ic08isc06ip50"
  Driver Info #0:
    Driver Status: usb_storage is active
    Driver Activation Cmd: "modprobe usb_storage"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #17 (USB Controller)

```

_hwinfo about the USB controller:_

```

17: PCI 04.2: 0c03 USB Controller (UHCI)
  [Created at pci.314]
  UDI: /org/freedesktop/Hal/devices/pci_1106_3038
  Unique ID: sRsQ.M6dR1NkQHEE
  SysFS ID: /devices/pci0000:00/0000:00:04.2
  SysFS BusID: 0000:00:04.2
  Hardware Class: usb controller
  Model: "VIA VT82xxxxx UHCI USB 1.1 Controller"
  Vendor: pci 0x1106 "VIA Technologies, Inc."
  Device: pci 0x3038 "VT82xxxxx UHCI USB 1.1 Controller"
  SubVendor: pci 0x0925 "First International Computer, Inc."
  SubDevice: pci 0x1234 "VA-502 Mainboard"
  Revision: 0x10
  Driver: "uhci_hcd"
  Driver Modules: "uhci_hcd"
  I/O Ports: 0xb400-0xb41f (rw)
  IRQ: 6 (200000 events)
  Module Alias: "pci:v00001106d00003038sv00000925sd00001234bc0Csc03i00"
  Driver Info #0:
    Driver Status: uhci-hcd is not active
    Driver Activation Cmd: "modprobe uhci-hcd"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

```


I will post the bonnie++ benchmark of the old drive soon. In the meantime, does anyone have a clue what could be causing this?

---

### Post by auvinen on 2010-03-11
Now that I think of it, there is another difference: I ran the back-up under screen.
I did 'screen bash' and then ran the back-up script.

But it seems strange that time or screen would cause such big differences in performance.

---

