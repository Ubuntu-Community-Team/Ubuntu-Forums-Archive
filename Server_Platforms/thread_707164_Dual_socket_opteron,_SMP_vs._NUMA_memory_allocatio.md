---
title: "Dual socket opteron, SMP vs. NUMA memory allocation"
date: 2008-02-25
forum: Server Platforms
---

### Post by remi_2 on 2008-02-25
Hello everyone!

My company is considering building a dual-socket 2*dual-core opteron machine (4 cores, 2 per socket) with 32 gigs of ram (16 Gigs per socket).

I'm wondering if on such a machine, the two 16 gigs memory banks would be actually handled as a single pool of 32 Gigs by the linux kernel present in Ubuntu 7.10.


I've read some papers and posts about SMP vs NUMA memory schemes, 

I'm puzzled because a dual socket opteron setup is advertised as a NUMA architecture, yet a linux SMP kernel seems to be able to run on such a machine, supposedly linux 2.6 is NUMA-aware ?

will that mean that a single program running on socket 1 would be allowed to access memory handled by the socket 2 cpu?

Thanks for any light you can bring on that dark topic

---

### Post by astrotech226 on 2008-02-25
If you bought an AMD server that was NUMA capable, I'm fairly certain you can still access the ram in a standard SMP fashion where each process has a bank of 16G.

I think the difference with NUMA is that you are asking the front of the bus (that can see all 32G) for information.  So ram access might be a little slower as the number of CPUs increases.

I've not tried NUMA myself, but have read others have done it in Ubuntu 7.04 64bit.  I would imagine 7.10 would work fine as well.

---

### Post by remi_2 on 2008-02-25
Hi astrotech226,

thanks for showing interest!


It looks like userspace NUMA support under linux is implemented through numactl, which somehow allows a user to run a process tying it to a certain CPU and giving priority to the local memory bank instead of a distant one upon allocation.

Yet I'm still unsure wether the whole 32gigs would be accessible by a single process.

I guess I'd have to ask the kernel devs directly on that topic, but I can't seem to find the entry point on kernel .org.


The machine has not been bought yet.

Thanks!

---

### Post by astrotech226 on 2008-02-25
If you do proceed with this, please post your results because I'd love to know if it works or not.

My gut tells me that when you get the NUMA stuff working correctly, a single process will definitely have access to the full 32G.  Can you tell me what you need 32G for?  This going to be a database server?

---

### Post by remi_2 on 2008-02-25
I'm not allowed to say much about it,  but basically its for running a SAT/SMT solver on a huge model.

If you want to know what's a SAT or SMT solver you can have a look here :
[http://en.wikipedia.org/wiki/Boolean_satisfiability_problem](http://en.wikipedia.org/wiki/Boolean_satisfiability_problem)
[http://en.wikipedia.org/wiki/Satisfiability_Modulo_Theories](http://en.wikipedia.org/wiki/Satisfiability_Modulo_Theories)

These can be worth the read too :
[http://research.microsoft.com/~leonardo/fmcad06.pdf](http://research.microsoft.com/~leonardo/fmcad06.pdf)
[http://fm.cs.uiuc.edu/talks/060406/slides.pdf](http://fm.cs.uiuc.edu/talks/060406/slides.pdf)

These solvers are used to verify properties of software or hardware systems, or any other system you can model using boolean algebra and linear rational/integer arithmetic.

I'll report on the experiment when its done !

:guitar:

---

### Post by remi_2 on 2008-02-27
now we have a choice between 

- a dual socket opteron 2222 machine with 32Gigs of RAM
- a dual socket XEON  5160 machine with 32Gigs of RAM


If I'm not mistalen the opteron machine qualifies as a NUMA architecture, whereas the XEON qualitfies as a SMP architecture.

Yet I recall reading some  post on a site I do not remember, that the newer XEONs had their on-chip dedicated memory controller just like the opteron do,
in which case the XEON machine would qualitfy as a NUMA architecture as well :confused:

---

### Post by astrotech226 on 2008-02-27
About two years ago, I switched to using AMD exclusively.  I love my Opterons.

It doesn't sound like your application is going to matter, but I've read that AMD processors/boards handle interrupt requests much more efficiently then the Xeon equivalent.  This is a big deal when dealing with highly IO intensive boards like the ones from Digium that handle voice T1/PRI circuits.

Not to mention, the Opterons are usually cheaper by quite a bit compared to the same speed Xeon.

Anyway, I doubt this helped much :)

---

