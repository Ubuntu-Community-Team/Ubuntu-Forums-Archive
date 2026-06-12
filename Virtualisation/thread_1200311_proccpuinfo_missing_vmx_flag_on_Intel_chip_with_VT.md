---
title: "/proc/cpuinfo missing vmx flag on Intel chip with VT"
date: 2009-06-29
forum: Virtualisation
---

### Post by AreonEpta on 2009-06-29
So, I'm running Jaunty 64, on a solid system. All is running well, but now it's time to make this thing run kvm. I followed all of the instructions to detect compatibility outlined in the KVM Tutorial found [here]("http://ubuntuforums.org/showthread.php?t=966739"), namely the command
```
grep vmx /proc/cpuinfo
```and it comes up with... nothing. Here's the output of my cpuinfo file. Intel P7350 inside a comfy little HP DV5-1000US. I'd love an idea of why, or, better yet, a workaround.

```
uname -a

Linux Bonsai 2.6.28-13-generic #44-Ubuntu SMP Tue Jun 2 07:55:09 UTC 2009 x86_64 GNU/Linux
```


```
cat /proc/cpuinfo

processor              : 0
vendor_id              : GenuineIntel
cpu family             : 6
model                  : 23
model name             : Intel(R) Core(TM)2 Duo CPU     P7350  @ 2.00GHz
stepping               : 6
cpu MHz                : 2000.000
cache size             : 3072 KB
physical id            : 0
siblings               : 2
core id                : 0
cpu cores              : 2
apicid                 : 0
initial apicid         : 0
fpu                    : yes
fpu_exception          : yes
cpuid level            : 10
wp                     : yes
flags                  : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm sse4_1 lahf_lm
bogomips               : 3990.39
clflush size           : 64
cache_alignment        : 64
address sizes          : 36 bits physical, 48 bits virtual
power management:


processor              : 1
vendor_id              : GenuineIntel
cpu family             : 6
model                  : 23
model name             : Intel(R) Core(TM)2 Duo CPU     P7350  @ 2.00GHz
stepping               : 6
cpu MHz                : 2000.000
cache size             : 3072 KB
physical id            : 0
siblings               : 2
core id                : 0
cpu cores              : 2
apicid                 : 0
initial apicid         : 0
fpu                    : yes
fpu_exception          : yes
cpuid level            : 10
wp                     : yes
flags                  : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm sse4_1 lahf_lm
bogomips               : 3990.39
clflush size           : 64
cache_alignment        : 64
address sizes          : 36 bits physical, 48 bits virtual
power management:

```

---

### Post by bodhi.zazen on 2009-06-30
Your processor does not appear to have VT.

The line of interest in your output is the "flags" line. This line does not have either vmx or svm.

---

### Post by AreonEpta on 2009-06-30
> **bodhi.zazen said:**
> Your processor does not appear to have VT.

The line of interest in your output is the "flags" line. This line does not have either vmx or svm.

My cpuinfo is very obviously showing no VT, however, BIOS shows it as a valid option, it is enabled, and I have used virtualization before. After reading your post, I searched Intel's product page on my processor (found in my signature), and it seems that you're right, and I do not have VT. Explain then, why BIOS shows it. And, more importantly, if I have no VT, is there another kind of virtualization I can use? Maybe software based?

---

### Post by bodhi.zazen on 2009-06-30
Well the BIOS is the initial stage of the boot process and drives the hardware on your motherboard, so it has to support all the potential hardware configurations. Your motherboard supports a 64 bit CPU and if you replace the CPU, your BIOS will support it (if that makes sense).

Basically the BIOS goes with the motherboard, of which the CPU is but one of several components and the CPU itself is variable. so your motherboard and BIOS will support a VT enabled CPU (if you really want, VT enabled CPU are not really that expensive).

KVM is only one option and is as you say hardware based. 

You can use (in my order of recommendations) 

Virtualbox
VMWare
QEMU
openvz (you probably do not want openvz at this time).

---

