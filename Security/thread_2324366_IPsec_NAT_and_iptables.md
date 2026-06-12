---
title: "IPsec NAT and iptables"
date: 2016-05-13
forum: Security
---

### Post by Drenriza on 2016-05-13
Hi all

I am fiddling around with two IPsec GW's in a test environment and ran into a issue.

The issue i ran into is that my "local" IPsec GW is on 172.16.5.5/32, the "remote" IPsec GW is on 10.1.10.50

On the "local" side i would like to NAT traffic from 192.168.1.0/24 through 172.16.5.5 and route this to 10.1.10.50/24.
But i am not quite sure how to tell iptables to

#1 NAT 192.168.1.0/24 network to 172.16.5.5/32
#2 Route 172.16.5.5/32 traffic to 10.1.10.50/24

Since it looks like that my iptables try to route the traffic from 192.168.1.0/24 directly to 10.1.10.50 around the tunnel.

Hope someone can help me in the right direction since i haven't quite found how to do the above yet.

Thanks on advance.
Kind regards

---

### Post by fugu2 on 2016-05-18
I'm no expert, but at least part of your solution might be in the route command ```
$ /sbin/route -n
```

---

