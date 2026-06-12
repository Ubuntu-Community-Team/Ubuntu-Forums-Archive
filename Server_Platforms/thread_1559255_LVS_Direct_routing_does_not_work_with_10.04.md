---
title: "LVS Direct routing does not work with 10.04"
date: 2010-08-23
forum: Server Platforms
---

### Post by brav0 on 2010-08-23
I have a setup with a  load balancer using ipvsadm round robin direct routing.
There are 18 web servers attached as real-servers. Ligttpd running on the machines, listening to both local IP and the load balancer IP ( set on lo0:0 with netmask 255.255.255.255) arp_ignore=1 and arp_announce=2 set on eth1 (external network).

This setup works really well using 8.04 LTS.

However, I recently upgraded a machine to 10.04 LTS and now I cant seem to get it working.

When I connect to the load balancer IP i just get a time out, connecting to the service locally works.

I guess this has to do with some changes made in the kernel or that a patch is missing from the ubuntu 10.04-server kernel.

Linux voyager15 2.6.32-22-server #36-Ubuntu SMP Thu Jun 3 20:38:33 UTC 2010 x86_64 GNU/Linux
Distributor ID:    Ubuntu
Description:    Ubuntu 10.04.1 LTS
Release:    10.04
Codename:    lucid

The load balancer is still running 8.04.

Any help is appreciated, or if anyone just can point me in a direction.

---

### Post by brav0 on 2010-08-26
Still haven't found any solution to this problem.

---

### Post by zdali on 2010-11-10
It should work if you have only one interface. If you're trying to traverse interfaces, reverse path filtering will get in the way. 

Set

net.ipv4.conf.default.rp_filter=0
net.ipv4.conf.all.rp_filter=0

in /etc/sysctl.d/10-network-security.conf

HTH

---

### Post by brav0 on 2010-11-11
Thanks!
I will try this.

;)

---

### Post by gelimeri on 2010-11-11
On the real server:
> 
echo "1" > /proc/sys/net/ipv4/conf/all/arp_ignore
echo "2" > /proc/sys/net/ipv4/conf/all/arp_announce

and the then turning up the interfaces works.

I've followed this:
[http://www.austintek.com/LVS/LVS-HOWTO/HOWTO/LVS-HOWTO.arp_problem.html](http://www.austintek.com/LVS/LVS-HOWTO/HOWTO/LVS-HOWTO.arp_problem.html)
[http://www.austintek.com/LVS/LVS-HOWTO/mini-HOWTO/LVS-mini-HOWTO.html](http://www.austintek.com/LVS/LVS-HOWTO/mini-HOWTO/LVS-mini-HOWTO.html)
[https://bugs.launchpad.net/ubuntu/+source/ifupdown/+bug/83715](https://bugs.launchpad.net/ubuntu/+source/ifupdown/+bug/83715)

---

### Post by zdali on 2011-01-11
That is correct when your real server has only one interface. If you have a situation, however, where source and destination packets to the same IP are going via different interfaces then the reverse path filtering will prevent those packets from being forwarded, even with ARP issues addressed and ip forwarding enabled.

See
[http://tldp.org/HOWTO/Adv-Routing-HOWTO/lartc.kernel.rpf.html]("http://tldp.org/HOWTO/Adv-Routing-HOWTO/lartc.kernel.rpf.html") and
[http://www.tolaris.com/2009/07/13/disabling-reverse-path-filtering-in-complex-networks/]("http://www.tolaris.com/2009/07/13/disabling-reverse-path-filtering-in-complex-networks/")

---

### Post by box2 on 2011-06-01
zdali I have read a few dozen papers/blogs about how to set up LVS and your comment was the only place I saw this fact of rp_filter mentioned.  Everywhere just claims "And these are the sysctl options you need for LVS to work" which is was simply not working for me.

I had log_martians enabled and still couldn't find the culprit for why traffic wasn't getting sent to any real servers.

Thank you so much for clarifying this!

---

