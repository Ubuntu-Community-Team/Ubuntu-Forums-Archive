---
title: "UltraSPARC T1/T2 and Network performance"
date: 2008-03-25
forum: Sun Sparc Users
---

### Post by blam_ on 2008-03-25
Hi All,

I've been now working for a while with Sun's T2000 (UltraSPARC T1) and T5120 (UltraSPARC T2) servers. They're running Ubuntu Gutsy versions 2.6.22-9-sparc64-smp (T2000) and 2.6.22-14-sparc64-smp (T5120).

They're both performing reasonably well in every other area except with networking. Have you ever noticed or heard of similar observations?

Both of these machines have four 1GB network interface cards. I've been using a little benchmark program called nttcp to generate some TCP networking traffic. Nttcp is not multithreaded, so I've been launching several simultaneous nttcp instances to make better use of the multiple cores (and since single threaded nttcp test run cannot even saturate a single 1GB bandwidth). Now, the problem is, that whenever I launch something like around 6-10 simultaneous benchmarks, Ksoftirq process(es) starts running wild practically destroying the performance. This leads to a very nasty problem where multiple nttcp instances are needed for high transferring rates, but too much 'network parallelism' causes significant performance problems. Actually, due to this problem I haven't been able to reach the optimal 4GB transferring rates (more like max 2.5GB). I also noticed these Ksoftirq daemons pop up with other network heavy benchmarks as well, and they always seem to have negative affect to the test results... I find this all very problematic, since it's often hard to control how many threads are being used for networking...

Btw. I also noticed that by default only the default (routing table) network interface is being used when transmitting, even though there's more available and even if it's wholly saturated.

Btw2. Anyone know how to reach David S. Miller? :)

Thanks for any input!

---

