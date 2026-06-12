---
title: "Iptables"
date: 2008-01-01
forum: Server Platforms
---

### Post by NullHead on 2008-01-01
Hi I would like help on the subject of iptables 

I'm trying to run a Call of duty 2 server using the udp port 28960 and I suspect iptables is blocking incoming traffic to that port. If anyone could help me open up that port it would be helpful. :)

---

### Post by p_quarles on 2008-01-01
You can get your iptables rules by running this:
```
sudo iptables -L -v
```

---

### Post by NullHead on 2008-01-01
> **p_quarles said:**
> You can get your iptables rules by running this:
```
sudo iptables -L -v
```

This is my output of you're command.```
$ sudo iptables -L -v
Chain INPUT (policy ACCEPT 434 packets, 129K bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 457 packets, 85005 bytes)
 pkts bytes target     prot opt in     out     source               destination 
```Is my requested port open? It seems like it isn't, but I don't know about iptables :) 

Anyways can you provide me with commands to forward my port?

---

### Post by p_quarles on 2008-01-01
All of your ports are open. The only things that could possibly be blocking the port in question are your ISP or your router.

---

