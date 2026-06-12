---
title: "Setting up an OpenVPN server on Ubuntu 16.04"
date: 2018-09-27
forum: Server Platforms
---

### Post by dycon on 2018-09-27
Hey everyone,

I'm a beginner in VPN servers and therefore have never set one up before. My problem:
I've got some friends of mine that are regularly using my homeserver (ESXi on it) for some test purposes, where they run their own VMs etc.
But for them not needing to come to my home every time to work on their stuff, I've came to the point where a VPN server would probably be the best way for me.
Now, I've seen there is an ESXi instance ready to use given by OpenVPN ("Access Server"), but it seems like it's limited to max. 2 connections, whereas I've got 6 friends of mine that sometimes need a connection simoultaneously. Since I don't want to pay anything for it, I've thought about setting up an ubuntu server 16.04 on a virtual ESXi VM, and install the OpenVPN server manually on there.
Before doing so, I would like to get some recommendations of maybe experienced users, that have had set up an OpenVPN server before, that's why I'm here.
I've seen that I'd need to portforward TCP443 and UDP1194 to the server - that'll be no problem. Is there anything else I need to worry about (pay close attention to?)
Can anyone recommend me a tutorial/guide that I could stick with? Because one of my friends has already tried to set one up on one of his VMs, but couldn't get through to the home network (OpenVPN has let him connect to his VM; but created a different network, not related to the actual network - giving him no access to my network, the internet or anything, just put him into a separate network without any devices in it except him). I don't know exactly what the problem was, but I would rather stick to a tutorial, than getting the same problems and ending up in frustration.

Thanks in advance!

---

