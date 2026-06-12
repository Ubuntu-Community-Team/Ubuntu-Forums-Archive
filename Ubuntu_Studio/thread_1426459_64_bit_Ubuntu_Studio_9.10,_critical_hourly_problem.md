---
title: "64 bit Ubuntu Studio 9.10, critical hourly problems"
date: 2010-03-10
forum: Ubuntu Studio
---

### Post by sunherd on 2010-03-10
I have a clean 64 bit Ubuntu Studio 9.10 install and I'm experiencing very big problems with the normal 2.6.31-9-rt kernel.

When I use Ubuntu's vanilla 2.6.31-20-generic kernel, the problems disappear, so I suppose this must be an Ubuntu Studio specific problem.

The problem is this: When I boot the realtime kernel, something from the following problems appear in 3-30 minutes:
- mouse gets real slow and jumpy. almost impossible to use
- network stops. ifconfig thinks everything's okay, but I can't ping out. "/etc/init.d/networking restart" helps, but the same problem always comes again in less than 10 minutes of use.
- everything in X seems to stop. mouse cursor moves okay but nothing else. I even can't login via tty1. I get the login prompt, but after I press enter after giving my username, I don't get even the password prompt.

I really have no idea where to start looking for a fix, but lspci might perhaps give a starting point for anyone that has time to help?

```
00:00.0 Host bridge: VIA Technologies, Inc. PT880 Ultra/PT894 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. PT894 I/O APIC Interrupt Controller
00:00.7 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. PT890 PCI to PCI Bridge Controller
00:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:0f.0 IDE interface: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 Host bridge: VIA Technologies, Inc. VT8237A Host Bridge
02:00.0 VGA compatible controller: nVidia Corporation G84 [GeForce 8600 GT] (rev a1)
80:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)

```EDIT: Oh, and I'm using the proprietary driver for NVIDIA, but the problems existed with the default driver too.

---

### Post by JC Cheloven on 2010-03-10
These symptoms somehow remind me an issue I had some time ago. An app was progressively eating all the ram (because of a bug), and the system became terribly slow after a while.

I don't have a fix for you really, but if you open your system monitor ans see what's happening with your ram, perhaps you'll find an starting point.

Have luck ;-)

---

### Post by markbuntu on 2010-03-12
Definitely sounds like a memory leak. Run top from the command line and it will telll you what is eating all the cpu and/or ram.

---

