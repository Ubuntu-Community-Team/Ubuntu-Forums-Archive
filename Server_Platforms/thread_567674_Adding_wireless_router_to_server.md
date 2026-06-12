---
title: "Adding wireless router to server?"
date: 2007-10-04
forum: Server Platforms
---

### Post by phend-one on 2007-10-04
Hey all,

Been trying a new Ubuntu Server 7.04 install recently, and I've set up the server/gateway pretty much the way I want it. 

Now I want wireless clients to connect through a wireless router (linksys).

The server/gateway is using dhcpd3 and i've set it to assign static IPs to the clients.

What do I need to do to add the wireless router (wrt54gs with Tomato firmware 1.07)? I know I have to connect the router to the existing network, disable the wrt54gs' dhcp functionality as well as set it to be a passive "switch".

How would I get my server to do everything WPA2, mac authentication, no broadcasting SSIDs etc? Is it something I configure on the Ubuntu server or the router itself?

Thanks!:KS

---

