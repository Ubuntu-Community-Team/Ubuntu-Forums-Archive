---
title: "Advice Building Rackmount Server"
date: 2009-03-23
forum: Server Platforms
---

### Post by steve_c on 2009-03-23
I've never built anything quite like this before, so I need some help.

I've been given a $50k budget to build a new server to process research simulations. The simulations will be highly parallelizable through mpi and/or charmrun. My understanding then is that the biggest bottleneck will be networking between the different nodes of the server, and so I'm planning to invest a fair amount in a fast switch.

Anyone with experience in this have any suggestions/recommendations? I'm not really sure how one goes about clustering a bunch of 1U rackmount boxes into a single powerful server, so if anyone knows where I can research that as well I'd greatly appreciate it.

Also if anyone has suggestions on good places to shop for our rack units that would be great. Right now I'm just planning to buy some reasonably priced dual-proc, quad-core Xeon units from Dell with a "data center" switch from Cisco. Let me know if any of this is not the way I should be going about it.

---

### Post by BkkBonanza on 2009-03-23
I did do some research on clusters a few years back. Unfortunately exact names escape me. Google cluster server etc. That's how I started. I did find that there are tailor made linux distros available designed for running on clusters in racks headless. There are quite a few university sites where they were doing this kind of thing and there is a lot of info out there about how they did and experiences.

One thing I was suprrised by and worth exploring: google was using celerons for their massive clusters - they didn't bother with real racks, they had rows upon rows of motherboard/power supply combos all stacked up on small shelfs. Turns out that if you calculate it out celerons had better cpu cycles per dollar then high end xeons. And the more you spend on fancy boxes the less you spend on active processor cores. 

I guess it depends on your goals. If most mips/$ is the goal then you may want to look at things like that. Your network infrastructure is going to depend more on what your actually doing then on how many cpus you have. If they spend most of their time processing numbers then network use will be low. If they are pumping large data sets around then disk access and network components are going to matter more.

Personally I like the idea of rows of shelves full of lowly celerons or core duos even. Questions like routing depend so much on what you are doing that it really needs thought before going wild with cash.

---

### Post by steve_c on 2009-03-24
Yeah, unfortunately since this will most likely get housed in the University's data center I don't think they'll let me use the motherboard-on-a-shelf approach.

The machine is going to mostly be running a program called namd, which is highly parallelizable through either charmrun or mpi (mpich). My coworkers who actually run the simulations tell me that the networking between nodes is the bottleneck, so in my preliminary budget I've invested a significant chunk of money in making the cluster run on 10 Gbit Ethernet. At the moment I've managed to put 10 Dell nodes (dual proc, quad core) and a Cisco Catalyst switch in a new Dell rack enclosure and still came up slightly under budget.

I may have to invest some of that budget in someone on these forums helping me get it set up. lol

---

### Post by BkkBonanza on 2009-04-02
I was just thinking of your scenario again. I was wondering if you ever looked at using Amazon EC2 for this? If not, then it might be worth considering because you could use huge resources as you need them and not have any of the hassles of actually setting up and maintaining a cluster. You're probably set on your course already. Just thought I'd mention it. Some of their instances are quite powerful and you can allocate and use as many as you need at any time, and then not pay for them when not running simulations.

[http://aws.amazon.com/ec2/instance-types/](http://aws.amazon.com/ec2/instance-types/)

---

