---
title: "bad scheduling on Nehalem?"
date: 2010-02-25
forum: Server Platforms
---

### Post by jandersonlee on 2010-02-25
I'm running Ubuntu Server 9.10 on a dual socket X5550 platform with hyperthreading disabled.  There should be 8 cores available for running processes: dual-socket, quad-core. When I start 8 single-threaded, cpu-intensive processes running, top shows six processes running at 100% and two at 50% (presumably sharing the seventh core).  No other processes are reported as having >1% cpu, and yet the 1-minute load average is listed as over 11.0?!

1) Why is it not running each process on its own core?

2) Why is the load average so much greater than 8?

3) Is there anything I can change in the configuration to fix this?

Thanks

Jeff Anderson-Lee

---

### Post by jandersonlee on 2010-02-25
If I use sched_setaffinity on each process I can get it to put each job on a separate core, but doing so within the batch system we have would be a pain.  Why is the default scheduling algorithm "reserving" a core?

---

### Post by Vegan on 2010-02-25
I would suggest enabling the hyperthreading and ignore the CPU scheduling and simply let the kernel assign threads as needed.

The Linux kernel is pretty well able to use the CPU very efficiently.

---

### Post by jandersonlee on 2010-02-25
> I would suggest enabling the hyperthreading and ignore the CPU scheduling and simply let the kernel assign threads as needed.

I started out that way (HT on) but found that even then running 8 CPU-intensive processes I get a load average of around 12.  I do get the jobs mapped to "separate cores", but I don't know if they are truly independent cores or if some are hyperthreads of the same core.  For the CPU/memory intensive code that I have it makes a big difference in throughput so I'd like to be sure.

---

