---
title: "[SOLVED] Virtualbox Gusty unable to ping, surfing ok"
date: 2007-12-06
forum: Virtualisation
---

### Post by wormser on 2007-12-06
I cannot ping by IP or host name in a Gusty Virtualbox machine.  Surfing the internet is fine and I can use apt-get to install.  Is my host Gusty machine blocking pings?  What could be causing this?

Also, is there anyway I can get Virtualbox to assign 192.168.1.x address instead of 10.0.2.x addresses?

---

### Post by mozetti on 2007-12-06
You need to follow the instructions in VirtualBox Help about setting up a virtual NIC. Right now, the Virtual Machine is getting an IP addy from the Host - basically it's working like Internet Connection Sharing (ICS) in XP.

Setting up a virtual NIC basically "creates" a 2nd NIC, but it actually just gives a 2nd name to your existing Host's NIC. The Virtual Machine sees this phony NIC as a separate hardware NIC and uses it. That way, when the VM starts up it sees the phony NIC as it's own and either assigns it the IP address you specify (if you use static IP) or it requests an IP from the DHCP server.

I have this set up on my VirtualBox because I needed the VM to be a separate computer on my LAN (to run TVersity to stream content to my Xbox 360), and not just piggy-backing on the Host.

The virtualbox help files were very easy to follow. The only downside for me is that during the Ubuntu loading, configuring NICs takes a bit longer which makes usplash go away showing the startup status messages (i.e. all the text you'd see when Linux loads if you don't use usplash).

---

### Post by Jdubs23 on 2008-07-01
This was very helpful, and I successfully was able to set up the interface and can ping my host from my guest and my guest from my host.  I am having a problem with TFTP however...

I have a network device attached to a switch and my PC attached to the same switch.  I would like to be able to TFTP files from my Host(XP) IP address to my network device, and also TFTP files from my Guest(Ubuntu) IP address to my network device.  This works fine when TFTPing from my Host device, however I get a TFTP timeout when trying to TFTP from the Guest device.

Any ideas?

---

### Post by amk007 on 2008-08-18
I am unable to find this - You need to follow the instructions in VirtualBox Help about setting up a virtual NIC. Could anyone please point me to a step by step directions if there is one?

---

### Post by brian mcgee on 2008-09-22
> **amk007 said:**
> ...Could anyone please point me to a step by step directions if there is one?

This should do it.
[https://help.ubuntu.com/community/VirtualBox#Networking](https://help.ubuntu.com/community/VirtualBox#Networking)

---

