---
title: "NAT and iptables"
date: 2007-03-25
forum: Server Platforms
---

### Post by christhemonkey on 2007-03-25
Evening,

I am trying to get my Ubuntu server to forward the ports for azureus which is currently 1 big NAT problem,
I have spent all evening googleing and trying to get it to work but i cant.

Here is my setup:
```

[INTERNET]
|
|
|
[SERVER] (dynamic ip on ppp0, need to forward 2 ports to eth0: 1 tcp, 1 udp)
|
|
[SWITCH]
|\
| \
|  \
|   \
|    \
|     \
[PC1][PC2] (both with dynamic ips from dhcp)

```
I have cant seem to get a working iptables rule that will forward both these ports, any help would be much appreciated!

---

### Post by simonn on 2007-03-25
You can't do what you want to do. 

New connections made from outside your LAN are not NATed per se. As the connection is not initiated inside the LAN, the router/NAT does not know which device inside the LAN it is meant to go to.

You can only forward one port to one destination and as you have only one external IP address your only option is to run azureus on a different port(s) on each of the PCs and forward each port to the correct PC. I do not know if this is possible with azureus though.

---

### Post by christhemonkey on 2007-03-26
Would this be possible if i only ran azureus on one pc?

(whose ip adress is still dynamic)

---

### Post by simonn on 2007-03-26
> **christhemonkey said:**
> Would this be possible if i only ran azureus on one pc?

Yes.

> **christhemonkey said:**
> (whose ip adress is still dynamic)

It is easier to use a static IP address for any server (Azureus is a server in this context).

However, you can often set the DHCP server (which is probably on your router(?)) to assign a static IP address based on the MAC address or sometimes the host name of a PC/device. This depends entirely on the capabilities of the DHCP server. This is handy if, for instance, you have a laptop because you can set the DHCP server to assign a static address dynamically when you are at home so things like Azureus work, but if you are elsewhere, e.g. friendly cafe with free wireless access, you do not have to change any network settings to get a DHCP address.

---

