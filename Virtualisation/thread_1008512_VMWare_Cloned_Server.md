---
title: "VMWare Cloned Server"
date: 2008-12-11
forum: Virtualisation
---

### Post by NetworkGuy on 2008-12-11
Hi All,

I've cloned a server in ESX server.  Now when I boot the cloned server, the Ethernet Interfaces do not come up.  The interfaces file is correct.  Am I thinking right that since the MAC addresses changed, the interfaces won't come up?  Where can I correct that?  

Am I totally out in right field?  What is the fix as I really don't want to have to create this cloned server from scratch.

Thanks.

---

### Post by PilotJLR on 2008-12-11
You're right. If you remove the mac addresses from the interfaces file in the clone, then either reboot it or restart networking, then you should be up and running. If not, then post the interfaces file and ifconfig -a in the clone.

---

### Post by NetworkGuy on 2008-12-12
Got it.

The interfaces were actually coming up as ETH2 and ETH3.

A quick look in the /etc/udev/rules.d/70-persistant-net.rules showed where udev created 2 new interfaces based on MAC address.   A quick edit of the file to change the address on ETH0 and ETH1 to match what ETH2 and ETH3 were set to, delete the ETH2 & ETH3 lines and restart UDEV and everything is looking good now.   

Thanks PilotJLR for pointing me in the right direction with the ifconfig -a command.

---

