---
title: "UEC and DHCP"
date: 2011-08-30
forum: Ubuntu Cloud and Juju
---

### Post by pantar on 2011-08-30
Hy there.

I have just set up a private cloud (UEC 10.10) and I have some problems that I can't figure out. I would like to run everything on a LAN network which includes a PC with CLC,CC,SC and Walrus controllers,another PC with NC, my desktop PC to access the eucalyptus admin panel via browser and a 3Com 4port switch. My problem is that I can't figure out how to configure my Cloud controller to also act as a DHCP on the network and to provide IP addresses to all PCs who are connected to the switch.

That is it for now. When I sole this problem I will ask more.

Thanks for any help?

---

### Post by Rusty au Lait on 2011-08-30
You have to have another host (not one of the UEC machines) be the DHCP server. Both DHCP servers can then be restricted to an IP range that only they issue. UEC will use its own DHCP server and only its own DHCP for it's instances. Any other host on the network will get its IP from the other DHCP.

---

