---
title: "linux doesn't know my CPU supports VT. Help please"
date: 2010-01-26
forum: Virtualisation
---

### Post by Xephyrind on 2010-01-26
Hi I am trying to do virtualization here so I did a

```
grep vmx /proc/cpuinfo
``` nothing showed up.

I checked my CPU to see if it supports Virtualization technology, it said yes. My CPU is:
Intel Core 2 Quad Q9550 Yorkfield 2.83GHz 12MB L2 Cache LGA 775 95W Quad-Core Desktop Processor. I checked it here:
[HTML]http://www.newegg.com/product/product.aspx?item=n82e16819115041[/HTML]
Why does my system show nothing when I grep vmx? I thought if my CPU supports VT, it should return something right? Could it be because I couldn't and have not installed xen-tools-2.7 properly yet?

```

sanguine:/tmp# cd xen-tools-2.7
sanguine:/tmp/xen-tools-2.7# make install
-bash: make: command not found
sanguine:/tmp/xen-tools-2.7# grep vmx /proc/cpuinfo
sanguine:/tmp/xen-tools-2.7# uname -a
Linux sanguine 2.6.26-1-xen-amd64 #1 SMP Fri Mar 13 21:39:38 UTC 2009 x86_64 GNU/Linux
sanguine:/tmp/xen-tools-2.7# cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Quad  CPU   Q9550  @ 2.83GHz
stepping	: 7
cpu MHz		: 2833.372
cache size	: 6144 KB
physical id	: 0
siblings	: 1
core id		: 0
cpu cores	: 1
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu de tsc msr pae cx8 apic sep mtrr cmov pat clflush acpi mmx fxsr sse sse2 ss ht syscall nx lm constant_tsc rep_good pni ssse3 cx16 sse4_1 lahf_lm
bogomips	: 5673.35
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Quad  CPU   Q9550  @ 2.83GHz
stepping	: 7
cpu MHz		: 2833.372
cache size	: 6144 KB
physical id	: 0
siblings	: 1
core id		: 3
cpu cores	: 1
apicid		: 3
initial apicid	: 3
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu de tsc msr pae cx8 apic sep mtrr cmov pat clflush acpi mmx fxsr sse sse2 ss ht syscall nx lm constant_tsc rep_good pni ssse3 cx16 sse4_1 lahf_lm
bogomips	: 5673.35
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 2
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Quad  CPU   Q9550  @ 2.83GHz
stepping	: 7
cpu MHz		: 2833.372
cache size	: 6144 KB
physical id	: 0
siblings	: 1
core id		: 2
cpu cores	: 1
apicid		: 2
initial apicid	: 2
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu de tsc msr pae cx8 apic sep mtrr cmov pat clflush acpi mmx fxsr sse sse2 ss ht syscall nx lm constant_tsc rep_good pni ssse3 cx16 sse4_1 lahf_lm
bogomips	: 5673.35
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 3
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Quad  CPU   Q9550  @ 2.83GHz
stepping	: 7
cpu MHz		: 2833.372
cache size	: 6144 KB
physical id	: 0
siblings	: 1
core id		: 1
cpu cores	: 1
apicid		: 1
initial apicid	: 1
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu de tsc msr pae cx8 apic sep mtrr cmov pat clflush acpi mmx fxsr sse sse2 ss ht syscall nx lm constant_tsc rep_good pni ssse3 cx16 sse4_1 lahf_lm
bogomips	: 5673.35
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

```

---

### Post by spongypants23 on 2010-01-26
Is it enabled in the BIOS?

VT was off by default in my BIOS settings.

---

### Post by pirateghost on 2010-01-26
yeah, you have to turn it on in BIOS.

---

