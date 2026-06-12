---
title: "32 or 64 bit ver for HPDL360 G3"
date: 2009-10-08
forum: Server Platforms
---

### Post by jmsgz on 2009-10-08
figured i would try to learn about server setup admin and enjoy a server with Ubuntu.
purchased a hpdl360 G3,,,,,which ver server do i install the 32 bit or the 64 bit?  

thanks in advance jsg

---

### Post by t3r0 on 2009-10-09
If you have 64bit CPU(s) then 64bit else 32bit... :D But you probably know that already ;) 

If you dont know what type of CPUs you have, then check the exact model from P.O.S.T. or bios or iLO console (if available) and then google the cpu model. HP usually uses Intel cpus so intels own search might also be useful.


- Tero

---

### Post by scorp123 on 2009-10-09
> **jmsgz said:**
> which ver server do i install the 32 bit or the 64 bit?  You could boot with a 32-bit Live CD and find out:
```
cat /proc/cpuinfo
```

Then take a look at the "CPU flags" it spits out. If there is a **[COLOR="Red"]"lm"[/COLOR]** (= "long mode") flag then the CPU is 64-bit, else it is 32-bit.

Example from my desktop PC:
```
> cat /proc/cpuinfo
 
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Quad CPU    Q9400  @ 2.66GHz
stepping	: 10
cpu MHz		: 2000.000
cache size	: 3072 KB
physical id	: 0
siblings	: 4
core id		: 0
cpu cores	: 4
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 13
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 
clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall 
nx **[COLOR="Red"]lm[/COLOR]** constant_tsc arch_perfmon pebs bts rep_good 
pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 
xsave lahf_lm tpr_shadow vnmi flexpriority
bogomips	: 5333.20
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management: 

...
``` So that is definitely a 64-bit CPU ...


Example from my old laptop:

```
> cat /proc/cpuinfo 
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 14
model name	: Genuine Intel(R) CPU           T2050  @ 1.60GHz
stepping	: 8
cpu MHz		: 800.000
cache size	: 2048 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr 
pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe 
nx constant_tsc arch_perfmon bts pni monitor est tm2 xtpr pdcm
bogomips	: 3191.98
clflush size	: 64
power management:

...
``` No **"lm"** flag ... so this is definitely a 32-bit CPU.

---

### Post by PrePenguin on 2009-10-09
Also if you dont have atleast 4 gigs of memory you wont see much advantage of 64 bit architecture anyways.

---

