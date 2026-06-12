---
title: "Bluetooth not detecting any devices | elementary freya | Thinkpad T420s"
date: 2015-12-23
forum: Ubuntu/Debian BASED
---

### Post by donkarziavelli on 2015-12-23
Hey !

I have a problem with my integrated bluetooth in my laptop (Thinkpad T420s). It seems as if bluetooth is installed correctly and there is no indication that it is hard- or softblocked.
Unfortunately my laptop won't find any devices. I tried with my phone and some bluetooth speakers I have. The bluetooth settings and blueman start searching for something to pair but end with nothing found.

I'm running on Kernel: 4.2.6-040206-generic

I have some outputs here, maybe you see something fishy.

> 
uname -a; lspci -nnk | grep -iA2 net; lsusb; dmesg | grep -i bluetooth; dmesg | grep -i firmware; lsmod | grep bluetooth
Linux Rumpelkiste 4.2.6-040206-generic #201511091832 SMP Mon Nov 9 23:34:22 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)
    Subsystem: Lenovo Device [17aa:21ce]
    Kernel driver in use: e1000e
--


03:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6205 [Taylor Peak] [8086:0085] (rev 34)
    Subsystem: Intel Corporation Centrino Advanced-N 6205 AGN [8086:1311]
    Kernel driver in use: iwlwifi


Bus 004 Device 003: ID 046d:c01e Logitech, Inc. MX518 Optical Mouse
Bus 004 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 004: ID 04f2:b221 Chicony Electronics Co., Ltd integrated camera
Bus 003 Device 003: ID 0a5c:217f Broadcom Corp. BCM2045B (BDC-2.1)
Bus 003 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


[    1.950171] usb 3-1.4: Product: Broadcom Bluetooth Device
[   17.064937] thinkpad_acpi: rfkill switch tpacpi_bluetooth_sw: radio is unblocked
[   17.737322] Bluetooth: Core ver 2.20
[   17.737341] Bluetooth: HCI device and connection manager initialized
[   17.737346] Bluetooth: HCI socket layer initialized
[   17.737349] Bluetooth: L2CAP socket layer initialized
[   17.737354] Bluetooth: SCO socket layer initialized
[   20.249658] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   20.249661] Bluetooth: BNEP filters: protocol multicast
[   20.249666] Bluetooth: BNEP socket layer initialized
[   20.266065] Bluetooth: RFCOMM TTY layer initialized
[   20.266072] Bluetooth: RFCOMM socket layer initialized
[   20.266076] Bluetooth: RFCOMM ver 1.11
[    0.111334] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.123397] acpi PNP0A08:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-3f] only partially covers this bridge
[    9.077147] psmouse serio2: trackpoint: IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   17.467909] iwlwifi 0000:03:00.0: loaded firmware version 18.168.6.1 op_mode iwldvm
bluetooth             516096  25 bnep,btbcm,btrtl,btusb,rfcomm,btintel




Thanks for any help, if you need more information I will gladly provide it!

---

### Post by howefield on 2015-12-23
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

