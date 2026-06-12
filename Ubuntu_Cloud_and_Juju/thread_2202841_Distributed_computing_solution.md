---
title: "Distributed computing solution"
date: 2014-01-31
forum: Ubuntu Cloud and Juju
---

### Post by Russell_Reid on 2014-01-31
I need some advice on if ubuntu cloud is the right solution for our needs.  We have several windows applications that can benefit from having more cores available to compute.  We do 3D rendering (using Autodesk Max), acoustics modeling (using Ease Aura, and EAW Resolution) and may have some others in the future.  Currently, we do our distributed 3d rendering on 9 dedicated server machines running windows os and mental ray nodes and the acoustics modeling on single workstations or a single node of the render server farm.  I would like to be able to combine these dedicated servers in a more flexible manner by clustering them and running a windows vm on top of the cluster to spread the computing load of all of these apps over more cores than is possible on a single machine or to deploy multiple render nodes to speed up the 3d rendering process when we are rendering animations instead of single images.  

I have looked at kerighed, beowulf, hadoop, Microsoft HPC, etc.  But i know Ubuntu server well and would like to know if Maas and Ubuntu cloud would be a viable solution for this. I would put Maas on all of the physical servers and then run ubuntu cloud on top.  Then i would deploy windows VMs with whatever resources (CPUs) are necessary for the individual need.  

Am i on track or not? 

Thanks.

---

### Post by thnewguy on 2014-03-04
This sounds like a lot of extra work and additional layers of abstraction just to run a handful of Windows servers. Sure, a cloud solution might be flexible, but if you are only using nine Windows servers, adding cloud and VMs into the mixs seems like more solution than you need. If your applications can make use of more cores, wouldn't it make more sense to spend your time/energy upgrading the CPUs of the Windows servers?

---

