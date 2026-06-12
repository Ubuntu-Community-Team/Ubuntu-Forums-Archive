---
title: "VirtualBox on Karmic Host not detecting hardware virtualization extensions"
date: 2010-06-25
forum: Virtualisation
---

### Post by sirlark on 2010-06-25
Hi all,

I'm trying to set up a headless virtualbox machine. The host system is an Intel Xeon quad core running karmic koala server. The guest OS is meant to be lucid lynx server. I installed X and virtualbox-ose on the host, and ssh'd into it using my gentoo laptop. I ran VirtualBox, the window appeared on my laptop (the host is headless too). I created a virtual machine, enabled VT-X, nested paging and PAE-NX, and started it. The machines starts, and I have installed lucid lynx as the guest OS. The catch is, VirtualBox tells me that none of the hardware virtualization extensions are enabled, i.e. VT-X and nested paging. Also, when I log in, I get this message

> Your CPU appears to be lacking expected security  protections.[FONT=monospace]
[/FONT]Please check your BIOS settings, or for  more information, run:
[FONT=monospace]  /usr/bin/check-bios-nx --verbose
[/FONT]
 

So these are my questions:

1. How do I tell if my host CPU even supports these extensions?
2. How do I get rid of the NX message, preferably by enabling NX somehow?

Thanks,

P.S. Herewith the contents of the host's /proc/cpuinfo for reference.

> 
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 26
model name    : Intel(R) Xeon(R) CPU           E5520  @ 2.27GHz
stepping    : 5
cpu MHz        : 1596.000
cache size    : 8192 KB
physical id    : 0
siblings    : 4
core id        : 0
cpu cores    : 4
apicid        : 0
initial apicid    : 0
fpu        : yes
fpu_exception    : yes
cpuid level    : 11
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good xtopology tsc_reliable nonstop_tsc pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm dca sse4_1 sse4_2 popcnt lahf_lm ida tpr_shadow vnmi flexpriority ept vpid
bogomips    : 4521.77
clflush size    : 64
cache_alignment    : 64
address sizes    : 40 bits physical, 48 bits virtual
power management:

processor    : 1
vendor_id    : GenuineIntel
cpu family    : 6
model        : 26
model name    : Intel(R) Xeon(R) CPU           E5520  @ 2.27GHz
stepping    : 5
cpu MHz        : 1596.000
cache size    : 8192 KB
physical id    : 0
siblings    : 4
core id        : 1
cpu cores    : 4
apicid        : 2
initial apicid    : 2
fpu        : yes
fpu_exception    : yes
cpuid level    : 11
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good xtopology tsc_reliable nonstop_tsc pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm dca sse4_1 sse4_2 popcnt lahf_lm ida tpr_shadow vnmi flexpriority ept vpid
bogomips    : 4521.92
clflush size    : 64
cache_alignment    : 64
address sizes    : 40 bits physical, 48 bits virtual
power management:

processor    : 2
vendor_id    : GenuineIntel
cpu family    : 6
model        : 26
model name    : Intel(R) Xeon(R) CPU           E5520  @ 2.27GHz
stepping    : 5
cpu MHz        : 1596.000
cache size    : 8192 KB
physical id    : 0
siblings    : 4
core id        : 2
cpu cores    : 4
apicid        : 4
initial apicid    : 4
fpu        : yes
fpu_exception    : yes
cpuid level    : 11
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good xtopology tsc_reliable nonstop_tsc pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm dca sse4_1 sse4_2 popcnt lahf_lm ida tpr_shadow vnmi flexpriority ept vpid
bogomips    : 4521.92
clflush size    : 64
cache_alignment    : 64
address sizes    : 40 bits physical, 48 bits virtual
power management:

processor    : 3
vendor_id    : GenuineIntel
cpu family    : 6
model        : 26
model name    : Intel(R) Xeon(R) CPU           E5520  @ 2.27GHz
stepping    : 5
cpu MHz        : 1596.000
cache size    : 8192 KB
physical id    : 0
siblings    : 4
core id        : 3
cpu cores    : 4
apicid        : 6
initial apicid    : 6
fpu        : yes
fpu_exception    : yes
cpuid level    : 11
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good xtopology tsc_reliable nonstop_tsc pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm dca sse4_1 sse4_2 popcnt lahf_lm ida tpr_shadow vnmi flexpriority ept vpid
bogomips    : 4521.92
clflush size    : 64
cache_alignment    : 64
address sizes    : 40 bits physical, 48 bits virtual
power management:


---

### Post by sirlark on 2010-06-25
Of course enabling virtualization in the HOST BIOS haleps alot ;) Feeling stupid now...

---

