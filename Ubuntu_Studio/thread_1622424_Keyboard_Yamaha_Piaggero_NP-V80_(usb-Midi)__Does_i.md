---
title: "Keyboard Yamaha Piaggero NP-V80 (usb-Midi) : Does ist work?"
date: 2010-11-15
forum: Ubuntu Studio
---

### Post by kefluxde on 2010-11-15
Hi all,

I plan to buy this keyboard which has an usb-port for midi and file transfer.
Yamaha provides drivers for Win and Mac, but not for Linux (I'm using Ubuntu 10.10 x64).

- Yamaha support did not help, they just said that Linux is not supported. :(
- I asked for vendor and device IDs, but received no further response. :mad:
- I also took a look at /usr/src/linux-source-2.6.33/sound/usb/usbquirks.h. There are some Yamaha keyboards listed, but not the NP-V80 (at least not by its name, but there are some devices without name).
- I extracted the inf-files from the windows driver msi-File. VID is 0499 which is listed in usbquirks.h. But as the driver-package contains 102 inf files with different PIDs, I could not figure out which one is used by the NP-V80. Hm....


Regards,
kefluxde

---

### Post by Aphax on 2011-02-08
I have this keyboard on loan from someone who recently bought it, and though I haven't actually tried to get it to work under Linux I guess I could just paste the device IDs here (if only so people can find it through google, or something):

[24733.342788] usb 7-2: new full speed USB device using uhci_hcd and address 2
[24733.488813] usb 7-2: New USB device found, idVendor=0499, idProduct=1037
[24733.488819] usb 7-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[24733.488823] usb 7-2: Product: DigitalKBD
[24733.488826] usb 7-2: Manufacturer: YAMAHA Corporation

from lsusb:

Bus 007 Device 002: ID 0499:1037 Yamaha Corp. PSR-E403

---

