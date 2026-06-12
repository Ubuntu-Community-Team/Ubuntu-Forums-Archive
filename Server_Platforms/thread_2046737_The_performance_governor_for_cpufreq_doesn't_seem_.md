---
title: "The performance governor for cpufreq doesn't seem to behave as advertised"
date: 2012-08-23
forum: Server Platforms
---

### Post by mgoldshteyn on 2012-08-23
The kernel in use: 3.2.0-23-generic on Ubuntu 12.04LTS
For example, I issue the following command:
```
sudo cpufreq-set -c 0 -g performance
```
Then I go to /sys/devices/system/cpu/cpu0/cpufreq and type in the following:
```
sudo cat cpuinfo_cur_freq
```
Sometimes I get the max frequency (3600 MHz) when I do this and sometimes I get the min frequency (1600 MHz).
If I do:
```
cat scaling_governor
```
The output is **performance**, showing that the governor is in fact set to performance.
Then, to make it even more weird, if I do:
```
cpufreq-info
```
I get:
```

analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which run at the same hardware frequency: 0 1 2 3 8 9 10 11
  CPUs which need to have their frequency coordinated by software: 0
  maximum transition latency: 10.0 us.
  hardware limits: 1.60 GHz - 3.60 GHz
  available frequency steps: 3.60 GHz, 3.60 GHz, 3.47 GHz, 3.33 GHz, 3.20 GHz, 3.07 GHz, 2.93 GHz, 2.80 GHz, 2.67 GHz, 2.53 GHz, 2.40 GHz, 2.27 GHz, 2.13 GHz, 2.00 GHz, 1.87 GHz, 1.73 GHz, 1.60 GHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 3.60 GHz and 3.60 GHz.
                  The governor "performance" may decide which speed to use
                  within this range.
  current CPU frequency is 3.60 GHz.
...

```
If you look at the current policy above, you will notice that it is telling me that the CPU should be pegged at 3.60 GHz. Yet, polling (i.e., displaying) cpuinfo_cur_freq once a second seems to tell a different story.

---

### Post by Doug S on 2012-08-23
I don't actually use the cpufrequtils package, and don't even have it installed.
However, and due to some specific work I have being trying to help with, I have been constantly forcing CPU frequencies on a test machine for many many months now. As long as I wait long enough after system boot (on the order of a couple of minutes), I have found that what I ask for is what I always get. This includes way back with kernel 3.2.0.23-generic.
I realize my reply doesn't help you much.

---

### Post by mgoldshteyn on 2012-08-23
My results are hours after the system was rebooted. So, sadly, this is not a timing issue...

---

### Post by Doug S on 2012-08-23
I wonder if your CPU 0 is being throttled back because it is getting to hot?

---

