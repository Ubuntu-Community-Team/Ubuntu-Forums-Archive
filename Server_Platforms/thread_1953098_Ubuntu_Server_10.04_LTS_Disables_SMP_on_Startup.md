---
title: "Ubuntu Server 10.04 LTS Disables SMP on Startup"
date: 2012-04-05
forum: Server Platforms
---

### Post by CH3CH2OH on 2012-04-05
My 64-bit Ubuntu Server 10.04 LTS installation is unable to enable more than one core of the six-core AMD chip installed. The system appears to load the first core, boot the kernel, and then disable symmetric multiprocessing rather than loading the last (non-boot) CPUs. 

My suspicion is that this has something to do with the APIC settings in the bios/bootloader, because that seems to have been the case in some other forums. I have not been able to get the kernel to load successfully without the nolapic flag in GRUB. I would appreciate any suggestions and will entertain any requests for log files or command outputs. To start with, I've included the output from several informative commands below. 

uname -a:
Linux maripaludis 2.6.32-40-server #87-Ubuntu **SMP** Tue Mar 6 02:10:02 UTC 2012 x86_64 GNU/Linux

cat /proc/cmdline 
BOOT_IMAGE=/boot/vmlinuz-2.6.32-40-server root=UUID=... ro splash  edd=on **nolapic** nomodeset quiet splash

Hardware:
ASRock 890FX Deluxe5
AMD Phenom X6 1090T

cat /proc/cpuinfo:
processor    : 0
vendor_id    : AuthenticAMD
cpu family    : 16
model        : 10
model name    : AMD Phenom(tm) II X6 1090T Processor
stepping    : 0
cpu MHz        : 3600.425
cache size    : 512 KB
physical id    : 0
siblings    : 1
core id        : 0
**cpu cores    : 1**
apicid        : 0
initial apicid    : 0
fpu        : yes
fpu_exception    : yes
cpuid level    : 6
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nonstop_tsc pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt nodeid_msr
bogomips    : 6400.74
TLB size    : 1024 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate [9]

excerpt from dmesg:
** [    0.000000] found SMP MP-table at [ffff8800000fd0a0] fd0a0**
...
[    0.000000] Intel MultiProcessor Specification v1.4
[    0.000000] MPTABLE: OEM ID: A M I
[    0.000000] MPTABLE: Product ID: ALASKA
[    0.000000] MPTABLE: APIC at: 0xFEE00000
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] Processor #1
[    0.000000] Processor #2
[    0.000000] Processor #3
[    0.000000] Processor #4
[    0.000000] Processor #5
[    0.000000] I/O APIC #0 Version 33 at 0xFEC20000.
[    0.000000] I/O APIC #7 Version 33 at 0xFEC00000.
[    0.000000] Processors: 6
** [    0.000000] SMP: Allowing 6 CPUs, 0 hotplug CPUs**
...
[    0.030052] Setting APIC routing to flat
** [    0.030054] SMP disabled**
(full output of dmesg attached)

---

### Post by CH3CH2OH on 2012-04-05
Solved the problem by disabling 'SATA IDE combined mode' in the Bios.

Cheers

---

### Post by CH3CH2OH on 2012-06-19
I encountered this problem again after upgrading from 10.04 LTS to 12.04 LTS. I was able to fix it again by enabling lapic in grub. It appears that sata/ide combined mode is still verboten.

---

### Post by ian dobson on 2012-06-20
Hi,

You don't say what motherboard you have, but I'd look for a BIOS update. That looks alot like a BIOS bug.

Regards
Ian Dobson

---

