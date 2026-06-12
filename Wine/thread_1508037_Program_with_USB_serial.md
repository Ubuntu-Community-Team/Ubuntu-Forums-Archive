---
title: "Program with USB serial"
date: 2010-06-12
forum: Wine
---

### Post by blowdesign on 2010-06-12
Hello, I've a program to manage my electric installation.

In microsoft windows (and also in VM with XP), I choose a COM Port who is in fact my USB Serial Port and all work fine.

I would like to to the same under Ubuntu directly with Wine, but Wine doesn't detect my USB Serial port.

When I do lsusb : 

> Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c504 Logitech, Inc. Cordless Mouse+Keyboard Receiver
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0403:6001 Future Technology Devices International, Ltd FT232 USB-Serial (UART) IC
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ID 0bc2:2300 Seagate RSS LLC 
Bus 001 Device 005: ID 15a4:1336 Afatech Technologies, Inc. 
Bus 001 Device 003: ID 05e3:0606 Genesys Logic, Inc. USB 2.0 Hub / D-Link DUB-H4 USB 2.0 Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

I think my USB Device is > Bus 002 Device 002: ID 0403:6001 Future Technology Devices  International, Ltd FT232 USB-Serial (UART) IC

Thank in advance.

---

### Post by blowdesign on 2010-06-19
up

---

