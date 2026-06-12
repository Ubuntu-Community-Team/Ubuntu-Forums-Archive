---
title: "can a private cloud do this?"
date: 2010-11-10
forum: Ubuntu Cloud and Juju
---

### Post by Morlok8k on 2010-11-10
I would like to know if the cloud can do the following setup:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=175253&stc=1&d=1289427635[/IMG]

---

### Post by marrusl on 2010-11-10
Hi Morlok8k,

If I'm reading your document right, no I don't think you can do that.  From what I can tell from the diagram, you want to have your Node Controller (NC) servers be virtual nodes on a single huge physical server.

However, UEC is based on KVM virtualization, which requires hardware virtualization support (Intel VT or AMD SVM) which can't be passed through to your virtual servers.  In any case, even if you could, your cloud instances would be nested, i.e. virtual machines running within other virtual machines.  The performance would probably be terrible.

The front end components (CLC, CC, SC, Walrus) can be virtual, but NCs should be installed on bare metal.

Regards,
Mark

---

### Post by kim0 on 2010-11-11
Hi Morlok,

My understanding is that you want to seamlessly "merge" all node controller into one large virtual computer. Basically the answer is "no", no software in the world can do that.

A more detailed answer is, you may be able to merge storage using software like gluster or ceph (most of which is next gen and not quite mature now), for CPU/RAM it can never be seamless and hidden, however if you write your application to make use of multiple nodes the end result can be very similar to what you describe. What I am saying is that if you application is specifically coded to make use of multiple computers, it will become faster and you can do what you describe. BUT if you get a legacy app or game like Quake3, that achieves 60FPS on one node, and expect it to achieve 180FPS on this cloud virtual super-computer, the answer is no that cannot happen

---

### Post by Morlok8k on 2010-11-11
> **marrusl said:**
> Hi Morlok8k,

If I'm reading your document right, no I don't think you can do that.   From what I can tell from the diagram, you want to have your Node  Controller (NC) servers be virtual nodes on a single huge physical  server.

However, UEC is based on KVM virtualization, which requires hardware  virtualization support (Intel VT or AMD SVM) which can't be passed  through to your virtual servers.  In any case, even if you could, your  cloud instances would be nested, i.e. virtual machines running within  other virtual machines.  The performance would probably be terrible.

The front end components (CLC, CC, SC, Walrus) can be virtual, but NCs should be installed on bare metal.

Regards,
Mark

nope you have this backwards - i want a large server from smaller ones

> **kim0 said:**
> Hi Morlok,

My understanding is that you want to seamlessly "merge" all node controller into one large virtual computer. Basically the answer is "no", no software in the world can do that.

A more detailed answer is, you may be able to merge storage using software like gluster or ceph (most of which is next gen and not quite mature now), for CPU/RAM it can never be seamless and hidden, however if you write your application to make use of multiple nodes the end result can be very similar to what you describe. What I am saying is that if you application is specifically coded to make use of multiple computers, it will become faster and you can do what you describe. BUT if you get a legacy app or game like Quake3, that achieves 60FPS on one node, and expect it to achieve 180FPS on this cloud virtual super-computer, the answer is no that cannot happen

seamless is taking it a bit far (i dont expect the ram to be shared between nodes for example), but i would like to run a program where i can specify the number of threads (all it does is get a file, reads it and compiles a new file based on it and its surrounding files). currently i specify the number of threads based on the processor i have (2 threads for a dual core, etc.).  so i would like multiple computers taking part in this, so by specifying 12 threads would use 4 cores on each of the 3 computers.

parallel computing or grid computing is more of what i'm looking for, as this program is "embarrassingly parallel".  it doenst matter which files are done first, as long as they all get done.

are there any distros/software that are publicly available that are made for parallel computing?  or any info that would help me get started?

---

### Post by marrusl on 2010-11-11
Ah, now your diagram looks perfectly clear to me.  :)

Have you looked into Hadoop at all?

One of the best things Hadoop does for you is take care of all the parallelization.  Hadoop is closely tied to the concept of "MapReduce" but it doesn't have to be.  Using Hadoop Streaming, you can parallelize pretty much any program or script as long as it reads from stdin and writes to stdout.

---

### Post by kim0 on 2010-11-12
Indeed hadoop might be an option, or since you say the problem is embarrassingly parallel, why wouldn't you write a script that:

1- Takes the input file, splits it into N units
2- launches N virtual servers on UEC
3- starts your crunching app on each virtual server
4- concatenate N outputs into the final one

Or some variation of the above

---

