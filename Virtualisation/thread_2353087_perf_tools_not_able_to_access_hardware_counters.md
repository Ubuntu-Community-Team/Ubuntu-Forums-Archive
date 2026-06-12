---
title: "perf tools not able to access hardware counters"
date: 2017-02-18
forum: Virtualisation
---

### Post by kcriswell on 2017-02-18
I'm not sure if I am asking this on the correct forum section. Please correct me if I need to ask it elsewhere.

I am running Ubuntu desktop on my Intel Joule.

When I run perf tools with the following flags, I receive a <not supported> notification in my output file:
dTLB-load-misses
dTLB-store-misses
iTLB-load-misses
LLC-loads
LLC-load-misses
LLC-stores
LLC-store-misses
L1-icache-loads
L1-icache-load-misses
branch-loads
branch-load-misses
L1-dcache-loads
L1-dcache-load-misses
L1-dcache-stores
L1-dcache-store-misses
 
According to:[http://unix.stackexchange.com/questions/98641/understanding-perf-tool-output](http://unix.stackexchange.com/questions/98641/understanding-perf-tool-output)  my platform doesn't support some of the  processor's performance monitoring unit (PMU) hardware counters. It also  says that there may be a way to access the hardware counters somehow.  But, I haven't been able to figure it out. Does anyone have any ideas of things I might try to get Ubuntu to be able to access the hardware counters on my Joule?  Thank you for your help.

---

