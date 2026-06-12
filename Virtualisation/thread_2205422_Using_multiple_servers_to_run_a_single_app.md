---
title: "Using multiple servers to run a single app?"
date: 2014-02-13
forum: Virtualisation
---

### Post by Nightcreeper on 2014-02-13
I was wondering, if through cloud architecture or MAAS, if I get 14x Blades in a blade rack, and start a private cloud, can I use the computing power of all 14 machines to run a single instance of a program across all of them? I did not know where to post this so I figured that virtualisation would be the best place, as I want a "virtual server" spanning across multiple real servers. Is this possible? Would the Ubuntu Server Cloud Distro be the ticket to accomplishment?

---

### Post by tgalati4 on 2014-02-14
Perhaps describe what this application would do.  It's possible, but programming an app to use multiprocessing is non-trivial.  You need to create threads to solve parts of a problem that get spun out to separate cores and then recombine the parts to create a whole answer.  This is called [decomposition]("http://en.wikipedia.org/wiki/Decomposition_%28computer_science%29") and only a few problems can really be solved this way.  Rendering, video and audio processing, or any problem with lots of repetitive computation can be recast to use multiple cores.  Using these cores across machines (blades) causes extra overhead and again such programming in nontrivial.  Now you have to set up a [cluster]("https://help.ubuntu.com/community/MpichCluster") to span across the blades to process the workload.

---

### Post by TheFu on 2014-02-19
"Cloud" workloads usually need straight through processing. Request file - store file ... that sort of thing. Not really hundreds of CPUs needed for a single task.

However, if you want to parse out the workloads as tgalati4 says (which is correct, BTW), then look into clustering like Beowulf clustering, grid computing and supercomputing workloads. It gets extremely complicated and for most business workloads, just isn't needed.  If you aren't planning to have 200+ cores working on a single problem then this added complexity probably isn't worth the effort.

Also ... for some specific math problems, learning CUDA and leveraging 500+ cores on a GPU can be highly cost effective, but Amazon isn't likely to have GPUs in any of the servers.

I hope this makes sense.  What is the problem to be solved?

---

### Post by Nightcreeper on 2014-04-22
Sorry, been out of pocket for a while.

I wanted to setup a personal cloud, and then use "All" of the associated processing power to run say ESXi on and then run virtual machines on. That way it would be transparently Up-Scaled or Down-Scaled without much effort. I guess what I am trying to say is I was wondering if I could use an "entire cloud" as one really powerful computer. Does this make sense?

---

### Post by tgalati4 on 2014-04-22
No, it doesn't make sense.  You can run hundreds of virtual machines on your blades, but they will still be separate instances.  You need a cluster framework to tie them together to accomplish one purpose.

A 14-blade rack is essentially a super computer.  To use it efficiently requires quite a bit of effort.  If you want to set up your own cloud-provisioning service on it then look into service orchistration--an abstraction of services where you don't care (or don't know) where the service is actually running.  

[https://help.ubuntu.com/community/UbuntuCloudInfrastructure](https://help.ubuntu.com/community/UbuntuCloudInfrastructure)

[https://help.ubuntu.com/community/Orchestra/Juju](https://help.ubuntu.com/community/Orchestra/Juju)

I do not know of a way to run a virtual machine host (such as Xen or ESXi) across blades.  Maybe IBM has a framework for such service.

---

### Post by TheFu on 2014-04-23
No, I agree with tgalati4, it doesn't make sense with the technology available today.  To do what you want requires extremely specialized programs - usually created by huge corporations or universities. These programs are built to solve extremely specific problems, not for general purpose uses. The reasoning is that interconnections between different computers are 1,000,000 slower than when those CPUs are inside the same system.  Normal network connections simply have too much overhead for this to be productive.  Even 10G networking is way, way, way, way too slow.

---

### Post by Nightcreeper on 2014-04-23
So, basically:
1) A Beowulf cluster wouldn't do what I am after?
2) If it did the performance gains from many computers making a Supercomputer for "Normal" Processing would be over-ridden due to the Networking backbone being a massive bottleneck?

---

### Post by TheFu on 2014-04-25
There aren't **any** performance gains for most end-user programs by using multiple CPUs. A few will use 2, perhaps 3 cores. Video transcoders can spawn threads, but those need to be synchronized.  Servers can make more use of more cores for specific applications, things like web crawlers and DBMS ... stuff that normal end-users just don't do.  Program performance is NOT just CPU.  It is storage, caching, RAM, and if multi-threaded, communications between threads.  

There is lots and lots of information about this online.  Computer science coursework covers this. You can find that online at Stanford, MIT an other places.

I'm dropping from this thread.  NO is the answer.

---

