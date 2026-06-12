---
title: "webcam on PanP6"
date: 2013-01-16
forum: System76 Support
---

### Post by brusegadi on 2013-01-16
Hello,

I have a PanP6 purchased in Dec 2009.  Everything has been great.  I installed ubuntu 12.04 and cant seem to get the webcam to show up.  I tried the Fn Keys.  I also tried a few commands and their output suggests that the device is not even being detected (I dont recall the exact commands tried.)  My question is, if it is a matter of drivers, what do you recommend?

Also, I have two other unrelated questions, do you prefer if I open a thread for each questions (better indexing) or just ask everything in one place?  Thanks!

---

### Post by brusegadi on 2013-01-16
lsusb says:

```

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 147e:2016 Upek Biometric Touchchip/Touchstrip Fingerprint Sensor

```
while lspci says:

```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode] (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: NVIDIA Corporation G98M [GeForce G 105M] (rev a1)
02:00.0 Network controller: Intel Corporation Ultimate N WiFi Link 5300
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
07:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
07:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller
07:00.3 System peripheral: JMicron Technology Corp. MS Host Controller

```


Thanks!

---

### Post by Carborundum on 2013-01-18
What software are you trying to get the webcam to work with? Does the file /dev/video0 exist on your system?

---

### Post by dannyboy79 on 2013-01-18
i like guvcviewer for a webcam recording app

---

### Post by brusegadi on 2013-01-18
> **Carborundum said:**
> What software are you trying to get the webcam to work with? Does the file /dev/video0 exist on your system?

I have been trying with **cheese**.  I also tried the tests in 

```
 gstreamer-properties 
```

and that did not detect it either.  Most tutorials I saw said to try v4l1 and v4l2 but I only had v4l2 as a choice.

**The file /dev/video0 does not exist.**  Thanks!

---

### Post by dannyboy79 on 2013-01-18
sounds like a hardware issue, have you tried contacting system76 directly?

---

### Post by brusegadi on 2013-01-18
> **dannyboy79 said:**
> sounds like a hardware issue, have you tried contacting system76 directly?

I wanted to make sure it was hardware before I contacted them, since, if its a hardware issue, fixing it will probably involve shipping the machine, and I cant do that. right now.  Oh well...  I'll mark the thread as solved.  Thanks!

---

### Post by isantop on 2013-01-21
> **brusegadi said:**
> I wanted to make sure it was hardware before I contacted them, since, if its a hardware issue, fixing it will probably involve shipping the machine, and I cant do that. right now.  Oh well...  I'll mark the thread as solved.  Thanks!

Is your webcam turned on? Try closing all applications that use the camera (including web browsers), then hit Fn+F10 on your keyboard.

---

### Post by brusegadi on 2013-01-22
> **isantop said:**
> Is your webcam turned on? Try closing all applications that use the camera (including web browsers), then hit Fn+F10 on your keyboard.


This was one of the first things I tried since it has always been the cause of my webcam issues!  However, it did not work this time.  I'll try booting from a live cd and seeing if its detected that way.  I have not emailed you because if its really a hardware issue I will have to ship it but I cant since school is in session.  Thanks!

---

