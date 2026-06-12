---
title: "Ubuntu 22.04 real time kernel and &quot;hiccups&quot; results"
date: 2022-06-23
forum: Ubuntu, Linux and OS Chat
---

### Post by adibaccoks on 2022-06-23
I installed the realtime kernel 5.15.0-1009-realtime on Ubuntu 22.04 and I did some experiments with "hiccups" ([https://github.dev/rigtorp/hiccups](https://github.dev/rigtorp/hiccups)) on isolated cores, I also set the the irqaffinity to avoid disturbing the isolated cores.  I expected better results compared to a normal kernel but it seems that the max interruption on a 2 minutes run is always around 20-30 microseconds.

I also repeated the tests with "osnoise tracing" available in this kernel but the results are similar.

Shouldn't the realtime kernel be better than a non-realtime one?

What am I doing wrong?

These are the results:


 ```

root@penguin# sudo taskset -c 48 ./hiccups -r 120 | column -t -R 1,2,3,4,5,6

cpu       threshold_ns      hiccups     pct99_ns      pct999_ns      max_ns
 48                      352     120067           2161              2303        20099

```
These are the boot options:

```
GRUB_CMDLINE_LINUX_DEFAULT="default_hugepagesz=1G hugepagesz=1G hugepages=64 hugepagesz=2M hugepages=1024 intel_iommu=on iommu=pt pci_pt_e820_access=on tsc=reliable clocksource=tsc mce=off mitigations=off intel_idle.max_cstate=0 processor.max_cstate=0 intel_pstate=disable audit=0 rcu_nocb_poll nosoftlockup irqaffinity=0-2,28-30 isolcpus=nohz,domain,3-27,31-55 nohz_full=3-27,31-55 rcu_nocbs=3-27,31-55 kthread_cpus=0-2,28-30"
```

---

