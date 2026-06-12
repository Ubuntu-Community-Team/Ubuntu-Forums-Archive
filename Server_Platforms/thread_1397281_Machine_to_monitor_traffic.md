---
title: "Machine to monitor traffic"
date: 2010-02-03
forum: Server Platforms
---

### Post by dragos2 on 2010-02-03
What is the setup required in order for a 2 NIC machine to only forward traffic ?

I am planning to set up a machine between the LAN and Router like this:

LAN  <--> machine <--> router <--> internet

This machine will only forward traffic. I will use it with ntop, squid, maybe snort
or maybe Untangle if I find it satisfactory.

Is my scenario fiable ?

I want to forward traffic, use ntop and squid on it.

Any suggestions regarding my setup ?

---

### Post by KiLaHuRtZ on 2010-02-03
Yes, what you need to research is 'iptables'; but, it can be done. :p

---

### Post by tlsarles on 2010-02-03
we have done a couple deployments with untangle. has a decent feature set, but has a few issues too. Once you set it up, it runs pretty solid tho. If you can get learned up on IPTables, that is a pretty solid recommendation.

---

