---
title: "Vista LAN connection screwed after uninstalling Comodo firewall"
date: 2007-12-28
forum: Windows
---

### Post by 67GTA on 2007-12-28
I installed Comodo firewall since it was the only 3rd party firewall available when I first got my new PC. I got tired of it not remembering rules, and decided to uninstall it. Upon rebooting, my internet connection did not work. Vista said no connection was detected. I checked in the device manager for my network adapter. Comodo had created three entries in the network adapters section. I didn't tell it to.

NVIDIA nforce Networking Controller(default)
[COLOR="Red"]NVIDIA nforce Networking - Comodo Firewall Miniport[/COLOR]
[COLOR="Red"]WAN Miniport (IP) - Comodo Firewall Miniport[/COLOR]
[COLOR="Red"]WAN Miniport (IPV6) - Comodo Firewall Miniport[/COLOR]

The default device says it is still working. The other three entries won't let me remove them. I deleted every file and registry entry that had to do with Comodo with no luck. I reinstalled the nforce drivers from Nvidia, and they didn't change. I reinstalled Comodo, and then uninstalled again with no luck. I tried to let Vista diagnose the problem, and it said that the drivers/hardware were having problems but offered no solution. My ethernet is integrated  , and can't be removed. How do I get rid of this crap and get my connection back?

---

### Post by LinuxIsInnovation on 2007-12-29
Check for the TCP/IP settings in the connection preferences. Set the network security level to Medium. If needed, perform a system restore.

---

### Post by 67GTA on 2007-12-29
Nothing works. That piece of !@#$ has got a strangle hold on my PC. There is no way I can find to get rid of these device manager entries. Every network setting is normal. What gets my goat is that the original device says it is working properly. Something Comodo put on my system has locked it up. I have system restore turned off, so no dice there. I guess I will wait until Hardy goes final and reinstall both. I don't use Windows much anymore except for online poker, and  online banking.

---

### Post by LinuxIsInnovation on 2007-12-30
Then why dont you format and go for a clean installation of Windows.. You may install Hardy when the final version is out..

---

### Post by 67GTA on 2007-12-30
Well, I'm dual booting with Kubuntu 7.10. I have it set up the way I want it. That takes a couple of days(I'm a tweaker). That's the only reason I wanted to wait. I won't miss Vista that much. I saw on one of my RSS feeds that the latest version of ZoneAlarm was Vista compatible. That is my favorite. I'll use it next time.

---

