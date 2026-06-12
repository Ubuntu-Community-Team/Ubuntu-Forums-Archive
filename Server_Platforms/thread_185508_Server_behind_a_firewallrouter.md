---
title: "Server behind a firewall/router"
date: 2006-05-31
forum: Server Platforms
---

### Post by wildem on 2006-05-31
Hey everyone,

This is mostly networking question. I have an interest in installing a ubuntu-server which will be local to a domain say '10.x.x.x'. This has a gateway/router 10.x.x.1 and so on. If the currently setup server is connected to the router with a static ip of ex: '10.x.x.100' - How would i be able to connect to this server from the outside/internet(home machine) and if it's at all possible. I imagine that setting port forwarding on a router may fix this problem, but does anyone have concrete suggestion on a step-by-step plan.

Any suggestions will be appreciated.

btw, Accessing this http server on local lan is solved (for both linux/windows clients)
it's just from outer internet client access im wondering about.

Cheers,

---

### Post by jgoguen on 2006-05-31
All you need to do is log into the router at 10.x.x.1 and set it to forward port 80 (and any other ports you may be using, like 443, 8008, 8080...) to 10.x.x.100.  As for step-by-step, we'd need to know what router you have before we could start that.

---

### Post by wildem on 2006-05-31
Thx for the tip about the forwarding- i suspected that it might be the first solution. 
As for the specs on the router, i just dont know yet. will try this out and post my findings..

---

