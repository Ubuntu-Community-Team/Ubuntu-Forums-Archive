---
title: "http proxy no longer working after installing eBox"
date: 2009-03-04
forum: Server Platforms
---

### Post by rockfx01 on 2009-03-04
Hello,

I installed eBox on Ubuntu 8.04 64-bit to try it out.  After installing the network and firewall modules and enabling them, I can no longer access the apt-get repositories or ping any websites, but I can ping computers on the local network.

Everything was working fine before I installed/enabled the network and firewall modules (I did it at the same time so I don't know which is to blame).

The server connects to the web through an http_proxy on port 80 (not the usual 8080).  How can I configure ebox so that it will allow the http_proxy traffic to get through?

The server is configured for DHCP.  I also thought perhaps the Gateway setting in ebox is the problem.  No gateways are listed, and if I try to add the gateway manually eBox returns an error saying "Gateway <IP> is not reachable".  However, if I ping the gateway, it is in fact reachable.

---

