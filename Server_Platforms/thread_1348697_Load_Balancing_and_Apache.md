---
title: "Load Balancing and Apache"
date: 2009-12-07
forum: Server Platforms
---

### Post by Spooky Neo on 2009-12-07
Hi everyone,
 
We are currently building an Ubuntu infrastructure of Ubuntu 9.10 Server. At this moment, we would like to configure and test a load balancing of 2 Apache Servers. I've been doing some research in the past hours and came up with several Linux softwares. Unfortunately, these softwares are not usnig the infrastructure we're looking for. Let me explain myself.
 
All the solutions I could find on the Internet, requires 1 physical (or virtual) load balancer computer. We would like a solution like the Microsoft Network Load Balance, where it does not require a Load Balancer. Microsoft NLB works like this:
 
[http://remoteitservices.com/files/images/NLB%20Cluster.gif](http://remoteitservices.com/files/images/NLB%20Cluster.gif)
 
Every server receives the request, but only one will accept it. Once it accepts it, it will tell the others so that they will drop the request.
 
The problem with having a Load Balancer computer (or VM) is that you get a Single Point of Failure. Of course, we could get a cluster or even a Load Balance of the Load Balancer, but that's not what we're looking for.
 
I was first looking at the mod_proxy_balancer of Apache2, but realized that it was not what we were looking for.
 
Is there something like the Microsoft way, that exists in Linux ? We want only 2 Apache Physical Servers that are load balancing themselves. 
 
 
Thanks for any help,
 
Guillaume.

---

