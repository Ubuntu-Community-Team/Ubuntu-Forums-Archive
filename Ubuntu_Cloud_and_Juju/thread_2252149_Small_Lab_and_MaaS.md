---
title: "Small Lab and MaaS"
date: 2014-11-09
forum: Ubuntu Cloud and Juju
---

### Post by Chris_Wolf on 2014-11-09
Hello,

I am looking for peoples opinion on setting up a a small lab. This lab has a good deal of processing power both cpu and gpu in 24 nodes but only has 4 users and the odd grad student. Currently we use a combination of apache hadoop and stand alone machines which results in a lot of wasted cycles. Ideally we are looking for one giant compute engine which runs containers and desktops as a service. My concern about moving to mass is currently we only have one network adapter in some of the machines. I believe the latest build recommends 2 in most nodes and 3 in compute nodes to reduce congestion on the important internal communications between the node. Our network is mostly 10gbit private and only the traffic of the 4 regular users.

Will MaaS work with just one adapter in some of the nodes and does anyone see any potential issues with running the cloud in this architecture?

Thanks

---

