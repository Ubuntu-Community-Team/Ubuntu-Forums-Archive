---
title: "Module kvm-intel refuses to load Pangolin Performance panp4n"
date: 2010-05-06
forum: System76 Support
---

### Post by bhaskar on 2010-05-06
I am trying to load the kvm-intel module for virtualization, and get an error:

# modprobe kvm-intel
FATAL: Error inserting kvm_intel (/lib/modules/2.6.32-22-generic/kernel/arch/x86/kvm/kvm-intel.ko): Operation not supported

However, the CPU does support virtualization:

# grep flags /proc/cpuinfo 
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 lahf_lm tpr_shadow vnmi flexpriority
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 lahf_lm tpr_shadow vnmi flexpriority

How do I get kvm-intel to load?  Thanks.

-- Bhaskar

---

### Post by bhaskar on 2010-05-06
Forgot to add - newly installed Lucid Lynx on this laptop.

---

### Post by PatrickVogeli on 2010-05-06
which processor do you have?

---

### Post by bhaskar on 2010-05-07
Patrick, here is the complete CPU information.  Thanks for your help.

-- Bhaskar

--------------------------------------------------
# cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 23
model name      : Intel(R) Core(TM)2 Duo CPU     P8600  @ 2.40GHz
stepping        : 6
cpu MHz         : 800.000
cache size      : 3072 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
apicid          : 0
initial apicid  : 0
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 lahf_lm tpr_shadow vnmi flexpriority
bogomips        : 4788.13
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 23
model name      : Intel(R) Core(TM)2 Duo CPU     P8600  @ 2.40GHz
stepping        : 6
cpu MHz         : 800.000
cache size      : 3072 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
apicid          : 1
initial apicid  : 1
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 lahf_lm tpr_shadow vnmi flexpriority
bogomips        : 4788.00
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:

#

---

### Post by thomasaaron on 2010-05-07
I think we've run into this before with the P8600s. 

While the P8600 is supposed to support VT, id doesn't seem to work with that motherboard and BIOS.

We've send the BIOS to the upstream BIOS developers, and they swear the VT flag is turned on.

Contact me via email with the output of...

sudo dmidecode -s bios-version

...and we can resume communication with the devs and see if they will have another look.

---

### Post by bhaskar on 2010-05-12
> **thomasaaron said:**
> I think we've run into this before with the P8600s. 

While the P8600 is supposed to support VT, id doesn't seem to work with that motherboard and BIOS.

We've send the BIOS to the upstream BIOS developers, and they swear the VT flag is turned on.

Contact me via email with the output of...

sudo dmidecode -s bios-version

...and we can resume communication with the devs and see if they will have another look.


[KSB] As requested, I e-mailed Tom the BIOS version.  With a BIOS upgrade that he sent me, the kvm-intel module now loads.  Thank you, Tom & System 76.

-- Bhaskar

---

### Post by eprv on 2010-09-20
have the same problem with Intel DG41MJ mini itx board and E7500 CPU.
The CPU has vmx support but doesn't load kvm_intel:
et@itx:~$ sudo modprobe kvm_intel
FATAL: Error inserting kvm_intel (/lib/modules/2.6.32-24-generic/kernel/arch/x86/kvm/kvm-intel.ko): Operation not supported

The BIOS version is the latest

solved: VM must be enabled in BIOS under security menu, not good place to look for but it is there.

---

