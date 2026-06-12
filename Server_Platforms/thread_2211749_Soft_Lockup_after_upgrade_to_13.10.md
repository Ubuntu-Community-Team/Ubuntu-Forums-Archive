---
title: "Soft Lockup after upgrade to 13.10"
date: 2014-03-17
forum: Server Platforms
---

### Post by andrew104 on 2014-03-17
I recently installed 13.04 server because I could not get the keyboard to work during a usb install of 13.10.  Once the system was set up and working fine, I did a do-release-upgrade to 13.10

Immediately upon reboot I began getting soft lockups.  Eventually I gave up and reinstalled 13.04.  I verified that it did work after reboot with no lockups, I have been running smoothly for days.  Decided to try an upgrade again (after making a backup of the system this time).  Same thing.  I can do a shutdown/restart and it usually works fine, but on a reboot the system begins giving me soft lockups.  Definitely a repeatable issue.

I have seen multiple reports of this, but nothing very current, and nothing that i think would apply to me.  Most of them consider it a hardware issue.  I am not Overclocking, have not changed the clock cycles in the BIOS, and the issue only occurs on 13.10 after a reboot.


Any help would be greatly appreciated.  I don't want to be stuck at 13.04 indefinitely.



```
andrew@deepthought:~$ uname -a
Linux deepthought 3.11.0-18-generic #32-Ubuntu SMP Tue Feb 18 21:11:14 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux



```

```
andrew@deepthought:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 21
model           : 1
model name      : AMD FX(tm)-4130 Quad-Core Processor
stepping        : 2
microcode       : 0x600063d
cpu MHz         : 1400.000
cache size      : 2048 KB
physical id     : 0
siblings        : 4
core id         : 0
cpu cores       : 2
apicid          : 16
initial apicid  : 0
fpu             : yes
fpu_exception   : yes
cpuid level     : 13
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni pclmulqdq monitor ssse3 cx16 sse4_1 sse4_2 popcnt aes xsave avx lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs xop skinit wdt lwp fma4 nodeid_msr topoext perfctr_core perfctr_nb arat cpb hw_pstate npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold
bogomips        : 7634.45
TLB size        : 1536 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 48 bits physical, 48 bits virtual
power management: ts ttp tm 100mhzsteps hwpstate cpb


processor       : 1
vendor_id       : AuthenticAMD
cpu family      : 21
model           : 1
model name      : AMD FX(tm)-4130 Quad-Core Processor
stepping        : 2
microcode       : 0x600063d
cpu MHz         : 1400.000
cache size      : 2048 KB
physical id     : 0
siblings        : 4
core id         : 1
cpu cores       : 2
apicid          : 17
initial apicid  : 1
fpu             : yes
fpu_exception   : yes
cpuid level     : 13
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni pclmulqdq monitor ssse3 cx16 sse4_1 sse4_2 popcnt aes xsave avx lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs xop skinit wdt lwp fma4 nodeid_msr topoext perfctr_core perfctr_nb arat cpb hw_pstate npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold
bogomips        : 7634.45
TLB size        : 1536 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 48 bits physical, 48 bits virtual
power management: ts ttp tm 100mhzsteps hwpstate cpb


processor       : 2
vendor_id       : AuthenticAMD
cpu family      : 21
model           : 1
model name      : AMD FX(tm)-4130 Quad-Core Processor
stepping        : 2
microcode       : 0x600063d
cpu MHz         : 1400.000
cache size      : 2048 KB
physical id     : 0
siblings        : 4
core id         : 2
cpu cores       : 2
apicid          : 18
initial apicid  : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 13
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni pclmulqdq monitor ssse3 cx16 sse4_1 sse4_2 popcnt aes xsave avx lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs xop skinit wdt lwp fma4 nodeid_msr topoext perfctr_core perfctr_nb arat cpb hw_pstate npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold
bogomips        : 7634.45
TLB size        : 1536 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 48 bits physical, 48 bits virtual
power management: ts ttp tm 100mhzsteps hwpstate cpb


processor       : 3
vendor_id       : AuthenticAMD
cpu family      : 21
model           : 1
model name      : AMD FX(tm)-4130 Quad-Core Processor
stepping        : 2
microcode       : 0x600063d
cpu MHz         : 1400.000
cache size      : 2048 KB
physical id     : 0
siblings        : 4
core id         : 3
cpu cores       : 2
apicid          : 19
initial apicid  : 3
fpu             : yes
fpu_exception   : yes
cpuid level     : 13
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni pclmulqdq monitor ssse3 cx16 sse4_1 sse4_2 popcnt aes xsave avx lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs xop skinit wdt lwp fma4 nodeid_msr topoext perfctr_core perfctr_nb arat cpb hw_pstate npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold
bogomips        : 7634.45
TLB size        : 1536 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 48 bits physical, 48 bits virtual
power management: ts ttp tm 100mhzsteps hwpstate cpb



```


```
andrew@deepthought:~$ cat /proc/meminfo
MemTotal:        7901236 kB
MemFree:         7508812 kB
Buffers:           16480 kB
Cached:           256372 kB
SwapCached:            0 kB
Active:            41688 kB
Inactive:         247776 kB
Active(anon):      16868 kB
Inactive(anon):      496 kB
Active(file):      24820 kB
Inactive(file):   247280 kB
Unevictable:           0 kB
Mlocked:               0 kB
SwapTotal:       8105980 kB
SwapFree:        8105980 kB
Dirty:                 0 kB
Writeback:             0 kB
AnonPages:         16612 kB
Mapped:            14552 kB
Shmem:               752 kB
Slab:              28292 kB
SReclaimable:      13172 kB
SUnreclaim:        15120 kB
KernelStack:        1584 kB
PageTables:         3940 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:    12056596 kB
Committed_AS:     131900 kB
VmallocTotal:   34359738367 kB
VmallocUsed:      294164 kB
VmallocChunk:   34359440932 kB
HardwareCorrupted:     0 kB
AnonHugePages:         0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
DirectMap4k:       41472 kB
DirectMap2M:     1775616 kB
DirectMap1G:     6291456 kB



```

```
andrew@deepthought:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] RS780 Host Bridge
00:01.0 PCI bridge: ASUSTeK Computer Inc. AMD RS780/RS880 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 0)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode]
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.1 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0 USB OHCI1 Controller
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.1 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0 USB OHCI1 Controller
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller (rev 3c)
00:14.1 IDE interface: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 IDE Controller
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge
00:14.5 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 0
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 5
01:05.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RS780L [Radeon 3000]
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 09)



```

---

### Post by andrew104 on 2014-03-17
Just found a suggestion to try a kernel update.  Testing that now...

---

### Post by andrew104 on 2014-03-17
I used [https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater](https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater) to update the kernel to 3.11.10-03111006-generic and it seems to be stable so far.  Can reboot or cold start with no soft lockups.  Hopefully that solved it.

---

### Post by andrew104 on 2014-03-17
Well, it apparantly did solve my original problem but created a new one.  This kernel doesn't have aufs, which I need.  The 3.11.0-18-generic #32 kernel does.  Now how do I find a working kernel with aufs support.....

---

