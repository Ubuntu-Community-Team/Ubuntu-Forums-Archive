---
title: "In ESXi can't access guest OS (Ubuntu 8.10) from outside"
date: 2009-03-24
forum: Virtualisation
---

### Post by Bailywolf on 2009-03-24
Here's the specs on the box:
 
Supermicro  
Xenon 2.8Ghz
1GB RAM
2x 80GB SATA drives  
 
ESXi version - 3i 3.5.0 build-123629
 
Current Config
4 VM's configured for Ubuntu Linux
1 currently installed with Ubuntu 8.10 Server (intended to be a LAMP web server).
 
Issue:
I can access ESXi just fine via the management client, start, stop, and config all my VM's.  That seems to be working fine.
 
I can term into the Ubuntu install and work with it, update it, and install applications via CL or the package manager.  
 
I can access the web via Firefox from within the Ubuntu guest.  
 
It's a bog-standard Ubuntu LAMP with a few of my favorite helper apps (Webmin, for example).  Nothing weird, and nothing I haven't installed identically for a standalone box.  
 
Problem is, if I assign the guest a static IP, I lose all connectivity to and from it.  Without a static IP, it gets one from *somewhere* (from esxi?) and so I can access the outside world, but can't access the Ubuntu guest from outside.  
 
With a static IP (all the network settings triple-checked)  I can't ping the box or ping from the box.  
 
There has to be something obvious I'm missing- how do I get the guest OS to behave like a proper webserver?
 
Thanks,
 
-B

---

### Post by lewtwo on 2009-03-26
If I remember correctly ESXi has a virtual switch. If you change from DHCP to Static you may need to look at the VSwitch and its VLAN configuration ... just a thought.

---

