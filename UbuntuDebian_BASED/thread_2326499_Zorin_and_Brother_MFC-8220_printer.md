---
title: "Zorin and Brother MFC-8220 printer"
date: 2016-06-01
forum: Ubuntu/Debian BASED
---

### Post by gweedoh on 2016-06-01
I am running Zorin 9.1 core 64bit.
I'm trying to get my Brother MFC-8220 printer working.
When I connect it to a USB port it does not show up in Printers control panel.
I ran this command:
```
sudo tail -f /var/log/syslog
```
and then pugged my printer in and this was the output:
```
Jun  1 12:04:16 Zorin-01 kernel: [  341.710594] usb 1-3: new high-speed USB device number 6 using ehci-pci
Jun  1 12:04:16 Zorin-01 kernel: [  341.846950] usb 1-3: New USB device found, idVendor=04f9, idProduct=0150
Jun  1 12:04:16 Zorin-01 kernel: [  341.846959] usb 1-3: New USB device strings: Mfr=0, Product=0, SerialNumber=3
Jun  1 12:04:16 Zorin-01 kernel: [  341.846964] usb 1-3: SerialNumber: 000J6J341923
Jun  1 12:04:16 Zorin-01 kernel: [  341.848798] usblp 1-3:1.0: usblp0: USB Bidirectional printer dev 6 if 0 alt 0 proto 2 vid 0x04F9 pid 0x0150
Jun  1 12:04:16 Zorin-01 mtp-probe: checking bus 1, device 6: "/sys/devices/pci0000:00/0000:00:12.2/usb1/1-3"
Jun  1 12:04:17 Zorin-01 mtp-probe: bus: 1, device: 6 was not an MTP device
Jun  1 12:04:17 Zorin-01 udev-configure-printer: add /devices/pci0000:00/0000:00:12.2/usb1/1-3/1-3:1.0
Jun  1 12:04:17 Zorin-01 udev-configure-printer: device devpath is /devices/pci0000:00/0000:00:12.2/usb1/1-3/1-3:1.0
Jun  1 12:04:17 Zorin-01 udev-configure-printer: MFG:Brother MDL:MFC-8220 SERN:- serial:-
Jun  1 12:04:18 Zorin-01 kernel: [  343.918681] usblp0: removed
Jun  1 12:04:18 Zorin-01 hp[10497]: io/hpmud/pp.c 627: unable to read device-id ret=-1
Jun  1 12:04:18 Zorin-01 python: io/hpmud/pp.c 627: unable to read device-id ret=-1
Jun  1 12:04:20 Zorin-01 udev-configure-printer: no corresponding CUPS device found

```

Thanks in advance for your help.  Please explain things to me like I'm a complete noob.  I've used linux in the past but it's been a while and I'm not super familiar with where to find/do things in Ubuntu/Zorin.

Thanks again.

Edit: One more thing.  I tried to install the printer manually from the control panel and I have "serial" and "LPT" options for ports.  Nothing for USB.

---

### Post by howefield on 2016-06-01
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by Rob Sayer on 2016-06-02
I'd suggest looking at your kernel version (uname -r in the terminal).  Then look for a solution for the Ubuntu release that uses that kernel.

However, and you may not want to hear this, you may be better off in the long run just doing a clean reinstall of Ubuntu.  I've looked at the Zorin support forum.  It's useless.  While I actually run Mint nowadays ... largely because their Xfce LTS version has longer support ythan Ubuntu's ... Ubuntu is the one I recommend to beginners.  There is no other distro suitable for the novice that compares for support.

---

### Post by gweedoh on 2016-06-03
> **Rob Sayer said:**
> you may be better off in the long run just doing a clean reinstall of Ubuntu.

Downloading the .iso now.  The last time I used Ubuntu (2013) I could not get my WiFi card going so that's why I didn't bother with it this time around.  Admittedly when I started down the Zorin path I didn't know it was based on Ubuntu - if I had realized it I wouldn't have tried it either.  Since Zorin picked up my WiFi card I have to assume Ubuntu will also.

Thanks for the help!

---

