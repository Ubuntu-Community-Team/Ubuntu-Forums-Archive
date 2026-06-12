---
title: "what is network requirement for ubuntu clouds, such as uec"
date: 2010-01-12
forum: Server Platforms
---

### Post by bvidinli on 2010-01-12
Hi,

can anobody tell me,
what kind of network between cloud controller and nodes, is required for a proper cloud installation?

I mean, 
Does all machines needs to be in same network, in same lan,
or may be in MAN or WAN ?

how much should be network throughput ? 
1Mbit/sec , 10Mbit per sec, or 1Gbit/sec ?

I ask because I need to know the possibility of running nodes on different locations.

Thanks.

---

### Post by munky99999 on 2010-01-12
You have to move the images from the controller to the nodes. So if you're using anything slower then fast ethernet. You will notice it quickly. Gigabit is recommended.

> I mean,
Does all machines needs to be in same network, in same lan,
or may be in MAN or WAN ?
In the cloud installation you set the range of where the nodes are. Since the nodes and controllers pretty much require 100mbit or better. You pretty much will need same subnet-lan.

If you have a capless 100mbit internet connection. You could always VPN for it... but not that recommended.

> 
I ask because I need to know the possibility of running nodes on different locations.
Essentially the biggest issue is the movement of images from node to node. If your intentions are to make use of Rocks Linux for clustering images. You pretty much wont get away with doing that over the internet. Intercommunication in clusters are usually the bottleneck.

---

