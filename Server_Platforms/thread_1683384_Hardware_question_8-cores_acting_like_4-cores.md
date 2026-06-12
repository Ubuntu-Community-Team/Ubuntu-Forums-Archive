---
title: "Hardware question: 8-cores acting like 4-cores"
date: 2011-02-07
forum: Server Platforms
---

### Post by zugvogel on 2011-02-07
Hello,

I have a computer with 8 cores, upon which I run parallel code, with ubuntu. What I find though is that I only get a speed-up up to 4 cores. There is no speed difference between 4 and 8 cores.

I'm guessing this is something to do with having 2 quad-core processors and the bridge between them being slow, but it's only a guess. I'm not entirely sure what the processor configuration precisely is. Indeed, running two separate calculations each with 4 processors causes both to run slowly, so it may not be such a "bridge" issue.

Does anyone know how I can get more information about why this is happening?

The software is running on MPich2 if that makes any difference. The output from /proc/cpuinfo is as follows:

```

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 30
model name      : Intel(R) Core(TM) i7 CPU         860  @ 2.80GHz
stepping        : 5
cpu MHz         : 1197.000
cache size      : 8192 KB
physical id     : 0
siblings        : 8
core id         : 0
cpu cores       : 4
apicid          : 0
initial apicid  : 0
fpu             : yes
fpu_exception   : yes
cpuid level     : 11
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm ida tpr_shadow vnmi flexpriority ept vpid
bogomips        : 5585.83
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 30
model name      : Intel(R) Core(TM) i7 CPU         860  @ 2.80GHz
stepping        : 5
cpu MHz         : 1197.000
cache size      : 8192 KB
physical id     : 0
siblings        : 8
core id         : 1
cpu cores       : 4
apicid          : 2
initial apicid  : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 11
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm ida tpr_shadow vnmi flexpriority ept vpid
bogomips        : 5585.84
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:

processor       : 2
vendor_id       : GenuineIntel
cpu family      : 6
model           : 30
model name      : Intel(R) Core(TM) i7 CPU         860  @ 2.80GHz
stepping        : 5
cpu MHz         : 1197.000
cache size      : 8192 KB
physical id     : 0
siblings        : 8
core id         : 2
cpu cores       : 4
apicid          : 4
initial apicid  : 4
fpu             : yes
fpu_exception   : yes
cpuid level     : 11
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm ida tpr_shadow vnmi flexpriority ept vpid
bogomips        : 5585.82
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:

processor       : 3
vendor_id       : GenuineIntel
cpu family      : 6
model           : 30
model name      : Intel(R) Core(TM) i7 CPU         860  @ 2.80GHz
stepping        : 5
cpu MHz         : 1197.000
cache size      : 8192 KB
physical id     : 0
siblings        : 8
core id         : 3
cpu cores       : 4
apicid          : 6
initial apicid  : 6
fpu             : yes
fpu_exception   : yes
cpuid level     : 11
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm ida tpr_shadow vnmi flexpriority ept vpid
bogomips        : 5585.83
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:

processor       : 4
vendor_id       : GenuineIntel
cpu family      : 6
model           : 30
model name      : Intel(R) Core(TM) i7 CPU         860  @ 2.80GHz
stepping        : 5
cpu MHz         : 1197.000
cache size      : 8192 KB
physical id     : 0
siblings        : 8
core id         : 0
cpu cores       : 4
apicid          : 1
initial apicid  : 1
fpu             : yes
fpu_exception   : yes
cpuid level     : 11
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm ida tpr_shadow vnmi flexpriority ept vpid
bogomips        : 5585.84
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:

processor       : 5
vendor_id       : GenuineIntel
cpu family      : 6
model           : 30
model name      : Intel(R) Core(TM) i7 CPU         860  @ 2.80GHz
stepping        : 5
cpu MHz         : 1197.000
cache size      : 8192 KB
physical id     : 0
siblings        : 8
core id         : 1
cpu cores       : 4
apicid          : 3
initial apicid  : 3
fpu             : yes
fpu_exception   : yes
cpuid level     : 11
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm ida tpr_shadow vnmi flexpriority ept vpid
bogomips        : 5585.83
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:

processor       : 6
vendor_id       : GenuineIntel
cpu family      : 6
model           : 30
model name      : Intel(R) Core(TM) i7 CPU         860  @ 2.80GHz
stepping        : 5
cpu MHz         : 1197.000
cache size      : 8192 KB
physical id     : 0
siblings        : 8
core id         : 2
cpu cores       : 4
apicid          : 5
initial apicid  : 5
fpu             : yes
fpu_exception   : yes
cpuid level     : 11
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm ida tpr_shadow vnmi flexpriority ept vpid
bogomips        : 5585.85
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:

processor       : 7
vendor_id       : GenuineIntel
cpu family      : 6
model           : 30
model name      : Intel(R) Core(TM) i7 CPU         860  @ 2.80GHz
stepping        : 5
cpu MHz         : 1197.000
cache size      : 8192 KB
physical id     : 0
siblings        : 8
core id         : 3
cpu cores       : 4
apicid          : 7
initial apicid  : 7
fpu             : yes
fpu_exception   : yes
cpuid level     : 11
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm ida tpr_shadow vnmi flexpriority ept vpid
bogomips        : 5585.83
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:

```

Thanks for any insight!

---

### Post by stmiller on 2011-02-07
For the i5/i7 etc processors, make sure you have kernel 2.6.33 or later.

The different processor 'c states' in those newer CPUs are only utilized in the newer Linux kernels.

Also maybe check another software to test to make sure it's not just that particular code?

For instance, Handbrake (handbrake.fr) will use as many cores as you can throw at it, which would be a good test.

---

### Post by rubylaser on 2011-02-07
Ahh, this is an i7 860.  So, it has 4 Physical Cores, and 4 Logical Cores ([http://ark.intel.com/Product.aspx?id=41316]("http://ark.intel.com/Product.aspx?id=41316")). You're not going to ever see the processing power of 8 cores with a 4 physical cores.  x264 (handbrake) will show you if it's able to use all 8 threads, but even when it does use them the improvement over just using 4 threads is slight.

---

### Post by dtfinch on 2011-02-07
I haven't heard of dual socket i7 motherboards existing yet. You'd have to go with Xeons for that. A single quad core i7 will appear as 8 cores in cpuinfo because of hyperthreading.

---

### Post by rubylaser on 2011-02-07
There aren't any dual socket non-Xeon boards available in socket 1156.  This is a quad core processor with hyperthreading.

---

