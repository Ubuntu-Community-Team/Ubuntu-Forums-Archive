---
title: "Cant see/use 2 CPU cores."
date: 2009-12-31
forum: Server Platforms
---

### Post by steven.jones on 2009-12-31
Hi,

I have just installed Ubuntu server on an existing home server only to find I cannot see the second core in top or /proc/cpuinfo.

steven@ubuntu:~$ uname -a
Linux ubuntu 2.6.31-16-server #53-Ubuntu SMP Tue Dec 8 05:08:02 UTC 2009 x86_64 GNU/Linux
steven@ubuntu:~$

steven@ubuntu:~$ cat /proc/cpuinfo

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Celeron(R) CPU        E1200  @ 1.60GHz
stepping        : 13
cpu MHz         : 1200.000
cache size      : 512 KB
physical id     : 0
siblings        : 1
core id         : 0
cpu cores       : 1
apicid          : 0
initial apicid  : 0
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx f
xsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc up arch_perfmon pebs bts rep_good pni dtes64 monitor ds_cpl
 est tm2 ssse3 cx16 xtpr pdcm lahf_lm
bogomips        : 3199.67
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:


Any ideas please?

regards

Steven

---

### Post by Mister.Vash on 2010-01-01
Two things that come to mind...

You don't have maxcpus=1 specified on the kernel line in your grub boot options do you?

The other thing, some motherboards allow for disabling a core via the bios - have you gone into the bios and made sure that a.) the bios is seeing it as a dual core, and 2.) making sure that it doesn't have a setting someplace to disable a core?

---

### Post by steven.jones on 2010-01-01
I am installing Debian right now so cant check grub, not something I did by hand....The motherboard should be set for 2 cores....it sees two cores in the bios, I couldnt find anything that says only allow one core in the Asus bios (Ive seen that before, on other boards, will double check though)....

I will se if the Debian install also has such an issue which would point to the bios....or maybe lack of interrupts? its a very full box not sure...

dmesg,

=======
root@ubuntu:~# dmesg |more
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-16-server (buildd@crested) (gcc version 4.4.
1 (Ubuntu 4.4.1-4ubuntu8) ) #53-Ubuntu SMP Tue Dec 8 05:08:02 UTC 2009 (Ubuntu 2
.6.31-16.53-server)
[    0.000000] Command line: BOOT_IMAGE=/vmlinuz-2.6.31-16-server root=/dev/mapp
er/root-root ro rootdelay=10 quiet splash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e800 (usable)
[    0.000000]  BIOS-e820: 000000000009e800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cff80000 (usable)
[    0.000000]  BIOS-e820: 00000000cff80000 - 00000000cff8e000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cff8e000 - 00000000cffe0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cffe0000 - 00000000d0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000130000000 (usable)
[    0.000000] DMI 2.4 present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) =
=> (reserved)
[    0.000000] last_pfn = 0x130000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-DFFFF write-protect
[    0.000000]   E0000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0D0000000 mask FF0000000 uncachable
[    0.000000]   1 base 0E0000000 mask FE0000000 uncachable
[    0.000000]   2 base 000000000 mask F00000000 write-back
[    0.000000]   3 base 100000000 mask FE0000000 write-back
[    0.000000]   4 base 120000000 mask FF0000000 write-back
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000d0000000 - 0000000100000000 (usable) =
=> (reserved)
[    0.000000] last_pfn = 0xcff80 max_arch_pfn = 0x400000000
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009e800 (usable)
[    0.000000]  modified: 000000000009e800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000cff80000 (usable)
[    0.000000]  modified: 00000000cff80000 - 00000000cff8e000 (ACPI data)
[    0.000000]  modified: 00000000cff8e000 - 00000000cffe0000 (ACPI NVS)
[    0.000000]  modified: 00000000cffe0000 - 00000000d0000000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000130000000 (usable)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] init_memory_mapping: 0000000000000000-00000000cff80000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0000000000 - 00cfe00000 page 2M
[    0.000000]  00cfe00000 - 00cff80000 page 4k
[    0.000000] kernel direct mapping tables up to cff80000 @ 10000-16000
[    0.000000] init_memory_mapping: 0000000100000000-0000000130000000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0100000000 - 0130000000 page 2M
[    0.000000] kernel direct mapping tables up to 130000000 @ 14000-1a000
[    0.000000] RAMDISK: 378dc000 - 37fef8d8
[    0.000000] ACPI: RSDP 00000000000fbb80 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 00000000cff80000 00038 (v01 A_M_I_ OEMRSDT  08000717 M
SFT 00000097)
[    0.000000] ACPI: FACP 00000000cff80200 00084 (v02 A_M_I_ OEMFACP  08000717 M
SFT 00000097)
[    0.000000] ACPI: DSDT 00000000cff805c0 08E13 (v01  A0840 A0840001 00000001 I
NTL 20060113)
[    0.000000] ACPI: FACS 00000000cff8e000 00040
[    0.000000] ACPI: MCFG 00000000cff80400 0003C (v01 A_M_I_ OEMMCFG  08000717 M
SFT 00000097)
[    0.000000] ACPI: OEMB 00000000cff8e040 00081 (v01 A_M_I_ AMI_OEM  08000717 M
SFT 00000097)
[    0.000000] ACPI: HPET 00000000cff893e0 00038 (v01 A_M_I_ OEMHPET  08000717 M
SFT 00000097)
[    0.000000] ACPI: OSFR 00000000cff89420 000B0 (v01 A_M_I_ OEMOSFR  08000717 M
SFT 00000097)
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000130000000
[    0.000000] Bootmem setup node 0 0000000000000000-0000000130000000
[    0.000000]   NODE_DATA [0000000000015000 - 0000000000019fff]
[    0.000000]   bootmap [000000000001a000 -  000000000003ffff] pages 26
[    0.000000] (8 early reservations) ==> bootmem [0000000000 - 0130000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 -
 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 -
 0000008000]
[    0.000000]   #2 [0001000000 - 00019e0ccc]    TEXT DATA BSS ==> [0001000000 -
 00019e0ccc]
[    0.000000]   #3 [00378dc000 - 0037fef8d8]          RAMDISK ==> [00378dc000 -
 0037fef8d8]
[    0.000000]   #4 [000009e800 - 0000100000]    BIOS reserved ==> [000009e800 -
 0000100000]
[    0.000000]   #5 [00019e1000 - 00019e1288]              BRK ==> [00019e1000 -
 00019e1288]
[    0.000000]   #6 [0000010000 - 0000014000]          PGTABLE ==> [0000010000 -
 0000014000]
[    0.000000]   #7 [0000014000 - 0000015000]          PGTABLE ==> [0000014000 -
 0000015000]
[    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
[    0.000000]  [ffffea0000000000-ffffea00043fffff] PMD -> [ffff880028600000-fff
f88002bffffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00130000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009e
[    0.000000]     0: 0x00000100 -> 0x000cff80
[    0.000000]     0: 0x00100000 -> 0x00130000
[    0.000000] On node 0 totalpages: 1048334
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 105 pages reserved
[    0.000000]   DMA zone: 3821 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 833464 pages, LIFO batch:31
[    0.000000]   Normal zone: 2688 pages used for memmap
[    0.000000]   Normal zone: 193920 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: No APIC-table, disabling MPS
[    0.000000] ACPI: HPET id: 0xffffffff base: 0xfed00000
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
8><----



I'd submit a bug report, but I seem to need to join a wiki/launchpad which keeps failing as I odnt have a valid email address, which actually I do.

PPl make things to complex....KISS, Keep It Simple and Stupid...

:/

---

### Post by steven.jones on 2010-01-01
I cant post a complete dmesg, the software says too many images...

Like I said KISS....

---

### Post by steven.jones on 2010-01-02
I think I have a hint why,

[http://ubuntuforums.org/showthread.php?t=1084326](http://ubuntuforums.org/showthread.php?t=1084326)

Unfortunately this was grub and now we are on grub2 and I hated grub because it was just OTT....now Ive seen grub2 and OMG....

OK solved it,

[http://ubuntuforums.org/showthread.php?t=272176](http://ubuntuforums.org/showthread.php?t=272176)

"Are your APIC/ACPI/SMP settings  enabled in your BIOS?"

my APIC/ACPI was set to disabled, once I switched to enabled top sees two cores!

oops

:/

---

