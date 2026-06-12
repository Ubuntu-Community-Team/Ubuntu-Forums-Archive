---
title: "laptop crashes on startup, logs corrupted"
date: 2020-09-29
forum: Ubuntu/Debian BASED
---

### Post by jucajuca on 2020-09-29
Hello,

My laptop crashes at start up. 
This only happens when:

- I start the laptop
- The power cord is disconnected (only battery)

The laptop just shuts down abruptly. The logs are corrupted and it is very difficul to know what happens. However I compared the logs of a normal session with the logs of the crashes. I guess this might be related to bluetooth but I am not sure.

How could I completely deactivate bluetooth to make further tests?


Snippet of a crash
```
Sep 20 15:14:55 pop-os kernel: [   16.686655] bridge: filtering via arp/ip/ip6tables is no longer available by default. Update your scripts to load br_netfilter if you need this.
Sep 20 15:14:55 pop-os kernel: [   16.691874] Bridge firewalling registered
Sep 20 15:14:55 pop-os kernel: [   16.704726] bpfilter: Loaded bpfilter_umh pid 1747
Sep 20 15:14:55 pop-os kernel: [   16.884523] Initializing XFRM netlink socket
Sep 20 15:14:55 pop-os kernel: [   17.225828] docker0: port 1(vethffeabeb) entered blocking state
Sep 20 15:14:55 pop-os kernel: [   17.225834] docker0: port 1(vethffeabeb) entered disabled state
Sep 20 15:14:55 pop-os kernel: [   17.226086] device vethffeabeb entered promiscuous mode
Sep 20 15:14:55 pop-os kernel: [   17.226444] docker0: port 1(vethffeabeb) entered blocking state
Sep 20 15:14:55 pop-os kernel: [   17.226449] docker0: port 1(vethffeabeb) entered forwarding state
Sep 20 15:14:55 pop-os kernel: [   17.226635] docker0: port 1(vethffeabeb) entered disabled state
Sep 20 15:14:55 pop-os kernel: [   17.242368] docker0: port 2(veth7cc5de9) entered blocking state
Sep 20 15:14:55 pop-os kernel: [   17.242375] docker0: port 2(veth7cc5de9) entered disabled state
Sep 20 15:14:55 pop-os kernel: [   17.242823] device veth7cc5de9 entered promiscuous mode
Sep 20 15:14:55 pop-os kernel: [   17.243217] docker0: port 2(veth7cc5de9) entered blocking state
Sep 20 15:14:55 pop-os kernel: [   17.243222] docker0: port 2(veth7cc5de9) entered forwarding state
Sep 20 15:14:55 pop-os kernel: [   17.243309] IPv6: ADDRCONF(NETDEV_CHANGE): docker0: link becomes ready
Sep 20 15:14:55 pop-os kernel: [   17.243882] docker0: port 2(veth7cc5de9) entered disabled state
Sep 20 15:14:56 pop-os kernel: [   17.437914] docker0: port 1(vethffeabeb) entered disabled state
Sep 20 15:14:56 pop-os kernel: [   17.449199] device vethffeabeb left promiscuous mode
Sep 20 15:14:56 pop-os kernel: [   17.449211] docker0: port 1(vethffeabeb) entered disabled state
Sep 20 15:14:56 pop-os kernel: [   17.826621] rfkill: input handler disabled
Sep 20 15:14:56 pop-os kernel: [   18.124559] eth0: renamed from veth765f958
Sep 20 15:14:56 pop-os kernel: [   18.148313] IPv6: ADDRCONF(NETDEV_CHANGE): veth7cc5de9: link becomes ready
Sep 20 15:14:56 pop-os kernel: [   18.148420] docker0: port 2(veth7cc5de9) entered blocking state
Sep 20 15:14:56 pop-os kernel: [   18.148424] docker0: port 2(veth7cc5de9) entered forwarding state
\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00....
```


full log of a crash: [https://paste.ubuntu.com/p/46vWYxjxvB/](https://paste.ubuntu.com/p/46vWYxjxvB/)

Snippet of normal session
```
Sep 15 13:43:16 pop-os kernel: [   10.578434] bridge: filtering via arp/ip/ip6tables is no longer available by default. Update your scripts to load br_netfilter if you need this.
Sep 15 13:43:16 pop-os kernel: [   10.581721] Bridge firewalling registered
Sep 15 13:43:16 pop-os kernel: [   10.592484] bpfilter: Loaded bpfilter_umh pid 1751
Sep 15 13:43:16 pop-os kernel: [   10.690893] Initializing XFRM netlink socket
Sep 15 13:43:16 pop-os kernel: [   11.068455] docker0: port 1(veth2901aef) entered blocking state
Sep 15 13:43:16 pop-os kernel: [   11.068460] docker0: port 1(veth2901aef) entered disabled state
Sep 15 13:43:16 pop-os kernel: [   11.068678] device veth2901aef entered promiscuous mode
Sep 15 13:43:16 pop-os kernel: [   11.069052] docker0: port 1(veth2901aef) entered blocking state
Sep 15 13:43:16 pop-os kernel: [   11.069056] docker0: port 1(veth2901aef) entered forwarding state
Sep 15 13:43:16 pop-os kernel: [   11.069217] docker0: port 1(veth2901aef) entered disabled state
Sep 15 13:43:16 pop-os kernel: [   11.081177] docker0: port 2(vethd8c4c7b) entered blocking state
Sep 15 13:43:16 pop-os kernel: [   11.081182] docker0: port 2(vethd8c4c7b) entered disabled state
Sep 15 13:43:16 pop-os kernel: [   11.081407] device vethd8c4c7b entered promiscuous mode
Sep 15 13:43:16 pop-os kernel: [   11.081834] docker0: port 2(vethd8c4c7b) entered blocking state
Sep 15 13:43:16 pop-os kernel: [   11.081840] docker0: port 2(vethd8c4c7b) entered forwarding state
Sep 15 13:43:16 pop-os kernel: [   11.082042] IPv6: ADDRCONF(NETDEV_CHANGE): docker0: link becomes ready
Sep 15 13:43:16 pop-os kernel: [   11.082299] docker0: port 2(vethd8c4c7b) entered disabled state
Sep 15 13:43:16 pop-os kernel: [   11.201138] docker0: port 2(vethd8c4c7b) entered disabled state
Sep 15 13:43:16 pop-os kernel: [   11.204880] device vethd8c4c7b left promiscuous mode
Sep 15 13:43:16 pop-os kernel: [   11.204891] docker0: port 2(vethd8c4c7b) entered disabled state
Sep 15 13:43:17 pop-os kernel: [   11.542104] eth0: renamed from veth9a78a71
Sep 15 13:43:17 pop-os kernel: [   11.558427] IPv6: ADDRCONF(NETDEV_CHANGE): veth2901aef: link becomes ready
Sep 15 13:43:17 pop-os kernel: [   11.558506] docker0: port 1(veth2901aef) entered blocking state
Sep 15 13:43:17 pop-os kernel: [   11.558509] docker0: port 1(veth2901aef) entered forwarding state
Sep 15 13:43:31 pop-os kernel: [   26.100626] Bluetooth: RFCOMM TTY layer initialized
Sep 15 13:43:31 pop-os kernel: [   26.100632] Bluetooth: RFCOMM socket layer initialized
Sep 15 13:43:31 pop-os kernel: [   26.100635] Bluetooth: RFCOMM ver 1.11
Sep 15 13:43:32 pop-os kernel: [   26.385936] rfkill: input handler enabled
Sep 15 13:43:34 pop-os kernel: [   28.384294] rfkill: input handler disabled
Sep 15 13:45:52 pop-os kernel: [  166.351585] rfkill: input handler enabled
```


// *******************************************************************************************************************************

Snippet of normal session
```
Sep 15 16:34:33 pop-os kernel: [   10.696064] bridge: filtering via arp/ip/ip6tables is no longer available by default. Update your scripts to load br_netfilter if you need this.
Sep 15 16:34:33 pop-os kernel: [   10.699520] Bridge firewalling registered
Sep 15 16:34:33 pop-os kernel: [   10.710909] bpfilter: Loaded bpfilter_umh pid 1747
Sep 15 16:34:33 pop-os kernel: [   10.798478] Initializing XFRM netlink socket
Sep 15 16:34:33 pop-os kernel: [   10.971783] docker0: port 1(veth77eaea2) entered blocking state
Sep 15 16:34:33 pop-os kernel: [   10.971787] docker0: port 1(veth77eaea2) entered disabled state
Sep 15 16:34:33 pop-os kernel: [   10.971947] device veth77eaea2 entered promiscuous mode
Sep 15 16:34:33 pop-os kernel: [   10.972158] docker0: port 1(veth77eaea2) entered blocking state
Sep 15 16:34:33 pop-os kernel: [   10.972161] docker0: port 1(veth77eaea2) entered forwarding state
Sep 15 16:34:33 pop-os kernel: [   10.972272] docker0: port 1(veth77eaea2) entered disabled state
Sep 15 16:34:33 pop-os kernel: [   10.983434] docker0: port 2(vethe6fc182) entered blocking state
Sep 15 16:34:33 pop-os kernel: [   10.983440] docker0: port 2(vethe6fc182) entered disabled state
Sep 15 16:34:33 pop-os kernel: [   10.983677] device vethe6fc182 entered promiscuous mode
Sep 15 16:34:33 pop-os kernel: [   10.983950] docker0: port 2(vethe6fc182) entered blocking state
Sep 15 16:34:33 pop-os kernel: [   10.983954] docker0: port 2(vethe6fc182) entered forwarding state
Sep 15 16:34:33 pop-os kernel: [   10.984035] IPv6: ADDRCONF(NETDEV_CHANGE): docker0: link becomes ready
Sep 15 16:34:33 pop-os kernel: [   10.984289] docker0: port 2(vethe6fc182) entered disabled state
Sep 15 16:34:33 pop-os kernel: [   11.030164] docker0: port 1(veth77eaea2) entered disabled state
Sep 15 16:34:33 pop-os kernel: [   11.031214] device veth77eaea2 left promiscuous mode
Sep 15 16:34:33 pop-os kernel: [   11.031216] docker0: port 1(veth77eaea2) entered disabled state
Sep 15 16:34:34 pop-os kernel: [   11.411275] eth0: renamed from vethca81f3f
Sep 15 16:34:34 pop-os kernel: [   11.447429] IPv6: ADDRCONF(NETDEV_CHANGE): vethe6fc182: link becomes ready
Sep 15 16:34:34 pop-os kernel: [   11.447515] docker0: port 2(vethe6fc182) entered blocking state
Sep 15 16:34:34 pop-os kernel: [   11.447518] docker0: port 2(vethe6fc182) entered forwarding state
Sep 15 16:34:41 pop-os kernel: [   18.541711] Bluetooth: RFCOMM TTY layer initialized
Sep 15 16:34:41 pop-os kernel: [   18.541717] Bluetooth: RFCOMM socket layer initialized
Sep 15 16:34:41 pop-os kernel: [   18.541721] Bluetooth: RFCOMM ver 1.11
Sep 15 16:34:41 pop-os kernel: [   18.759403] rfkill: input handler enabled
Sep 15 16:34:44 pop-os kernel: [   21.686392] rfkill: input handler disabled
Sep 15 16:34:59 pop-os kernel: [   37.018673] usb 1-12: new high-speed USB device number 7 using xhci_hcd
Sep 15 16:34:59 pop-os kernel: [   37.171903] usb 1-12: New USB device found, idVendor=0951, idProduct=1689, bcdDevice= 1.00
Sep 15 16:34:59 pop-os kernel: [   37.171906] usb 1-12: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Sep 15 16:34:59 pop-os kernel: [   37.171908] usb 1-12: Product: DataTraveler SE9
Sep 15 16:34:59 pop-os kernel: [   37.171910] usb 1-12: Manufacturer: Kingston
Sep 15 16:34:59 pop-os kernel: [   37.171911] usb 1-12: SerialNumber: F46D04613D6BBCB139200070
Sep 15 16:34:59 pop-os kernel: [   37.212210] usb-storage 1-12:1.0: USB Mass Storage device detected
Sep 15 16:34:59 pop-os kernel: [   37.212356] scsi host1: usb-storage 1-12:1.0
Sep 15 16:34:59 pop-os kernel: [   37.212522] usbcore: registered new interface driver usb-storage
Sep 15 16:34:59 pop-os kernel: [   37.215126] usbcore: registered new interface driver uas
Sep 15 16:35:00 pop-os kernel: [   38.323678] scsi 1:0:0:0: Direct-Access     Kingston DataTraveler SE9 PMAP PQ: 0 ANSI: 4
Sep 15 16:35:00 pop-os kernel: [   38.324194] sd 1:0:0:0: Attached scsi generic sg1 type 0
Sep 15 16:35:02 pop-os kernel: [   39.729568] sd 1:0:0:0: [sdb] 61408128 512-byte logical blocks: (31.4 GB/29.3 GiB)
Sep 15 16:35:02 pop-os kernel: [   39.729705] sd 1:0:0:0: [sdb] Write Protect is off
Sep 15 16:35:02 pop-os kernel: [   39.729706] sd 1:0:0:0: [sdb] Mode Sense: 23 00 00 00
Sep 15 16:35:02 pop-os kernel: [   39.729859] sd 1:0:0:0: [sdb] No Caching mode page found
Sep 15 16:35:02 pop-os kernel: [   39.729861] sd 1:0:0:0: [sdb] Assuming drive cache: write through
Sep 15 16:35:02 pop-os kernel: [   39.772094]  sdb:
Sep 15 16:35:02 pop-os kernel: [   39.773671] sd 1:0:0:0: [sdb] Attached SCSI removable disk
Sep 15 16:35:03 pop-os kernel: [   41.258905] ISO 9660 Extensions: RRIP_1991A
Sep 15 16:35:18 pop-os kernel: [   55.937285] rfkill: input handler enabled
```

---

### Post by QIII on 2020-09-29
Moved to Ubuntu/Debian BASED

---

