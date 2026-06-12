---
title: "PTP camera will not mount in 12.04"
date: 2012-04-20
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Malcy on 2012-04-20
My Fujifilm Finepix X100 camera connects through USB using PTP. It worked perfectly on various flavours of Ubuntu but since moving from 11.10 to 12.04 (clean install) the camera will not mount. This is not a change in hardware problem as that has not changed and the camera still connects happily in  older versions of Ubuntu, SUSE, Windows 7 and 8 on the same computer in VMs.

lsusb gives the following:

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 04e8:329f Samsung Electronics Co., Ltd 
Bus 001 Device 003: ID 0409:0058 NEC Corp. HighSpeed Hub
Bus 001 Device 005: ID 0424:2514 Standard Microsystems Corp. USB 2.0 Hub
Bus 003 Device 002: ID 055f:021c Mustek Systems, Inc. BearPaw 1200 CU Plus
Bus 001 Device 006: ID 058f:6377 Alcor Micro Corp. Multimedia Card Reader
Bus 001 Device 007: ID 0603:00f2 Novatek Microelectronics Corp. 
Bus 001 Device 008: ID 046d:c01d Logitech, Inc. MX510 Optical Mouse
Bus 001 Device 013: ID 04cb:022c Fuji Photo Film Co., Ltd 

The camera is recognised by 12.04, it's the bottom line. It just does nothing with it.

I'm not really sure where to go with this, any ideas?

---

### Post by cariboo on 2012-04-20
Does it show up in dmesg, when you plug the camera in?

---

### Post by Malcy on 2012-04-21
dmesg shows the following when the camera is connected, disconnected and connected again:

[  205.412146] usb 1-3.4: new high-speed USB device number 9 using ehci_hcd
[  287.118655] usb 1-3.4: USB disconnect, device number 9
[  308.324165] usb 1-3.4: new high-speed USB device number 10 using ehci_hcd

So it is at least detecting it.

---

