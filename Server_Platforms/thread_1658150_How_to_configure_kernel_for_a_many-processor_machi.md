---
title: "How to configure kernel for a many-processor machine (32 cores)?"
date: 2011-01-02
forum: Server Platforms
---

### Post by beepyou on 2011-01-02
I have Ubuntu 10.10 Server installed on a 32 core machine(quad AMD Magny Cours 6128 ), and I was wondering what kernel configuration would optimize its performance?

So far, I have only found the obvious configurations that are checked off:
1) Processor type and features ---> Support for big SMP systems with more than 8 CPUs
2) Processor type and features ---> Maximum num of CPUs
3) Multi-core scheduler support

Is there anything else I should consider? 

I plan on running multi-threaded programs with moderate amount of inter-processor communication, shouldn't there be some options related to the shared memory? 

Thanks!

---

### Post by samosamo on 2011-01-02
If I were you, I would just leave everything at defaults.  Make sure the OS can see all 32 cores by doing "cat /proc/cpuinfo" or similar, and then do some performance testing of your applications. Come back only if you are not happy with the results.  Something tells me you'll be happy though.

---

### Post by beepyou on 2011-01-02
well, I am unhappy with the result, my program does not scale beyond 2x threads. I do see all 32 cores and the memory is fine.

I know there may be algorithmic issues, but I was wondering if there are any "common" tweaks people do on the OS side that could help?

---

### Post by Vegan on 2011-01-02
The number of cores used is determined by the application as well as the OS.

---

### Post by beepyou on 2011-01-03
> **Vegan said:**
> The number of cores used is determined by the application as well as the OS.

Thanks. 

I can control how many threads I spawn and through thread_affinity I can control which which physical core each thread gets executed on. 

I'm interested to see if anyone has done any kernel related optimizations.

---

