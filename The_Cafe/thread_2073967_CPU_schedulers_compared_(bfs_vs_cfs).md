---
title: "CPU schedulers compared (bfs vs cfs)"
date: 2012-10-20
forum: The Cafe
---

### Post by graysky on 2012-10-20
**Abstract**
Con Kolivas&#8217; Brain **** Scheduler (bfs) was designed to provide superior desktop _interactivity_ and _responsiveness_ to machines running it.[1]  However, it was not implicitly designed to provide superior performance.  The purpose of this study was to evaluate the Completely Fair Scheduler (cfs) in the vanilla Linux kernel and the bfs in the corresponding kernel patched with the ck1 patchset.  Seven (7) different machines were used to see if differences exist and, to what degree they scale using *performance based metrics*.  Again, these end-points were never factors in the primary design goals of the bfs.  Results were encouraging.  

Kernels patched with the ck1 patch set including the bfs *outperformed* the vanilla kernel using the cfs at nearly all the performance-based benchmarks tested. Further study with a larger test set could be conducted, but based on the small test set of 7 PCs evaluated, these increases in process queuing, efficiency/speed are, on the whole, independent of CPU type (mono, dual, quad, hyperthreaded, etc.), CPU architecture (32-bit and 64-bit), 64 bit) and of CPU multiplicity (mono or dual socket). 

Moreover, several "modern" CPUs (Intel C2D and Ci7) that represent common workstations and laptops, consistently outperformed the cfs in the vanilla kernel at all benchmarks.  Efficiency and speed gains were small to moderate.

**Link to complete study**
[http://repo-ck.com/bench/cpu_schedulers_compared.pdf](http://repo-ck.com/bench/cpu_schedulers_compared.pdf)

[1] [http://ck.kolivas.org/patches/bfs/bfs-faq.txt](http://ck.kolivas.org/patches/bfs/bfs-faq.txt)

Comments are welcomed.

---

