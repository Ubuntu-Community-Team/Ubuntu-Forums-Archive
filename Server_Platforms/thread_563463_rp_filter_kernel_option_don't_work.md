---
title: "rp_filter kernel option don't work"
date: 2007-09-30
forum: Server Platforms
---

### Post by frankabel on 2007-09-30
Hi all,

I just want forward IP packages that its source address belong to the network  assigned to the interface that they come from. 

For that I put 1 in 
/proc/sys/net/ipv4/conf/eth5.102/rp_filter and  
/proc/sys/net/ipv4/conf/all/rp_filter, 

even I put 1 in  /proc/sys/net/ipv4/conf/eth5/rp_filter 

but nothing. I mean, after that, ICMP (ping) packages are for forwarded even they have an source address that don't belong to the network of the interface  they come from.

Any help? Is not that kernel option to avoid some kind of ip spoofing?

Ubuntu 6.10 and 2.6.17-10-server #2 SMP

Salute
Frank Abel

---

### Post by steve.horsley on 2007-09-30
I believe that rp-filter uses the routing table to decide which source addresses are accepted through an interface. Packets will be accepted not only if they originate from the connected network, but also if they originate from a network that (according to the routing table) is connected via that network.

It may be that a simple iptables entry might be easier.

---

### Post by frankabel on 2007-09-30
Thanks for your reply steve.

The Iptables will work fine, but I just wandering why that option don't work and if is just in my box. 

Salute
Frank Abel

---

