---
title: "Ubuntu Server Power Mode"
date: 2021-10-05
forum: Server Platforms
---

### Post by outlaw67 on 2021-10-05
Running latest version of Ubuntu Server.is there a setting for power mode like in windows ?

---

### Post by Doug S on 2021-10-05
I don't know about windows.

The answer to your question depends on your hardware, processor make and model. Have a look at this:

```
doug@s19:~$ grep . /sys/devices/system/cpu/cpu0/cpufreq/*
/sys/devices/system/cpu/cpu0/cpufreq/affected_cpus:0
/sys/devices/system/cpu/cpu0/cpufreq/base_frequency:4100000
/sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_max_freq:4800000
/sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_min_freq:800000
/sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_transition_latency:0
/sys/devices/system/cpu/cpu0/cpufreq/energy_performance_available_preferences:default performance balance_performance balance_power power
/sys/devices/system/cpu/cpu0/cpufreq/energy_performance_preference:balance_performance
/sys/devices/system/cpu/cpu0/cpufreq/related_cpus:0
/sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors:performance powersave
/sys/devices/system/cpu/cpu0/cpufreq/scaling_cur_freq:800161
/sys/devices/system/cpu/cpu0/cpufreq/scaling_driver:intel_pstate
/sys/devices/system/cpu/cpu0/cpufreq/scaling_governor:powersave
/sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq:4800000
/sys/devices/system/cpu/cpu0/cpufreq/scaling_min_freq:800000
/sys/devices/system/cpu/cpu0/cpufreq/scaling_setspeed:<unsupported>
```

---

### Post by ActionParsnip on 2021-10-06
What do you mean by power mode? What would it do and achieve?

---

### Post by slickymaster on 2021-10-06
*Thread moved to **Server Platforms**.*

---

