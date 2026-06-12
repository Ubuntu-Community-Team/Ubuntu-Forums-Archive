---
title: "CUPS doesn't find USB-Printer"
date: 2008-11-03
forum: Server Platforms
---

### Post by hanspech on 2008-11-03
Hi there,

first of all, please excuse my bad language.
In my private LAN I run a small server (Geode) to host network services.
AOT the server hosts CUPS to print on a Samsung ML-1410 laserprinter connected on USB. CUPS publish this printer by IPP to other network clients. The administration is done via embedded  WebFrontEnd by a network client.
Befor upgrade from Dapper Drake (TLS) to Hardy Heron (TLS) this system works perfectly. After the upgrade CUPS can't find the connected printer anymore. I try some hard-wired configuration values like /dev/usb/lp0 or /dev/usblp0 but nothing perform well.
The system by itself knows the printer ("lsusb" returns logic values).

Thank you in advance for your time.

Regards,
hanspech

---

