---
title: "LXC Networking Problem..."
date: 2014-06-24
forum: Virtualisation
---

### Post by rayj00 on 2014-06-24
This is my first attempt at playing with LXC and containers.
I think it's a pretty neat feature from what I read about it.

Ok, my host is Ubuntu 12.04.  I created a container using default setting,
so the container OS is the same as the host. I made no configuration
additions or changes to LXC data.

I think I read that LXC does it's own DHCP?  The container's IP is 10.0.3.177.
The host is 192.168.1.131.  The host and container can ping each other.
The container can ping other 192.168.1.x IP's on the network, but they 
cannot ping the container?  Ideas why?

The host is connected to my LAN over WiFi is that means anything.

I'm sure this is something simple.  Thanks for your help.

Ray

---

### Post by Doug S on 2014-06-24
While the Ubuntu Serverguide suffers from a severe lack of subject matter expert input, the LXC chapter had a complete overhaul and re-write for 14.04.
The answer and "how to" for your questions are there: Chapter 20 - Virtualization, Section 4 - LXC, Sub-Section 4.4 - Networking.

[https://help.ubuntu.com/14.04/serverguide/lxc.html#lxc-network](https://help.ubuntu.com/14.04/serverguide/lxc.html#lxc-network) 
or the pdf version: [https://help.ubuntu.com/14.04/serverguide/serverguide.pdf](https://help.ubuntu.com/14.04/serverguide/serverguide.pdf)

I do not know how LXC may have changed since 12.04 and / or if these methods can be used the same way with 12.04.

---

