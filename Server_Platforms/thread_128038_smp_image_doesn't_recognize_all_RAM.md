---
title: "smp image doesn't recognize all RAM"
date: 2006-02-10
forum: Server Platforms
---

### Post by awynne on 2006-02-10
Hi,

I am running a dell poweredge 1850 with two Xeon procs and 4GB RAM.  The BIOS recognizes all the ram.  I installed ubuntu 5.10 then upgraded my kernel to linux-image-2.6.12-9-686-smp.  Doing a cat /proc/meminfo shows: "MemTotal:      3370568 kB", when I expect it to show alot closer to 4GB. 

Do I need to compile a kernel from scratch?  If so, what option will allow the OS to access all the ram?  Any help is appreciated!

Thanks

---

### Post by awynne on 2006-02-10
setting HIMEM option to 64GB allows the system to see all 4GB, but setting to 4GB does not.  a little weird, but that was the solution.

---

### Post by ariek on 2006-02-10
I had exactly the same problem with a PowerEdge 1850, with 6Gb RAM. I used the AMD64 cd instead of the i386 cd, and it worked.
After this I installed the K8-SMP package, which gave me SMP back.
Hopefully this wasn't a foolish thing to do...

---

### Post by awynne on 2006-02-10
I don't know if that will cause problems for you.   At any rate, it wasn't hard to recompile the kernel to include HIMEM=64GB.

---

