---
title: "Server or Desktop version?"
date: 2013-02-17
forum: Server Platforms
---

### Post by shiyoushi on 2013-02-17
Hello,

I am setting up an HP N40L ProLiant Microserver for home use and would like some advice on whether the desktop or server version would be better for my uses.

The server will have 6-9 3tb WD Red drives (depending on how many I can afford), plus 128GB SSD as the boot drive. I will need to buy a SAS card to be able to use the extra drives but have not picked one out yet, so if anyone has any recommendations for a low profile PCIe SAS card that will recognise 3TB drives that would be good too.

The drives will all be 1 ZFS pool, and used for storing the households multimedia.

Apart from that the server will be doing the following:
Minecraft server
SABnzb
Sickbeard
CouchPotato
XBMC (purely so I can build the library and share it with XBMC clients in the house via uPnP)

I haven't had much experience using linux and while most of the administration will be via SSH I'm sure there will be times when I will need to hook it up to a monitor and use a gui to sort things out as I am still learning.

With all this in mind, would Server with xfce installed just incase I need it be suitable, or should I install the full Desktop version?

---

### Post by Merrattic on 2013-02-17
I would probably install Server and webmin to administer but then add xfce/similar. 

IIRC XBMC won't run without x.

---

### Post by MrKaliman on 2013-02-17
If you want you can install the desktop or server version and user the Free No Machine NX to administer your server from you workstation/laptop.

[https://help.ubuntu.com/community/NomachineNX](https://help.ubuntu.com/community/NomachineNX)

Pretty fast (compression) and very easy to install.

Have fun!

---

### Post by Bucky Ball on 2013-02-17
Install server. Add xfce or lxde. Desktop install will drag in a bunch of stuff you definitely won't/don't need. For xfce DE the actual name is xfce4.

---

### Post by shiyoushi on 2013-02-17
Thanks for the input guys, looks like server it is! 
And thanks for pointing me to No Machine NX MrKaliman, it looks like a very useful tool.

---

### Post by sandyd on 2013-02-17
**Moved to Server Platforms**

---

### Post by hitjim on 2013-04-18
Hello!  I'm about to attempt a similar configuration using a G7 N54L.  Shiyoushi, any successes or pitfalls you can share?  Thanks!

---

