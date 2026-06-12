---
title: "Bluetooth hangs after some time on Intel 7260 on Wily"
date: 2015-08-04
forum: Ubuntu Development Version
---

### Post by donbowman on 2015-08-04
OK, i broke the cardinal rule, and upgraded 2 things @ once.
I have a Samsung Series 9 laptop (np900x3c), and changed the NIC (mini-pcie Intel 6235 WiFi+Bluetooth) to an Intel 7260 (also WiFi + Bluetooth).
I also upgraded to 15.10 from 15.04. All seemed good, so i packed up and left (so i can't try the test of reverting the nic card).

Now I'm finding that, after some time of operation (5 minutes to maybe 60 minutes), the Bluetooth will hang (e.g. the mouse will stop responding). When this happens, I get an 'hci0 command 0x#### tx timeout' in dmesg. I can't seem to rescue it, if I try to reset the USB (bus 3, slot 3), the machine will hang. [I used the usbreset from this [thread]("http://askubuntu.com/questions/645/how-do-you-reset-a-usb-device-from-the-command-line")].

The microcode selected for iwlwifi is iwlwifi-7260-12.ucode and ibt-hw-37.7.10-fw-1.80.1.2d.d.bseq from the 4.1.0-3-generic kernel.

Does anyone have any suggestions? I see some things online about xhci vs ehci. But I don't think this applies to me since a) my bios has no option to disable, and b) i think this slot is using ehci anyway.

The relevant dmesg lines are:
```
[    9.062516] Bluetooth: Core ver 2.20
[    9.062535] Bluetooth: HCI device and connection manager initialized
[    9.062539] Bluetooth: HCI socket layer initialized
[    9.062542] Bluetooth: L2CAP socket layer initialized
[    9.062549] Bluetooth: SCO socket layer initialized
[    9.083653] Bluetooth: hci0: read Intel version: 3707100180012d0d00
[    9.088589] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.7.10-fw-1.80.1.2d.d.bseq
[    9.257740] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[    9.482514] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    9.482519] Bluetooth: BNEP filters: protocol multicast
[    9.482524] Bluetooth: BNEP socket layer initialized
[    9.493302] Bluetooth: RFCOMM TTY layer initialized
[    9.493311] Bluetooth: RFCOMM socket layer initialized
[    9.493317] Bluetooth: RFCOMM ver 1.11
[   36.983137] Bluetooth: HIDP (Human Interface Emulation) ver 1.2
[   36.983144] Bluetooth: HIDP socket layer initialized
[   36.987100] input: Ultrathin Touch Mouse as /devices/pci0000:00/0000:00:1d.0/usb3/3-1/3-1.5/3-1.5:1.0/bluetooth/hci0/hci0:256/0005:046D:B00D.0001/input/input11
[   36.987315] hid-generic 0005:046D:B00D.0001: input,hidraw0: BLUETOOTH HID v7.00 Keyboard [Ultrathin Touch Mouse] on d8:fc:93:e4:84:13

```

---

### Post by PaulW2U on 2015-08-04
*Thread moved to **Ubuntu Development Version*** as you're now using 15.10.

---

