---
title: "Linux Limits"
date: 2007-11-06
forum: Server Platforms
---

### Post by loupy on 2007-11-06
I am hoping someone here can help me.  I am looking for documentation that states the limits of linux in terms of total# of processors, memory, etc.  I have searched everywhere and the one piece of information I have found I am unsure how reliable it is:

```
Intel x86

    * Maximum CPUs: 32 (including logical CPUs)
    * Maximum memory: 64GB
    * Maximum filesize: 8TB
    * Maximum filesystem size (ext3): 16TB
    * Maximum per-process virtual address space: 4GB

AMD 64/EM64T

    * Maximum CPUs: 64
    * Maximum memory: 128GB
    * Maximum filesize: 8TB
    * Maximum filesystem size (ext3): 16TB
    * Maximum per-process virtual address space: N/A

Please note that above are standard maximum limitations and do not get confused with Linux cluster systems, which can scale up to 1,024 CPUS.
```

---

### Post by HermanAB on 2007-11-06
It depends on how you configure it.  Linux can run on anything from cell phones to super computers...

---

### Post by loupy on 2007-11-06
I understand that it's portable.  What I am trying to find out is what the limits are  like can I run linux on a 64 processor computer with 512GB of ram and have all the processors and ram recoginized?  I would like to find out the stand alone limits - I understand that clustering is a different animal altogether.  My question is more about kernel limits not architectures supported.

---

### Post by John.Michael.Kane on 2007-11-06
> **loupy said:**
> I understand that it's portable.  What I am trying to find out is what the limits are  like can I run linux on a 64 processor computer with 512GB of ram and have all the processors and ram recoginized?  My question is more about kernel limits not architectures supported.

Yes you can run Linux/Ubuntu on 64bit with 512mb of memory. it's not an optimal configuration but it's doable.

As for The kernels theoretical limits this should help [http://www.sc.army.mil/systems.html](http://www.sc.army.mil/systems.html)

---

### Post by loupy on 2007-11-06
Thank you **SD-Plissken** that helps me quite a bit.

---

### Post by Darko-TheRaven on 2007-11-06
with limits like those why should it matter lol there huge

---

### Post by zekopeko on 2007-11-06
> **SD-Plissken said:**
> Yes you can run Linux/Ubuntu on 64bit with 512mb of memory. it's not an optimal configuration but it's doable.

As for The kernels theoretical limits this should help [http://www.sc.army.mil/systems.html](http://www.sc.army.mil/systems.html)

read what he wrote. 64 PROCESSORS and 512GB of RAM. not 64bit and 512 MB of RAM.

and yes it's 4 in the morning here and i'm stingy.

---

### Post by John.Michael.Kane on 2007-11-06
> **zekopeko said:**
> read what he wrote. 64 PROCESSORS and 512GB of RAM. not 64bit and 512 MB of RAM.

and yes it's 4 in the morning here and i'm stingy.

Well either way he is covered.

---

### Post by zekopeko on 2007-11-06
not if he plans to run "The Matrix" from home :D
i think he'll need more processors for that....

---

### Post by zekopeko on 2007-11-06
EDIT: Double Post

---

### Post by loupy on 2007-11-06
**Zekopeko** - Thanks for the chuckle.  Not planning to run the Matrix, but I've been looking at different options for work.  We have a need for heavy mathematical computations and believe it or not our current 32way proc servers take forever :)

---

### Post by steve.horsley on 2007-11-07
It may be worth looking at those PlayStation 3 clusters everyone is doing. I gather that their floating point throughput is seriously heavy duty.

---

### Post by galeron on 2007-11-08
But supposedly programming the beast to do your bidding isn't that easy, which explains why the PS3 game developers haven't really been able to maximize the potential of the Cell processor.

---

