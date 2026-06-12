---
title: "Can I use my Web Server as a Print Server also?"
date: 2013-02-09
forum: Server Platforms
---

### Post by magpie03 on 2013-02-09
My little NAS/Print Server on my home network has died. Instead of buying another one, since my web server is on 24/7, can I use my web server as a print server also? My web server is just a small one with few hits, basicly for testing/learning. I'm currently using Ubuntu 11.04 on a headless computer with no GUI but have Webmin installed. This is on my home network and only printing from the internal home network is all I want. My home network has two Ubuntu machines, three Windows XP machines, and one dual boot Ubuntu/Windows 7. Please note I only installed the basic LAMP package and no Mail or Printer packages.

Thanks all.

magpie

---

### Post by Vegan on 2013-02-09
SAMBA can help create a printer server that even Windows clients can take advantage of.

I found it to be very useful.

CUPS is the usual lower layer for the printer in Linux.

---

### Post by tgalati4 on 2013-02-09
```
sudo apt-get install cups
```

Log in using [http://yourserveripaddress:631](http://yourserveripaddress:631).

---

### Post by magpie03 on 2013-02-10
OK. I'll try it. Thank you.

---

