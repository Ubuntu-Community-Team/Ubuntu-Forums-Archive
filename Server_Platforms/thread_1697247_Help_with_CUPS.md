---
title: "Help with CUPS"
date: 2011-02-28
forum: Server Platforms
---

### Post by wolfgang89 on 2011-02-28
I seem to be running into a wall trying to install a DeskJet 9650 on my 10.04 server. I have webmin and the hplip packages installed. When I run dmesg | grep usb I am given alot of code but the only line mentioning a printer is 
```
[ 8477.127905] usblp0: USB Bidirectional printer dev 2 if 0 alt 0 proto 2 vid 0x03F0 pid 0x0B12
```
I've tried setting it to use USB Printer1,2,3, and 4 but none worked when trying to print a test page. I tried the LaserJet 9500 driver included with the hplip but I always get a command failed when trying to print a test page. Any ideas?

---

