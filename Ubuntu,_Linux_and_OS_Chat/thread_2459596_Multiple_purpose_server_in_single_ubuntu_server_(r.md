---
title: "Multiple purpose server in single ubuntu server (raspberry pi)"
date: 2021-03-22
forum: Ubuntu, Linux and OS Chat
---

### Post by shseahsg601 on 2021-03-22
Is it possible to configure or install multiple purpose programs or server in single ubuntu server with raspberry pi 4?
For example, creating a Plex server in the rpi4 and then creating a VPN server that can be used to connect rpi4 from other network (outside of home) and various other server (web server, password manager etc)...
Is there security flaw with this kind of setup?

---

### Post by mastablasta on 2021-03-22
yes and yes.

you have multiple attack vectors to one machine. so make you harden it properly.

servers are actually services (CLI based apps that run on server). so just as you can have mutiple desktop applications running at the same time you can have on server. is it a good idea? sometimes it makes sense to do it.

maybe for VPN would be better if it ran separately.

---

### Post by TheFu on 2021-03-22
+1 for what mastablasta wrote.

A vpn server really should be a separate device. It is a security design/architecture decision.

Having to any programs on the same OS install can cause conflicting dependencies. The best practice is to logically split dissimilar services into their own VM or container.  I don't think VMs work on raspberry pi HW yet. Containers do and can be used for many complex services.

Services that are directly available on the internet probably shouldn't run in the same container as LAN-only services. Security consideration.

r-pi hardware has some limits for throughput. They are impressive devices for what they are but I/O isn't something they are designed to excel. 

And while many processed can be put into a container, I think VPNs are not one. 

If yo are just learning Unix, building Containers is a non-beginner skill. Sure you can type the commands, but really understanding the repercussions and security aspects of containers requires years. There are many hidden aspects and considerations.

---

