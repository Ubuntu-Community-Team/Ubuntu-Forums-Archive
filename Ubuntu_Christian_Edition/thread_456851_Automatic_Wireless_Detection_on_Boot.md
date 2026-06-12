---
title: "Automatic Wireless Detection on Boot"
date: 2007-05-28
forum: Ubuntu Christian Edition
---

### Post by jopv on 2007-05-28
hi

Installed Ubuntu Fiesty fawn on my laptop (Thinkpad Z60T) a few weeks ago and it went fairly smooth.  My wireless network was not automatically detected but I managed to get it to work using 'Static IP Address'.  

The problem I have is that every time I shut down the laptop and boot back up I have to manually switch on the wireless connection i.e. I have to first uncheck and then check the check box in the Network Settings window.

Is there a way I can get the wireless connection to switch on automatically when I boot up?  Do I have to change something in the 'interfaces' file under /etc/network/ ?

Also, how do I get the wireless LED to work?  I also have an external wireless switch and would love to get that working.  Any help would be appreciated.

Thanks, JOHN

---

### Post by savantelite on 2007-09-11
there is a program called network manager for switching between wireless networks and wired networks, however your problem maybe your wireless card. If it is a broadcom good luck, I have had some success with a Restricted drivers program in gusty gibbon, but that only worked in the first alpha. After that it broke with the updates.

so reveiw
network manger

and 

restricted drivers

---

### Post by mamanmapillai on 2008-02-04
Hi,
I am using netgear wireless PCI adapter. I coppied xp driver to ubuntu
and installed ndiswrapper and point out the .INF location and now it is working. But when the access point is restarted Ubuntu fails to detect the access point there after I am not able to browse the net. In order to get connection again I have to restart the network. How can I get the connection without restarting the network file in init.d.

Any Ideas?

---

