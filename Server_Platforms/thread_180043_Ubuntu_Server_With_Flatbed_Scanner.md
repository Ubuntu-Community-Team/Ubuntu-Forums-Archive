---
title: "Ubuntu Server With Flatbed Scanner"
date: 2006-05-21
forum: Server Platforms
---

### Post by stijn on 2006-05-21
Hi,

I'm trying to get my scanner (Acer 620u) running on Ubuntu Breezy (server).

When connecting scanner to my Breezy portable, scanning with XSane scanning program works flawless (including command line scanimage works like a charm), nothing has to be done but connecting the usb cable.

When connecting with my breezy server, and trying first to get the scanner running via command line, server complains about necessary firmware, which I installed (not necessary on portable), then when trying to scan, this the error message I get:

 scanimage: open of device snapscan:libusb:001:003 failed: Error during device I/O


Scanner is recognised trough 'sane-find-scanner' and 'scanimage --list-devices'

Anyone an idea what to do to fix this?

Thanks in advance!

---

