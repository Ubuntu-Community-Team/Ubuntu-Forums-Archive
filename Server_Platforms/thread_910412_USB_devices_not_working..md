---
title: "USB devices not working."
date: 2008-09-04
forum: Server Platforms
---

### Post by tillywern on 2008-09-04
I have 8.04 server installed on an HP Compaq dc7600.   Everything is going well except that none of my USB devices are working.

Running 'lsusb -v' yields nothing.   Looking in dmesg, I don't see references to the a usb host adapter or any usb device that is plugged into the bus.

It is all very odd.

A 'modprobe -c|grep usb' shows that modules are loaded or available.  Looking in /proc I don't see any output for usb devices.

I looks as though the machine doesn't have usb hardware on it.

Any ideas?

---

### Post by tillywern on 2008-09-04
Ok So I am seeing the following.

# modprobe -c |grep usbhi
alias usb:v*p*d*dc*dsc*dp*ic03isc*ip* usbhid
alias symbol:hiddev_hid_event usbhid

# modprobe -c |grep uhci
alias pci:v*d*sv*sd*bc0Csc03i00* uhci_hcd

# dmesg |grep usb
[   22.004748] usbcore: registered new interface driver usbfs
[   22.004783] usbcore: registered new interface driver hub
[   22.004829] usbcore: registered new device driver usb

Still I'm not seeing any output in dmesg when a device is plugged in.

---

### Post by tillywern on 2008-09-04
Ok all.   I solved it.

Looking at  "lspci -v" I verified that the usb controllers were missing from the list.   This indicated that the issue was lower than the OS.

Into the BIOS and the obscure settings.  I located a setting that was "hiding" my usb ports.   Probably because people can't be trusted to manage usb devices properly.

Reset it and all is well.

---

