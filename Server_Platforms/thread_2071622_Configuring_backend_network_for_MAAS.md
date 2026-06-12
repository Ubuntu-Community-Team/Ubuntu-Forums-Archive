---
title: "Configuring backend network for MAAS"
date: 2012-10-15
forum: Server Platforms
---

### Post by griffinmt on 2012-10-15
I have added a couple of spare server systems to my house network (pretty standard config) running off 192.168.1.0/24 subnet.
One system has a second enet to run a different subnet (thru a switch) of 10.0.0.0/24. That switch also connects to the second server with its only enet. 
The dual enet server will be the maas controller and the second server will be pxe booting from it on the small subnet.
 
So, I need to setup a dhcp service that ONLY services the 10.0.0.0/24 subnet and it needs to able to route traffic thru to the 192.168.1.0/24 subnet which connects to the outside world as well.
 
What goes into the dnsmasq.conf file to only do dhcp to the second enet path, and how do I setup the router commands so both subnets with talk etc.
 
Martyn

---

### Post by griffinmt on 2012-10-16
With some offline help, this is solved.

---

