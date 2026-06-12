---
title: "Swap problems using Xen on server 8.04 64bit"
date: 2009-04-29
forum: Server Platforms
---

### Post by wxman on 2009-04-29
I'm looking to see if anyone else has any experience using Xen on 64bit Ubuntu servers? I'm using 8.04 on two physical machines, each with two Xen virtual servers set up in there own partitions. One is a load balancer/failover, and the other is the web server.

I had to use an adaptation of several how-to's including [http://www.howtoforge.com/the-perfect-load-balanced-and-high-availability-web-cluster-with-2-servers-running-xen-on-ubuntu-8.04-hardy-heron](http://www.howtoforge.com/the-perfect-load-balanced-and-high-availability-web-cluster-with-2-servers-running-xen-on-ubuntu-8.04-hardy-heron). I installed Xen by adapting the how-to [http://blogama.org/node/92](http://blogama.org/node/92). 

Things seem to be working OK, but I don't think all is correct. I noticed that when I run the console after loading all the Xen drives, I see on all of them:
```
  * Setting kernel variables...    [ OK ]
  * Activating swap...             [fail]
```

I also installed Webmin on the web server, and it reports that that there is no swap drive:
```
Virtual Memory (swap) IDE device A partition 3 not in use
```
I was never very clear on how to set up the partitions to begin with, but I thought I had it worked out. I am able to get to my web server test site from the Internet, and my failover is working, but I don't like to looks of the swap files. I would appreciate any help from others who might have gone  this route already.

---

