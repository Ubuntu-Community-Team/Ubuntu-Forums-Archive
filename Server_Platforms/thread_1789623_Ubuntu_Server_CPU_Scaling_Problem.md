---
title: "Ubuntu Server CPU Scaling Problem"
date: 2011-06-24
forum: Server Platforms
---

### Post by DeltaVI on 2011-06-24
I have recent installed ubuntu server on a Hp pavilion a700n that has a XP 3000+ processor 

looking around i have found a few things about cpu scaling such as this topic [here]("http://ubuntuforums.org/showthread.php?t=944190")
but no matter what i try from reading in that topic, my /proc/cpuinfo is always the same-- 
```

processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 6
model           : 10
model name      : AMD Athlon(tm) XP 3000+
stepping        : 0
cpu MHz         : 2099.971
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow up
bogomips        : 4199.94
clflush size    : 32
cache_alignment : 32
address sizes   : 34 bits physical, 32 bits virtual
power management: ts

```Is there anything i can do to get the cpu scaling to work correctly?

Thanks,
DeltaVI

---

### Post by DeltaVI on 2011-06-24
Bump

---

### Post by deadite66 on 2011-06-26
I haven't found anything yet, best i can do i manually change speed.

---

### Post by DeltaVI on 2011-06-26
thanks for the reply, how are you able to change it manually?

---

### Post by deadite66 on 2011-06-26
sudo apt-get install cpufrequtils
sudo modprobe p4_clockmod
this module might be different for other cpu's, mine is a Celeron M 2.0Ghz

cpufreq-info
will show current settings

sudo cpufreq-set -f 750Mhz
sets my cpu to 750Mhz.

> lee@sakura:~$ cpufreq-info
cpufrequtils 007: cpufreq-info (C) Dominik Brodowski 2004-2009
Report errors and bugs to [email]cpufreq@vger.kernel.org[/email], please.
analyzing CPU 0:
  driver: p4-clockmod
  CPUs which run at the same hardware frequency: 0
  CPUs which need to have their frequency coordinated by software: 0
  maximum transition latency: 10.00 ms.
  hardware limits: 188 MHz - 1.50 GHz
  available frequency steps: 188 MHz, 375 MHz, 563 MHz, 750 MHz, 938 MHz, 1.13 GHz, 1.31 GHz, 1.50 GHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 188 MHz and 1.50 GHz.
                  The governor "userspace" may decide which speed to use
                  within this range.
  current CPU frequency is 750 MHz.


---

