---
title: "Running program on it's own core"
date: 2008-03-10
forum: Server Platforms
---

### Post by Sir Jake on 2008-03-10
To start off I am running ubuntu 7.10 server 64bit with ubuntu-desktop installed on it. As I am still new to linux.
The servers I run only use single core, so I need to know how to setup them to run on their own core.  system specs are two quad core xeons.
So I have 8 cores and I'm not sure how to get my program to run on it's own core.
Also not sure if you can or if it's recomended to have ubuntu itself run on it's own core.

Thanks very much for any help.

---

### Post by craigp84 on 2008-03-10
Hi Sir Jake,

> The servers I run only use single core

I'm not 100% sure i follow, but i think you're saying that the services you're running are single threaded and can only use 1 core at a time? Rather than you have an 8 core box, but only one core appears in /proc/cpuinfo?

If it is the latter, switch to an SMP kernel, but i'm fairly sure you meant the first :)

> I need to know how to setup them to run on their own core

While it's possible to set a processor affinity mask for each process, and this would tie the process to a specific, or a set of specific processors, it's generally not a good idea to do this.

Performance of each of the services will actually degrade if you do this.

As an example, we have some very compute intensive processes at my work which we run over a large compute farm. We fan them out 1 process per CPU, and with 4 or 8 cpus per compute node that's 4 or 8 processes per blade. As an experiment i wrote a tiny wee C app to set the processor affinity (there's not tools in the standard redhat distro to do this unlike the prset functionality of solaris) of a given PID.

After constraining each process to it's own CPU, the number of work units completed per hour actually dropped significantly.

I think the only valid reason for doing this kind of constrainment would be in the case that a dept only paid for say 3 cores of a 4 core host and you wanted to ensure they didn;t breach their share.

Hope this helps,

-c

p.s. i can dig out that C code i wrote after reading the man pages if you want to go ahead with your own tests anyway

---

### Post by Sir Jake on 2008-03-10
Hey thanks for the reply what I ment was the services I am running are not a multithreaded application.  I heard someone talk about taskset or something like that.

---

