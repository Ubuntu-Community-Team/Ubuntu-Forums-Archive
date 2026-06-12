---
title: "Configure USB Ethernet Adapter (Headless Server)"
date: 2013-08-29
forum: Server Platforms
---

### Post by Jack Waugh on 2013-08-29
I have a USB Ethernet adapter (adaptor is also a correct spelling).  When I connect it to my Xubuntu headful desktopful system while I am logged in to the desktop, this adapter Just Works (at least shows up in 'ifconfig', with an assigned IPv4 number even).  So that tells me that whatever driver support is required for this pretty little dongle, exists.

How do I configure a headless Ubuntu server installation to recognize the adapter and make it show up with 'ifconfig'?  'lsusb' does show it.

Thanks in advance.

---

### Post by lukeiamyourfather on 2013-08-29
There are rules about how to handle hardware and those rules differ between servers and the desktop install because most people wouldn't want their server network configuration changing from a new device being plugged in. I think the rules are stored in /etc/udev and you could potentially copy some of the rules from a desktop system, or maybe install them from the Ubuntu repositories but I'm not sure where to start looking on that one.

---

