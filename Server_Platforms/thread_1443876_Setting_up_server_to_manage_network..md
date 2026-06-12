---
title: "Setting up server to manage network."
date: 2010-03-31
forum: Server Platforms
---

### Post by undecim on 2010-03-31
I have a server on my home network. It's currently running a DNS server (bind9) and an HTTP caching server (squid).

What I would like to do is redirect all outgoing port 80 connections to the squid server and also make the server responsible for managing DHCP on the network.

Do I just need to install a DHCP daemon on the server, disable it on the router, then set my server as the default gateway and configure iptables to route all connections like I want? Or is it more complicated than that?

Also, would that mean that all communication between two computers on the network will go through the server?

---

### Post by Iowan on 2010-03-31
I'm fond of DNSMasq as a combination DNS/DHCP server. Proxy (squid) is still on my "not yet tried" list. If the server connects to a switch (on the LAN side) communication between two machines on the LAN side wouldn't necessarily go through server (although the server might be involved in name lookup).

---

### Post by theozzlives on 2010-03-31
I would think you could setup Port forwarding in your router. Just use the router for DHCP.

---

### Post by undecim on 2010-03-31
> **theozzlives said:**
> I would think you could setup Port forwarding in your router. Just use the router for DHCP.

It's not port forwarding that I need. If a computer on my network goes to [www.google.com](www.google.com), I want it to connect to the squid (192.168.1.x:8080) instead. As far as I can tell, my router won't do this (its a linksys WRT120N, if anything with a similar model knows how to do this; also, OpenWRT is too big for this router without some hardhacks, so that's out of the question.)

I should also point out that this server has only 1 NIC, so it will connect through the router anyways, but I still want to take advantage of squid's caching capabilities.

---

### Post by undecim on 2010-03-31
> **Iowan said:**
> I'm fond of DNSMasq as a combination DNS/DHCP server. Proxy (squid) is still on my "not yet tried" list. If the server connects to a switch (on the LAN side) communication between two machines on the LAN side wouldn't necessarily go through server (although the server might be involved in name lookup).

So if my server has DNSMasq properly configured, and I disable the DHCP server on my router, I should be good?

** consults DNSMasq documentation **

---

### Post by fang0654 on 2010-03-31
You can always block all outbound 80/443 traffic from any IP except the proxy server on the router.  That prevents users from just bypassing the proxy by disabling it.  We do this with DNS and OpenDNS, to keep people from just specifying their own DNS servers to get around content blocks.

---

### Post by undecim on 2010-03-31
> **fang0654 said:**
> You can always block all outbound 80/443 traffic from any IP except the proxy server on the router.  That prevents users from just bypassing the proxy by disabling it.  We do this with DNS and OpenDNS, to keep people from just specifying their own DNS servers to get around content blocks.

I don't mind people on the network getting around it. In fact, a way to easily bypass the proxy would be a plus. There's no filter at all, just the performance boost from caching external web pages.

---

### Post by fang0654 on 2010-03-31
Ahh, scratch that then!

---

### Post by hscomp2002 on 2010-04-04
I got the same problem !!!
help plz

---

### Post by Iowan on 2010-04-04
> **hscomp2002 said:**
> I got the same problem !!!
help plzMight I recommend you start a separate thread and reference (link to ) this one for information?

---

### Post by confusedstingray on 2010-04-05
from what you are trying you might look in to this tutorial 
[http://www.howtoforge.com/squid-proxy-server-on-ubuntu-9.04-server-with-dansguardian-clamav-and-wpad-proxy-auto-detection](http://www.howtoforge.com/squid-proxy-server-on-ubuntu-9.04-server-with-dansguardian-clamav-and-wpad-proxy-auto-detection)
this uses most of what you have installed already 
just a suggestion

---

