---
title: "Hardware question"
date: 2012-04-07
forum: Server Platforms
---

### Post by Robert Finley on 2012-04-07
I have an HP DL360 G4.  It has a couple of 3.4Ghz processors, these I believe: [Link]("http://ark.intel.com/products/27085/64-bit-Intel-Xeon-Processor-3_40-GHz-1M-Cache-800-MHz-FSB")

My question is why does Ubuntu see 4 processors?

---

### Post by jerrrys on 2012-04-07
Hyperthreading on?

---

### Post by Robert Finley on 2012-04-07
> **jerrrys said:**
> Hyperthreading on?

Yes

---

### Post by jerrrys on 2012-04-07
That will make 1 core show as two physical cores and two cores as 4.  Is that whats going on?

---

### Post by Robert Finley on 2012-04-07
> **jerrrys said:**
> Hyperthreading on?

Ok, yeah I do have hyper-threading and now that you pointed that out, and I've gone and read about what that actually means, I get it.  Thanks.

---

### Post by jerrrys on 2012-04-07
Your welcome

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by hawkmage on 2012-04-07
Hyper threading the a is basically a dual set of CPU registers each of which allows for keeping track the execution context of a process even through there is only one core to execute on.  This allows for very fast execution context switching so that you can have an executing tread for each of these context so to the OS it looks like there are multiple cores per CPU.  

Hyper threading is not as efficient as actually having two cores so an modern OS will detect the differenace between a true CPU and a hyper threading CPU and will try to schedule threads on separate physical CPUs instead of on the one.  Linux has had this in the kernel for a while.

---

