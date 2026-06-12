---
title: "USB 3.0 doesn't work properly during booting with plugged usb devices"
date: 2017-12-28
forum: Ubuntu/Debian BASED
---

### Post by arturk80 on 2017-12-28
How can I manualy switch usb device to vbus2(5000Mb) from vbus1(480Mb) what it done during booting system (with plugged usb device)? Can I using usb_modeswitch to  do that or I must use udev rules or somthing else?

The setup:
We connected two devices (USRP B210 radio) using two usb 3.0 port to carrier board J120. This devices work correctly when we plug them when system(Ubuntu 16.04) is  working. But after booting system again (with plugged usb 3.0 device(or  two devices)), the problem which occures is below in logs:

[    2.980938] regulator_get() failed for (tegra-ehci.0,usb_vbus), -19
[    2.980941] usb_phy: failed regulator_get vdd_vbus_usb:-19, inst:0
[    3.230200] usb 1-3: new high-speed USB device number 2 using tegra-xhci
[    3.314854] usb 1-3: New USB device found, idVendor=2500, idProduct=0020
[    3.314859] usb 1-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    3.314863] usb 1-3: Product: WestBridge 
[    3.314866] usb 1-3: Manufacturer: Cypress
[    3.314869] usb 1-3: SerialNumber: 0000000004BE

[  144.271552] usb 1-3: reset high-speed USB device number 2 using tegra-xhci
[  145.349386] usb 1-3: Device not responding to set address.
[  146.628406] usb 1-3: Device not responding to set address.
[  146.830799] usb 1-3: device not accepting address 2, error -71
[  146.951060] usb 1-3: reset high-speed USB device number 2 using tegra-xhci
[  148.028833] usb 1-3: Device not responding to set address.
[  149.308257] usb 1-3: Device not responding to set address.
[  149.510736] usb 1-3: device not accepting address 2, error -71
[  149.631082] usb 1-3: reset high-speed USB device number 2 using tegra-xhci
[  150.708899] usb 1-3: Device not responding to set address.
[  151.988646] usb 1-3: Device not responding to set address.
[  152.190766] usb 1-3: device not accepting address 2, error -71
[  152.320514] usb 1-3: reset high-speed USB device number 2 using tegra-xhci
[  153.397717] usb 1-3: Device not responding to set address.

adding DRIVERS to rules doesn't switch to vbus2 :(
SUBSYSTEMS=="usb", ATTRS{idVendor}=="2500", ATTRS{idProduct}=="0020", MODE:="0666", DRIVERS="tegra-xhci"

We have got Auvidea carrier board J120 for jetson TX1 and use firmware  downloaded from Auvidea webpage (kernel and patches) v.2.2. We have  installed it to L4T 24.2.1(based on ubuntu 16.04) and flashed to jetson TX1 module.

---

### Post by howefield on 2017-12-28
Moved to the "*Ubuntu/Debian BASED*" forum.

---

