---
title: "Internet slows to a halt in VirtualBox Ubuntu 10.04"
date: 2010-07-13
forum: Virtualisation
---

### Post by tommytas on 2010-07-13
Hi all

I am running Ubuntu 10.04 as a virtual machine using VirtualBox, on a Ubuntu host using NAT. In the virtual machine I am trying to crawl Web data using 20 wget processes in parallel (although I have experienced the same problem with more sophisticated crawlers such as Heritrix).

This works fine but after a lengthy period of time (I was able to download about 8GB worth of data), my Internet connection ceases to work (even after I stop all the crawling processes). If I enter an address in my browser it will say "Looking up example.com" and never proceed past that point.

Pinging an IP of a server that I know is working returns "Destination host unreachable".

However, if I go to Devices > Network Adapters and 'disconnect the cable' and then reconnect it again, the Internet works just fine - except this time the performance degradation is much quicker once I restart the crawl - almost instant, in fact.

Does anyone know why this might be happening and have any suggestions? Let me know if you need any more information or if there are any tests I can run to pinpoint the problem.

Thanks

---

