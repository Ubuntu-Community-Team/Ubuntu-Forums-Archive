---
title: "Pagolin Performance and Gentoo"
date: 2009-11-26
forum: System76 Support
---

### Post by malachias on 2009-11-26
Hi

I just received my Pagolin Performance and have installed Gentoo on it. Mostly went off without a hitch, but I can't seem to figure out what the webcam is - lspci doesn't list anything obviously webcammy, so I'm at a loss which drivers to install...

Does anyone know the make and model of the webcams in the Pagolin Performance?

Thanks!
-Mala

lspci:
```

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation ICH9M/M-E 2 port SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.5 IDE interface: Intel Corporation ICH9M/M-E 2 port SATA IDE Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation Device 06ec (rev a1)
02:00.0 Network controller: Intel Corporation Device 4235
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
07:00.0 System peripheral: JMicron Technologies, Inc. Device 2382
07:00.2 SD Host controller: JMicron Technologies, Inc. Device 2381
07:00.3 System peripheral: JMicron Technologies, Inc. Device 2383

```

lsusb:
```

Bus 002 Device 002: ID 5986:0300 Acer, Inc 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 147e:2016 Upek Biometric Touchchip/Touchstrip Fingerprint Sensor
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

---

### Post by HotShotDJ on 2009-11-26
On my PanP5, the built-in webcam is listed as Bisoncam NB Pro, using the uvcvideo driver.  The driver is part of the kernel, so you shouldn't need to install any separate driver.  Just make sure that when you compiled your kernel that the uvcvideo driver is compiled as a module.

Have you tried testing your webcam?  The easiest way is to install cheese through portage and see if the webcam is already detected. You can also check for the drivers by running lsmod in a terminal and see if uvcvideo is loaded.  If not, try running sudo modprobe uvcvideo.  If that doesn't work, you'll need to recompile your kernel with uvcvideo compiled as a module.

I hope this helps... I'm not up-to-date with how Gentoo does things.  Although I used it for many years, I moved to Ubuntu about 3 years ago, so Gentoo has become a fading memory to me. :)

---

### Post by malachias on 2009-11-26
Hi

Thanks for your help! It is indeed a Bisoncam NB pro, as shown in /proc/bus/usb/devices. And I hadn't configured my kernel to do anything with uvcvideo... whoopsie ;)

Thanks again!

---

### Post by thomasaaron on 2009-11-27
malachias, 

Did you try pressing Fn-F10 to turn on the webcam?

---

