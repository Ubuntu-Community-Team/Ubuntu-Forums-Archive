---
title: "Ports open on localhost, but not on internal IP"
date: 2012-04-04
forum: Server Platforms
---

### Post by hughr2005 on 2012-04-04
Hello all,

I realise this may be a problem with my network configuration in a router, and therefore off topic, but in case it is to do with ubuntu server any help would be much appreciated.

I'm running Ubuntu Server 11.04 in a Virtualbox VM on my MacBook Pro. I have bridged the network connection in the VM to my wireless connection on my MacBook. I have checked the DHCP table on my router, and the Ubuntu VM is showing up properly. Pings to the machine work from other machines on the network, using the internal IP address, however there's something weird going on with the ports. I've tried to open the ports for ssh and irc (which I would've thought would happen during installation of the servers) with ufw, and when I nmap localhost from within the machine it says that all the ports are open. However, when I nmap the internal IP of the Ubuntu VM, I see all ports shut. I have done this before and it worked, but only with 10.04. Has some default setting changed between versions?

Thanks in advance for any help,

Hugh

---

