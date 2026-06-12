---
title: "Oneiric i386 - CPU scaling doesn't work?"
date: 2012-01-09
forum: Server Platforms
---

### Post by Calimerorulez on 2012-01-09
I have a HP dc7800 USDT, with an Intel E4500, with kernel 3.0.0.14, Oneiric.

According to Intel, it's a dual core 2.2GHz CPU. The problem is, the CPU frequency seems to be fixed at 1.2GHz.

cat /proc/cpuinfo states:

```
patrick@headphones:/proc$ cat cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 Duo CPU     E4500  @ 2.20GHz
stepping        : 13
cpu MHz         : 1200.000
cache size      : 2048 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
apicid          : 0
initial apicid  : 0
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm dts
bogomips        : 4389.12
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 Duo CPU     E4500  @ 2.20GHz
stepping        : 13
cpu MHz         : 1200.000
cache size      : 2048 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
apicid          : 1
initial apicid  : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm dts
bogomips        : 4389.01
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:
```

cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies:

```
1600000 1200000
```

Scaling governor is 'ondemand'.

Is there a way to use the 'full' 2.2GHz? And preferably dynamically? 

Thanks :D

---

