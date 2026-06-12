---
title: "Sun Grid Engine"
date: 2007-12-09
forum: Server Platforms
---

### Post by leeping on 2007-12-09
Dear community,

I've recently set up a small compute cluster (currently it's at 3 nodes, but soon to be 20).  There's a master node and two compute nodes; one of the compute nodes is a golden client that I use to clone the other compute nodes with Systemimager.  So far, I think I have everything working fine.

The next step is to install a queueing system that distributes computing jobs to the nodes in the cluster.  I was thinking of using Sun Grid Engine but it seems like the Ubuntu community doesn't support it.  Are there any feasible alternatives to Sun Grid Engine that is supported by Ubuntu?  Or, alternatively, could I expect to install Sun Grid Engine and not run into too many problems?

PS: Please don't mention Rocks to me.  I've been through enough pain with the Rocks installation program conflicting with my hardware that I've decided not to walk down that path... :(

- Lee-Ping, a new system admin

---

### Post by meatpan on 2007-12-10
SGE works fine on ubuntu, but I've never seen it in the repositories.  I just ran a package search at debian, and couldn't find anything.   Oddly enough, there doesn't seem to be a main ubuntu/debian package for some other major clustering systems like openPBS, condor, or cluster express.

Sun Grid engine does have a decent knowledge base, as well as some direct user support:  [http://gridengine.sunsource.net/](http://gridengine.sunsource.net/)

---

### Post by leeping on 2007-12-10
Thanks a lot for the help. :)  I'll post updates here if I run into problems during the implementation / usage.

---

