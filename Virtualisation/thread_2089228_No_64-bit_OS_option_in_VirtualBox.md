---
title: "No 64-bit OS option in VirtualBox"
date: 2012-11-28
forum: Virtualisation
---

### Post by jaeddu on 2012-11-28
I am unable to create a 64-bit virtual machine in Oracle VirtualBox. Machine is Toshiba Satellite-L505. I am on 12.04 LTS. VBox v4.1.12_Ubuntu r77245. I have verified the processor using $cat /proc/cpuinfo. It lists 'lm' in "flags" section. It is my understanding that the 'lm' flag denotes a 64-bit processor. I also verified this was a 64-bit machine before I nuked win7 as primary OS. I am not dual booting. Ubuntu is only OS. I am trying to create the VBox to store the files from my win7 install. Any help is greatly appreciated. Thanks.

---

### Post by Habitual on 2012-11-28
is your host a 64bit OS?

---

### Post by jaeddu on 2012-11-28
It is. Ubuntu 12.04 LTS 64-bit

---

### Post by efflandt on 2012-11-28
Did you install it per **Debian-based Linux distributions** at [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

Did you add your user to **vboxusers** group in the host computer?

Works for me (PC in my sig) in 64-bit 12.04 as host.  As guests I installed a real slim 64-bit Debian base system using 512 MB and adding lxde myself to get a feel for Raspian for when I receive a Raspberry Pi (computer on a small board), 64-bit Debian with default gnome in 1 GB to figure out how to get audio working in the other lxde vbox, and 64-bit Ubuntu 12.10 guest that I gave 2 to 3 GB and 2 cores.  Although, in Debian versions I had to remove their older default guest additions to use current 4.2.4 guest additions included in /usr/share/virtualbox (which requires kernel headers in the guests).

How much RAM does your laptop have and how many cores?  What OS are you trying to install as a guest in vbox?

---

### Post by jaeddu on 2012-11-29
I installed from Software Center. I added user to vboxusers. I have Pentium(R) Dual-Core CPU T4400 @ 2.20GHz × 2 with 2.8GiB usable RAM. I am trying to install Windows 7 64-bit. When i first start the process of creating virtual box, I am unable to select a 64-bit version of anything. I am using the same Linux distro and VBox version on my other laptop without issue. That machine is i7 Vaio with 8Gib RAM. I belive the machine with the issue meets specs to run VBox. Very strange. Here are the results from running $cat /proc/cpuinfo:

cat /proc/cpuinfo
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 23
model name    : Pentium(R) Dual-Core CPU       T4400  @ 2.20GHz
stepping    : 10
microcode    : 0xa07
cpu MHz        : 1200.000
cache size    : 1024 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 2
apicid        : 0
initial apicid    : 0
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm xsave lahf_lm dtherm
bogomips    : 4388.84
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 1
vendor_id    : GenuineIntel
cpu family    : 6
model        : 23
model name    : Pentium(R) Dual-Core CPU       T4400  @ 2.20GHz
stepping    : 10
microcode    : 0xa07
cpu MHz        : 1200.000
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
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm xsave lahf_lm dtherm
bogomips    : 4388.94
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual

And for the record, I am not familiar with all the fields returned by that command. I was told the 'lm' preceding the 'constant_tsc' flag denotes 64-bit processor.

---

### Post by pkadeel on 2012-11-29
> **jaeddu said:**
> I am unable to create a 64-bit virtual machine in Oracle VirtualBox. Machine is Toshiba Satellite-L505. I am on 12.04 LTS. VBox v4.1.12_Ubuntu r77245. I have verified the processor using $cat /proc/cpuinfo. It lists 'lm' in "flags" section. It is my understanding that the 'lm' flag denotes a 64-bit processor. I also verified this was a 64-bit machine before I nuked win7 as primary OS. I am not dual booting. Ubuntu is only OS. I am trying to create the VBox to store the files from my win7 install. Any help is greatly appreciated. Thanks.
This is what Virtualbox help says
> **virtualbox]  p, li { white-space: pre-wrap said:**
> [COLOR=#0000ff]_1_[/COLOR][/URL][COLOR=#0000ff]_1_[/COLOR]] provided that the following conditions are met:
 
[LIST]
[*]You need a 64-bit processor with hardware virtualization support (see [[COLOR=#0000ff]_Section 10.3, “Hardware vs. software virtualization”_[/COLOR]]("http://ubuntuforums.org/ch10s03.html")).
[*]You must enable hardware virtualization for the particular VM for which you want 64-bit support; software virtualization is not supported for 64-bit VMs.
[*]If you want to use 64-bit guest support on a 32-bit host operating system, you must also select a 64-bit operating system for the particular VM. Since supporting 64 bits on 32-bit hosts incurs additional overhead, VirtualBox only enables this support upon explicit request.
[/LIST]
 On 64-bit hosts (which typically come with hardware virtualization support), 64-bit guest operating systems are always supported regardless of settings, so you can simply install a 64-bit operating system in the guest.
 Warning
 On any host, you should enable the I/O APIC for virtual machines that you intend to use in 64-bit mode. This is especially true for 64-bit Windows VMs. See [[COLOR=#0000ff]_Section 3.3.2, “"Advanced" tab”_[/COLOR]]("http://ubuntuforums.org/ch03s03.html#settings-general-advanced"). In addition, for 64-bit Windows guests, you should make sure that the VM uses the Intel networking device, since there is no 64-bit driver support for the AMD PCNet card; see [[COLOR=#0000ff]_Section 6.1, “Virtual networking hardware”_[/COLOR]]("http://ubuntuforums.org/ch06.html#nichardware").
 p, li { white-space: pre-wrap; }
According to this, we can create a 64bit guest on 32bit OS if

[LIST=1]
[*]we have a 64bit processor with virtualization support in BIOS
[*]we have enabled VT-x/AMD-V in VM guest settings
[*]we have enabled I/O APIC if the guest will be windows
[/LIST]

---

### Post by jaeddu on 2012-11-29
I looked in system BIOS and I do not see any explicit virtualization support. But I don't understand why that would prevent 64-bit guest on 64-bit host. I reinstalled from the link provided by efflandt just to be sure. Same result. When I just select the Windows 7 (no 64-bit option) and create the virtual machine, then I try to install the guest OS and i get an error from the guest machine saying  a 64-bit application is not supported.

---

### Post by jaeddu on 2012-11-29
I also am unable to create any 64-bit guest OS. Including Ubuntu.

---

### Post by pkadeel on 2012-11-29
> **jaeddu said:**
> I looked in system BIOS and I do not see any explicit virtualization support. But I don't understand why that would prevent 64-bit guest on 64-bit host. I reinstalled from the link provided by efflandt just to be sure. Same result. When I just select the Windows 7 (no 64-bit option) and create the virtual machine, then I try to install the guest OS and i get an error from the guest machine saying  a 64-bit application is not supported.
On a 64bit hardware 64bit OS you shall be able to install 64bit guest regardless of whether virtualization setting is enabled or disabled in BIOS and VM settings.

If enabling I/O APIC option on "System" tab of VM setting does not solve your problem then I would recommend upgrading your virtualbox software to version 4.2.4 directly from [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)
Instead of downloading the .deb file follow the "debian based linux distributions" method

---

### Post by Cheesemill on 2012-11-29
> **pkadeel said:**
> On a 64bit hardware 64bit OS you shall be able to install 64bit guest regardless of whether virtualization setting is enabled or disabled in BIOS and VM settings.
You'd think so but that isn't the case, you need hardware virtualization enabled to install any 64-bit OS.

@jaeddu
What make and model is your motherboard? You may just be unlucky and have a rare motherboard that doesn't support hardware virtualisation.

Also can you post the output of:
```
uname -a
```

---

### Post by jaeddu on 2012-11-29
I ran $cpuid and got this (uname -a results below):

Vendor ID: "GenuineIntel"; CPUID level 13

Intel-specific functions:
Version 0001067a:
Type 0 - Original OEM
Family 6 - Pentium Pro
Model 7 - Pentium III/Pentium III Xeon - external L2 cache
Stepping 10
Reserved 4

Extended brand string: "Pentium(R) Dual-Core CPU       T4400  @ 2.20GHz"
CLFLUSH instruction cache line size: 8
Initial APIC ID: 1
Hyper threading siblings: 2

Feature flags bfebfbff:
FPU    Floating Point Unit
VME    Virtual 8086 Mode Enhancements
DE     Debugging Extensions
PSE    Page Size Extensions
TSC    Time Stamp Counter
MSR    Model Specific Registers
PAE    Physical Address Extension
MCE    Machine Check Exception
CX8    COMPXCHG8B Instruction
APIC   On-chip Advanced Programmable Interrupt Controller present and enabled
SEP    Fast System Call
MTRR   Memory Type Range Registers
PGE    PTE Global Flag
MCA    Machine Check Architecture
CMOV   Conditional Move and Compare Instructions
FGPAT  Page Attribute Table
PSE-36 36-bit Page Size Extension
CLFSH  CFLUSH instruction
DS     Debug store
ACPI   Thermal Monitor and Clock Ctrl
MMX    MMX instruction set
FXSR   Fast FP/MMX Streaming SIMD Extensions save/restore
SSE    Streaming SIMD Extensions instruction set
SSE2   SSE2 extensions
SS     Self Snoop
HT     Hyper Threading
TM     Thermal monitor
31     reserved

TLB and cache info:
b1: unknown TLB/cache descriptor
b0: unknown TLB/cache descriptor
05: unknown TLB/cache descriptor
f0: unknown TLB/cache descriptor
57: unknown TLB/cache descriptor
56: unknown TLB/cache descriptor
78: unknown TLB/cache descriptor
30: unknown TLB/cache descriptor
b4: unknown TLB/cache descriptor
2c: unknown TLB/cache descriptor
Processor serial: 0001-067A-0000-0000-0000-0000



$ uname -a
Linux Satellite-L505 3.2.0-33-generic #52-Ubuntu SMP Thu Oct 18 16:29:15 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by Cheesemill on 2012-11-29
The problem is your CPU doesn't have hardware virtualisation support (VT-x).
You are never going to be able to run a 64-bit VM on that CPU.

[http://ark.intel.com/products/40739/Intel-Pentium-Processor-T4400-1M-Cache-2_20-GHz-800-MHz-FSB-Socket-P](http://ark.intel.com/products/40739/Intel-Pentium-Processor-T4400-1M-Cache-2_20-GHz-800-MHz-FSB-Socket-P)

---

### Post by pkadeel on 2012-11-29
> **Cheesemill said:**
> You'd think so but that isn't the case, you need hardware virtualization enabled to install any 64-bit OS.
Yes my fault. Hardware virtualization support is a must in BIOS to run a 64bit OS

---

### Post by jaeddu on 2012-11-29
Well that stinks. Thanks for your help. I really appreciate it.

---

