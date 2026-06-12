---
title: "lpadmin: File device URIs have been disabled!"
date: 2009-04-11
forum: Server Platforms
---

### Post by and12345 on 2009-04-11
guys.. i'm trying to make my ubuntu 8.04 LTS box as print server for my canon IP1980.
i already trying to add it from CUPS web interface port 631, but when i try to select device, it just don't show USB.
the strange thing is when i checked lsusb

> root@GatewayServer:/home/myhome/ip1980# lsusb
Bus 001 Device 003: ID 04a9:10cd Canon, Inc.
Bus 001 Device 002: ID 0e0f:0002
Bus 001 Device 001: ID 0000:0000

it shows that my printer already connected, but there's still no usb under CUPS device

here's the result when i trying to install it from command line


> root@GatewayServer:/home/myhome/ip1980# /usr/sbin/lpadmin -p Canon_IP1980 -E -v /dev/bus/usb/001 -m canon1980.ppd
lpadmin: File device URIs have been disabled! To enable, see the FileDevice directive in "/etc/cups/cupsd.conf".


is the device URI that i'm using already correct? and how to know device URI on ubuntu?

---

### Post by mang0 on 2012-02-23
Bump. I'm having the same problem, with my IP4200 on 11.10...

---

### Post by bpb_21 on 2012-03-11
Same issue in Ubuntu Server 11.10 with an HP Officejet 5610.  I take comfort in the fact that if my system is so secure that even I can't get into it - then surely no one else on the web is!

---

