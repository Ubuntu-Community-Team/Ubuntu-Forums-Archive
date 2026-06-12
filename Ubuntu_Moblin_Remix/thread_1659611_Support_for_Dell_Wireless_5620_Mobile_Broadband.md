---
title: "Support for Dell Wireless 5620 Mobile Broadband?"
date: 2011-01-04
forum: Ubuntu Moblin Remix
---

### Post by velcroy on 2011-01-04
Hey guys, been lurking around the forums for a while.

I just got a Dell Inspiron Mini 1012 Netbook with the Dell Wireless 5620 Mobile Wireless Card.

On Dells website, they have the Ubuntu Moblin download.  But i'm a little worried as to whether or not i will be able to use my Mobile Card.

Does anyone have any experience with the 5620? Or know of a [how-to] i could start studying?

Any help would be greatly appreciated! :)

Thanks,
Vel

---

### Post by peterfernandes238 on 2011-01-05
I just got a Dell Inspiron Mini 1012 Netbook with the Dell Wireless 5620 Mobile Wireless Card.
-----------
Peter

---

### Post by velcroy on 2011-01-05
Yeah i've looked for quite a while can't seem to find a driver for it :(

---

### Post by velcroy on 2011-01-05
Incase any of you need this; here is my LSUSB and LSPCI list


ubuntu@ubuntu:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 001 Device 005: ID 8086:0188 Intel Corp. WiMAX Connection 2400m
Bus 001 Device 004: ID 413c:8185 Dell Computer Corp. Gobi 2000 Wireless Modem (QDL mode)
Bus 001 Device 003: ID 0c45:641d Microdia 
Bus 001 Device 002: ID 13fe:3100 Kingston Technology Company Inc. 2 GB USB stick
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
07:00.0 Network controller: Intel Corporation Centrino Advanced-N + WiMAX 6250 (rev 35)
ubuntu@ubuntu:~$

---

### Post by slw0000 on 2011-02-10
Penitence is something that enervates our spirit, causing a greater loss than loss itself and making a bigger mistake than mistake itself, so never regret.

---

