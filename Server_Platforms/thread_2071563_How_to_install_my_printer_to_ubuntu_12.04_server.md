---
title: "How to install my printer to ubuntu 12.04 server"
date: 2012-10-15
forum: Server Platforms
---

### Post by lazarojhr16 on 2012-10-15
hello, I configured the printer server and installed my printer the same way I installed it on my Ubuntu 12.04 desktop, i followed the instructions here
 [http://forums.linuxmint.com/viewtopic.php?f=51&t=105027&p=598497](http://forums.linuxmint.com/viewtopic.php?f=51&t=105027&p=598497)
I have a canon ip2600, it works on my desktop but not on the server. when i go to 192.XXX.X.X:631 i get the gui and when i navigate to printers, nothing is there. how can i get my printer to install on the server. 
also my ubuntu server has a static ip.
thanks for all the help.

---

### Post by dniMretsaM on 2012-10-15
Go to the Administration tab of the CUPS page and click the "Find New Printers" button. If it's connected, it should find it.

---

### Post by lazarojhr16 on 2012-10-15
> **dniMretsaM said:**
> Go to the Administration tab of the CUPS page and click the "Find New Printers" button. If it's connected, it should find it.

hey thanks to your comment i got it fixed. it was similar but instead of going to "find new printer" i had to actually "add printer" from the cups server, not from my actual server. thanks hopefully this helps someone else.

---

