---
title: "Drives slow down when echi_hcd loaded"
date: 2008-11-08
forum: Server Platforms
---

### Post by SJI on 2008-11-08
Hello everyone.

I've just noticed an odd thing on my server.
The server is a K6-500 machine so not blindingly fast, but it does what i need it too.

Disc throughput is usually:
```
/dev/hda:
 Timing cached reads:   108 MB in  2.03 seconds =  53.15 MB/sec
 Timing buffered disk reads:   70 MB in  3.07 seconds =  22.81 MB/sec
```

If a usb2 device is inserted into a usb port and ehci_hcd is loaded the disk throughput drops to:
```
/dev/hda:
 Timing cached reads:    12 MB in  2.23 seconds =   5.38 MB/sec
 Timing buffered disk reads:   16 MB in  3.17 seconds =   5.05 MB/sec
```

If I remove the USB device the drives are still slow.
If I then modprobe -r ehci_hcd the drives return to their normal throughput.

USB1 devices don't cause a jot of trouble.

Machine is running Ubuntu 8.04.1 2.6.24.3 with a cut down kernel.

lspci:
```
00:00.0 Host bridge: ALi Corporation M1541 (rev 04)
00:01.0 PCI bridge: ALi Corporation M1541 PCI to AGP Controller (rev 04)
00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:03.0 Non-VGA unclassified device: ALi Corporation M7101 Power Management Controller [PMU]
00:07.0 ISA bridge: ALi Corporation M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+] (rev c3)
00:0e.0 SCSI storage controller: LSI Logic / Symbios Logic 53c875 (rev 04)
00:0f.0 IDE interface: ALi Corporation M5229 IDE (rev c1)
00:10.0 Ethernet controller: Intel Corporation 8255xER/82551IT Fast Ethernet Controller (rev 09)
00:12.0 Ethernet controller: Intel Corporation 8255xER/82551IT Fast Ethernet Controller (rev 09)
00:14.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
00:14.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
00:14.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 65)
00:14.3 RAID bus controller: VIA Technologies, Inc. VT6421 IDE RAID Controller (rev 50)
```

lsmod:
```
Module                  Size  Used by
sata_via                7876  1
cifs                  216816  3
i2c_ali15x3             5604  0
libata                109272  1 sata_via
```

Any ideas anyone? :confused:

TIA

Stephen

---

### Post by cariboo on 2008-11-09
I saw the same thing happen on a computer running windows xp a couple of years ago. The owner bought an external 2.5" hard drive, that also got it's power from usb with a seperate usb cable, even plugging the usb power cable into a powered hub didn't seem to make any difference. She always complained that the computer ran slower when the external drive was plugged in. She has since replaced the computer with an Acer laptop and the problem has disappeared.

You could also blacklist the sata drivers, as I doubt you have any sata ports:

```
sata_via
libata 
```

Add the above to files to /etc/modprobe.d/blacklist

Jim

---

### Post by SJI on 2008-11-09
Thanks for the reply Jim,

> **cariboo907 said:**
> 
You could also blacklist the sata drivers, as I doubt you have any sata ports:

```
sata_via
libata 
```

Add the above to files to /etc/modprobe.d/blacklist


I have a couple of TB drives hanging off a via sata controller, but i'll try booting without those drivers and see if there's any change.

Is libata not required for the onboard IDE controller?

Stephen

---

### Post by SJI on 2008-11-09
I've just tried booting with all modules except ehci_hcd blacklisted and there's no change. Drive throughput is still slow whenever the ehci_hcd module is loaded.

There's no process that looks suspect when viewing the output for TOP either, but I notice that the CPU temperature is raised to that seen when a backup with compression is running. 

The CPU temperature reverts to normal when ehci_hcd is unloaded.

Stephen

---

