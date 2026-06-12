---
title: "Help with building a cluster"
date: 2014-03-17
forum: Server Platforms
---

### Post by RL600 on 2014-03-17
Hello all,

A couple of days ago I made my own ltsp server. 
I thought it would be cool to build my own cluster with ltsp on it.
I know what a cluster is and there stops my knowledge!
Can somebody can give me some information on how to make your own cluster what hardware is needed and what software to use.
Thanks in advanced!

---

### Post by aerokid240 on 2014-03-18
Do some google searches for High Availability, Tons of information out there. My experience is with utilities such as haproxy for load balancing and keepalived for IP failover for a backup load balancing (haproxy) server. They work awesome together.

---

