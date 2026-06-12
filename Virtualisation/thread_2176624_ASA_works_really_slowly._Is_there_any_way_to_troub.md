---
title: "ASA works really slowly. Is there any way to troubleshoot?"
date: 2013-09-25
forum: Virtualisation
---

### Post by alexy2 on 2013-09-25
Hello all!

I'm trying to run ASA on GNS3, seems like i have  managed to get it started. I can connect to console. But, here goes a  real issue, it works really slow, so all i have managed to do was to  type enable and show commands:( 

I tryed to figure out the root  cause but was getting nowhere. The only thing i saw suspicious was that QEMU was taking 100% of CPU. But i have no idea how to deal with that.  I'm a Cisco gay, not a VMware guru. Would you, please, give me any ideas  how  try to solve it.

It seems that i ran GNS3 on a solid CPU

```
alexy@Linux:/$ cat /proc/cpuinfo  
processor   : 0 
vendor_id   : GenuineIntel 
cpu family   : 6 
model      : 23 
model name   : Intel(R) Core(TM)2 Quad CPU    Q9400  @ 2.66GHz 
stepping   : 10 
cpu MHz      : 2667.000 
cache size   : 3072 KB 
physical id   : 0 
siblings   : 4 
core id      : 0 
cpu cores   : 4 
apicid      : 0 
initial apicid   : 0 
fpu      : yes 
fpu_exception   : yes 
cpuid level   : 13 
wp      : yes 
flags      : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca  cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall  nx lm constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64  monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm  dts tpr_shadow vnmi flexpriority 
bogomips   : 5332.41 
clflush size   : 64 
cache_alignment   : 64 
address sizes   : 36 bits physical, 48 bits virtual 
power management: 
 
processor   : 1 
vendor_id   : GenuineIntel 
cpu family   : 6 
model      : 23 
model name   : Intel(R) Core(TM)2 Quad CPU    Q9400  @ 2.66GHz 
stepping   : 10 
cpu MHz      : 2000.000 
cache size   : 3072 KB 
physical id   : 0 
siblings   : 4 
core id      : 3 
cpu cores   : 4 
apicid      : 3 
initial apicid   : 3 
fpu      : yes 
fpu_exception   : yes 
cpuid level   : 13 
wp      : yes 
flags      : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca  cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall  nx lm constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64  monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm  dts tpr_shadow vnmi flexpriority 
bogomips   : 5332.98 
clflush size   : 64 
cache_alignment   : 64 
address sizes   : 36 bits physical, 48 bits virtual 
power management: 
 
processor   : 2 
vendor_id   : GenuineIntel 
cpu family   : 6 
model      : 23 
model name   : Intel(R) Core(TM)2 Quad CPU    Q9400  @ 2.66GHz 
stepping   : 10 
cpu MHz      : 2000.000 
cache size   : 3072 KB 
physical id   : 0 
siblings   : 4 
core id      : 1 
cpu cores   : 4 
apicid      : 1 
initial apicid   : 1 
fpu      : yes 
fpu_exception   : yes 
cpuid level   : 13 
wp      : yes 
flags      : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca  cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall  nx lm constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64  monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm  dts tpr_shadow vnmi flexpriority 
bogomips   : 5332.73 
clflush size   : 64 
cache_alignment   : 64 
address sizes   : 36 bits physical, 48 bits virtual 
power management: 
 
processor   : 3 
vendor_id   : GenuineIntel 
cpu family   : 6 
model      : 23 
model name   : Intel(R) Core(TM)2 Quad CPU    Q9400  @ 2.66GHz 
stepping   : 10 
cpu MHz      : 2667.000 
cache size   : 3072 KB 
physical id   : 0 
siblings   : 4 
core id      : 2 
cpu cores   : 4 
apicid      : 2 
initial apicid   : 2 
fpu      : yes 
fpu_exception   : yes 
cpuid level   : 13 
wp      : yes 
flags      : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca  cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall  nx lm constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64  monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm  dts tpr_shadow vnmi flexpriority 
bogomips   : 5332.73 
clflush size   : 64 
cache_alignment   : 64 
address sizes   : 36 bits physical, 48 bits virtual 
power management:
```

---

