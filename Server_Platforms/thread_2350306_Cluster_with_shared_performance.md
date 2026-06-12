---
title: "Cluster with shared performance"
date: 2017-01-23
forum: Server Platforms
---

### Post by martin-juras-001 on 2017-01-23
Hello everyone reading this post, I would like to ask you, if you know about solution to my problem described below.

First of all I have two computers (kinda old, AMD-powered) and I want to connect them to cluster to share their computing power.

I was wondering why I couldn't find any tutorials, probably it is not possible to do. What I want to do is connect to computers in cluster (first one is 1core with 2GB RAM and second 2-core 4GB) and get 3-core and 6GB power. That means if I open (e.g. h/top) I will get sum of their computing power. 

Is this even possible? If yes, I would be very happy, if you share with me some of your knowledge.

Thanks for help.

---

### Post by raja.genupula on 2017-01-24
Woow good thinking, We can call this as **Virtualization for aggregation**

[https://en.wikipedia.org/wiki/Virtualization_for_aggregation](https://en.wikipedia.org/wiki/Virtualization_for_aggregation)

And with a little google search I found this [http://www.scalemp.com/products/selective-scaling/](http://www.scalemp.com/products/selective-scaling/)

And its worth reading. 

Hope it helps.

---

### Post by martin-juras-001 on 2017-01-24
> **raja.genupula said:**
> Woow good thinking, We can call this as **Virtualization for aggregation**

[https://en.wikipedia.org/wiki/Virtualization_for_aggregation](https://en.wikipedia.org/wiki/Virtualization_for_aggregation)

And with a little google search I found this [http://www.scalemp.com/products/selective-scaling/](http://www.scalemp.com/products/selective-scaling/)

And its worth reading. 

Hope it helps.

Thank you very much for your time and respond. I will try this software. :)

---

### Post by raja.genupula on 2017-01-24
Glad you have found what you are looking for, Please mark this thread as solved. 

Thank you.

---

### Post by TheFu on 2017-01-25
We see this question all the time. Something so simple really isn't simple. The latency between systems is a major issue - even 100Gbps links are slow.

Generally, clustering is of 2 types - redundancy or dealing with highly, highly, specialized workloads specific ally designed to run on a specific cluster type.  Neither of these are suitable for general purpose, end-user, applications.  top/htop will not see the combined resources.

On systems like you have, I'd guess server process redundancy would be better. Basically, a website load balancer or reverse proxy.  Firefox won't run faster. 

[http://www.tecmint.com/what-is-clustering-and-advantages-disadvantages-of-clustering-in-linux/](http://www.tecmint.com/what-is-clustering-and-advantages-disadvantages-of-clustering-in-linux/) is an introduction for the type of clustering you can do.

BTW, I'd bet that product link will be for something in the $10K or higher price range. Not something for a home user with old systems.  It will be more cost effective to build a faster system for $150.  It is amazing what a $500 system can accomplish these days with selected, used, specific Xeon CPUs coming off-lease.  The E5-2670 and 2660 CPUs are extremely impressive for the $70-$90/ea prices. Usually a Core i7 with similar performance runs $600-$1200.

Of course, some of the AMD CPUs were fantastic for their time.  I had an AMD 64 2000+ that completely rocked! [https://www.cpubenchmark.net/cpu.php?cpu=AMD+Athlon+64+2000%2B&id=2096](https://www.cpubenchmark.net/cpu.php?cpu=AMD+Athlon+64+2000%2B&id=2096) ... but 120 passmarks compared to a modern $60 CPU with just under 4000 passmarks is no comparison.

People are building clusters with raspberry pis.  [http://makezine.com/projects/build-a-compact-4-node-raspberry-pi-cluster/](http://makezine.com/projects/build-a-compact-4-node-raspberry-pi-cluster/) - interesting to me as a cluster trial, but a modern CPU would be both faster and cheaper.

Anyway, lots of options and knowledge out there.

---

