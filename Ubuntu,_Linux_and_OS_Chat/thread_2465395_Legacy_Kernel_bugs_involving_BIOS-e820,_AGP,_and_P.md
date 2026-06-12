---
title: "Legacy Kernel bugs involving BIOS-e820, AGP, and PCI-DMA"
date: 2021-07-31
forum: Ubuntu, Linux and OS Chat
---

### Post by bcschmerker on 2021-07-31
**I have an *e*machines®/ac*e*r® EL1210-09 in prep for projector duty at a house of worship.**  The hardware on this EL1210 consists of an nVIDIA® nForce® 780a SLI chipset (the planar C77 geForce GPU by-passed in favor of an add-on GF119), Advance Micro Devices Inc. Athlon LE-1620 single-core (P/N ADH1620IAA5DH), Micro Star International N610GT-1GD3-LP (nVIDIA® GF119, 1 GiB GDDR-3), and secondary storage, powered by a Shuttle® PC6300001 (replaced the stock 220W LITEON®, which had a specvio - no +3.3VDC to SATA Power).  As of 31 July 2021 I'm running 5.8.0-63 with 5.4.0-82 as a backup; both kernels are armed with appropriate modules for the GF119 CUDA from nVIDIA Corporation (packages linux-*-nvidia-390-5.8.0-63-generic, linux-*-nvidia-390-5.4.0-82-generic); I am treating nvidia-340 (for the by-passed planar C77) as a WontFix for screen and user-interface lock-ups.

In the K8, Advance Micro Devices used a graphic address remapping table to accommodate memory-mapped I/O, a then-new requirement for Microsoft® Windows® NT&#8482; 5.x (viz., 2000 Pro and XP).  The following redact of /var/log/dmesg was recorded after three reboots on 30 July 2021 for the purpose of adjusting Kernel parameters; Phoenix Award WorkstationBIOS R01.A0 (stock; as delivered with Microsoft® Windows® 6.0.6000) is apparently unable to report the AGP Aperture Size (currently set to 128 MB) or Location to the Kernel, and I don't have the docs necessary to build a Coreboot firmware for the EL1210's stock DAO78L Boxer planar.
```
[    0.000000] kernel: Linux version 5.8.0-63-generic (buildd@lgw01-amd64-035) (gcc (Ubuntu 9.3.0-17ubuntu1~20.04) 9.3.0, GNU ld (GNU Binutils for Ubuntu) 2.34) #71~20.04.1-Ubuntu SMP Thu Jul 15 17:46:08 UTC 2021 (Ubuntu 5.8.0-63.71~20.04.1-generic 5.8.18)
[    0.000000] kernel: Command line: BOOT_IMAGE=/vmlinuz-5.8.0-63-generic root=UUID=c4248af1-a4cf-49a2-ba18-4de2c65c815c ro hashdist=0 mce=bios_cmci_threshold acpi_force_32bit_fadt_addr numa=off agp=off pcie_aspm=off hpet=verbose
[    0.000000] kernel: KERNEL supported cpus:
[    0.000000] kernel:   Intel GenuineIntel
[    0.000000] kernel:   AMD AuthenticAMD
[    0.000000] kernel:   Hygon HygonGenuine
[    0.000000] kernel:   Centaur CentaurHauls
[    0.000000] kernel:   zhaoxin   Shanghai  
[    0.000000] kernel: x86/fpu: x87 FPU will use FXSAVE
[    0.000000] kernel: BIOS-provided physical RAM map:
[    0.000000] kernel: BIOS-e820: [mem 0x0000000000000000-0x000000000009e7ff] usable
[    0.000000] kernel: BIOS-e820: [mem 0x000000000009e800-0x000000000009ffff] reserved
[    0.000000] kernel: BIOS-e820: [mem 0x00000000000f0000-0x00000000000fffff] reserved
[    0.000000] kernel: BIOS-e820: [mem 0x0000000000100000-0x00000000b7eeffff] usable
[    0.000000] kernel: BIOS-e820: [mem 0x00000000b7ef0000-0x00000000b7ef2fff] ACPI NVS
[    0.000000] kernel: BIOS-e820: [mem 0x00000000b7ef3000-0x00000000b7efffff] ACPI data
[    0.000000] kernel: BIOS-e820: [mem 0x00000000b8000000-0x00000000bfffffff] reserved
[    0.000000] kernel: BIOS-e820: [mem 0x00000000f0000000-0x00000000f3ffffff] reserved
[    0.000000] kernel: BIOS-e820: [mem 0x00000000fec00000-0x00000000ffffffff] reserved
[    0.000000] kernel: BIOS-e820: [mem 0x0000000100000000-0x000000013fffffff] usable
[    0.000000] kernel: ACPI: Forcing 32 Bit FADT addresses
[    0.000000] kernel: NX (Execute Disable) protection: active
[    0.000000] kernel: SMBIOS 2.5 present.
[    0.000000] kernel: DMI: eMachines EL1210-09/WMCP78M, BIOS R01-A0 09/23/2008
[    0.000000] kernel: tsc: Fast TSC calibration using PIT
[    0.000000] kernel: tsc: Detected 2400.010 MHz processor
[    0.003764] kernel: e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.003766] kernel: e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.010183] kernel: AGP: No AGP bridge found
[    0.010244] kernel: last_pfn = 0x140000 max_arch_pfn = 0x400000000
[    0.010249] kernel: MTRR default type: uncachable
[    0.010250] kernel: MTRR fixed ranges enabled:
[    0.010252] kernel:   00000-9FFFF write-back
[    0.010253] kernel:   A0000-BFFFF uncachable
[    0.010254] kernel:   C0000-CFFFF write-protect
[    0.010255] kernel:   D0000-D7FFF uncachable
[    0.010256] kernel:   D8000-DFFFF write-protect
[    0.010258] kernel:   E0000-FFFFF uncachable
[    0.010259] kernel: MTRR variable ranges enabled:
[    0.010261] kernel:   0 base 0000000000 mask FF80000000 write-back
[    0.010263] kernel:   1 base 0080000000 mask FFC0000000 write-back
[    0.010264] kernel:   2 base 0100000000 mask FFC0000000 write-back
[    0.010265] kernel:   3 disabled
[    0.010266] kernel:   4 disabled
[    0.010267] kernel:   5 disabled
[    0.010267] kernel:   6 disabled
[    0.010268] kernel:   7 disabled
[    0.010269] kernel: TOM2: 0000000140000000 aka 5120M
[    0.010610] kernel: x86/PAT: Configuration [0-7]: WB  WC  UC- UC  WB  WP  UC- WT  
[    0.010717] kernel: e820: update [mem 0xc0000000-0xffffffff] usable ==> reserved
[    0.010717] kernel: e820: update [mem 0xc0000000-0xffffffff] usable ==> reserved
[    0.010724] kernel: last_pfn = 0xb7ef0 max_arch_pfn = 0x400000000
[    0.012902] kernel: found SMP MP-table at [mem 0x000f4020-0x000f402f]
[    0.019507] kernel: check: Scanning 1 areas for low memory corruption
[    0.019880] kernel: RAMDISK: [mem 0x30ff3000-0x347f0fff]
[    0.019894] kernel: ACPI: Early table checksum verification disabled
[    0.019901] kernel: ACPI: RSDP 0x00000000000F82B0 000014 (v00 GATEWA)
[    0.019905] kernel: ACPI: RSDT 0x00000000B7EF3000 00003C (v01 GATEWA SYSTEM   42302E31 NVDA 00000000)
[    0.019913] kernel: ACPI: FACP 0x00000000B7EF3080 000074 (v01 GATEWA SYSTEM   42302E31 NVDA 00000000)
[    0.019919] kernel: ACPI BIOS Warning (bug): Optional FADT field Pm2ControlBlock has valid Length but zero Address: 0x0000000000000000/0x1 (20200528/tbfadt-615)
[    0.019925] kernel: ACPI: DSDT 0x00000000B7EF3100 00AE39 (v01 GATEWA SYSTEM   00001000 MSFT 03000000)
[    0.019930] kernel: ACPI: FACS 0x00000000B7EF1800 000040
[    0.019934] kernel: ACPI: SSDT 0x00000000B7EFE000 000136 (v01 PTLTD  POWERNOW 00000001  LTP 00000001)
[    0.019938] kernel: ACPI: HPET 0x00000000B7EFE140 000038 (v01 GATEWA SYSTEM   42302E31 NVDA 00000098)
[    0.019943] kernel: ACPI: SLIC 0x00000000B7EFE180 000176 (v01 GATEWA SYSTEM   42302E31 NVDA 00000000)
[    0.019947] kernel: ACPI: MCFG 0x00000000B7EFE300 00003C (v01 GATEWA SYSTEM   42302E31 NVDA 00000000)
[    0.019952] kernel: ACPI: APIC 0x00000000B7EFDF40 00008E (v01 GATEWA SYSTEM   42302E31 NVDA 00000000)
[    0.019956] kernel: ACPI: Reserving FACP table memory at [mem 0xb7ef3080-0xb7ef30f3]
[    0.019958] kernel: ACPI: Reserving DSDT table memory at [mem 0xb7ef3100-0xb7efdf38]
[    0.019959] kernel: ACPI: Reserving FACS table memory at [mem 0xb7ef1800-0xb7ef183f]
[    0.019961] kernel: ACPI: Reserving SSDT table memory at [mem 0xb7efe000-0xb7efe135]
[    0.019963] kernel: ACPI: Reserving HPET table memory at [mem 0xb7efe140-0xb7efe177]
[    0.019964] kernel: ACPI: Reserving SLIC table memory at [mem 0xb7efe180-0xb7efe2f5]
[    0.019966] kernel: ACPI: Reserving MCFG table memory at [mem 0xb7efe300-0xb7efe33b]
[    0.019967] kernel: ACPI: Reserving APIC table memory at [mem 0xb7efdf40-0xb7efdfcd]
[    0.019979] kernel: ACPI: Local APIC address 0xfee00000
[    0.020058] kernel: NUMA turned off
[    0.020060] kernel: Faking a node at [mem 0x0000000000000000-0x000000013fffffff]
[    0.020074] kernel: NODE_DATA(0) allocated [mem 0x13ffd3000-0x13fffcfff]
[    0.020767] kernel: Zone ranges:
[    0.020768] kernel:   DMA      [mem 0x0000000000001000-0x0000000000ffffff]
[    0.020770] kernel:   DMA32    [mem 0x0000000001000000-0x00000000ffffffff]
[    0.020772] kernel:   Normal   [mem 0x0000000100000000-0x000000013fffffff]
[    0.020773] kernel:   Device   empty
[    0.020775] kernel: Movable zone start for each node
[    0.020780] kernel: Early memory node ranges
[    0.020782] kernel:   node   0: [mem 0x0000000000001000-0x000000000009dfff]
[    0.020783] kernel:   node   0: [mem 0x0000000000100000-0x00000000b7eeffff]
[    0.020785] kernel:   node   0: [mem 0x0000000100000000-0x000000013fffffff]
[    0.020787] kernel: Initmem setup node 0 [mem 0x0000000000001000-0x000000013fffffff]
[    0.020789] kernel: On node 0 totalpages: 1015437
[    0.020791] kernel:   DMA zone: 64 pages used for memmap
[    0.020791] kernel:   DMA zone: 21 pages reserved
[    0.020793] kernel:   DMA zone: 3997 pages, LIFO batch:0
[    0.021714] kernel:   DMA zone: 28771 pages in unavailable ranges
[    0.021716] kernel:   DMA32 zone: 11708 pages used for memmap
[    0.021717] kernel:   DMA32 zone: 749296 pages, LIFO batch:63
[    0.041404] kernel:   DMA32 zone: 272 pages in unavailable ranges
[    0.041406] kernel:   Normal zone: 4096 pages used for memmap
[    0.041407] kernel:   Normal zone: 262144 pages, LIFO batch:63
[    0.048540] kernel: Detected use of extended apic ids on hypertransport bus
...
[    0.087966] kernel: AGP: Checking aperture...
[    0.094380] kernel: AGP: No AGP bridge found
[    0.094383] kernel: AGP: Node 0: aperture [bus addr 0x1c000000-0x1dffffff] (32MB)
[    0.094385] kernel: Aperture pointing to e820 RAM. Ignoring.
[    0.094386] kernel: AGP: Your BIOS doesn't leave an aperture memory hole
[    0.094388] kernel: AGP: Please enable the IOMMU option in the BIOS setup
[    0.094389] kernel: AGP: This costs you 64MB of RAM
[    0.094393] kernel: AGP: Mapping aperture over RAM [mem 0xac000000-0xafffffff] (65536KB)
...
[    0.217749] kernel: PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf0000000-0xf3ffffff] (base 0xf0000000)
[    0.217902] kernel: PCI: MMCONFIG at [mem 0xf0000000-0xf3ffffff] reserved in E820
[    0.218022] kernel: PCI: Using configuration type 1 for base access
...
[    0.223028] kernel: ACPI: Added _OSI(Module Device)
[    0.223127] kernel: ACPI: Added _OSI(Processor Device)
[    0.223225] kernel: ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.223325] kernel: ACPI: Added _OSI(Processor Aggregator Device)
[    0.223427] kernel: ACPI: Added _OSI(Linux-Dell-Video)
[    0.223526] kernel: ACPI: Added _OSI(Linux-Lenovo-NV-HDMI-Audio)
[    0.223628] kernel: ACPI: Added _OSI(Linux-HPI-Hybrid-Graphics)
[    0.239627] kernel: ACPI: 2 ACPI AML tables successfully acquired and loaded
[    0.240393] kernel: ACPI Error: AE_NOT_FOUND, While resolving a named reference package element - \_PR_.CPU0 (20200528/dspkginit-438)
[    0.244169] kernel: ACPI: Interpreter enabled
[    0.244289] kernel: ACPI: (supports S0 S3 S4 S5)
[    0.244386] kernel: ACPI: Using IOAPIC for interrupt routing
[    0.244524] kernel: PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.245300] kernel: ACPI: Enabled 11 GPEs in block 00 to 1F
[    0.273880] kernel: ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-05])
[    0.273997] kernel: acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig Segments MSI HPX-Type3]
[    0.274302] kernel: acpi PNP0A08:00: _OSC: not requesting OS control; OS requires [ExtendedConfig ASPM ClockPM MSI]
[    0.276703] kernel: PCI host bridge to bus 0000:00
...
[    0.804145] kernel: PCI-DMA: Disabling AGP.
[    0.804315] kernel: PCI-DMA: aperture base @ ac000000 size 65536 KB
[    0.804418] kernel: PCI-DMA: using GART IOMMU.
[    0.804516] kernel: PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
...
```Is the false "no aperture memory hole" fixable for Kernels 5.0-up; or is the Kernel Project treating the "no memory hole" as a WontFix (or -- oje! -- a CantFix)?  If fixable, what measures will be necessary?

**Addendum:**  I cannot enlarge the AGP Node 0 aperture on the EL1210; but the *available* settings yield different errors.  With VideoMemory = 256 MB and GPU = Onboard, the AGP portion of DMesg yields (ref: dmesg.20210830):
```
[    0.086937] kernel: AGP: Checking aperture...
[    0.086942] kernel: AGP: Node 0: aperture [bus addr 0xb0000000-0xb1ffffff] (32MB)
[    0.086946] kernel: Aperture too small (32 MB) than (64 MB)
[    0.086948] kernel: AGP: Your BIOS doesn't leave an aperture memory hole
[    0.086950] kernel: AGP: Please enable the IOMMU option in the BIOS setup
[    0.086952] kernel: AGP: This costs you 32MB of RAM
[    0.086956] kernel: AGP: Mapping aperture over RAM [mem 0xa8000000-0xa9ffffff] (32768KB)

```  Anything else accessible yields (ref: dmesg.20210903):
```
[    0.086912] kernel: AGP: Checking aperture...
[    0.086916] kernel: AGP: Node 0: aperture [bus addr 0x3c000000-0x3dffffff] (32MB)
[    0.086920] kernel: Aperture pointing to e820 RAM. Ignoring.
[    0.086922] kernel: AGP: Your BIOS doesn't leave an aperture memory hole
[    0.086924] kernel: AGP: Please enable the IOMMU option in the BIOS setup
[    0.086926] kernel: AGP: This costs you 32MB of RAM
[    0.086930] kernel: AGP: Mapping aperture over RAM [mem 0xa8000000-0xa9ffffff] (32768KB)

```I had " iommu=noagp,memaper=0 " (viz., K8 AGPGART at 32 MiB for the IO memory map) interpreted for the File /boot/grub/grub.cfg in both instances, preselected via the GRUB_CMDLINE_LINUX line in /etc/default/grub.

**Addendum 2:**  Every now and then I encounter a combination in the BIOS Settings that bull's-eyes the Node 0 aperture for the IO memory map.  From dmesg.20210905 (redacted):
```
[    0.000000] kernel: Linux version 5.11.0-27-generic (buildd@lcy01-amd64-019) (gcc (Ubuntu 9.3.0-17ubuntu1~20.04) 9.3.0, GNU ld (GNU Binutils for Ubuntu) 2.34) #29~20.04.1-Ubuntu SMP Wed Aug 11 15:58:17 UTC 2021 (Ubuntu 5.11.0-27.29~20.04.1-generic 5.11.22)
[    0.000000] kernel: Command line: BOOT_IMAGE=/vmlinuz-5.11.0-27-generic root=UUID=c4248af1-a4cf-49a2-ba18-4de2c65c815c ro acpi_force_table_verification mce=bios_cmci_threshold trace_clock=global hashdist=0 numa=off gart_fix_e820=off iommu=memaper=0 access=v1 hpet=verbose
[    0.000000] kernel: KERNEL supported cpus:
[    0.000000] kernel:   Intel GenuineIntel
[    0.000000] kernel:   AMD AuthenticAMD
[    0.000000] kernel:   Hygon HygonGenuine
[    0.000000] kernel:   Centaur CentaurHauls
[    0.000000] kernel:   zhaoxin   Shanghai  
[    0.000000] kernel: x86/fpu: x87 FPU will use FXSAVE
[    0.000000] kernel: BIOS-provided physical RAM map:
[    0.000000] kernel: BIOS-e820: [mem 0x0000000000000000-0x000000000009e7ff] usable
[    0.000000] kernel: BIOS-e820: [mem 0x000000000009e800-0x000000000009ffff] reserved
[    0.000000] kernel: BIOS-e820: [mem 0x00000000000f0000-0x00000000000fffff] reserved
[    0.000000] kernel: BIOS-e820: [mem 0x0000000000100000-0x00000000afeeffff] usable
[    0.000000] kernel: BIOS-e820: [mem 0x00000000afef0000-0x00000000afef2fff] ACPI NVS
[    0.000000] kernel: BIOS-e820: [mem 0x00000000afef3000-0x00000000afefffff] ACPI data
[    0.000000] kernel: BIOS-e820: [mem 0x00000000b0000000-0x00000000bfffffff] reserved
[    0.000000] kernel: BIOS-e820: [mem 0x00000000f0000000-0x00000000f3ffffff] reserved
[    0.000000] kernel: BIOS-e820: [mem 0x00000000fec00000-0x00000000ffffffff] reserved
[    0.000000] kernel: BIOS-e820: [mem 0x0000000100000000-0x000000013fffffff] usable
[    0.000000] kernel: NX (Execute Disable) protection: active
[    0.000000] kernel: SMBIOS 2.5 present.
[    0.000000] kernel: DMI: eMachines EL1210-09/WMCP78M, BIOS R01-A0 09/23/2008
[    0.000000] kernel: tsc: Fast TSC calibration using PIT
[    0.000000] kernel: tsc: Detected 2399.919 MHz processor
[    0.003718] kernel: e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.003723] kernel: e820: remove [mem 0x000a0000-0x000fffff] usable
...
[    0.086848] kernel: AGP: Checking aperture...
[    0.086852] kernel: AGP: Node 0: aperture [bus addr 0xa8000000-0xa9ffffff] (32MB)
[    0.086856] kernel: Aperture pointing to e820 RAM. Ignoring.
[    0.086858] kernel: AGP: Your BIOS doesn't leave an aperture memory hole
[    0.086860] kernel: AGP: Please enable the IOMMU option in the BIOS setup
[    0.086862] kernel: AGP: This costs you 32MB of RAM
[    0.086866] kernel: AGP: Mapping aperture over RAM [mem 0xa8000000-0xa9ffffff] (32768KB)
...
[    0.811491] kernel: PCI-DMA: Disabling AGP.
[    0.811596] kernel: PCI-DMA: aperture base @ a8000000 size 32768 KB
[    0.811658] kernel: PCI-DMA: using GART IOMMU.
[    0.811715] kernel: PCI-DMA: Warning: Small IOMMU 32MB. Consider increasing the AGP aperture in BIOS
[    0.811796] kernel: PCI-DMA: Reserving 32MB of IOMMU area in the AGP aperture
...
```

---

