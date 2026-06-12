---
title: "PPTP Server Routing"
date: 2011-10-24
forum: Server Platforms
---

### Post by Frizianz on 2011-10-24
Hey guys,

Wondering if you guys could help me with some routing which i need to get configured but i have no idea how to do.

So i have two interfaces on the Linux Server one External interface which has a straight public IP to it (eth0). And one internal interface which is not able to access the internet at all (eth1).

Now i've got the PPTPD server assigning client ip's in the subnet 172.30.0.0/24 and got nat working so i can tunnel everything through eth0 to the internet. However i need to also access things on eth1 which is in the 10.0.0.0/16 subnet. 

Would someone be able to help me with getting the routing in place so i can connect to everything on the eth1 interface via pptp vpn?

Cheers

---

