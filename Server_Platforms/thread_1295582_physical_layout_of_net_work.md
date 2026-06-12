---
title: "physical layout of net work"
date: 2009-10-19
forum: Server Platforms
---

### Post by mnduck on 2009-10-19
It's been a loooooong time since I was involved in any networking (Novel 3.2 win3 + dos) so that gives some idea. 

The layout I'm thinking of is:-

Wireless router-modem (dlink2640b) having a wired connection to both the server + possibly a wired connection to a Buffalo nas (linkstation mini)and PC's via a wireless connection.

I want to serve files from the server to all machines, backup to the server and the nas. I would also like to back up a e-commerce site directly from the net so the server needs net access FTP/HTTP.

The firewall in the router has been more than adequate + I'm happy to keep using it. 

Is this layout workable? I have a static external web address do I need to go to static addressing on the Lan side as well?  Server DNS off?


Thanks for your help.   MNDuck

---

### Post by Iowan on 2009-10-19
Just my opinion - looks like a workable plan.  By "static addressing on the Lan side" did you mean other LAN computers - or just the server? I guess I'm not sure what "Server DNS off?" means, either...  I suspect the server could be configured as a DHCP server as well (or the router).

---

### Post by cariboo on 2009-10-20
IF you have a router, you may as well use that for dhcp, just give the server and the nas static ip addresses, there is nothing worse than an ip address change when the lease runs out. With the server being connected to the router, you will have internet access, so backing up the ecommerce site should be a snap

---

### Post by running_rabbit07 on 2009-10-20
You could even assign the server a static IP while allowing DHCP with the other hosts. At least my Cisco router allows it. Then you just have to tell the router where to go to get to the website if the gateway is different from your LAN hosts. As far as bossing the router, I can't offer much help, haven't finished that CCNA class yet.

In my router I can give DHCP 3 hosts, while living a subnet that allows more, then give the server a static address with a higher number such as;

Subnet- 255.255.255.224
Network Address- 192.168.1.0
Default Gateway- 192.168.1.30
Broadcast-192.168.1.31
DHCP- 192.168.1.4-192.168.1.6
Server 1- 192.168.1.29

---

### Post by mnduck on 2009-10-20
Thanks all.

I thought that it should work,I'll leave the router running the dhcp and use static addressing for the pc's and nas on the lan side.


Best Regards     MNDuck

---

### Post by Iowan on 2009-10-20
Just remember to avoid the DHCP server's address range with your static addresses. 
(I'm also fond of static leases.)

---

