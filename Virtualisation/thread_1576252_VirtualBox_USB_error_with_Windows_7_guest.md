---
title: "VirtualBox USB error with Windows 7 guest"
date: 2010-09-17
forum: Virtualisation
---

### Post by todlangweilig on 2010-09-17
I'm running Ubuntu 10.04 with the PUEL version of VirtualBox 3.2.8. When I connect the USB device, VirtualBox pops up a message that says > Failed to attach the USB device Texas Instruments MSP-FET430UIF JTAG Tool [0101] to the virtual machine Windows 7.
Failed to create a proxy device for the USB device. (Error: VERR_READ_ERROR).

Things I have tried:
Added my user to group vboxusers
Created a USB filter in VirtualBox
Installed Guest Additions in Windows 7 guest
Try changing MODE="664" to MODE="666" in /etc/udev/rules.d/10-vboxdrv.rules, but it had no positive effect. (I thought it might work, so I decided to give it a try)

Windows recognizes my built-in usb webcam, so some usb devices seem to work. I have attached various log files and anything else I could think to try. I'm out of ideas to try. I tried searching google and the forums, but the methods which were suggested seem to use usbfs, which doesn't seem to used with Ubuntu 10.04.

---

### Post by lukeiamyourfather on 2010-09-17
I've had hit and miss luck with USB devices in a VirtualBox guest. Generally speaking if hardware support is needed and not just support for applications, then I dual boot a system instead of using virtual machines. If you decide to pursue it, this might help.

[https://help.ubuntu.com/community/VirtualBox/USB](https://help.ubuntu.com/community/VirtualBox/USB)

---

### Post by todlangweilig on 2010-09-17
If I was able to get Ubuntu to support the hardware, would VirtualBox be happy with the hardware as well?

Unfortunately, the Ubuntu Community Documentation page just has the "add user to vboxusers group" bit. And everything else is mostly out of date now.

I had a multi boot system, but then I reinstalled Ubuntu, and somehow Windows 7 got borked. But that's a problem for a different forum...

---

### Post by todlangweilig on 2010-09-17
After playing with it some more, I noticed that it creates a /dev/ttyUSB0 when the FET programmer is plugged in. When I start the virtual guest, however, the /dev/ttyUSB0 is killed. 

Before:
> Sep 17 14:14:21 aaron-laptop kernel: [12342.331382] usb 8-1: configuration #1 chosen from 1 choice
Sep 17 14:14:21 aaron-laptop kernel: [12342.337492] ti_usb_3410_5052 8-1:1.0: TI USB 3410 1 port adapter converter detected
Sep 17 14:14:21 aaron-laptop kernel: [12342.337499] usb 8-1: firmware: requesting ti_usb-v0451-pf430.fw
Sep 17 14:14:21 aaron-laptop kernel: [12342.343062] usb 8-1: firmware: requesting ti_3410.fw
Sep 17 14:14:22 aaron-laptop kernel: [12342.921030] usb 8-1: reset full speed USB device using uhci_hcd and address 4
Sep 17 14:14:22 aaron-laptop kernel: [12343.064232] usb 8-1: device firmware changed
Sep 17 14:14:22 aaron-laptop kernel: [12343.064263] ti_usb_3410_5052: probe of 8-1:1.0 failed with error -5
Sep 17 14:14:22 aaron-laptop kernel: [12343.064310] usb 8-1: USB disconnect, address 4
Sep 17 14:14:22 aaron-laptop kernel: [12343.177042] usb 8-1: new full speed USB device using uhci_hcd and address 5
Sep 17 14:14:22 aaron-laptop kernel: [12343.402523] usb 8-1: configuration #1 chosen from 2 choices
Sep 17 14:14:22 aaron-laptop kernel: [12343.406321] ti_usb_3410_5052 8-1:1.0: TI USB 3410 1 port adapter converter detected
Sep 17 14:14:22 aaron-laptop kernel: [12343.406342] ti_usb_3410_5052: probe of 8-1:1.0 failed with error -5
Sep 17 14:14:22 aaron-laptop kernel: [12343.410404] ti_usb_3410_5052 8-1:2.0: TI USB 3410 1 port adapter converter detected
Sep 17 14:14:22 aaron-laptop kernel: [12343.410525] usb 8-1: TI USB 3410 1 port adapter converter now attached to ttyUSB0

> aaron@aaron-laptop:/dev$ ls -al ttyUSB0 
crw-rw---- 1 root dialout 188, 0 2010-09-17 14:14 ttyUSB0

and this is what happens after I start the Windows 7 guest.

> Sep 17 14:16:08 aaron-laptop kernel: [12449.364899] ti_usb_3410_5052_1 ttyUSB0: TI USB 3410 1 port adapter converter now disconnected from ttyUSB0
Sep 17 14:16:08 aaron-laptop kernel: [12449.364929] ti_usb_3410_5052 8-1:2.0: device disconnected
Sep 17 14:16:09 aaron-laptop kernel: [12450.329772] ti_usb_3410_5052 8-1:1.0: TI USB 3410 1 port adapter converter detected
Sep 17 14:16:09 aaron-laptop kernel: [12450.329791] ti_usb_3410_5052: probe of 8-1:1.0 failed with error -5
Sep 17 14:16:09 aaron-laptop kernel: [12450.333918] ti_usb_3410_5052 8-1:2.0: TI USB 3410 1 port adapter converter detected
Sep 17 14:16:09 aaron-laptop kernel: [12450.334001] usb 8-1: TI USB 3410 1 port adapter converter now attached to ttyUSB0
Sep 17 14:16:09 aaron-laptop kernel: [12450.334106] ti_usb_3410_5052_1 ttyUSB0: TI USB 3410 1 port adapter converter now disconnected from ttyUSB0
Sep 17 14:16:09 aaron-laptop kernel: [12450.334119] ti_usb_3410_5052 8-1:2.0: device disconnected

Any ideas anyone?

---

### Post by wilee-nilee on 2010-09-19
Just a theory here, but if Vbox is recognizing some things and not others it sounds like a driver issue. Now which where and when and it what system I would guess.

---

