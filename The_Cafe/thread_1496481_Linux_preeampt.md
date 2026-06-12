---
title: "Linux preeampt"
date: 2010-05-29
forum: The Cafe
---

### Post by danlo8600 on 2010-05-29
Hi, I have a little question about a new kernel.
I have installed on my kubuntu 10.04 the deb file called:
linux-image-2.6.32-22-preempt and linux-headers-2.6.32-22-preempt

What is this, what change from the genric kernl?

Thanks all for help 
and sorry for my bad english. :D

---

### Post by Phrea on 2010-05-29
[http://packages.ubuntu.com/lucid/linux-image-preempt](http://packages.ubuntu.com/lucid/linux-image-preempt)

Apparently it's a "Linux kernel image for Low Latency Servers."

---

### Post by red_Marvin on 2010-05-29
Simply put, you do have a lot of threads (code) that run on the computer, and since you probably have more threads than cores, you need a scheduler that manages which thread gets to run when.

If the scheduler can switch away a running thread *before* the thread states it is done, in order to run another thread for a while, it is called preemptive multitasking.

Kernel preemption is that even kernel threads (pretty low level system stuff) can be preempted.

[http://en.wikipedia.org/wiki/Computer_multitasking#Preemptive_multitasking.2Ftime-sharing](http://en.wikipedia.org/wiki/Computer_multitasking#Preemptive_multitasking.2Ftime-sharing)
[http://en.wikipedia.org/wiki/Preemption_%28computing%29](http://en.wikipedia.org/wiki/Preemption_%28computing%29)
[http://en.wikipedia.org/wiki/Kernel_preemption](http://en.wikipedia.org/wiki/Kernel_preemption)

---

### Post by ssj6akshat on 2010-05-29
[http://en.wikipedia.org/wiki/Preemption_(computing](http://en.wikipedia.org/wiki/Preemption_(computing))
:)

---

### Post by Shining Arcanine on 2010-05-29
> **Phrea said:**
> [http://packages.ubuntu.com/lucid/linux-image-preempt](http://packages.ubuntu.com/lucid/linux-image-preempt)

Apparently it's a "Linux kernel image for Low Latency Servers."

Ubuntu traditionally has never had a preemption aware kernel. This is a nice change. The preemption aware kernel is ideal for a low latency desktop (i.e. one without lag). Server performance will likely suffer from it, because servers focus on throughput, not latencies.

---

