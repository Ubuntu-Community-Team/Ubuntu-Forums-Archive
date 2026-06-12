---
title: "CPU frequency not going over stock"
date: 2011-10-18
forum: Server Platforms
---

### Post by 04blatca on 2011-10-18
Hi,
I've been running a minecraft server in Ubuntu for a while now and recently purchased a new server. 

The CPU I have is a i7 990x @ 3.47GHz

After overclocking the processor and checking the frequencies with egrep  'GHz|MHz' /proc/cpuinfo, I noticed that the CPU was still running at the clock frequency, as shown below:

```
model name      : Intel(R) Core(TM) i7 CPU       X 990  @ 3.47GHz
cpu MHz         : 3468.000
model name      : Intel(R) Core(TM) i7 CPU       X 990  @ 3.47GHz
cpu MHz         : 3468.000
model name      : Intel(R) Core(TM) i7 CPU       X 990  @ 3.47GHz
cpu MHz         : 3468.000
model name      : Intel(R) Core(TM) i7 CPU       X 990  @ 3.47GHz
cpu MHz         : 3468.000
model name      : Intel(R) Core(TM) i7 CPU       X 990  @ 3.47GHz
cpu MHz         : 3468.000
model name      : Intel(R) Core(TM) i7 CPU       X 990  @ 3.47GHz
cpu MHz         : 3468.000
model name      : Intel(R) Core(TM) i7 CPU       X 990  @ 3.47GHz
cpu MHz         : 3468.000
model name      : Intel(R) Core(TM) i7 CPU       X 990  @ 3.47GHz
cpu MHz         : 3468.000
model name      : Intel(R) Core(TM) i7 CPU       X 990  @ 3.47GHz
cpu MHz         : 3468.000
model name      : Intel(R) Core(TM) i7 CPU       X 990  @ 3.47GHz
cpu MHz         : 3468.000
model name      : Intel(R) Core(TM) i7 CPU       X 990  @ 3.47GHz
cpu MHz         : 3468.000
model name      : Intel(R) Core(TM) i7 CPU       X 990  @ 3.47GHz
cpu MHz         : 3468.000
```

After some research, I found that cpufreq was limiting the CPU frequency after running: cat /sys/devices/system/cpu/*/cpufreq/cpuinfo_max_freq.

What's the best way to change the max frequency for the CPUs? Or is that something completely different? Any help would be appreciated here.


Thanks in advance
-04blatca

---

