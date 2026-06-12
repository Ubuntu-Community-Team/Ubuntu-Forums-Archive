---
title: "Need help debugging performance problem on a grid"
date: 2005-11-16
forum: Server Platforms
---

### Post by vinjvinj on 2005-11-16
I have about 10 servers running as a compute grid. I have a scheduler that breaks job into smaller portions on each of the servers. There are two machines which run a lot slower than the other servers. 

Is there any way I can debug the performance problem on my servers? These servers start up loading about 1 gig of data from a NFS disk into memory. They are written in python and do a lot of processing. I'm thinking it is something to do with memory. All the servers are built from the same disk image so I'm thinking it is a hardware problem of some sort. 

What tools can I use to get a performance overview. Even better is there any hardware benchmark that I can run on all the machines and find out which ones are slower.

---

### Post by spade_shark on 2005-11-19
First let me say this is SWEEEEEEEEEEEEEEET.  Clusters are cool or maybe not so cool :D .    

[http://www.rocklinux.org/](http://www.rocklinux.org/) 
and of course [https://wiki.ubuntu.com/UbuntuOnCluster](https://wiki.ubuntu.com/UbuntuOnCluster)  not much here. 
 
Benchmarking... try the LINPACK testing.  Maybe look at this " High performance Linux clustering, Part 2: Build a working cluster  " [http://www-128.ibm.com/developerworks/linux/library/l-cluster2/]("http://www-128.ibm.com/developerworks/linux/library/l-cluster2/")

Wouldn't it be great to get a Ubuntu cluster in the top 500 list?  FYI the current number one seat has something like 131,100 processors and 33,000 GB of ram.  IBM rules.   [http://www.top500.org/lists/2005/11/basic]("http://www.top500.org/lists/2005/11/basic")

Keep us posted on you LINPACK results! :cool:

---

