---
title: "Think i found two 3.15 kernel issues (after suspend)"
date: 2014-06-15
forum: Ubuntu Development Version
---

### Post by pqwoerituytrueiwoq on 2014-06-15
1. On wake from suspend the sound device is changed to "Dummy Output"
2. On wake from suspend the permissions are changed on /sys/devices/system/cpu/cpu*/cpufreq/cpuinfo_cur_freq (where * is > 1) so that only root can read it

i am testing the kernel under trusty, anyone able to confirm this issue under utopic?

---

### Post by Doug S on 2014-06-19
> **pqwoerituytrueiwoq said:**
> 2. On wake from suspend the permissions are changed on /sys/devices/system/cpu/cpu*/cpufreq/cpuinfo_cur_freq (where * is > 1) so that only root can read it
i am testing the kernel under trusty, anyone able to confirm this issue under utopic?I only have the ability to confirm or deny "2", which I confirm.
Kernel:```
Linux s15 3.16.0-rc1-doug1 #118 SMP Tue Jun 17 07:51:18 PDT 2014 x86_64 x86_64 x86_64 GNU/Linux
```(the doug 1 part is only something trivial and it will be in RC2).
Before suspend: The access was 444 for all files.
After suspend:```
doug@s15:~$ ls -l /sys/devices/system/cpu/cpu*/cpufreq/cpuinfo_cur_freq
-r--r--r-- 1 root root 4096 Jun 17 11:22 /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_cur_freq
-r-------- 1 root root 4096 Jun 18 22:13 /sys/devices/system/cpu/cpu1/cpufreq/cpuinfo_cur_freq
-r-------- 1 root root 4096 Jun 18 22:13 /sys/devices/system/cpu/cpu2/cpufreq/cpuinfo_cur_freq
-r-------- 1 root root 4096 Jun 18 22:13 /sys/devices/system/cpu/cpu3/cpufreq/cpuinfo_cur_freq
-r-------- 1 root root 4096 Jun 18 22:13 /sys/devices/system/cpu/cpu4/cpufreq/cpuinfo_cur_freq
-r-------- 1 root root 4096 Jun 18 22:13 /sys/devices/system/cpu/cpu5/cpufreq/cpuinfo_cur_freq
-r-------- 1 root root 4096 Jun 18 22:13 /sys/devices/system/cpu/cpu6/cpufreq/cpuinfo_cur_freq
-r-------- 1 root root 4096 Jun 18 22:13 /sys/devices/system/cpu/cpu7/cpufreq/cpuinfo_cur_freq
```As mentioned via PM, I am running trusty, I know you wanted someone running utopic, but hopefully this helps anyhow.

---

