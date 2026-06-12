---
title: "Interface issues: Traffic flow"
date: 2006-11-29
forum: Server Platforms
---

### Post by Mr Fat Bat on 2006-11-29
Hi guys,

I've just started playing around with Server 6.10 and I'm having problems with some routing.  I have two Ethernet adapters:

eth0:
192.168.0.2/24
gw: 192.168.0.10

and

eth1:
10.0.0.1/24
gw: 10.0.0.1

The first adapter was enabled when I installed Ubuntu and the 2nd wasn't.  When I set up the second adapter all my traffic destined for the Internet (using gw 192.168.0.10 going out through eth0) is now attempting to go out eth1.  I can ping PC's on both networks, how can I make sure that all traffic destined for the web goes out eth0?

Cheers!

---

### Post by Mr Fat Bat on 2006-11-29
Actually I think I can solve this easily using *route. *Does anybody know how to manually edit the routing tables?  The entries in my table go
eth1 
eth0
eth1
eth0

I want them to go 
eth0
eth1
eth0
eth1

Sorry I can't supply the details, i'm at work and my server box is at home ;)

---

