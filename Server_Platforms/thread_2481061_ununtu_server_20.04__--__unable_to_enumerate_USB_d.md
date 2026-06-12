---
title: "ununtu server 20.04  --  unable to enumerate USB device  -- trendnet four port KV"
date: 2022-11-17
forum: Server Platforms
---

### Post by tross9 on 2022-11-17
I just completed rebuilding my ubuntu server   ( samba share , webserver and mysql server) after the main boot drive failed.

i pulled the server from the rack and attached a keyboard and monitor directly to it.
 I started with 16.04  to get the Raid drive mounted then  upgraded to 18.04  finished the rest of the the install ( add users, install mysql, and setup samba shares)
    then  I upgraded to Ubuntu 20.04.5 LTS (GNU/Linux 5.4.0-132-generic x86_64)  then put the server back in the rack and attached it to the KVM,
now it does not see the keyboard in the KVM.   it seem that other have the same problem with KVMs and ubuntu 20.04.

is there a ticket for this issue? or is there another option or fix?

lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


~$ dmesg | grep usb
[    0.312800] usbcore: registered new interface driver usbfs
[    0.312800] usbcore: registered new interface driver hub
[    0.312800] usbcore: registered new device driver usb
[    1.180378] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002, bcdDevice= 5.04
[    1.180751] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.181077] usb usb1: Product: EHCI Host Controller
[    1.181297] usb usb1: Manufacturer: Linux 5.4.0-132-generic ehci_hcd
[    1.181584] usb usb1: SerialNumber: 0000:00:1d.7
[    1.267521] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001, bcdDevice= 5.04
[    1.279644] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.291757] usb usb2: Product: UHCI Host Controller
[    1.303794] usb usb2: Manufacturer: Linux 5.4.0-132-generic uhci_hcd
[    1.315962] usb usb2: SerialNumber: 0000:00:1d.0
[    1.478268] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001, bcdDevice= 5.04
[    1.503885] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.529403] usb usb3: Product: UHCI Host Controller
[    1.554596] usb usb3: Manufacturer: Linux 5.4.0-132-generic uhci_hcd
[    1.567187] usb usb3: SerialNumber: 0000:00:1d.1
[    1.736921] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001, bcdDevice= 5.04
[    1.764213] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.778002] usb usb4: Product: UHCI Host Controller
[    1.805923] usb usb4: Manufacturer: Linux 5.4.0-132-generic uhci_hcd
[    1.805924] usb usb4: SerialNumber: 0000:00:1d.2
[    1.992231] usb 3-1: new full-speed USB device number 2 using uhci_hcd
[    2.036500] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001, bcdDevice= 5.04
[    2.051435] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.066345] usb usb5: Product: UHCI Host Controller
[    2.081198] usb usb5: Manufacturer: Linux 5.4.0-132-generic uhci_hcd
[    2.096128] usb usb5: SerialNumber: 0000:00:1d.3
[    2.176075] usb 3-1: device descriptor read/64, error -71
[    2.522196] usb 3-1: device descriptor read/64, error -71
[    2.780020] usb 3-1: new full-speed USB device number 3 using uhci_hcd
[    3.076029] usb 3-1: device descriptor read/64, error -71
[    3.340037] usb 3-1: device descriptor read/64, error -71
[    3.479575] usb usb3-port1: attempt power cycle
[    3.512069] usb usb3-port1: failed to disable port power
[    3.686354] usb 3-1: new full-speed USB device number 4 using uhci_hcd
[    4.152027] usb 3-1: device not accepting address 4, error -71
[    4.280027] usb 3-1: new full-speed USB device number 5 using uhci_hcd
[    4.696028] usb 3-1: device not accepting address 5, error -71
[    4.696108] usb usb3-port1: unable to enumerate USB device

TIA
Tim

---

