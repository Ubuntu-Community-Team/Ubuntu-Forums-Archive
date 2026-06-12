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


---> Mods: if you feel it is more appropriate for this thread to be posted in another forum, (ie - server platform), feel free to move it!

---

