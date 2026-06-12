---
title: "Serval Pro: Wifi problems when using usb3"
date: 2011-08-26
forum: System76 Support
---

### Post by xvedejas on 2011-08-26
When I plug in a usb3 drive, my wireless card stops working. If I try to use an SD card in the SD slot, the system freezes up. Locking the screen seems to also sometimes mess with the wifi.

dmesg output;

```
[30736.777509] usb 2-1.5: usbfs: process 7384 (fingerprint-hel) did not claim interface 0 before use
[31575.216843] usb 3-2: new SuperSpeed USB device using xhci_hcd and address 2
[31575.239574] xhci_hcd 0000:02:00.0: WARN: short transfer on control ep
[31575.240258] xhci_hcd 0000:02:00.0: WARN: short transfer on control ep
[31575.240870] xhci_hcd 0000:02:00.0: WARN: short transfer on control ep
[31575.241492] xhci_hcd 0000:02:00.0: WARN: short transfer on control ep
[31575.871900] usbcore: registered new interface driver uas
[31575.894551] Initializing USB Mass Storage driver...
[31575.894786] scsi7 : usb-storage 3-2:1.0
[31575.894998] usbcore: registered new interface driver usb-storage
[31575.894999] USB Mass Storage support registered.
[31576.888204] scsi 7:0:0:0: Direct-Access     Fantom   Extemal HDD      JP2O PQ: 0 ANSI: 5
[31576.889656] sd 7:0:0:0: Attached scsi generic sg4 type 0
[31576.889694] sd 7:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[31576.889946] xhci_hcd 0000:02:00.0: WARN: Stalled endpoint
[31576.890841] sd 7:0:0:0: [sdb] Write Protect is off
[31576.890850] sd 7:0:0:0: [sdb] Mode Sense: 23 00 00 00
[31576.891252] sd 7:0:0:0: [sdb] No Caching mode page present
[31576.891262] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[31576.891933] xhci_hcd 0000:02:00.0: WARN: Stalled endpoint
[31576.894255] sd 7:0:0:0: [sdb] No Caching mode page present
[31576.894267] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[31576.906986]  sdb: sdb1
[31576.907728] xhci_hcd 0000:02:00.0: WARN: Stalled endpoint
[31576.908714] sd 7:0:0:0: [sdb] No Caching mode page present
[31576.908724] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[31576.908731] sd 7:0:0:0: [sdb] Attached SCSI disk
[31577.142433] xhci_hcd 0000:02:00.0: WARN: Stalled endpoint
[31589.653897] EXT4-fs (dm-1): mounted filesystem with ordered data mode. Opts: (null)
[31607.478742] xhci_hcd 0000:02:00.0: WARN: Stalled endpoint
[31607.479615] xhci_hcd 0000:02:00.0: WARN: Stalled endpoint
[31607.586945] xhci_hcd 0000:02:00.0: WARN: Stalled endpoint
[31607.721178] xhci_hcd 0000:02:00.0: WARN: Stalled endpoint
[31607.820047] xhci_hcd 0000:02:00.0: WARN: Stalled endpoint
[31607.820747] sd 7:0:0:0: [sdb]  Sense Key : Recovered Error [current] [descriptor]
[31607.820765] Descriptor sense data with sense descriptors (in hex):
[31607.820771]         72 01 04 1d 00 00 00 0e 09 0c 00 00 00 00 00 00 
[31607.820796]         00 4f 00 c2 00 50 
[31607.820812] sd 7:0:0:0: [sdb]  ASC=0x4 ASCQ=0x1d
```

After plugging in, bars shown on nm-applet go from 2 to 3, but webpages stop loading. Disconnect:

```
[31747.171834] usb 3-2: USB disconnect, address 2
```

I upgraded the computer from ubuntu 10.10 to 11.04, with no changes. I've tried on an 11.04 live CD, and the problems still persist there. Here's some more information;

```
sudo lshw -C network

  *-network               
       description: Ethernet interface
       product: JMC250 PCI Express Gigabit Ethernet Controller
       vendor: JMicron Technology Corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 05
       serial: 00:90:f5:b7:89:a2
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msix msi bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=jme driverversion=1.0.7 duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:56 memory:f6320000-f6323fff ioport:d100(size=128) ioport:d000(size=256) memory:f6310000-f631ffff memory:f6300000-f630ffff
  *-network
       description: Wireless interface
       product: Centrino Ultimate-N 6300
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 35
       serial: 00:24:d7:90:e0:78
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=2.6.38-8-generic firmware=9.221.4.1 build 25532 ip=192.168.1.148 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:54 memory:f6200000-f6201fff
```
```

lspci | grep Network

Network controller: Intel Corporation Centrino Ultimate-N 6300 (rev 35)
```

---

### Post by xvedejas on 2011-08-28
No help?

---

### Post by isantop on 2011-08-30
Can you try testing it while connected to Ethernet instead of WiFi? This will help tell me if it's a software problem.

---

