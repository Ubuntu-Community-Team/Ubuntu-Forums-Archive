---
title: "Cloud and virtualization"
date: 2009-09-25
forum: Virtualisation
---

### Post by scheeri on 2009-09-25
Dear Community!

Can anyone describe me, how will be a cloud 100% fail tolrant?

Is this true? One cluster controller and five phisical node controller can be, a super server, on which you can define several virtual machines.

But what will be happen, when a phisical node controller will be crashed?
How will be managed virtual machines, wich phisicaly ran on the crashed
node controller?

Thanks for your answers
Best Regards

---

### Post by openfly on 2009-09-25
Well scheeri,

   It depends on what you mean here.  If you are talking about things like VMWare VMotion ( and other high availability solutions ) you would basically define a cluster to exist across multiple physical datacenters and allow for cluster failover to occur between ESX hosts in that cluster.

   In a major organization that's made possible by gobs of bandwidth and proper infrastructure.

   Other approaches would be for applications and services being served to be massively paralleled.  In effect you would be load balancing applications across many virtual machines and servers in a sort of ad hoc n+1 configuration.  In this situation something like a datacenter failing over would likely trip some alerts or raise utilization / load on the remaining datacenters to a point where a datacenter automation solution such as opsware would start to provision new systems based off of that massively paralleled build.  Those new systems would be automatically brought into the pool of available resources and reduce the stress on the remaining datacenters.

   In a situation like that you would be relying on a fault tolerant automated provisioning / management solution.

   The point is, there's multiple ways to approach the situation.  Depends at what layer you want to abstract your hardware from your software.

---

### Post by scheeri on 2009-09-27
Dear openfly!

At first, thanks for your answers!

When I understand, the my situation can be the next:
[IMG]http://www.scheer.hu/images/cloud.jpg[/IMG]


1. The nodelan1 will be a complete cluster, and the nodelan1 will be a complete cluster.

2. So if I want, I can start 2 virtual machines by Letters.nodelan1 on .nodelan1 cluster. So there will be 2 vm's with very high perfomance,because these will be ran on 5 phisical server. When Beta.nodelan1 server will be crashed, the 2vm's will run without stopping time on the other nodelan1 servers with high performance too.

3. For example on the cloud.controller I have 2 several vm's: 1 database server vm and 1 application server vm. I need for nodelan2 because I can start only one type (database or application) of vm's in same time.
Or not? Why I need a second cluster in a node? What's the role in this environment of the nodelan2 cluster?

4. What will happen with nodelan1, when the letters.nodelan1 server will be crashed? Will the animals.nodelan2 works instead of letters.nodelan1? I think will not.


5. What will happen with nodelan1 and nodelan2, when the cloud.controller server will be crashed? I think, I can't start new vm instances on cluster, but the nodelan1 and nodelan2 clusters will work. Or not?


Please explain these situation for me.

Thank You & Best Regards

---

### Post by openfly on 2009-09-28
I don't know what specific technology you are using.  I can't give you an accurate description, as there are several unique approaches to providing the availability you are asking about.

However, as to a point of clarification.  A cluster is not so much a cloud.  A cluster ( there are various types that can differ a great deal ) is simply a number of delineated machines or hosts that are working together to accomplish some task beyond their own individual compositions.  A "cloud" is an abstraction of resources available at any time from anywhere. 

The idea of the cloud is built around the premise that the physical hardware ultimately should be completely abstracted from the software.  Some of the technology employed in that is virtualization, automation, and high availability technologies.  In that regard, a cloud could have 1 cluster or 20000 clusters it would be irrelevant.

However, in terms of providing your now abstracted cloud with the resources it needs to stay up means taking into account resource availability in your physical hardware pool.  That means paying attention to physical failover needs, resource utilization, and statistical growth models.  Your cloud fails if it grows beyond what the hardware it rests upon can support.

So, having multiple clusters could simply be a function of offsite databackup.  Having master controllers may or may not require full redundancy in the controller depending on the design, but it would be my guess that you would want multiple controllers.

---

