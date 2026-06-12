---
title: "Intense Static After Extended Guitar Amp Sim Use"
date: 2017-01-09
forum: Ubuntu Studio
---

### Post by muddpup64 on 2017-01-09
Hello ya'll!

I've been having this issue where, after my laptop has run for a while, when I use my various amp simulator it produces an unbearable, ear bleeding, static. It works fine directly after restarting. Is it possible that over time the processes of my computer are slowly building up and can no longer keep up? I do run this all through wine (Guitar Rig 5 and Amplitube), is it possible that this may be the problem? I did have some latency issues after set up. Maybe I'm missing something.

Thanks guys!

---

### Post by marseille2 on 2017-01-10
That's a lot of factors to guess at... 


[LIST]
[*]Laptop specs
[*]Wine version
[*]Kernel type
[*]Sound Layer set-up
[*]Power conditioning
[/LIST]

 If you can, share a bit more about tech specs... If I remember right... [Crocoduck]("https://ubuntuforums.org/member.php?u=1635112") is pretty good at working with wine and getting the most out of CPU performance.

---

### Post by muddpup64 on 2017-01-10
Laptop Spec: Lenovo T410i
64 bit, Ubuntu 16.04 LTS
7.6 gb of RAM
Intel i3 Processor

I can't seem to be able to double check what headers I'm using but they should actually be the low latency headers. If I remember correctly.

I'm unfamilar with the terms Sound Layering and Power Conditioning

---

### Post by muddpup64 on 2017-01-10
[ATTACH=CONFIG]273139[/ATTACH]

Maybe this will help.

---

### Post by marseille2 on 2017-01-11
Hmmm... It's hard to say. Personally, I'd start out by testing sound without wine. If you sound produces static without wine then the culprit can't be the plugin. 

I've had some plugins in wine that would crash and produce a never ending noise, that forced me to kill all wine processes (normally if I run 1 plugin -- i use Carla if I want to use Windows VSTs -- it has at least 3 windows processes ... all of them have to die). But I've also gone through horrible distortion with static using pulseaudio ... depending on Ubuntu OS version (these days I'm sticking with 14.04 and I just run the 4.x kernel). 

There's also cases of ALSA not playing well in certain set-ups which seems to blow sound altogether and sends folks to launchpad to report bugs (OUCH). As for latency... if your using the RT-kernel and your sound is good without wine, then ... assuming you're using [hopefully] wine-rt (their real time patch to lower latency), debug wine (see [developer's guide]("https://wiki.winehq.org/Wine_Developer%27s_Guide/Debugging_Wine#Using_the_Wine_Debugger")). It could be as easy as changing wine versions ... or not.

If all that fails and you can't trace it back to the problem software or the laptop ... check your [power]("http://furmansound.com/page.php?div=01&id=WHY_PWR").

BTW... you can check your kernel version with:

```
$ uname -a
```

You might want to also post the output of:

```
$ dmesg
```

... just in case there really is something going on with computer hardware. But probably start with debugging wine...

---

### Post by muddpup64 on 2017-01-11
I don't really have any trouble with any other sound programs (that being said it could be the audio interface for some reason, given the circumstances I doubt it). I actually have an all linux amp sim I could use. Let me run that for a little while and see if I can replicate the results, eliminating wine as the issue.

Furthermore, once I get home, I can run some commands to give you more information about the problem.

---

### Post by CrocoDuck on 2017-01-11
> **marseille2 said:**
> If I remember right... [Crocoduck]("https://ubuntuforums.org/member.php?u=1635112") is pretty good at working with wine and getting the most out of CPU performance.

Oh really?!! :lolflag: Actually I think I am not very keen of wine... I never use it. The last time I messed with it was a solid 6 years ago I think.

Other than what suggested by marseille2, I would double check you don't have any feedback loop, either software or hardware.

---

### Post by muddpup64 on 2017-01-11
I don't really have any trouble with any other sound programs (that being said it could be the audio interface for some reason, given the circumstances I doubt it). I actually have an all linux amp sim I could use. Let me run that for a little while and see if I can replicate the results, eliminating wine as the issue.

Furthermore, once I get home, I can run some commands to give you more information about the problem.

---

### Post by muddpup64 on 2017-01-11
uname -a
Produces: ```
Linux Foghorn 4.4.0-57-lowlatency #78-Ubuntu SMP PREEMPT Sat Dec 10 01:37:35 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
```

dmesg
Produces: ```
[    0.000000] microcode: CPU0 microcode updated early to revision 0xe, date = 2013-06-26
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 4.4.0-57-lowlatency (buildd@lgw01-54) (gcc version 5.4.0 20160609 (Ubuntu 5.4.0-6ubuntu1~16.04.4) ) #78-Ubuntu SMP PREEMPT Sat Dec 10 01:37:35 UTC 2016 (Ubuntu 4.4.0-57.78-lowlatency 4.4.35)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-57-lowlatency root=UUID=72a9e6a3-2b57-407b-bd62-c7223c8ece94 ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] x86/fpu: Legacy x87 FPU detected.
[    0.000000] x86/fpu: Using 'lazy' FPU context switches.
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009e7ff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009e800-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000d2000-0x00000000000d3fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000dc000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000bb27bfff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bb27c000-0x00000000bb281fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000bb282000-0x00000000bb35efff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bb35f000-0x00000000bb370fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000bb371000-0x00000000bb3f1fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000bb3f2000-0x00000000bb40efff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000bb40f000-0x00000000bb46efff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bb46f000-0x00000000bb667fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000bb668000-0x00000000bb6e7fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000bb6e8000-0x00000000bb70efff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000bb70f000-0x00000000bb716fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bb717000-0x00000000bb71efff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000bb71f000-0x00000000bb76bfff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bb76c000-0x00000000bb777fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000bb778000-0x00000000bb77afff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000bb77b000-0x00000000bb78afff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000bb78b000-0x00000000bb78bfff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000bb78c000-0x00000000bb79efff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000bb79f000-0x00000000bb7fefff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000bb7ff000-0x00000000bb7fffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bb800000-0x00000000bfffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000feaff000-0x00000000feafffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec0ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed00000-0x00000000fed003ff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed8ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x00000001fbffffff] usable
[    0.000000] BIOS-e820: [mem 0x0000000200000000-0x000000023bffffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.6 present.
[    0.000000] DMI: LENOVO 2516CTO/2516CTO, BIOS 6IET78WW (1.38 ) 05/20/2011
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] e820: last_pfn = 0x23c000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-D3FFF write-protect
[    0.000000]   D4000-DBFFF uncachable
[    0.000000]   DC000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 disabled
[    0.000000]   1 base 000000000 mask F80000000 write-back
[    0.000000]   2 base 080000000 mask FC0000000 write-back
[    0.000000]   3 base 100000000 mask F00000000 write-back
[    0.000000]   4 base 200000000 mask FC0000000 write-back
[    0.000000]   5 base 23C000000 mask FFC000000 uncachable
[    0.000000]   6 base 0BC000000 mask FFC000000 uncachable
[    0.000000]   7 disabled
[    0.000000] x86/PAT: Configuration [0-7]: WB  WC  UC- UC  WB  WC  UC- WT  
[    0.000000] original variable MTRRs
[    0.000000] reg 1, base: 0GB, range: 2GB, type WB
[    0.000000] reg 2, base: 2GB, range: 1GB, type WB
[    0.000000] reg 3, base: 4GB, range: 4GB, type WB
[    0.000000] reg 4, base: 8GB, range: 1GB, type WB
[    0.000000] reg 5, base: 9152MB, range: 64MB, type UC
[    0.000000] reg 6, base: 3008MB, range: 64MB, type UC
[    0.000000] total RAM covered: 8064M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 128M     num_reg: 6  lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3008MB, range: 64MB, type UC
[    0.000000] reg 3, base: 4GB, range: 4GB, type WB
[    0.000000] reg 4, base: 8GB, range: 1GB, type WB
[    0.000000] reg 5, base: 9152MB, range: 64MB, type UC
[    0.000000] e820: update [mem 0xbc000000-0xffffffff] usable ==> reserved
[    0.000000] e820: last_pfn = 0xbb800 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000f68b0-0x000f68bf] mapped at [ffff8800000f68b0]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000098000] 98000 size 24576
[    0.000000] BRK [0x021fc000, 0x021fcfff] PGTABLE
[    0.000000] BRK [0x021fd000, 0x021fdfff] PGTABLE
[    0.000000] BRK [0x021fe000, 0x021fefff] PGTABLE
[    0.000000] BRK [0x021ff000, 0x021fffff] PGTABLE
[    0.000000] BRK [0x02200000, 0x02200fff] PGTABLE
[    0.000000] BRK [0x02201000, 0x02201fff] PGTABLE
[    0.000000] RAMDISK: [mem 0x33a0a000-0x35cfcfff]
[    0.000000] ACPI: Early table checksum verification disabled
[    0.000000] ACPI: RSDP 0x00000000000F6870 000024 (v02 LENOVO)
[    0.000000] ACPI: XSDT 0x00000000BB7EF2C4 000094 (v01 LENOVO TP-6I    00001380  LTP 00000000)
[    0.000000] ACPI: FACP 0x00000000BB7EF400 0000F4 (v04 LENOVO TP-6I    00001380 LNVO 00000001)
[    0.000000] ACPI BIOS Warning (bug): 32/64X length mismatch in FADT/Pm1aControlBlock: 16/32 (20150930/tbfadt-623)
[    0.000000] ACPI BIOS Warning (bug): Invalid length for FADT/Pm1aControlBlock: 32, using default 16 (20150930/tbfadt-704)
[    0.000000] ACPI: DSDT 0x00000000BB7EF7D1 00F36C (v01 LENOVO TP-6I    00001380 MSFT 03000001)
[    0.000000] ACPI: FACS 0x00000000BB6E7000 000040
[    0.000000] ACPI: FACS 0x00000000BB6E7000 000040
[    0.000000] ACPI: SSDT 0x00000000BB7EF5B4 00021D (v01 LENOVO TP-6I    00001380 MSFT 03000001)
[    0.000000] ACPI: ECDT 0x00000000BB7FEB3D 000052 (v01 LENOVO TP-6I    00001380 LNVO 00000001)
[    0.000000] ACPI: APIC 0x00000000BB7FEB8F 000084 (v01 LENOVO TP-6I    00001380 LNVO 00000001)
[    0.000000] ACPI: MCFG 0x00000000BB7FEC4B 00003C (v01 LENOVO TP-6I    00001380 LNVO 00000001)
[    0.000000] ACPI: HPET 0x00000000BB7FEC87 000038 (v01 LENOVO TP-6I    00001380 LNVO 00000001)
[    0.000000] ACPI: ASF! 0x00000000BB7FEDBE 0000A4 (v16 LENOVO TP-6I    00001380 PTL  00000001)
[    0.000000] ACPI: SLIC 0x00000000BB7FEE62 000176 (v01 LENOVO TP-6I    00001380  LTP 00000000)
[    0.000000] ACPI: BOOT 0x00000000BB7FEFD8 000028 (v01 LENOVO TP-6I    00001380  LTP 00000001)
[    0.000000] ACPI: SSDT 0x00000000BB6E591A 00084B (v01 LENOVO TP-6I    00001380 INTL 20050513)
[    0.000000] ACPI: TCPA 0x00000000BB78B000 000032 (v02 PTL     CRESTLN 06040000      00005A52)
[    0.000000] ACPI: SSDT 0x00000000BB77A000 0009F1 (v01 PmRef  CpuPm    00003000 INTL 20061109)
[    0.000000] ACPI: SSDT 0x00000000BB779000 000259 (v01 PmRef  Cpu0Tst  00003000 INTL 20061109)
[    0.000000] ACPI: SSDT 0x00000000BB778000 00049F (v01 PmRef  ApTst    00003000 INTL 20061109)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000023bffffff]
[    0.000000] NODE_DATA(0) allocated [mem 0x23bff4000-0x23bff8fff]
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x0000000000001000-0x0000000000ffffff]
[    0.000000]   DMA32    [mem 0x0000000001000000-0x00000000ffffffff]
[    0.000000]   Normal   [mem 0x0000000100000000-0x000000023bffffff]
[    0.000000]   Device   empty
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x0000000000001000-0x000000000009dfff]
[    0.000000]   node   0: [mem 0x0000000000100000-0x00000000bb27bfff]
[    0.000000]   node   0: [mem 0x00000000bb282000-0x00000000bb35efff]
[    0.000000]   node   0: [mem 0x00000000bb40f000-0x00000000bb46efff]
[    0.000000]   node   0: [mem 0x00000000bb70f000-0x00000000bb716fff]
[    0.000000]   node   0: [mem 0x00000000bb71f000-0x00000000bb76bfff]
[    0.000000]   node   0: [mem 0x00000000bb7ff000-0x00000000bb7fffff]
[    0.000000]   node   0: [mem 0x0000000100000000-0x00000001fbffffff]
[    0.000000]   node   0: [mem 0x0000000200000000-0x000000023bffffff]
[    0.000000] Initmem setup node 0 [mem 0x0000000000001000-0x000000023bffffff]
[    0.000000] On node 0 totalpages: 2044844
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 21 pages reserved
[    0.000000]   DMA zone: 3997 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 11921 pages used for memmap
[    0.000000]   DMA32 zone: 762895 pages, LIFO batch:31
[    0.000000]   Normal zone: 20224 pages used for memmap
[    0.000000]   Normal zone: 1277952 pages, LIFO batch:31
[    0.000000] Reserving Intel graphics stolen memory at 0xbe000000-0xbfffffff
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] smpboot: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: [mem 0x00000000-0x00000fff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009efff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000d1fff]
[    0.000000] PM: Registered nosave memory: [mem 0x000d2000-0x000d3fff]
[    0.000000] PM: Registered nosave memory: [mem 0x000d4000-0x000dbfff]
[    0.000000] PM: Registered nosave memory: [mem 0x000dc000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xbb27c000-0xbb281fff]
[    0.000000] PM: Registered nosave memory: [mem 0xbb35f000-0xbb370fff]
[    0.000000] PM: Registered nosave memory: [mem 0xbb371000-0xbb3f1fff]
[    0.000000] PM: Registered nosave memory: [mem 0xbb3f2000-0xbb40efff]
[    0.000000] PM: Registered nosave memory: [mem 0xbb46f000-0xbb667fff]
[    0.000000] PM: Registered nosave memory: [mem 0xbb668000-0xbb6e7fff]
[    0.000000] PM: Registered nosave memory: [mem 0xbb6e8000-0xbb70efff]
[    0.000000] PM: Registered nosave memory: [mem 0xbb717000-0xbb71efff]
[    0.000000] PM: Registered nosave memory: [mem 0xbb76c000-0xbb777fff]
[    0.000000] PM: Registered nosave memory: [mem 0xbb778000-0xbb77afff]
[    0.000000] PM: Registered nosave memory: [mem 0xbb77b000-0xbb78afff]
[    0.000000] PM: Registered nosave memory: [mem 0xbb78b000-0xbb78bfff]
[    0.000000] PM: Registered nosave memory: [mem 0xbb78c000-0xbb79efff]
[    0.000000] PM: Registered nosave memory: [mem 0xbb79f000-0xbb7fefff]
[    0.000000] PM: Registered nosave memory: [mem 0xbb800000-0xbfffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xc0000000-0xdfffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xefffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xfeafefff]
[    0.000000] PM: Registered nosave memory: [mem 0xfeaff000-0xfeafffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfeb00000-0xfebfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec0ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec10000-0xfecfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed00000-0xfed1bfff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed1c000-0xfed8ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed90000-0xfedfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xfeffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xff000000-0xffffffff]
[    0.000000] PM: Registered nosave memory: [mem 0x1fc000000-0x1ffffffff]
[    0.000000] e820: [mem 0xc0000000-0xdfffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] clocksource: refined-jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 1910969940391419 ns
[    0.000000] setup_percpu: NR_CPUS:512 nr_cpumask_bits:512 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 34 pages/cpu @ffff88023bc00000 s98648 r8192 d32424 u524288
[    0.000000] pcpu-alloc: s98648 r8192 d32424 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 2012614
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-57-lowlatency root=UUID=72a9e6a3-2b57-407b-bd62-c7223c8ece94 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 7927092K/8179376K available (8485K kernel code, 1295K rwdata, 3960K rodata, 1428K init, 1316K bss, 252284K reserved, 0K cma-reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Preemptible hierarchical RCU implementation.
[    0.000000]     Build-time adjustment of leaf fanout to 64.
[    0.000000]     RCU restricting CPUs from NR_CPUS=512 to nr_cpu_ids=4.
[    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=64, nr_cpu_ids=4
[    0.000000] NR_IRQS:33024 nr_irqs:456 16
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] clocksource: hpet: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 133484882848 ns
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] tsc: Detected 2128.056 MHz processor
[    0.000038] Calibrating delay loop (skipped), value calculated using timer frequency.. 4256.11 BogoMIPS (lpj=2128056)
[    0.000042] pid_max: default: 32768 minimum: 301
[    0.000049] ACPI: Core revision 20150930
[    0.017223] ACPI: 6 ACPI AML tables successfully acquired and loaded
[    0.017249] Security Framework initialized
[    0.017251] Yama: becoming mindful.
[    0.017273] AppArmor: AppArmor initialized
[    0.017903] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.019993] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.020867] Mount-cache hash table entries: 16384 (order: 5, 131072 bytes)
[    0.020881] Mountpoint-cache hash table entries: 16384 (order: 5, 131072 bytes)
[    0.021172] Initializing cgroup subsys io
[    0.021177] Initializing cgroup subsys memory
[    0.021186] Initializing cgroup subsys devices
[    0.021189] Initializing cgroup subsys freezer
[    0.021191] Initializing cgroup subsys net_cls
[    0.021194] Initializing cgroup subsys perf_event
[    0.021196] Initializing cgroup subsys net_prio
[    0.021201] Initializing cgroup subsys hugetlb
[    0.021203] Initializing cgroup subsys pids
[    0.021226] CPU: Physical Processor ID: 0
[    0.021227] CPU: Processor Core ID: 0
[    0.021234] mce: CPU supports 9 MCE banks
[    0.021246] CPU0: Thermal monitoring enabled (TM1)
[    0.021254] process: using mwait in idle threads
[    0.021258] Last level iTLB entries: 4KB 512, 2MB 7, 4MB 7
[    0.021259] Last level dTLB entries: 4KB 512, 2MB 32, 4MB 32, 1GB 0
[    0.021649] Freeing SMP alternatives memory: 28K (ffffffff820aa000 - ffffffff820b1000)
[    0.031129] ftrace: allocating 32061 entries in 126 pages
[    0.049381] smpboot: APIC(0) Converting physical 0 to logical package 0
[    0.049385] smpboot: Max logical packages: 2
[    0.049895] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.161848] smpboot: CPU0: Intel(R) Core(TM) i3 CPU       M 330  @ 2.13GHz (family: 0x6, model: 0x25, stepping: 0x2)
[    0.161863] Performance Events: PEBS fmt1+, 16-deep LBR, Westmere events, Intel PMU driver.
[    0.161884] core: CPUID marked event: 'bus cycles' unavailable
[    0.161887] ... version:                3
[    0.161889] ... bit width:              48
[    0.161890] ... generic registers:      4
[    0.161891] ... value mask:             0000ffffffffffff
[    0.161892] ... max period:             000000007fffffff
[    0.161893] ... fixed-purpose events:   3
[    0.161894] ... event mask:             000000070000000f
[    0.170881] x86: Booting SMP configuration:
[    0.170887] .... node  #0, CPUs:      #1
[    0.173348] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.175881]  #2
[    0.176454] microcode: CPU2 microcode updated early to revision 0xe, date = 2013-06-26
[    0.180883]  #3
[    0.183203] x86: Booted up 1 node, 4 CPUs
[    0.183208] smpboot: Total of 4 processors activated (17024.44 BogoMIPS)
[    0.185952] devtmpfs: initialized
[    0.189329] evm: security.selinux
[    0.189331] evm: security.SMACK64
[    0.189332] evm: security.SMACK64EXEC
[    0.189333] evm: security.SMACK64TRANSMUTE
[    0.189334] evm: security.SMACK64MMAP
[    0.189335] evm: security.ima
[    0.189336] evm: security.capability
[    0.189419] PM: Registering ACPI NVS region [mem 0xbb371000-0xbb3f1fff] (528384 bytes)
[    0.189430] PM: Registering ACPI NVS region [mem 0xbb668000-0xbb6e7fff] (524288 bytes)
[    0.189439] PM: Registering ACPI NVS region [mem 0xbb76c000-0xbb777fff] (49152 bytes)
[    0.189441] PM: Registering ACPI NVS region [mem 0xbb77b000-0xbb78afff] (65536 bytes)
[    0.189444] PM: Registering ACPI NVS region [mem 0xbb78c000-0xbb79efff] (77824 bytes)
[    0.189544] clocksource: jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 1911260446275000 ns
[    0.189652] pinctrl core: initialized pinctrl subsystem
[    0.189791] RTC time:  2:02:22, date: 01/11/17
[    0.189953] NET: Registered protocol family 16
[    0.193859] cpuidle: using governor ladder
[    0.197556] cpuidle: using governor menu
[    0.197566] PCCT header not found.
[    0.197654] Simple Boot Flag at 0x35 set to 0x1
[    0.197683] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.197686] ACPI: bus type PCI registered
[    0.197688] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.197772] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.197775] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.197795] PCI: Using configuration type 1 for base access
[    0.203319] ACPI: Added _OSI(Module Device)
[    0.203321] ACPI: Added _OSI(Processor Device)
[    0.203323] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.203325] ACPI: Added _OSI(Processor Aggregator Device)
[    0.204981] ACPI : EC: EC description table is found, configuring boot EC
[    0.204997] ACPI : EC: EC started
[    0.209806] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.285126] ACPI: Dynamic OEM Table Load:
[    0.285135] ACPI: SSDT 0xFFFF880231CDA800 00042D (v01 PmRef  Cpu0Ist  00003000 INTL 20061109)
[    0.285690] ACPI: Dynamic OEM Table Load:
[    0.285696] ACPI: SSDT 0xFFFF880231CDB000 0006B2 (v01 PmRef  Cpu0Cst  00003001 INTL 20061109)
[    0.286459] ACPI: Dynamic OEM Table Load:
[    0.286465] ACPI: SSDT 0xFFFF880231CEB000 000303 (v01 PmRef  ApIst    00003000 INTL 20061109)
[    0.287028] ACPI: Dynamic OEM Table Load:
[    0.287034] ACPI: SSDT 0xFFFF880231D0BC00 000119 (v01 PmRef  ApCst    00003000 INTL 20061109)
[    0.289123] ACPI: Interpreter enabled
[    0.289147] ACPI: (supports S0 S3 S4 S5)
[    0.289149] ACPI: Using IOAPIC for interrupt routing
[    0.289178] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.296038] ACPI: Power Resource [PUBS] (on)
[    0.296895] acpi PNP0C0A:01: ACPI dock station (docks/bays count: 1)
[    0.299445] acpi LNXIOBAY:00: ACPI dock station (docks/bays count: 2)
[    0.301868] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11)
[    0.301968] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11)
[    0.302045] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
[    0.302142] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11)
[    0.302251] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11)
[    0.302349] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11)
[    0.302425] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
[    0.302522] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11)
[    0.302619] ACPI: PCI Root Bridge [UNCR] (domain 0000 [bus ff])
[    0.302625] acpi PNP0A03:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.302631] acpi PNP0A03:00: _OSC failed (AE_NOT_FOUND); disabling ASPM
[    0.302691] PCI host bridge to bus 0000:ff
[    0.302695] pci_bus 0000:ff: root bus resource [bus ff]
[    0.302703] pci 0000:ff:00.0: [8086:2c62] type 00 class 0x060000
[    0.302769] pci 0000:ff:00.1: [8086:2d01] type 00 class 0x060000
[    0.302833] pci 0000:ff:02.0: [8086:2d10] type 00 class 0x060000
[    0.302892] pci 0000:ff:02.1: [8086:2d11] type 00 class 0x060000
[    0.302945] pci 0000:ff:02.2: [8086:2d12] type 00 class 0x060000
[    0.302997] pci 0000:ff:02.3: [8086:2d13] type 00 class 0x060000
[    0.303082] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-fe])
[    0.303087] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.303294] acpi PNP0A08:00: _OSC: platform does not support [PCIeCapability]
[    0.303385] acpi PNP0A08:00: _OSC: not requesting control; platform does not support [PCIeCapability]
[    0.303388] acpi PNP0A08:00: _OSC: OS requested [PCIeHotplug PME AER PCIeCapability]
[    0.303391] acpi PNP0A08:00: _OSC: platform willing to grant [PCIeHotplug PME AER]
[    0.303393] acpi PNP0A08:00: _OSC failed (AE_SUPPORT); disabling ASPM
[    0.303589] PCI host bridge to bus 0000:00
[    0.303593] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7 window]
[    0.303595] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff window]
[    0.303597] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff window]
[    0.303599] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff window]
[    0.303601] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff window]
[    0.303603] pci_bus 0000:00: root bus resource [mem 0xc0000000-0xfebfffff window]
[    0.303605] pci_bus 0000:00: root bus resource [bus 00-fe]
[    0.303613] pci 0000:00:00.0: [8086:0044] type 00 class 0x060000
[    0.303636] DMAR: BIOS has allocated no shadow GTT; disabling IOMMU for graphics
[    0.303706] pci 0000:00:02.0: [8086:0046] type 00 class 0x030000
[    0.303722] pci 0000:00:02.0: reg 0x10: [mem 0xf2000000-0xf23fffff 64bit]
[    0.303729] pci 0000:00:02.0: reg 0x18: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.303734] pci 0000:00:02.0: reg 0x20: [io  0x1800-0x1807]
[    0.303880] pci 0000:00:16.0: [8086:3b64] type 00 class 0x078000
[    0.303925] pci 0000:00:16.0: reg 0x10: [mem 0xf2827800-0xf282780f 64bit]
[    0.304009] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.304106] pci 0000:00:19.0: [8086:10ea] type 00 class 0x020000
[    0.304144] pci 0000:00:19.0: reg 0x10: [mem 0xf2600000-0xf261ffff]
[    0.304156] pci 0000:00:19.0: reg 0x14: [mem 0xf2625000-0xf2625fff]
[    0.304168] pci 0000:00:19.0: reg 0x18: [io  0x1820-0x183f]
[    0.304251] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
[    0.304294] pci 0000:00:19.0: System wakeup disabled by ACPI
[    0.304346] pci 0000:00:1a.0: [8086:3b3c] type 00 class 0x0c0320
[    0.304382] pci 0000:00:1a.0: reg 0x10: [mem 0xf2828000-0xf28283ff]
[    0.304478] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.304519] pci 0000:00:1a.0: System wakeup disabled by ACPI
[    0.304570] pci 0000:00:1b.0: [8086:3b56] type 00 class 0x040300
[    0.304609] pci 0000:00:1b.0: reg 0x10: [mem 0xf2620000-0xf2623fff 64bit]
[    0.304703] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.304758] pci 0000:00:1b.0: System wakeup disabled by ACPI
[    0.304807] pci 0000:00:1c.0: [8086:3b42] type 01 class 0x060400
[    0.304912] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.304960] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.305010] pci 0000:00:1c.1: [8086:3b44] type 01 class 0x060400
[    0.305111] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.305158] pci 0000:00:1c.1: System wakeup disabled by ACPI
[    0.305216] pci 0000:00:1c.3: [8086:3b48] type 01 class 0x060400
[    0.305319] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.305366] pci 0000:00:1c.3: System wakeup disabled by ACPI
[    0.305415] pci 0000:00:1c.4: [8086:3b4a] type 01 class 0x060400
[    0.305517] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.305563] pci 0000:00:1c.4: System wakeup disabled by ACPI
[    0.305617] pci 0000:00:1d.0: [8086:3b34] type 00 class 0x0c0320
[    0.305654] pci 0000:00:1d.0: reg 0x10: [mem 0xf2828400-0xf28287ff]
[    0.305747] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.305790] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    0.305837] pci 0000:00:1e.0: [8086:2448] type 01 class 0x060401
[    0.305983] pci 0000:00:1f.0: [8086:3b07] type 00 class 0x060100
[    0.306165] pci 0000:00:1f.2: [8086:3b2f] type 00 class 0x010601
[    0.306210] pci 0000:00:1f.2: reg 0x10: [io  0x1860-0x1867]
[    0.306222] pci 0000:00:1f.2: reg 0x14: [io  0x1814-0x1817]
[    0.306234] pci 0000:00:1f.2: reg 0x18: [io  0x1818-0x181f]
[    0.306246] pci 0000:00:1f.2: reg 0x1c: [io  0x1810-0x1813]
[    0.306257] pci 0000:00:1f.2: reg 0x20: [io  0x1840-0x185f]
[    0.306269] pci 0000:00:1f.2: reg 0x24: [mem 0xf2827000-0xf28277ff]
[    0.306319] pci 0000:00:1f.2: PME# supported from D3hot
[    0.306402] pci 0000:00:1f.3: [8086:3b30] type 00 class 0x0c0500
[    0.306427] pci 0000:00:1f.3: reg 0x10: [mem 0xf2828800-0xf28288ff 64bit]
[    0.306458] pci 0000:00:1f.3: reg 0x20: [io  0x1880-0x189f]
[    0.306563] pci 0000:00:1f.6: [8086:3b32] type 00 class 0x118000
[    0.306603] pci 0000:00:1f.6: reg 0x10: [mem 0xf2626000-0xf2626fff 64bit]
[    0.306798] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.306945] pci 0000:03:00.0: [8086:4239] type 00 class 0x028000
[    0.307045] pci 0000:03:00.0: reg 0x10: [mem 0xf2400000-0xf2401fff 64bit]
[    0.307314] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
[    0.307546] pci 0000:00:1c.1: PCI bridge to [bus 03]
[    0.307554] pci 0000:00:1c.1:   bridge window [mem 0xf2400000-0xf24fffff]
[    0.307649] acpiphp: Slot [1] registered
[    0.307657] pci 0000:00:1c.3: PCI bridge to [bus 05-0c]
[    0.307662] pci 0000:00:1c.3:   bridge window [io  0x2000-0x2fff]
[    0.307667] pci 0000:00:1c.3:   bridge window [mem 0xf0000000-0xf1ffffff]
[    0.307675] pci 0000:00:1c.3:   bridge window [mem 0xf2900000-0xf29fffff 64bit pref]
[    0.307801] pci 0000:0d:00.0: [1180:e822] type 00 class 0x080500
[    0.307844] pci 0000:0d:00.0: MMC controller base frequency changed to 50Mhz.
[    0.307870] pci 0000:0d:00.0: reg 0x10: [mem 0xf2500000-0xf25000ff]
[    0.308061] pci 0000:0d:00.0: supports D1 D2
[    0.308063] pci 0000:0d:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.308249] pci 0000:0d:00.1: [1180:e230] type 00 class 0x088000
[    0.308298] pci 0000:0d:00.1: reg 0x10: [mem 0xf2500400-0xf25004ff]
[    0.308479] pci 0000:0d:00.1: supports D1 D2
[    0.308481] pci 0000:0d:00.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.308622] pci 0000:0d:00.3: [1180:e832] type 00 class 0x0c0010
[    0.308670] pci 0000:0d:00.3: reg 0x10: [mem 0xf2500800-0xf2500fff]
[    0.308819] pci 0000:0d:00.3: supports D1 D2
[    0.308821] pci 0000:0d:00.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.311298] pci 0000:00:1c.4: PCI bridge to [bus 0d]
[    0.311307] pci 0000:00:1c.4:   bridge window [mem 0xf2500000-0xf25fffff]
[    0.311411] pci 0000:00:1e.0: PCI bridge to [bus 0e] (subtractive decode)
[    0.311425] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7 window] (subtractive decode)
[    0.311427] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff window] (subtractive decode)
[    0.311430] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff window] (subtractive decode)
[    0.311432] pci 0000:00:1e.0:   bridge window [mem 0x000d4000-0x000d7fff window] (subtractive decode)
[    0.311434] pci 0000:00:1e.0:   bridge window [mem 0x000d8000-0x000dbfff window] (subtractive decode)
[    0.311436] pci 0000:00:1e.0:   bridge window [mem 0xc0000000-0xfebfffff window] (subtractive decode)
[    0.313374] ACPI: Enabled 3 GPEs in block 00 to 3F
[    0.313466] ACPI : EC: GPE = 0x11, I/O: command/status = 0x66, data = 0x62
[    0.313606] vgaarb: setting as boot device: PCI:0000:00:02.0
[    0.313609] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.313613] vgaarb: loaded
[    0.313614] vgaarb: bridge control possible 0000:00:02.0
[    0.313910] SCSI subsystem initialized
[    0.313977] libata version 3.00 loaded.
[    0.314018] ACPI: bus type USB registered
[    0.314038] usbcore: registered new interface driver usbfs
[    0.314048] usbcore: registered new interface driver hub
[    0.314068] usbcore: registered new device driver usb
[    0.314236] PCI: Using ACPI for IRQ routing
[    0.324245] PCI: pci_cache_line_size set to 64 bytes
[    0.324462] e820: reserve RAM buffer [mem 0x0009e800-0x0009ffff]
[    0.324465] e820: reserve RAM buffer [mem 0xbb27c000-0xbbffffff]
[    0.324468] e820: reserve RAM buffer [mem 0xbb35f000-0xbbffffff]
[    0.324471] e820: reserve RAM buffer [mem 0xbb46f000-0xbbffffff]
[    0.324474] e820: reserve RAM buffer [mem 0xbb717000-0xbbffffff]
[    0.324476] e820: reserve RAM buffer [mem 0xbb76c000-0xbbffffff]
[    0.324478] e820: reserve RAM buffer [mem 0xbb800000-0xbbffffff]
[    0.324633] NetLabel: Initializing
[    0.324635] NetLabel:  domain hash size = 128
[    0.324636] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.324651] NetLabel:  unlabeled traffic allowed by default
[    0.324755] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.324761] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.326787] amd_nb: Cannot enumerate AMD northbridges
[    0.326806] clocksource: Switched to clocksource hpet
[    0.334786] AppArmor: AppArmor Filesystem Enabled
[    0.334901] pnp: PnP ACPI init
[    0.336484] system 00:00: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.336488] system 00:00: [mem 0x000c0000-0x000c3fff] could not be reserved
[    0.336491] system 00:00: [mem 0x000c4000-0x000c7fff] could not be reserved
[    0.336493] system 00:00: [mem 0x000c8000-0x000cbfff] has been reserved
[    0.336495] system 00:00: [mem 0x000cc000-0x000cffff] has been reserved
[    0.336498] system 00:00: [mem 0x000d0000-0x000d3fff] could not be reserved
[    0.336500] system 00:00: [mem 0x000dc000-0x000dffff] could not be reserved
[    0.336503] system 00:00: [mem 0x000e0000-0x000e3fff] could not be reserved
[    0.336505] system 00:00: [mem 0x000e4000-0x000e7fff] could not be reserved
[    0.336507] system 00:00: [mem 0x000e8000-0x000ebfff] could not be reserved
[    0.336509] system 00:00: [mem 0x000ec000-0x000effff] could not be reserved
[    0.336512] system 00:00: [mem 0x000f0000-0x000fffff] could not be reserved
[    0.336514] system 00:00: [mem 0x00100000-0xbfffffff] could not be reserved
[    0.336517] system 00:00: [mem 0xfec00000-0xfed3ffff] could not be reserved
[    0.336519] system 00:00: [mem 0xfed4c000-0xffffffff] could not be reserved
[    0.336525] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.336917] system 00:01: [io  0x164e-0x164f] has been reserved
[    0.336920] system 00:01: [io  0x1000-0x107f] could not be reserved
[    0.336923] system 00:01: [io  0x1180-0x11ff] has been reserved
[    0.336926] system 00:01: [io  0x0800-0x080f] has been reserved
[    0.336928] system 00:01: [io  0x15e0-0x15ef] has been reserved
[    0.336930] system 00:01: [io  0x1600-0x1641] has been reserved
[    0.336932] system 00:01: [io  0x1644-0x167f] could not be reserved
[    0.336935] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
[    0.336938] system 00:01: [mem 0xfeaff000-0xfeafffff] has been reserved
[    0.336940] system 00:01: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.336943] system 00:01: [mem 0xfed10000-0xfed13fff] has been reserved
[    0.336945] system 00:01: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.336947] system 00:01: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.336950] system 00:01: [mem 0xfed45000-0xfed4bfff] has been reserved
[    0.336954] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.337020] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.337051] pnp 00:03: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.337080] pnp 00:04: Plug and Play ACPI device, IDs LEN0015 PNP0f13 (active)
[    0.337416] pnp 00:05: Plug and Play ACPI device, IDs SMO1200 PNP0c31 (active)
[    0.338415] pnp: PnP ACPI: found 6 devices
[    0.345463] clocksource: acpi_pm: mask: 0xffffff max_cycles: 0xffffff, max_idle_ns: 2085701024 ns
[    0.345530] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.345546] pci 0000:00:1c.1: PCI bridge to [bus 03]
[    0.345553] pci 0000:00:1c.1:   bridge window [mem 0xf2400000-0xf24fffff]
[    0.345564] pci 0000:00:1c.3: PCI bridge to [bus 05-0c]
[    0.345568] pci 0000:00:1c.3:   bridge window [io  0x2000-0x2fff]
[    0.345574] pci 0000:00:1c.3:   bridge window [mem 0xf0000000-0xf1ffffff]
[    0.345580] pci 0000:00:1c.3:   bridge window [mem 0xf2900000-0xf29fffff 64bit pref]
[    0.345588] pci 0000:00:1c.4: PCI bridge to [bus 0d]
[    0.345594] pci 0000:00:1c.4:   bridge window [mem 0xf2500000-0xf25fffff]
[    0.345606] pci 0000:00:1e.0: PCI bridge to [bus 0e]
[    0.345622] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7 window]
[    0.345624] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff window]
[    0.345626] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff window]
[    0.345628] pci_bus 0000:00: resource 7 [mem 0x000d4000-0x000d7fff window]
[    0.345630] pci_bus 0000:00: resource 8 [mem 0x000d8000-0x000dbfff window]
[    0.345632] pci_bus 0000:00: resource 9 [mem 0xc0000000-0xfebfffff window]
[    0.345634] pci_bus 0000:03: resource 1 [mem 0xf2400000-0xf24fffff]
[    0.345637] pci_bus 0000:05: resource 0 [io  0x2000-0x2fff]
[    0.345639] pci_bus 0000:05: resource 1 [mem 0xf0000000-0xf1ffffff]
[    0.345641] pci_bus 0000:05: resource 2 [mem 0xf2900000-0xf29fffff 64bit pref]
[    0.345643] pci_bus 0000:0d: resource 1 [mem 0xf2500000-0xf25fffff]
[    0.345646] pci_bus 0000:0e: resource 4 [io  0x0000-0x0cf7 window]
[    0.345648] pci_bus 0000:0e: resource 5 [io  0x0d00-0xffff window]
[    0.345650] pci_bus 0000:0e: resource 6 [mem 0x000a0000-0x000bffff window]
[    0.345652] pci_bus 0000:0e: resource 7 [mem 0x000d4000-0x000d7fff window]
[    0.345654] pci_bus 0000:0e: resource 8 [mem 0x000d8000-0x000dbfff window]
[    0.345656] pci_bus 0000:0e: resource 9 [mem 0xc0000000-0xfebfffff window]
[    0.345701] NET: Registered protocol family 2
[    0.345935] TCP established hash table entries: 65536 (order: 7, 524288 bytes)
[    0.346178] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.346533] TCP: Hash tables configured (established 65536 bind 65536)
[    0.346577] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.346649] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.346769] NET: Registered protocol family 1
[    0.346800] pci 0000:00:02.0: Video device with shadowed ROM
[    0.347275] PCI: CLS 64 bytes, default 64
[    0.347344] Trying to unpack rootfs image as initramfs...
[    1.073286] Freeing initrd memory: 35788K (ffff880033a0a000 - ffff880035cfd000)
[    1.073300] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    1.073303] software IO TLB [mem 0xb727c000-0xbb27c000] (64MB) mapped at [ffff8800b727c000-ffff8800bb27bfff]
[    1.073545] Scanning for low memory corruption every 60 seconds
[    1.074033] futex hash table entries: 1024 (order: 4, 65536 bytes)
[    1.074069] audit: initializing netlink subsys (disabled)
[    1.074097] audit: type=2000 audit(1484100142.881:1): initialized
[    1.074558] Initialise system trusted keyring
[    1.074693] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.076570] zbud: loaded
[    1.076845] VFS: Disk quotas dquot_6.6.0
[    1.076889] VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.077209] squashfs: version 4.0 (2009/01/31) Phillip Lougher
[    1.077497] fuse init (API version 7.23)
[    1.077659] Key type big_key registered
[    1.077682] Allocating IMA MOK and blacklist keyrings.
[    1.078216] Key type asymmetric registered
[    1.078221] Asymmetric key parser 'x509' registered
[    1.078272] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 249)
[    1.078313] io scheduler noop registered
[    1.078317] io scheduler deadline registered (default)
[    1.078355] io scheduler cfq registered
[    1.079011] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.079018] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.079054] vesafb: mode is 1280x800x32, linelength=5120, pages=0
[    1.079056] vesafb: scrolling: redraw
[    1.079058] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    1.079078] vesafb: framebuffer at 0xd0000000, mapped to 0xffffc90001000000, using 4032k, total 4032k
[    1.079201] Console: switching to colour frame buffer device 160x50
[    1.079236] fb0: VESA VGA frame buffer device
[    1.079254] intel_idle: MWAIT substates: 0x1120
[    1.079256] intel_idle: v0.4.1 model 0x25
[    1.079257] intel_idle: lapic_timer_reliable_states 0xffffffff
[    1.079839] ACPI: AC Adapter [AC] (on-line)
[    1.079918] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    1.080125] ACPI: Lid Switch [LID]
[    1.080236] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    1.080240] ACPI: Sleep Button [SLPB]
[    1.080294] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    1.080297] ACPI: Power Button [PWRF]
[    1.085227] thermal LNXTHERM:00: registered as thermal_zone0
[    1.085233] ACPI: Thermal Zone [THM0] (50 C)
[    1.085335] GHES: HEST is not enabled!
[    1.085702] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.090234] Linux agpgart interface v0.103
[    1.090379] agpgart-intel 0000:00:00.0: Intel HD Graphics Chipset
[    1.090458] agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
[    1.091128] agpgart-intel 0000:00:00.0: detected 32768K stolen memory
[    1.091447] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    1.102895] tpm_tis 00:05: 1.2 TPM (device-id 0x0, rev-id 78)
[    1.109814] ACPI: Battery Slot [BAT0] (battery present)
[    1.138970] tpm_tis 00:05: TPM is disabled/deactivated (0x6)
[    1.144733] brd: module loaded
[    1.146975] loop: module loaded
[    1.147265] libphy: Fixed MDIO Bus: probed
[    1.147270] tun: Universal TUN/TAP device driver, 1.6
[    1.147271] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.147330] PPP generic driver version 2.4.2
[    1.147419] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.147426] ehci-pci: EHCI PCI platform driver
[    1.147573] ehci-pci 0000:00:1a.0: EHCI Host Controller
[    1.147582] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.147598] ehci-pci 0000:00:1a.0: debug port 2
[    1.151520] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
[    1.151584] ehci-pci 0000:00:1a.0: irq 23, io mem 0xf2828000
[    1.156875] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    1.156998] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.157004] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.157009] usb usb1: Product: EHCI Host Controller
[    1.157013] usb usb1: Manufacturer: Linux 4.4.0-57-lowlatency ehci_hcd
[    1.157017] usb usb1: SerialNumber: 0000:00:1a.0
[    1.157388] hub 1-0:1.0: USB hub found
[    1.157409] hub 1-0:1.0: 3 ports detected
[    1.157964] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    1.157979] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.158001] ehci-pci 0000:00:1d.0: debug port 2
[    1.161945] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    1.162041] ehci-pci 0000:00:1d.0: irq 19, io mem 0xf2828400
[    1.167954] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.168028] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    1.168032] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.168035] usb usb2: Product: EHCI Host Controller
[    1.168038] usb usb2: Manufacturer: Linux 4.4.0-57-lowlatency ehci_hcd
[    1.168041] usb usb2: SerialNumber: 0000:00:1d.0
[    1.168344] hub 2-0:1.0: USB hub found
[    1.168360] hub 2-0:1.0: 3 ports detected
[    1.168573] ehci-platform: EHCI generic platform driver
[    1.168596] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.168603] ohci-pci: OHCI PCI platform driver
[    1.168620] ohci-platform: OHCI generic platform driver
[    1.168633] uhci_hcd: USB Universal Host Controller Interface driver
[    1.168728] i8042: PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[    1.171999] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.172097] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.172569] mousedev: PS/2 mouse device common for all mice
[    1.173379] rtc_cmos 00:02: RTC can wake from S4
[    1.173685] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    1.173831] rtc_cmos 00:02: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.173844] i2c /dev entries driver
[    1.173912] device-mapper: uevent: version 1.0.3
[    1.174046] device-mapper: ioctl: 4.34.0-ioctl (2015-10-28) initialised: dm-devel@redhat.com
[    1.174089] ledtrig-cpu: registered to indicate activity on CPUs
[    1.175078] NET: Registered protocol family 10
[    1.175315] NET: Registered protocol family 17
[    1.175329] Key type dns_resolver registered
[    1.175698] microcode: CPU0 sig=0x20652, pf=0x10, revision=0xe
[    1.175711] microcode: CPU1 sig=0x20652, pf=0x10, revision=0xe
[    1.175739] microcode: CPU2 sig=0x20652, pf=0x10, revision=0xe
[    1.175752] microcode: CPU3 sig=0x20652, pf=0x10, revision=0xe
[    1.175843] microcode: Microcode Update Driver: v2.01 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.176483] registered taskstats version 1
[    1.176531] Loading compiled-in X.509 certificates
[    1.176904] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.179384] Loaded X.509 cert 'Build time autogenerated kernel key: 05dc8f9eb81add1095fcec2727708871ffd07578'
[    1.179440] zswap: loaded using pool lzo/zbud
[    1.182669] Key type trusted registered
[    1.193250] Key type encrypted registered
[    1.193271] AppArmor: AppArmor sha1 policy hashing enabled
[    1.198906] tpm_tis 00:05: A TPM error (6) occurred attempting to read a pcr value
[    1.198914] ima: No TPM chip found, activating TPM-bypass!
[    1.198967] evm: HMAC attrs: 0x1
[    1.199899]   Magic number: 1:963:4
[    1.200127] rtc_cmos 00:02: setting system clock to 2017-01-11 02:02:23 UTC (1484100143)
[    1.207894] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.207896] EDD information not available.
[    1.208022] PM: Hibernation image not present or could not be loaded.
[    1.209704] Freeing unused kernel memory: 1428K (ffffffff81f45000 - ffffffff820aa000)
[    1.209707] Write protecting the kernel read-only data: 14336k
[    1.210414] Freeing unused kernel memory: 1744K (ffff88000184c000 - ffff880001a00000)
[    1.210890] Freeing unused kernel memory: 136K (ffff880001dde000 - ffff880001e00000)
[    1.229025] random: systemd-udevd: uninitialized urandom read (16 bytes read, 10 bits of entropy available)
[    1.229119] random: systemd-udevd: uninitialized urandom read (16 bytes read, 10 bits of entropy available)
[    1.229136] random: systemd-udevd: uninitialized urandom read (16 bytes read, 10 bits of entropy available)
[    1.229662] random: udevadm: uninitialized urandom read (16 bytes read, 10 bits of entropy available)
[    1.229718] random: udevadm: uninitialized urandom read (16 bytes read, 10 bits of entropy available)
[    1.230088] random: udevadm: uninitialized urandom read (16 bytes read, 10 bits of entropy available)
[    1.230159] random: udevadm: uninitialized urandom read (16 bytes read, 10 bits of entropy available)
[    1.230228] random: udevadm: uninitialized urandom read (16 bytes read, 10 bits of entropy available)
[    1.230294] random: udevadm: uninitialized urandom read (16 bytes read, 10 bits of entropy available)
[    1.230367] random: udevadm: uninitialized urandom read (16 bytes read, 10 bits of entropy available)
[    1.269476] wmi: Mapper loaded
[    1.273590] FUJITSU Extended Socket Network Device Driver - version 1.0 - Copyright (c) 2015 FUJITSU LIMITED
[    1.283168] pps_core: LinuxPPS API ver. 1 registered
[    1.283172] pps_core: Software ver. 5.3.6 - Copyright 2005-2007 Rodolfo Giometti <giometti@linux.it>
[    1.285830] PTP clock support registered
[    1.286851] sdhci: Secure Digital Host Controller Interface driver
[    1.286854] sdhci: Copyright(c) Pierre Ossman
[    1.289708] sdhci-pci 0000:0d:00.0: SDHCI controller found [1180:e822] (rev 1)
[    1.290016] sdhci-pci 0000:0d:00.0: Will use DMA mode even though HW doesn't fully claim to support it.
[    1.290028] sdhci-pci 0000:0d:00.0: No vmmc regulator found
[    1.290030] sdhci-pci 0000:0d:00.0: No vqmmc regulator found
[    1.294458] [drm] Initialized drm 1.1.0 20060810
[    1.295580] e1000e: Intel(R) PRO/1000 Network Driver - 3.2.6-k
[    1.295583] e1000e: Copyright(c) 1999 - 2015 Intel Corporation.
[    1.295851] e1000e 0000:00:19.0: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[    1.298813] mmc0: SDHCI controller on PCI [0000:0d:00.0] using DMA
[    1.353854] firewire_ohci 0000:0d:00.3: added OHCI v1.10 device as card 0, 4 IR + 4 IT contexts, quirks 0x11
[    1.458903] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    1.469852] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    1.481639] e1000e 0000:00:19.0 eth0: (PCI Express:2.5GT/s:Width x1) f0:de:f1:11:67:f7
[    1.481649] e1000e 0000:00:19.0 eth0: Intel(R) PRO/1000 Network Connection
[    1.481697] e1000e 0000:00:19.0 eth0: MAC: 9, PHY: 10, PBA No: A002FF-0FF
[    1.481748] intel ips 0000:00:1f.6: CPU TDP doesn't match expected value (found 25, expected 29)
[    1.481961] intel ips 0000:00:1f.6: failed to get i915 symbols, graphics turbo disabled until i915 loads
[    1.482137] intel ips 0000:00:1f.6: IPS driver initialized, MCP temp limit 90
[    1.482164] ahci 0000:00:1f.2: version 3.0
[    1.482341] ahci 0000:00:1f.2: SSS flag set, parallel bus scan disabled
[    1.482416] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 3 Gbps 0x33 impl SATA mode
[    1.482420] ahci 0000:00:1f.2: flags: 64bit ncq sntf ilck stag pm led clo pio slum part ems sxs apst 
[    1.482640] e1000e 0000:00:19.0 enp0s25: renamed from eth0
[    1.489661] scsi host0: ahci
[    1.489853] scsi host1: ahci
[    1.490004] scsi host2: ahci
[    1.490382] scsi host3: ahci
[    1.490527] scsi host4: ahci
[    1.490661] scsi host5: ahci
[    1.490721] ata1: SATA max UDMA/133 abar m2048@0xf2827000 port 0xf2827100 irq 25
[    1.490724] ata2: SATA max UDMA/133 abar m2048@0xf2827000 port 0xf2827180 irq 25
[    1.490726] ata3: DUMMY
[    1.490727] ata4: DUMMY
[    1.490730] ata5: SATA max UDMA/133 abar m2048@0xf2827000 port 0xf2827300 irq 25
[    1.490732] ata6: SATA max UDMA/133 abar m2048@0xf2827000 port 0xf2827380 irq 25
[    1.491365] [drm] Memory usable by graphics device = 2048M
[    1.491370] checking generic (d0000000 3f0000) vs hw (d0000000 10000000)
[    1.491371] fb: switching to inteldrmfb from VESA VGA
[    1.491406] Console: switching to colour dummy device 80x25
[    1.491481] [drm] Replacing VGA console driver
[    1.498922] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    1.498924] [drm] Driver supports precise vblank timestamp query.
[    1.500130] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    1.532913] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[    1.534224] acpi device:01: registered as cooling_device4
[    1.534365] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input6
[    1.534530] [drm] Initialized i915 1.6.0 20151010 for 0000:00:02.0 on minor 0
[    1.573436] usb 1-1: New USB device found, idVendor=8087, idProduct=0020
[    1.573445] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.573928] hub 1-1:1.0: USB hub found
[    1.574010] hub 1-1:1.0: 6 ports detected
[    1.584625] usb 2-1: New USB device found, idVendor=8087, idProduct=0020
[    1.584634] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.585150] hub 2-1:1.0: USB hub found
[    1.585314] hub 2-1:1.0: 8 ports detected
[    1.592852] [drm] GMBUS [i915 gmbus dpb] timed out, falling back to bit banging on pin 5
[    1.601923] fbcon: inteldrmfb (fb0) is primary device
[    1.602014] Console: switching to colour frame buffer device 160x50
[    1.602052] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[    1.795943] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.797853] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
[    1.797866] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    1.797871] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    1.799693] ata1.00: ATA-8: ST9320423AS, 0003LVM1, max UDMA/100
[    1.799701] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.801972] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
[    1.801981] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    1.801987] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    1.803794] ata1.00: configured for UDMA/100
[    1.804189] scsi 0:0:0:0: Direct-Access     ATA      ST9320423AS      LVM1 PQ: 0 ANSI: 5
[    1.804752] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    1.804787] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.804842] sd 0:0:0:0: [sda] Write Protect is off
[    1.804846] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.804869] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.841829]  sda: sda1 sda2 < sda5 sda6 >
[    1.843057] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.848861] usb 1-1.6: new high-speed USB device number 3 using ehci-pci
[    1.855010] firewire_core 0000:0d:00.3: created device fw0: GUID f0def1ff1167f7ff, S400
[    1.862847] usb 2-1.1: new full-speed USB device number 3 using ehci-pci
[    1.940228] usb 1-1.6: New USB device found, idVendor=17ef, idProduct=480f
[    1.940237] usb 1-1.6: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.940242] usb 1-1.6: Product: Integrated Camera
[    1.940246] usb 1-1.6: Manufacturer: Chicony Electronics Co., Ltd.
[    1.954226] usb 2-1.1: config 1 has an invalid interface number: 5 but max is 4
[    1.954235] usb 2-1.1: config 1 has no interface number 3
[    1.954245] usb 2-1.1: config 1 interface 1 altsetting 1 endpoint 0x83 has an invalid bInterval 32, changing to 4
[    1.955732] usb 2-1.1: New USB device found, idVendor=4406, idProduct=3a80
[    1.955739] usb 2-1.1: New USB device strings: Mfr=2, Product=1, SerialNumber=0
[    1.955743] usb 2-1.1: Product: iUR2
[    1.955748] usb 2-1.1: Manufacturer: TEAC Corporation     
[    2.075879] tsc: Refined TSC clocksource calibration: 2127.999 MHz
[    2.075885] clocksource: tsc: mask: 0xffffffffffffffff max_cycles: 0x1eac822addd, max_idle_ns: 440795285886 ns
[    2.109925] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.116785] psmouse serio1: synaptics: queried max coordinates: x [..5888], y [..4820]
[    2.117713] ata2.00: ACPI cmd e3/00:1f:00:00:00:a0 (IDLE) succeeded
[    2.122829] ata2.00: ACPI cmd e3/00:02:00:00:00:a0 (IDLE) succeeded
[    2.124659] ata2.00: ATAPI: Optiarc DVD RW AD-7930H, 1.D0, max UDMA/100
[    2.137443] ata2.00: ACPI cmd e3/00:1f:00:00:00:a0 (IDLE) succeeded
[    2.142442] ata2.00: ACPI cmd e3/00:02:00:00:00:a0 (IDLE) succeeded
[    2.144170] ata2.00: configured for UDMA/100
[    2.160874] scsi 1:0:0:0: CD-ROM            Optiarc  DVD RW AD-7930H  1.D0 PQ: 0 ANSI: 5
[    2.194821] psmouse serio1: synaptics: Touchpad model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd047b3/0xb40000/0xa0000/0x0, board id: 0, fw id: 578367
[    2.194834] psmouse serio1: synaptics: serio: Synaptics pass-through port at isa0060/serio1/input0
[    2.208774] sr 1:0:0:0: [sr0] scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.208779] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.209061] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.209278] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.244802] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input5
[    2.513908] ata5: SATA link down (SStatus 0 SControl 300)
[    2.818903] ata6: SATA link down (SStatus 0 SControl 300)
[    3.076001] clocksource: Switched to clocksource tsc
[    3.217459] random: nonblocking pool is initialized
[    6.681865] intel ips 0000:00:1f.6: i915 driver attached, reenabling gpu turbo
[    7.369685] psmouse serio2: trackpoint: IBM TrackPoint firmware: 0x0e, buttons: 3/3
[    7.618634] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio1/serio2/input/input7
[    8.761143] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   10.605968] systemd[1]: systemd 229 running in system mode. (+PAM +AUDIT +SELINUX +IMA +APPARMOR +SMACK +SYSVINIT +UTMP +LIBCRYPTSETUP +GCRYPT +GNUTLS +ACL +XZ -LZ4 +SECCOMP +BLKID +ELFUTILS +KMOD -IDN)
[   10.606135] systemd[1]: Detected architecture x86-64.
[   10.622691] systemd[1]: Set hostname to <Foghorn>.
[   12.223438] systemd[1]: Started Forward Password Requests to Wall Directory Watch.
[   12.223517] systemd[1]: Listening on fsck to fsckd communication Socket.
[   12.223574] systemd[1]: Listening on Journal Socket.
[   12.223594] systemd[1]: Reached target Remote File Systems (Pre).
[   12.223710] systemd[1]: Created slice User and Session Slice.
[   12.223725] systemd[1]: Reached target User and Group Name Lookups.
[   12.223738] systemd[1]: Reached target Remote File Systems.
[   12.223783] systemd[1]: Listening on Journal Socket (/dev/log).
[   12.223942] systemd[1]: Set up automount Arbitrary Executable File Formats File System Automount Point.
[   12.223987] systemd[1]: Listening on /dev/initctl Compatibility Named Pipe.
[   12.224068] systemd[1]: Listening on Journal Audit Socket.
[   12.224099] systemd[1]: Listening on udev Kernel Socket.
[   12.224139] systemd[1]: Listening on udev Control Socket.
[   12.224226] systemd[1]: Created slice System Slice.
[   12.229861] systemd[1]: Started Braille Device Support.
[   12.230801] systemd[1]: Mounting Huge Pages File System...
[   12.230932] systemd[1]: Created slice system-systemd\x2dcryptsetup.slice.
[   12.231481] systemd[1]: Started Read required files in advance.
[   12.232446] systemd[1]: Starting Create list of required static device nodes for the current kernel...
[   12.233025] systemd[1]: Starting Uncomplicated firewall...
[   12.233606] systemd[1]: Mounting Debug File System...
[   12.410714] systemd[1]: Reached target Slices.
[   12.410814] systemd[1]: Listening on Syslog Socket.
[   12.418770] systemd[1]: Starting Journal Service...
[   12.492765] systemd[1]: Starting Load Kernel Modules...
[   12.493582] systemd[1]: Mounting POSIX Message Queue File System...
[   12.494401] systemd[1]: Starting Set console keymap...
[   12.497011] systemd[1]: Started Create list of required static device nodes for the current kernel.
[   12.521752] systemd[1]: Starting Create Static Device Nodes in /dev...
[   12.714853] systemd[1]: Mounted POSIX Message Queue File System.
[   12.715018] systemd[1]: Mounted Debug File System.
[   12.715105] systemd[1]: Mounted Huge Pages File System.
[   12.751400] systemd[1]: Started Uncomplicated firewall.
[   13.279421] lp: driver loaded but no devices found
[   13.471186] systemd[1]: Started Journal Service.
[   13.694730] ppdev: user-space parallel port driver
[   15.629064] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   16.084638] systemd-journald[326]: Received request to flush runtime journal from PID 1
[   16.337978] ACPI Warning: SystemIO range 0x0000000000001028-0x000000000000102F conflicts with OpRegion 0x0000000000001000-0x000000000000107F (\_SB_.PCI0.LPC_.PMIO) (20150930/utaddress-254)
[   16.337987] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   16.337991] ACPI Warning: SystemIO range 0x00000000000011C0-0x00000000000011CF conflicts with OpRegion 0x0000000000001180-0x00000000000011FF (\_SB_.PCI0.LPC_.LPIO) (20150930/utaddress-254)
[   16.337995] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   16.337997] ACPI Warning: SystemIO range 0x00000000000011B0-0x00000000000011BF conflicts with OpRegion 0x0000000000001180-0x00000000000011FF (\_SB_.PCI0.LPC_.LPIO) (20150930/utaddress-254)
[   16.338001] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   16.338002] ACPI Warning: SystemIO range 0x0000000000001180-0x00000000000011AF conflicts with OpRegion 0x0000000000001180-0x00000000000011FF (\_SB_.PCI0.LPC_.LPIO) (20150930/utaddress-254)
[   16.338006] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   16.338007] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   16.421691] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   17.504942] Intel(R) Wireless WiFi driver for Linux
[   17.504946] Copyright(c) 2003- 2015 Intel Corporation
[   17.505213] iwlwifi 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[   17.728568] media: Linux media interface: v0.10
[   17.734111] iwlwifi 0000:03:00.0: Direct firmware load for iwlwifi-6000-6.ucode failed with error -2
[   17.741087] iwlwifi 0000:03:00.0: Direct firmware load for iwlwifi-6000-5.ucode failed with error -2
[   17.745325] Non-volatile memory driver v1.3
[   17.905982] thinkpad_acpi: ThinkPad ACPI Extras v0.25
[   17.905986] thinkpad_acpi: http://ibm-acpi.sf.net/
[   17.905988] thinkpad_acpi: ThinkPad BIOS 6IET78WW (1.38 ), EC 6IHT39WW-1.14
[   17.905989] thinkpad_acpi: Lenovo ThinkPad T410, model 2516CTO
[   17.906665] thinkpad_acpi: detected a 16-level brightness capable ThinkPad
[   17.906838] thinkpad_acpi: radio switch found; radios are enabled
[   17.906863] thinkpad_acpi: This ThinkPad has standard ACPI backlight brightness control, supported by the ACPI video driver
[   17.906865] thinkpad_acpi: Disabling thinkpad-acpi brightness events by default...
[   17.910332] thinkpad_acpi: Standard ACPI backlight interface available, not loading native one
[   17.912209] input: ThinkPad Extra Buttons as /devices/platform/thinkpad_acpi/input/input8
[   17.954913] iwlwifi 0000:03:00.0: loaded firmware version 9.221.4.1 build 25532 op_mode iwldvm
[   18.059935] Linux video capture interface: v2.00
[   18.402675] kvm: VM_EXIT_LOAD_IA32_PERF_GLOBAL_CTRL does not work properly. Using workaround
[   18.559634] usbcore: registered new interface driver snd-usb-audio
[   18.744883] snd_hda_codec_conexant hdaudioC0D0: CX20585: BIOS auto-probing.
[   18.745417] snd_hda_codec_conexant hdaudioC0D0: autoconfig for CX20585: line_outs=1 (0x1f/0x0/0x0/0x0/0x0) type:speaker
[   18.745421] snd_hda_codec_conexant hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   18.745425] snd_hda_codec_conexant hdaudioC0D0:    hp_outs=2 (0x1c/0x19/0x0/0x0/0x0)
[   18.745428] snd_hda_codec_conexant hdaudioC0D0:    mono: mono_out=0x0
[   18.745430] snd_hda_codec_conexant hdaudioC0D0:    inputs:
[   18.745434] snd_hda_codec_conexant hdaudioC0D0:      Internal Mic=0x23
[   18.745437] snd_hda_codec_conexant hdaudioC0D0:      Mic=0x1b
[   18.745440] snd_hda_codec_conexant hdaudioC0D0:      Dock Mic=0x1a
[   18.746848] snd_hda_codec_conexant hdaudioC0D0: Enable sync_write for stable communication
[   18.869030] uvcvideo: Found UVC 1.00 device Integrated Camera (17ef:480f)
[   18.870291] input: Integrated Camera as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0/input/input13
[   18.870400] usbcore: registered new interface driver uvcvideo
[   18.870402] USB Video Class driver (1.1.1)
[   18.878991] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   18.878997] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   18.878999] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   18.879002] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Advanced-N 6200 AGN, REV=0x74
[   18.879102] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[   18.890090] input: HDA Intel MID Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   18.890308] input: HDA Intel MID Dock Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   18.892341] input: HDA Intel MID Dock Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   18.892428] input: HDA Intel MID Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   18.892509] input: HDA Intel MID HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
[   18.892586] input: HDA Intel MID HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input15
[   18.892670] input: HDA Intel MID HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input16
[   19.217567] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   19.235919] iwlwifi 0000:03:00.0 wlp3s0: renamed from wlan0
[   19.580313] cfg80211: World regulatory domain updated:
[   19.580319] cfg80211:  DFS Master region: unset
[   19.580321] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[   19.580323] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[   19.580326] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[   19.580328] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (N/A, 2000 mBm), (N/A)
[   19.580330] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (N/A)
[   19.580332] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (0 s)
[   19.580335] cfg80211:   (5490000 KHz - 5730000 KHz @ 160000 KHz), (N/A, 2000 mBm), (0 s)
[   19.580336] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 2000 mBm), (N/A)
[   19.580338] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 0 mBm), (N/A)
[   22.591006] audit: type=1400 audit(1484100164.889:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=779 comm="apparmor_parser"
[   22.591018] audit: type=1400 audit(1484100164.889:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=779 comm="apparmor_parser"
[   22.591026] audit: type=1400 audit(1484100164.889:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-helper" pid=779 comm="apparmor_parser"
[   22.591033] audit: type=1400 audit(1484100164.889:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=779 comm="apparmor_parser"
[   22.609852] audit: type=1400 audit(1484100164.908:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/snapd/snap-confine" pid=783 comm="apparmor_parser"
[   22.715036] audit: type=1400 audit(1484100165.013:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=778 comm="apparmor_parser"
[   22.715049] audit: type=1400 audit(1484100165.013:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session//chromium" pid=778 comm="apparmor_parser"
[   22.732099] audit: type=1400 audit(1484100165.030:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="webbrowser-app" pid=782 comm="apparmor_parser"
[   22.732114] audit: type=1400 audit(1484100165.030:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="webbrowser-app//oxide_helper" pid=782 comm="apparmor_parser"
[   22.736606] audit: type=1400 audit(1484100165.035:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=785 comm="apparmor_parser"
[   23.935797] Adding 8178172k swap on /dev/mapper/cryptswap1.  Priority:-1 extents:1 across:8178172k FS
[   35.588000] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[   35.588162] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[   35.594634] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[   35.594728] iwlwifi 0000:03:00.0: Radio type=0x1-0x3-0x1
[   35.803696] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[   35.810179] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[   35.810273] iwlwifi 0000:03:00.0: Radio type=0x1-0x3-0x1
[   35.888192] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[   35.893996] IPv6: ADDRCONF(NETDEV_UP): enp0s25: link is not ready
[   36.097370] IPv6: ADDRCONF(NETDEV_UP): enp0s25: link is not ready
[   38.351816] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[  131.431622] wlp3s0: authenticate with e4:f4:c6:1d:10:1c
[  131.462231] wlp3s0: send auth to e4:f4:c6:1d:10:1c (try 1/3)
[  131.465062] wlp3s0: authenticated
[  131.465539] wlp3s0: associate with e4:f4:c6:1d:10:1c (try 1/3)
[  131.468607] wlp3s0: RX AssocResp from e4:f4:c6:1d:10:1c (capab=0x1411 status=0 aid=10)
[  131.471094] wlp3s0: associated
[  131.471142] IPv6: ADDRCONF(NETDEV_CHANGE): wlp3s0: link becomes ready
[ 1003.507018] perf interrupt took too long (2863 > 2500), lowering kernel.perf_event_max_sample_rate to 50000
[ 1627.964591] perf interrupt took too long (5011 > 5000), lowering kernel.perf_event_max_sample_rate to 25000
[ 2260.659781] [drm:intel_cpu_fifo_underrun_irq_handler [i915]] *ERROR* CPU pipe A FIFO underrun
[ 2260.659858] [drm:intel_pch_fifo_underrun_irq_handler [i915]] *ERROR* PCH transcoder A FIFO underrun
[ 9167.575038] thinkpad_acpi: EC reports that Thermal Table has changed
[ 9172.379173] usb 2-1.1: USB disconnect, device number 3
[ 9175.312828] do_trap: 33 callbacks suppressed
[ 9175.312836] traps: pool[13047] trap int3 ip:7f43fbde3a6b sp:7f43d8f955b0 error:0
[10359.604736] wlp3s0: deauthenticating from e4:f4:c6:1d:10:1c by local choice (Reason: 3=DEAUTH_LEAVING)
[10359.623547] cfg80211: World regulatory domain updated:
[10359.623554] cfg80211:  DFS Master region: unset
[10359.623556] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[10359.623559] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[10359.623563] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[10359.623565] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (N/A, 2000 mBm), (N/A)
[10359.623568] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (N/A)
[10359.623571] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (0 s)
[10359.623574] cfg80211:   (5490000 KHz - 5730000 KHz @ 160000 KHz), (N/A, 2000 mBm), (0 s)
[10359.623576] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 2000 mBm), (N/A)
[10359.623579] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 0 mBm), (N/A)
[10360.649733] PM: Syncing filesystems ... done.
[10361.162415] PM: Preparing system for sleep (mem)
[10361.162778] Freezing user space processes ... (elapsed 0.002 seconds) done.
[10361.165217] Freezing remaining freezable tasks ... (elapsed 0.001 seconds) done.
[10361.166245] PM: Suspending system (mem)
[10361.166329] Suspending console(s) (use no_console_suspend to debug)
[10361.325931] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[10361.352655] sd 0:0:0:0: [sda] Stopping disk
[10361.571443] e1000e: EEE TX LPI TIMER: 00000000
[10361.729129] PM: suspend of devices complete after 562.763 msecs
[10361.740181] PM: late suspend of devices complete after 11.048 msecs
[10361.742069] ehci-pci 0000:00:1d.0: System wakeup enabled by ACPI
[10361.742247] e1000e 0000:00:19.0: System wakeup enabled by ACPI
[10361.742249] ehci-pci 0000:00:1a.0: System wakeup enabled by ACPI
[10361.752973] PM: noirq suspend of devices complete after 12.791 msecs
[10361.753128] ACPI: Preparing to enter system sleep state S3
[10361.795961] ACPI : EC: EC stopped
[10361.795961] PM: Saving platform NVS memory
[10361.797200] Disabling non-boot CPUs ...
[10361.805020] Broke affinity for irq 25
[10361.806251] smpboot: CPU 1 is now offline
[10361.828985] Broke affinity for irq 25
[10361.828987] Broke affinity for irq 26
[10361.830027] smpboot: CPU 2 is now offline
[10361.843946] Broke affinity for irq 1
[10361.843955] Broke affinity for irq 9
[10361.843960] Broke affinity for irq 12
[10361.843965] Broke affinity for irq 19
[10361.843970] Broke affinity for irq 23
[10361.843973] Broke affinity for irq 25
[10361.843975] Broke affinity for irq 26
[10361.843976] Broke affinity for irq 28
[10361.845004] smpboot: CPU 3 is now offline
[10361.849181] ACPI: Low-level resume complete
[10361.849240] ACPI : EC: EC started
[10361.849240] PM: Restoring platform NVS memory
[10361.850348] microcode: CPU0 microcode updated early to revision 0xe, date = 2013-06-26
[10361.850399] Enabling non-boot CPUs ...
[10361.858648] x86: Booting SMP configuration:
[10361.858649] smpboot: Booting Node 0 Processor 1 APIC 0x1
[10361.876558]  cache: parent cpu1 should not be sleeping
[10361.892501] CPU1 is up
[10361.900661] smpboot: Booting Node 0 Processor 2 APIC 0x4
[10361.901136] microcode: CPU2 microcode updated early to revision 0xe, date = 2013-06-26
[10361.903400] NOHZ: local_softirq_pending 282
[10361.903425] NOHZ: local_softirq_pending 282
[10361.919537]  cache: parent cpu2 should not be sleeping
[10361.935482] CPU2 is up
[10361.943688] smpboot: Booting Node 0 Processor 3 APIC 0x5
[10361.961532]  cache: parent cpu3 should not be sleeping
[10361.977472] CPU3 is up
[10361.980246] ACPI: Waking up from system sleep state S3
[10362.030022] thinkpad_acpi: EC reports that Thermal Table has changed
[10362.070866] ehci-pci 0000:00:1d.0: System wakeup disabled by ACPI
[10362.070969] ehci-pci 0000:00:1a.0: System wakeup disabled by ACPI
[10362.071085] sdhci-pci 0000:0d:00.0: MMC controller base frequency changed to 50Mhz.
[10362.071159] PM: noirq resume of devices complete after 11.758 msecs
[10362.073334] PM: early resume of devices complete after 2.152 msecs
[10362.073452] e1000e 0000:00:19.0: System wakeup disabled by ACPI
[10362.074543] rtc_cmos 00:02: System wakeup disabled by ACPI
[10362.076637] sd 0:0:0:0: [sda] Starting disk
[10362.098416] tpm_tis 00:05: TPM is disabled/deactivated (0x6)
[10362.300355] usb 1-1.6: reset high-speed USB device number 3 using ehci-pci
[10362.384391] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[10362.386944] ata5: SATA link down (SStatus 0 SControl 300)
[10362.388304] ata6: SATA link down (SStatus 0 SControl 300)
[10362.574310] sdhci-pci 0000:0d:00.0: Will use DMA mode even though HW doesn't fully claim to support it.
[10362.577240] PM: resume of devices complete after 504.063 msecs
[10362.577525] PM: Finishing wakeup.
[10362.577526] Restarting tasks ... done.
[10362.610292] video LNXVIDEO:00: Restoring backlight state
[10362.611187] ata2.00: ACPI cmd e3/00:1f:00:00:00:a0 (IDLE) succeeded
[10362.612041] ata2.00: ACPI cmd e3/00:02:00:00:00:a0 (IDLE) succeeded
[10362.627209] firewire_core 0000:0d:00.3: rediscovered device fw0
[10362.629679] ata2.00: ACPI cmd e3/00:1f:00:00:00:a0 (IDLE) succeeded
[10362.630050] ata2.00: ACPI cmd e3/00:02:00:00:00:a0 (IDLE) succeeded
[10362.631854] ata2.00: configured for UDMA/100
[10362.842455] psmouse serio1: synaptics: queried max coordinates: x [..5888], y [..4820]
[10364.633599] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[10364.827283] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
[10364.827294] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[10364.827300] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[10364.831428] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
[10364.831437] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[10364.831443] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[10364.833221] ata1.00: configured for UDMA/100
[10365.293025] e1000e: enp0s25 NIC Link is Down
[10365.294635] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[10365.294965] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[10365.295190] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[10365.295283] iwlwifi 0000:03:00.0: Radio type=0x1-0x3-0x1
[10365.505199] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[10365.505732] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[10365.505826] iwlwifi 0000:03:00.0: Radio type=0x1-0x3-0x1
[10365.579978] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[10365.582399] IPv6: ADDRCONF(NETDEV_UP): enp0s25: link is not ready
[10365.786557] IPv6: ADDRCONF(NETDEV_UP): enp0s25: link is not ready
[10365.818388] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[10368.976757] wlp3s0: authenticate with e4:f4:c6:1d:10:1c
[10368.977878] wlp3s0: send auth to e4:f4:c6:1d:10:1c (try 1/3)
[10368.980678] wlp3s0: authenticated
[10368.981308] wlp3s0: associate with e4:f4:c6:1d:10:1c (try 1/3)
[10368.986577] wlp3s0: RX AssocResp from e4:f4:c6:1d:10:1c (capab=0x1411 status=0 aid=9)
[10368.997996] wlp3s0: associated
[10368.998068] IPv6: ADDRCONF(NETDEV_CHANGE): wlp3s0: link becomes ready
[10370.216794] usb 2-1.1: new full-speed USB device number 4 using ehci-pci
[10370.307869] usb 2-1.1: config 1 has an invalid interface number: 5 but max is 4
[10370.307875] usb 2-1.1: config 1 has no interface number 3
[10370.307884] usb 2-1.1: config 1 interface 1 altsetting 1 endpoint 0x83 has an invalid bInterval 32, changing to 4
[10370.309339] usb 2-1.1: New USB device found, idVendor=4406, idProduct=3a80
[10370.309344] usb 2-1.1: New USB device strings: Mfr=2, Product=1, SerialNumber=0
[10370.309347] usb 2-1.1: Product: iUR2
[10370.309350] usb 2-1.1: Manufacturer: TEAC Corporation
```






I came home and ran Rakarrack a little bit. It does appear to be behaving the same way. I then recorded some basic strumming while the static from hell had a field. When I went back to review the recording, all the static had disappeared. My guess is interface.

---

### Post by CrocoDuck on 2017-01-12
If you can't record the noise when streaming the plugin output directly to a recorder, then it would mean that the noise is not digitally generated. You might be right about the fact it comes from the soundcard somehow. Give us more information about your audio card. Repost the output of:

```
aplay -l
```
```
arecord -l
```

[This guy]("https://linuxmusicians.com/viewtopic.php?f=6&t=16347") had probably a self oscillation problem given by how his mic loads the soundcard input, plus some port related noise. It might contain some insights for you.

---

### Post by marseille2 on 2017-01-12
OOPS:) ... Sorry! I was thinking about that one long review thread that someone wrote about a year+ ago. it's pretty awesome actually. They went out of their way to make a list of tips on how to get great sound with wine using some Windows app, and CPU adjustments. For some reason... I thought you wrote it. Need to dig that joker out!:)

.

---

### Post by CrocoDuck on 2017-01-12
> **marseille2 said:**
> OOPS:) ... Sorry! I was thinking about that one long review thread that someone wrote about a year+ ago. it's pretty awesome actually. They went out of their way to make a list of tips on how to get great sound with wine using some Windows app, and CPU adjustments. For some reason... I thought you wrote it. Need to dig that joker out!:)

.

Oh I see. Perhaps [this thread]("https://ubuntuforums.org/showthread.php?t=2309922")?

---

### Post by muddpup64 on 2017-01-12
Here you are sir.

aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: MID [HDA Intel MID], device 0: CX20585 Analog [CX20585 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: MID [HDA Intel MID], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: MID [HDA Intel MID], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: MID [HDA Intel MID], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: iUR2 [iUR2], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

arecord -l
```
**** List of CAPTURE Hardware Devices ****
card 0: MID [HDA Intel MID], device 0: CX20585 Analog [CX20585 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: iUR2 [iUR2], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

I don't know if this matters but I did not take these readings while the static was present. (that I know of) I just came home, plugged in the interface, and went ham.

---

### Post by CrocoDuck on 2017-01-13
A quick search shows few results of problem with noise when using your Tascam:

[http://forum.audacityteam.org/viewtopic.php?f=46&t=77438](http://forum.audacityteam.org/viewtopic.php?f=46&t=77438)
[http://www.tascamforums.com/threads/2-recording-problems-w-iur2.2116/](http://www.tascamforums.com/threads/2-recording-problems-w-iur2.2116/)

Are you on a laptop? If so: does the noise happens if the laptop is connected to power?

Also, do you have an external power supply for the interface? I am afraid it could be that the current output of your USB ports might be just sufficient to correctly power the device. Not all the USB ports on a computer are equal, have a try to see if there are ports where you don't observe noise.

---

### Post by muddpup64 on 2017-01-14
> **CrocoDuck said:**
> A quick search shows few results of problem with noise when using your Tascam:

[http://forum.audacityteam.org/viewtopic.php?f=46&t=77438](http://forum.audacityteam.org/viewtopic.php?f=46&t=77438)
[http://www.tascamforums.com/threads/2-recording-problems-w-iur2.2116/](http://www.tascamforums.com/threads/2-recording-problems-w-iur2.2116/)

Are you on a laptop? If so: does the noise happens if the laptop is connected to power?

Also, do you have an external power supply for the interface? I am afraid it could be that the current output of your USB ports might be just sufficient to correctly power the device. Not all the USB ports on a computer are equal, have a try to see if there are ports where you don't observe noise.

Yes, this is on a laptop. There seems to be no correlation to whether or not it's having trouble and power. For example, as I type this, I am unplugged with no static. That being said, for the majority of it's use it's plugged in.



I'm dumbfounded, there are two specific ports in which I get no static. I'll have to give it some time before it's confirmable but thats where I'm at.

---

