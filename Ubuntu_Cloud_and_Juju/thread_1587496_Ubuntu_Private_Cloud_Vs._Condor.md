---
title: "Ubuntu Private Cloud Vs. Condor?"
date: 2010-10-03
forum: Ubuntu Cloud and Juju
---

### Post by csharpplus on 2010-10-03
Hi There,

I am an ubuntu newbie, hence, any advice would be greatly appreciated.

Assuming one is interested to run an app (that crunches numbers...) on 20-30 different machines, where each such run, on every machine, is independent of all other runs (meaning, there is no dependency between the runs; the goal is to have a centralized location point where one can control/supervise all the 20-30 'slave' machines). 

Is there a benefit to installing (and using) an Ubuntu Private Cloud vs. using a tool like condor using Ubuntu's desktop version?

---

### Post by kim0 on 2010-10-04
Hi,
I don't really know much about condor, but if it gets your HPC job done, then I don't really think you'd gain much by switching to UEC. Basically, the main advantage to using UEC is having a virtualized infrastructure that is multi-tenant (different users) with management tools that are ec2 compatible. so you can manage and migrate the VMs like EC2. If you're the single user of a HPC cluster and you don't need virtualization or ec2 api compatibility, I don't think you'd stand to gain much.

> **csharpplus said:**
> Hi There,

I am an ubuntu newbie, hence, any advice would be greatly appreciated.

Assuming one is interested to run an app (that crunches numbers...) on 20-30 different machines, where each such run, on every machine, is independent of all other runs (meaning, there is no dependency between the runs; the goal is to have a centralized location point where one can control/supervise all the 20-30 'slave' machines). 

Is there a benefit to installing (and using) an Ubuntu Private Cloud vs. using a tool like condor using Ubuntu's desktop version?

---

### Post by csharpplus on 2010-10-04
thanks kim0, I appreciate your help.

---

### Post by obast on 2010-10-11
If condor is what I think it is, the advantage of using UEC is that UEC would enhance condor. 

[http://www.cs.wisc.edu/condor/](http://www.cs.wisc.edu/condor/)

It's sort of a pain to get everything configured with a whole bunch of machines with something like condor, and its definitely hard to tweak the config afterward. 

So you could use UEC coupled with condor by building a machine image that provided condor with a node, or a condor node of a certain flavor. You could then use UEC to dynamically change the mix of condor nodes available for work. 


So UEC would control the machine mix, and Condor would control job execution.

---

### Post by csharpplus on 2010-10-12
obast,
 
thank you so much for your help. Since setting up condor is complicated (a pain, as you say), is it possible to then UEC instead of condor?
 
Is this the best way to go for one that has many IDLE machines and want to use them for executing various jobs from within a central location?  are there any other good alternatives to this?  thank you.

---

### Post by Rusty au Lait on 2010-10-13
Before using UEC consider this. Nodes can only run on VT hardware. If you want to make use of a bunch of machines you have they must comply. Ubuntu supports many cluster servers. Most have minimal hardware requirements. I believe most virtualization servers(see forum) can run on machines not having VT capability.

---

### Post by obast on 2010-10-13
UEC is really for dedicated machines, that is, you setup some machines to be a general compute resource, and essentially, every core in that machine can then be available for processing. You could use something like gclusterFS so that all nodes can access the same set of data and so on. 

Condor on the other hand is more about the idle machines, i.e. Seti@Home or Folding@Home, though you can dedicate machines to always be available. 

But its no so much that Condor is a pain to setup, as the application you want to use may be a pain to setup. Let's say you're, I dunno, analyzing genomes. Well, each running copy of the application would probably need access to the genome, which might be say, 4GB. So to start up the processing, Condor might have to copy 4GB to the running copy so it can work on it. 



The setup costs really has nothing to do with Condor, its about the complexity of your app. Condor is just a toolkit to do some of that heavy lifting. So you would setup a job with Condor to say "I need a machine with 64 bit addressing, and 4GB of free disk space). When a node became available, Condor would farm the job out to that node. 

With Condor+UEC, some of those available nodes could be part of your UEC cluster. If you were servicing several types of internal customers, you could make different flavors of nodes available: Some with more cores, some with more disk, some with GlusterFS, etc. Then someone can submit a Condor job, Condor would figure out which of the available nodes are the best fit, and run jobs on those. Someone else could submit a different Condor job, and condor might match a different set of nodes. If all the nodes are busy, or none of the right type are available, it will queue the job and run it when they become available. 

So lets continue with my Genome example. If you have the genome mounted on a GlusterFS disk, then you can declare that as a particular kind of resource in Condor. You would have certain running instances able to access that GlusterFS disk. Then people could submit a job and request nodes with access to the "GenomeDisk". Condor would then run jobs on those nodes instead of other nodes.

So you use UEC to manage the mix of stuff in your compute cluster, then use Condor to match jobs to nodes. 

But UEC assumes non-idle machines. If you want to use only idle machines, you would have to use straight Condor. Or you can mix and match. Use UEC to manage the compute cluster machines, use regular Condor to provide raw processing without any resources.

---

