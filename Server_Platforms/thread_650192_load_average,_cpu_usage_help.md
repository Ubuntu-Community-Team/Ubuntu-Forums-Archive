---
title: "load average, cpu usage help"
date: 2007-12-26
forum: Server Platforms
---

### Post by mbradlcu on 2007-12-26
Hi all,
could someone explain (in simple terms) why often times a system can have a very high load average >5, but top will show no processes using <%2 cpu?.. all the sites that have described load average by running a loading program run (as I would expect) very high in 'top' with cpu usage.
O, and if anyone could illustrate with a simple shell script that would be very cool!
thanks!

---

### Post by tgalati4 on 2007-12-26
Sometimes there are I/O waits that show up in top and that will cause the load to rise (# of processes waiting to be processed).  During these I/O waits, there is really nothing for the CPU to do so the CPU % goes down, but load continues to rise.  

A good example of this is copying large files from one disk to another, or from one machine to another.  The buffering and transfer of data is bound by the I/O transfer speed of the disk, yet the processor has little to do.  Loads can rise quite high during these transfers, but CPU may be 5%.

---

