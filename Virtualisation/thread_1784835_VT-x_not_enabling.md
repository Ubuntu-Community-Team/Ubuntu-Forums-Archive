---
title: "VT-x not enabling"
date: 2011-06-17
forum: Virtualisation
---

### Post by emiller12345 on 2011-06-17
Trying to get VT-x working eventually with Virtualbox.
Running Lucid-x64 fresh install... with a brand new processor, retail sealed box...

```

Boxed Intel® Celeron® Processor E3500 (1M Cache, 2.70 GHz, 800 MHz FSB) LGA775
Socket    StepTDP        Ordering Code    SpecCode    HalogenFree    VT-x
LGA775    65Watts        BX80571E3500    SLGTY        No        Yes

```

...Made sure VT is enabled in the BIOS...

```

BIOS 
-Security
--XD    ENABLED
--VT    ENABLED

```


Now to check if VT-x is enabled
> 
FROM: [http://www.howtogeek.com/howto/linux/linux-tip-how-to-tell-if-your-processor-supports-vt/](http://www.howtogeek.com/howto/linux/linux-tip-how-to-tell-if-your-processor-supports-vt/)

...It’s quite simple: We’ll need to take a peek inside the /proc/cpuinfo file and look at the flags section for one of two values, vmx or svm...


```

$ cat /proc/cpuinfo | grep "vmx"
$ cat /proc/cpuinfo | grep "svm"
$

```

???

```

$ cat /proc/cpuinfo
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 23
model name    : 06/17
stepping    : 10
cpu MHz        : 2699.947
cache size    : 1024 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 2
apicid        : 0
initial apicid  : 0
fpu        : yes
fpu_exception   : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni monitor tm2 ssse3 lahf_lm
bogomips    : 5399.89
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:

processor    : 1
vendor_id    : GenuineIntel
cpu family    : 6
model        : 23
model name    : 06/17
stepping    : 10
cpu MHz        : 2699.947
cache size    : 1024 KB
physical id    : 0
siblings    : 2
core id        : 1
cpu cores    : 2
apicid        : 1
initial apicid    : 1
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni monitor tm2 ssse3 lahf_lm
bogomips    : 5399.86
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

```

Anyone know why VT-x is not showing up as available in the OS? Any suggestions?

---

### Post by emiller12345 on 2011-06-17
I set the VM to directly enable VT-x...
```

$ VBoxManage modifyvm 64bitTest --hwvirtex on
$

```Running Natty 11.04 x64 guest OS I get 
```
This kernel requires an x86-64 CPU but only detected an i686 CPU.
Unable to boot - please use a kernel appropriate for your CPU.
```

---

### Post by emiller12345 on 2011-07-24
I figured out what the problem was.  VT-x in Virtualbox requires 3 things to work.  First, you need a processor that is VT-x capable (check, just got a brand new one). Second, you need an OS that is VT-x capable (Ubuntu - check).  Next, your motherboard needs to be able to recognize VT-x.  My MOBO wasn't able to recognize the VT-x part of the new processor, but was still able to use the processor.  A BIOS update fixed everything.

---

