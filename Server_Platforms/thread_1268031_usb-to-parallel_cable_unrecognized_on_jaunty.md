---
title: "usb-to-parallel cable unrecognized on jaunty"
date: 2009-09-16
forum: Server Platforms
---

### Post by reikod on 2009-09-16
Hi, I'm having a bit of a problem here. I bought a USB-PARALLEL cable to set up a printer HP 1100. I've installed in HP proliant ML115 the UBUNTU SERVER 9.04 when I plug in my cable dmesg comes up wtth:

[  107.142522] usb 4-2: new full speed USB device using uhci_hcd and address 2
[  107.322521] usb 4-2: device descriptor read/64, error -71
[  107.620026] usb 4-2: device descriptor read/64, error -71
[  107.850023] usb 4-2: new full speed USB device using uhci_hcd and address 3
[  108.390012] usb 4-2: device not accepting address 3, error -71
[  108.510017] usb 4-2: new full speed USB device using uhci_hcd and address 4
[  108.546083] usb 4-2: device descriptor read/all, error -71
[  108.660022] usb 4-2: new full speed USB device using uhci_hcd and address 5
[  109.080013] usb 4-2: device not accepting address 5, error -71
[  109.080030] hub 4-0:1.0: unable to enumerate USB device on port 2

on every USB port. Anyways I checked my lsmod and found out that usblp was not loaded so I changed my /etc/modules, rebooted and still the same message. I plugged the cable in another server I have running 8.04 and works perfectly. Sets up the device as /dev/usb/lp0 and I can print fine. I guess this is a jaunty problem, but I'm really frustrated because I've been at this for almost 3 days and can't get it to work. 

PLEASE HELP!

---

### Post by reikod on 2009-09-17
Hi, me again. Just wanted to let you know that I have usbcore running on my 8.04 system but not on my 9.04 and that's the only usb module difference in both systems. I tried "sudo apt-get install usbcore" and it says it's already been installed, but when I try "sudo modprobe usbcore" it says there is none. Could this be the problem?, and if so, should I remove usbcore package with apt-get and then re-install it or should I compile usbcore? Although I'm not exactly sure how to compile usbcore modules.
 
Any help is highly appreciated!

---

