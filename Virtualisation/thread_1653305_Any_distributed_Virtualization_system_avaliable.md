---
title: "Any distributed Virtualization system avaliable?"
date: 2010-12-26
forum: Virtualisation
---

### Post by mxu on 2010-12-26
I just wonder if there is any vm system that can run one vm over  multiple computers, and the guest system sees a single computer with  memory and CPU number that is sum of all physical computers. 

The reason why I look for such virtualization is..  basically I do scientific computing, which often need tens of GBs of  memory and hundreds of processing units. To parallelize this computation  over multiple computers, I have to either separate the whole task into  independent jobs or do some MPI programming. On the other hand, if the  whole job was performed on a single physical computer with multiple  processing cores, I can do multithread programming, which is much much  easier to handle and much more flexible. To my understanding,  visualization hides physical details (to some extents) from users. If  there could be a single VM over multiple physical machines (these  machines are homogeneous), based on sufficiently efficient scheduling of  memory and processor resources, then many many multi-thread programs  that were designed for a single multi-core physical computer immediately  become distributed programs. 

I just found there are Java Virtual Machines of this kind:

[http://en.wikipedia.org/wiki/Terracotta_Cluster](http://en.wikipedia.org/wiki/Terracotta_Cluster)

I am not familiar with the field of virtualization.  Could anyone give any hints?

---

### Post by HermanAB on 2010-12-27
VMware has a cloud system.

It basically changes a bunch of cheapish servers into a mainframe.

---

### Post by mxu on 2011-01-03
Thanks Herman. I'll look at it.

> **HermanAB said:**
> VMware has a cloud system.

It basically changes a bunch of cheapish servers into a mainframe.

---

