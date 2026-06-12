---
title: "Slow Transparent Proxy/Squid"
date: 2008-09-12
forum: Server Platforms
---

### Post by jiffydos on 2008-09-12
I am running Ubuntu Server 8.04:

 2.6.24-19-server #1 SMP Fri Jul 11 21:50:43 UTC 2008 x86_64 GNU/Linux

It's the latest greatest and patched version.

I am using squid to transparent proxy:

iptables -A PREROUTING -s 209.80.0.0/16 -p tcp -t nat --dport 80 -j REDIRECT --to-ports 8616 
iptables -A PREROUTING -s 216.20.0.0/16 -p tcp -t nat --dport 80 -j REDIRECT --to-ports 8617 

It works great, initially.  But, once traffic starts to ramp up (I do more then 20-30 Mb throughput), it slows WAY down.  It is not CPU load as squid only uses 10% of the CPU.  In fact, if I put it statically in my browser settings, it's is still blazing fast.  It's only when I go through my gateway and the traffic is redirected that things slow down.

I have no errors in dmesg or any logs.  It almost looks like an connection tracking issue.  But, my nf_conntrack_max is set to 65536 and my "count" never gets over 1000.  So, I am not reaching any limits there.

Any ideas?

---

### Post by jiffydos on 2008-09-12
Well, Interestingly, I installed conntrack-tools and without doing anything else, it seems to have solved the problem. Anyone have any idea why this might be?

---

