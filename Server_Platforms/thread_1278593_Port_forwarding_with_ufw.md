---
title: "Port forwarding with ufw"
date: 2009-09-29
forum: Server Platforms
---

### Post by ene_dene on 2009-09-29
I just installed ubuntu server 9.04 and I'm having a problem. Here s my situation:

Router (192.168.1.254) -> ubuntu server (eth1 192.168.1.1, eth0 192.168.0.1 which is connected to another router).
Now I have two more computers with addresses 192.168.0.2, 192.168.0.3 (connected to same router as eth0 from ubuntu server). Their default gateway is 192.168.0.1, and DNS 192.168.1.254.
Now it was easy to setup such configuration when I used ubuntu desktop with gui instead of ubuntu server, because I used Frestarter and it's easy to NAT and forward ports.

Now I'm using ufw (uncomplicated firewall). I've followed the instructions from ubuntu server documentation and enabled masquerading for my other two computers to have Internet connection:
```
#nat Table rules
*nat
:POSTROUTING ACCEPT [0:0]
#forward from eth0 through eth1
-A POSTROUTING -s 192.168.0.0/24 -o eth1 -j MASQUERADE
COMMIT

```
was the code for enabling it.

I was hoping that this was the hard part, since I don't understand iptables syntax. Anyway... now I need to forward some ports. For example, let's say that 192.168.0.2 s Debian web server, and I that my ubuntu server (192.168.1.1, 192.168.0.1) needs to forwards port 80 to Debian server.
In Firestarter I would just forward port. 
How do I do that with ufw?

---

