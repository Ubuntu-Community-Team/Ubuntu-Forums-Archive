---
title: "linux firewall/router forward ports"
date: 2010-09-08
forum: Server Platforms
---

### Post by chrisbay90 on 2010-09-08
Hi,

I have linux server setup on a network with 2 interfaces. One (eth0) is connected to the regular network and the other (eth1) has a DHCP server and transparent web cache listening on it. The machines connected on the eth1 side are on a different subnet and the linux server is there gateway. Untrusted machines are introduced to this network to keep them isolated.

This isolation works well, too well. There are a small set of resources on the regular network I would like to make available to machines on untrustworthy network. I think I need to use iptables but alas I've had no luck in piecing together the command I need (in one case looking myself out and having to physically reset the machine).

Can anyone supply me with the command I would need?

---

### Post by BkkBonanza on 2010-09-08
You will need a rule in the FORWARD chain that selectively allows some traffic to pass based on criteria you want. If you can explain the criteria and example IPs/ports then I can help you with the rule.

---

### Post by chrisbay90 on 2010-09-08
> **BkkBonaza said:**
> You will need a rule in the FORWARD chain that selectively allows some traffic to pass based on criteria you want. If you can explain the criteria and example IPs/ports then I can help you with the rule.
Thank you for the quick and helpful reply :). Normally I'm a little more self sufficient but I've been struggling in vein all week. If you could me further than that would be greatly appreciated.

Regular subnet: 10.1.69.0/24
Server is connected to regular subnet on eth0
Untrustworthy subnet: 10.1.1.0/24
Server is connected to untrustworthy subnet on eth1

Example specification
All TCP traffic originating from 10.1.1.0/24 destined for 10.1.69.10:445 should be forwarded through.
All other traffic should not be forwarded (as is currently the case)

---

### Post by BkkBonanza on 2010-09-08
sudo iptables -A FORWARD -s 10.1.1.0/24 -d 10.1.69.10 -p tcp --dport 445 -j ACCEPT

Assuming policy is currently DROP this allows through that criteria.
If policy is ACCEPT on the FORWARD chain then you should either change it or add a default rule to DROP. But if you drop everything except above then nothing else will pass the gateway, both directions. Usually you'll have some other allowed traffic in one direction with allowance for ESTABLISHED.RELATED return traffic.

Anyway, above rule should handle just this one case. But you mentioned this machine is the gateway - so you will want more than just this traffic allowed.

also, nothing forwards at all unless you enable forwarding,

echo 1 > /proc/sys/net/ipv4/ip_forward

---

