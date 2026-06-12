---
title: "Monitoring Internet usage"
date: 2007-11-29
forum: Server Platforms
---

### Post by pevans_om on 2007-11-29
Ok, not about Ubuntu, but where else do I find all the Linux gurus? :)

I'm having a bit of a dilemma at work. We consistently overrun our monthly bandwidth limit and I'm trying to find out what's using all the bandwidth.

I currently run everyone in the office through a censornet proxy server. (Censornet being a linux content filtering distro) The censornet web interface gives me reports on usage per person. Unfortunately It seems that the culprit is something other than http based applications since the web usage reports (from the cache server) indicate about 2.2GB used for the month, but the total usage is 7.3GB!

So, does anyone know how I can get information about what else is using my bandwidth? I'm sure the info must be available somewhere in the depths of the machine....

---

### Post by timcredible on 2007-11-29
the proxy is allowing all protocols, but will only report on  http?  if so, get another proxy.

---

### Post by n3tfury on 2007-11-29
> **pevans_om said:**
> Ok, not about Ubuntu, but where else do I find all the Linux gurus? :)

I'm having a bit of a dilemma at work. We consistently overrun our monthly bandwidth limit and I'm trying to find out what's using all the bandwidth.

I currently run everyone in the office through a censornet proxy server. (Censornet being a linux content filtering distro) The censornet web interface gives me reports on usage per person. Unfortunately It seems that the culprit is something other than http based applications since the web usage reports (from the cache server) indicate about 2.2GB used for the month, but the total usage is 7.3GB!

So, does anyone know how I can get information about what else is using my bandwidth? I'm sure the info must be available somewhere in the depths of the machine....

[http://www.ntop.org/overview.html](http://www.ntop.org/overview.html)

---

### Post by lespaul_rentals on 2007-11-29
Sounds like someone's doing some p2p-ing?

---

### Post by craigp84 on 2007-11-29
Ok, stop right there buddy! :-)

> We consistently overrun our monthly bandwidth limit

> the total usage is 7.3GB!

! indeed. You don't need a new reporting tool, you need a new ISP!!!

-c

---

