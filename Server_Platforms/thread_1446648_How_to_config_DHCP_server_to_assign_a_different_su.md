---
title: "How to config DHCP server to assign a different subnet for VPN users?"
date: 2010-04-04
forum: Server Platforms
---

### Post by alps_xing on 2010-04-04
I'm establishing a server that runs DHCP server, NAT gateway and VPN server. It have two physical interfaces, one for intranet and one for internet. The NAT gateway will give internet access for intranet. Another site will connect to this server by VPN. I need the server to assign a different subnet for that site other than the local site. Do anyone know how to config the DHCP server? Should I config the client classing, and how to do it?

Thanks.

---

### Post by alps_xing on 2010-04-05
Anybody can help?

---

### Post by spynappels on 2010-04-05
OpenVPN in Routing mode will hand out IP addresses in whatever subnet you want it to. You can even get it to assign the same IP to a specific client every time. This is set in the the server.conf file that OpenVPN reads when it starts its Daemon.

It is not very efficient in that it will only hand out every 4th IP address, but unless you will be connecting more than about 50 clients, there is more than enough scope under a 255.255.255.0 subnet.

If this does not answer your question, perhaps you could explain what you want in a little more detail?

---

### Post by netztier on 2010-04-05
> **alps_xing said:**
> I'm establishing a server that runs DHCP server, NAT gateway and VPN server. It have two physical interfaces, one for intranet and one for internet. The NAT gateway will give internet access for intranet. Another site will connect to this server by VPN. I need the server to assign a different subnet for that site other than the local site. Do anyone know how to config the DHCP server? Should I config the client classing, and how to do it?


If that is a site to site VPN - why would you want to assign IP addresses from your DHCP server? The remote site would have to run it's own DHCP service, wouldn't it?


regards

Marc

---

