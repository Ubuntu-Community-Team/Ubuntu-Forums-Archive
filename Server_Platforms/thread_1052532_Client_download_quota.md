---
title: "Client download quota"
date: 2009-01-27
forum: Server Platforms
---

### Post by starling on 2009-01-27
I have been searching all morning without success. (I thought it would be a common question)

I have an ubuntu 8.04 server in my house set up to be a gateway with NAT. There are 6+ client computers. I want to impose an internet download quota on each computer and throttle them when they reach that quota (not QoS).

I don't want to make it a proxy, but will if I have to.
The router is not a candidate for firmware replacement.


So I need to monitor the connection and log downloads against local MAC address, then impose a speed limit when they reach the defined download quota.
Suggestions?

---

### Post by starling on 2009-01-28
Ok, looks like iptables might do what I want after patch-o-matic and kernel rebuild. Sounds scary.

I'm looking at [http://linuxgazette.net/108/odonovan.html](http://linuxgazette.net/108/odonovan.html) and [http://www.linux-noob.com/forums/index.php?showtopic=3036](http://www.linux-noob.com/forums/index.php?showtopic=3036) ATM. Anyone have sage advice or a pre-made firewall rule for me?

---

