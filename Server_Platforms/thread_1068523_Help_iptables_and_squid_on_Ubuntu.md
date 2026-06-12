---
title: "Help iptables and squid on Ubuntu"
date: 2009-02-13
forum: Server Platforms
---

### Post by getut on 2009-02-13
Please help me. I've been trying for a week to set up squid and iptables on Ubuntu server.

I've been following many of the squid tutorials out there. The problem is that every single one of them assumes that the linux box is the router/firewall and has two NICS. One LAN and one on the WAN.

That is not the case for me. I have hardware router/firewall that is on 192.168.0.254.

I have a squid box sitting on 192.168.0.253 with a single NIC. All of my clients are DHCP assigned and gateway is defined as the squid box (192.168.0.253).

I need the squid cache/proxy to accept the requests and foward them to the REAL gateway if not in the cache.

I am completely lost on how to get this to work and I have munged iptables so many times it isn't funny. How can I get this to work?

---

### Post by Neural oD on 2009-02-13
I did a setup like this a long time ago - as I recall it wasn't too hard. Sorry - I don't have squid at the moment, and it was long ago - so I'm not to sure on the whole process. Why don't u look at webmin - it is a web based configuration tool - maybe that could help you out a bit in your setup problem.

---

### Post by Neural oD on 2009-02-13
oh - by the way - it's always good to backup the configuration files before you begin tinkering :)

---

