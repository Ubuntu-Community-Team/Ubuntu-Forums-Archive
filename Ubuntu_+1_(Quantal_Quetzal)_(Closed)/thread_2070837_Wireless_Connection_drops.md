---
title: "Wireless Connection drops"
date: 2012-10-13
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by notoriousdbp on 2012-10-13
Hi,
I'm trying out 12.10 - installed yesterday, all updates applied and the wireless connection keeps dropping randomly.  It appears to still be connected in Network Manager but I get no response from web pages and can't even log in to my router home page.  Clicking on the network manager and selecting my wireless network gets me back up and running.

I have a Broadcom BCM4313 in an HP G62 laptop using the brcmsmac driver.

I had a look on the forum but this didn't come up in any searches so I apologise if this has already been discussed.  Is anyone else having issues or does anyone else know of a fix on it's way?

---

### Post by victor9098 on 2012-10-13
I have been noticing this over the last week too. WiFi just dies on me, I try disconnecting and reconnecting via network manager but does not help. Always have to do a restart.

I know its not the router as I have other devices connected and their connection is stable.

---

### Post by kbrodenhau on 2012-10-14
Go to  [http://ubuntuguide.org/wiki/Ubuntu:Precise#Wicd_Network_Manager](http://ubuntuguide.org/wiki/Ubuntu:Precise#Wicd_Network_Manager)

Which is "38.2 Wicd Network Manager" in the guide

But the instructions have you remove the network manager, reboot, and then get/install wicd.... I would do the "sudo apt-get install wicd" before removing the network manager and rebooting...

Also, I didn't want to remove network-manager because that would have removed gnome and gnome-core.

You'll need to start Main Menu -> Internet -> Wicd Network Manager to create your connection. See also [https://help.ubuntu.com/community/WICD](https://help.ubuntu.com/community/WICD)...

---

At first, I thought too that it was my provider causing the dropped connections... Wicd feels more stable.

---

