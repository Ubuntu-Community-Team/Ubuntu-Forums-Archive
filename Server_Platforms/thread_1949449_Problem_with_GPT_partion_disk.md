---
title: "Problem with GPT partion disk"
date: 2012-03-30
forum: Server Platforms
---

### Post by edika32 on 2012-03-30
Hi I'm running ubuntu server 11.10 with kernel 3.0.0-17-server and have BIG problem gettig 3TB internal drives that have its partion table with setted up with GTP. I also have some ubuntu 10.04 servers that without any problem can mount these disks, so there is nothing wrong with the disk itself.

Here is output from **dmesg**:


```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.0.0-17-server (buildd@yellow) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #30-Ubuntu SMP Thu Mar 8 22:15:30 UTC 2012 (Ubuntu 3.0.0-17.30-server 3.0.22)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-17-server root=UUID=be36497e-8ebf-4b7c-aea9-79b6aa6530cb ro
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 0000000000099800 (usable)
[    0.000000]  BIOS-e820: 0000000000099800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000df780000 (usable)
[    0.000000]  BIOS-e820: 00000000df78e000 - 00000000df790000 (reserved)
[    0.000000]  BIOS-e820: 00000000df790000 - 00000000df79e000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000df79e000 - 00000000df7d0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000df7d0000 - 00000000df7e0000 (reserved)
[    0.000000]  BIOS-e820: 00000000df7ec000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffc00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000620000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI present.
[    0.000000] DMI: Supermicro X8ST3/X8ST3, BIOS 2.0        07/29/10  
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x620000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-D3FFF write-protect
[    0.000000]   D4000-DFFFF uncachable
[    0.000000]   E0000-E3FFF write-protect
[    0.000000]   E4000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask C00000000 write-back
[    0.000000]   1 base 400000000 mask E00000000 write-back
[    0.000000]   2 base 600000000 mask FE0000000 write-back
[    0.000000]   3 base 0E0000000 mask FE0000000 uncachable
[    0.000000]   4 base 0DF800000 mask FFF800000 uncachable
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 16GB, type WB
[    0.000000] reg 1, base: 16GB, range: 8GB, type WB
[    0.000000] reg 2, base: 24GB, range: 512MB, type WB
[    0.000000] reg 3, base: 3584MB, range: 512MB, type UC
[    0.000000] reg 4, base: 3576MB, range: 8MB, type UC
[    0.000000] total RAM covered: 24568M
[    0.000000]  gran_size: 64K     chunk_size: 64K     num_reg: 8      lose cover RAM: 20992M
[    0.000000]  gran_size: 64K     chunk_size: 128K     num_reg: 8      lose cover RAM: 20992M
[    0.000000]  gran_size: 64K     chunk_size: 256K     num_reg: 8      lose cover RAM: 20992M
[    0.000000]  gran_size: 64K     chunk_size: 512K     num_reg: 8      lose cover RAM: 20992M
[    0.000000]  gran_size: 64K     chunk_size: 1M     num_reg: 8      lose cover RAM: 20992M
[    0.000000]  gran_size: 64K     chunk_size: 2M     num_reg: 8      lose cover RAM: 20992M
[    0.000000]  gran_size: 64K     chunk_size: 4M     num_reg: 8      lose cover RAM: 20992M
[    0.000000]  gran_size: 64K     chunk_size: 8M     num_reg: 8      lose cover RAM: 20992M
[    0.000000]  gran_size: 64K     chunk_size: 16M     num_reg: 8      lose cover RAM: 0G
[    0.000000]  gran_size: 64K     chunk_size: 32M     num_reg: 8      lose cover RAM: 0G
[    0.000000]  gran_size: 64K     chunk_size: 64M     num_reg: 8      lose cover RAM: 0G
[    0.000000]  gran_size: 64K     chunk_size: 128M     num_reg: 8      lose cover RAM: 0G
[    0.000000]  gran_size: 64K     chunk_size: 256M     num_reg: 8      lose cover RAM: 0G
[    0.000000]  gran_size: 64K     chunk_size: 512M     num_reg: 8      lose cover RAM: 0G
[    0.000000]  gran_size: 64K     chunk_size: 1G     num_reg: 8      lose cover RAM: 0G
[    0.000000] *BAD*gran_size: 64K     chunk_size: 2G     num_reg: 8      lose cover RAM: -1G
[    0.000000]  gran_size: 128K     chunk_size: 128K     num_reg: 8      lose cover RAM: 20992M
[    0.000000]  gran_size: 128K     chunk_size: 256K     num_reg: 8      lose cover RAM: 20992M
[    0.000000]  gran_size: 128K     chunk_size: 512K     num_reg: 8      lose cover RAM: 20992M
[    0.000000]  gran_size: 128K     chunk_size: 1M     num_reg: 8      lose cover RAM: 20992M
[    0.000000]  gran_size: 128K     chunk_size: 2M     num_reg: 8      lose cover RAM: 20992M
[    0.000000]  gran_size: 128K     chunk_size: 4M     num_reg: 8      lose cover RAM: 20992M
[    0.000000]  gran_size: 128K     chunk_size: 8M     num_reg: 8      lose cover RAM: 20992M
[    0.000000]  gran_size: 128K     chunk_size: 16M     num_reg: 8      lose cover RAM: 0G
[    0.000000]  gran_size: 128K     chunk_size: 32M     num_reg: 8      lose cover RAM: 0G
[    0.000000]  gran_size: 128K     chunk_size: 64M     num_reg: 8      lose cover RAM: 0G
[    0.000000]  gran_size: 128K     chunk_size: 128M     num_reg: 8      lose cover RAM: 0G
[    0.000000]  gran_size: 128K     chunk_size: 256M     num_reg: 8      lose cover RAM: 0G
[    0.000000]  gran_size: 128K     chunk_size: 512M     num_reg: 8      lose cover RAM: 0G
[    0.000000]  gran_size: 128K     chunk_size: 1G     num_reg: 8      lose cover RAM: 0G
[    0.000000] *BAD*gran_size: 128K     chunk_size: 2G     num_reg: 8      lose cover RAM: -1G
[    0.000000]  gran_size: 256K     chunk_size: 256K     num_reg: 8      lose cover RAM: 20992M
[    0.000000]  gran_size: 256K     chunk_size: 512K     num_reg: 8      lose cover RAM: 20992M
[    0.000000]  gran_size: 256K     chunk_size: 1M     num_reg: 8      lose cover RAM: 20992M
[    0.000000]  gran_size: 256K     chunk_size: 2M     num_reg: 8      lose cover RAM: 20992M
[    0.000000]  gran_size: 256K     chunk_size: 4M     num_reg: 8      lose cover RAM: 20992M
[    0.000000]  gran_size: 256K     chunk_size: 8M     num_reg: 8      lose cover RAM: 20992M
[    0.000000]  gran_size: 256K     chunk_size: 16M     num_reg: 8      lose cover RAM: 0G
[    0.000000]  gran_size: 256K     chunk_size: 32M     num_reg: 8      lose cover RAM: 0G
[    0.000000]  gran_size: 256K     chunk_size: 64M     num_reg: 8      lose cover RAM: 0G
[    0.000000]  gran_size: 256K     chunk_size: 128M     num_reg: 8      lose cover RAM: 0G
[    0.000000]  gran_size: 256K     chunk_size: 256M     num_reg: 8      lose cover RAM: 0G
[    0.000000]  gran_size: 256K     chunk_size: 512M     num_reg: 8      lose cover RAM: 0G
[    0.000000]  gran_size: 256K     chunk_size: 1G     num_reg: 8      lose cover RAM: 0G
[    0.000000] *BAD*gran_size: 256K     chunk_size: 2G     num_reg: 8      lose cover RAM: -1G
[    0.000000]  gran_size: 512K     chunk_size: 512K     num_reg: 8      lose cover RAM: 20992M
[    0.000000]  gran_size: 512K     chunk_size: 1M     num_reg: 8      lose cover RAM: 20992M
[    0.000000]  gran_size: 512K     chunk_size: 2M     num_reg: 8      lose cover RAM: 20992M
[    0.000000]  gran_size: 512K     chunk_size: 4M     num_reg: 8      lose cover RAM: 20992M
[    0.000000]  gran_size: 512K     chunk_size: 8M     num_reg: 8      lose cover RAM: 20992M
[    0.000000]  gran_size: 512K     chunk_size: 16M     num_reg: 8      lose cover RAM: 0G
[    0.000000]  gran_size: 512K     chunk_size: 32M     num_reg: 8      lose cover RAM: 0G
[    0.000000]  gran_size: 512K     chunk_size: 64M     num_reg: 8      lose cover RAM: 0G
[    0.000000]  gran_size: 512K     chunk_size: 128M     num_reg: 8      lose cover RAM: 0G
[    0.000000]  gran_size: 512K     chunk_size: 256M     num_reg: 8      lose cover RAM: 0G
[    0.000000]  gran_size: 512K     chunk_size: 512M     num_reg: 8      lose cover RAM: 0G
[    0.000000]  gran_size: 512K     chunk_size: 1G     num_reg: 8      lose cover RAM: 0G
[    0.000000] *BAD*gran_size: 512K     chunk_size: 2G     num_reg: 8      lose cover RAM: -1G
[    0.000000]  gran_size: 1M     chunk_size: 1M     num_reg: 8      lose cover RAM: 20992M
[    0.000000]  gran_size: 1M     chunk_size: 2M     num_reg: 8      lose cover RAM: 20992M
[    0.000000]  gran_size: 1M     chunk_size: 4M     num_reg: 8      lose cover RAM: 20992M
[    0.000000]  gran_size: 1M     chunk_size: 8M     num_reg: 8      lose cover RAM: 20992M
[    0.000000]  gran_size: 1M     chunk_size: 16M     num_reg: 8      lose cover RAM: 0G
[    0.000000]  gran_size: 1M     chunk_size: 32M     num_reg: 8      lose cover RAM: 0G
[    0.000000]  gran_size: 1M     chunk_size: 64M     num_reg: 8      lose cover RAM: 0G
[    0.000000]  gran_size: 1M     chunk_size: 128M     num_reg: 8      lose cover RAM: 0G
[    0.000000]  gran_size: 1M     chunk_size: 256M     num_reg: 8      lose cover RAM: 0G
[    0.000000]  gran_size: 1M     chunk_size: 512M     num_reg: 8      lose cover RAM: 0G
[    0.000000]  gran_size: 1M     chunk_size: 1G     num_reg: 8      lose cover RAM: 0G
[    0.000000] *BAD*gran_size: 1M     chunk_size: 2G     num_reg: 8      lose cover RAM: -1G
[    0.000000]  gran_size: 2M     chunk_size: 2M     num_reg: 8      lose cover RAM: 20992M
[    0.000000]  gran_size: 2M     chunk_size: 4M     num_reg: 8      lose cover RAM: 20992M
[    0.000000]  gran_size: 2M     chunk_size: 8M     num_reg: 8      lose cover RAM: 20992M
[    0.000000]  gran_size: 2M     chunk_size: 16M     num_reg: 8      lose cover RAM: 0G
[    0.000000]  gran_size: 2M     chunk_size: 32M     num_reg: 8      lose cover RAM: 0G
[    0.000000]  gran_size: 2M     chunk_size: 64M     num_reg: 8      lose cover RAM: 0G
[    0.000000]  gran_size: 2M     chunk_size: 128M     num_reg: 8      lose cover RAM: 0G
[    0.000000]  gran_size: 2M     chunk_size: 256M     num_reg: 8      lose cover RAM: 0G
[    0.000000]  gran_size: 2M     chunk_size: 512M     num_reg: 8      lose cover RAM: 0G
[    0.000000]  gran_size: 2M     chunk_size: 1G     num_reg: 8      lose cover RAM: 0G
[    0.000000] *BAD*gran_size: 2M     chunk_size: 2G     num_reg: 8      lose cover RAM: -1G
[    0.000000]  gran_size: 4M     chunk_size: 4M     num_reg: 8      lose cover RAM: 20992M
[    0.000000]  gran_size: 4M     chunk_size: 8M     num_reg: 8      lose cover RAM: 20992M
[    0.000000]  gran_size: 4M     chunk_size: 16M     num_reg: 8      lose cover RAM: 0G
[    0.000000]  gran_size: 4M     chunk_size: 32M     num_reg: 8      lose cover RAM: 0G
[    0.000000]  gran_size: 4M     chunk_size: 64M     num_reg: 8      lose cover RAM: 0G
[    0.000000]  gran_size: 4M     chunk_size: 128M     num_reg: 8      lose cover RAM: 0G
[    0.000000]  gran_size: 4M     chunk_size: 256M     num_reg: 8      lose cover RAM: 0G
[    0.000000]  gran_size: 4M     chunk_size: 512M     num_reg: 8      lose cover RAM: 0G
[    0.000000]  gran_size: 4M     chunk_size: 1G     num_reg: 8      lose cover RAM: 0G
[    0.000000] *BAD*gran_size: 4M     chunk_size: 2G     num_reg: 8      lose cover RAM: -1G
[    0.000000]  gran_size: 8M     chunk_size: 8M     num_reg: 8      lose cover RAM: 20992M
[    0.000000]  gran_size: 8M     chunk_size: 16M     num_reg: 8      lose cover RAM: 0G
[    0.000000]  gran_size: 8M     chunk_size: 32M     num_reg: 8      lose cover RAM: 0G
[    0.000000]  gran_size: 8M     chunk_size: 64M     num_reg: 8      lose cover RAM: 0G
[    0.000000]  gran_size: 8M     chunk_size: 128M     num_reg: 8      lose cover RAM: 0G
[    0.000000]  gran_size: 8M     chunk_size: 256M     num_reg: 8      lose cover RAM: 0G
[    0.000000]  gran_size: 8M     chunk_size: 512M     num_reg: 8      lose cover RAM: 0G
[    0.000000]  gran_size: 8M     chunk_size: 1G     num_reg: 8      lose cover RAM: 0G
[    0.000000] *BAD*gran_size: 8M     chunk_size: 2G     num_reg: 8      lose cover RAM: -1G
[    0.000000]  gran_size: 16M     chunk_size: 16M     num_reg: 8      lose cover RAM: 16904M
[    0.000000]  gran_size: 16M     chunk_size: 32M     num_reg: 8      lose cover RAM: 8M
[    0.000000]  gran_size: 16M     chunk_size: 64M     num_reg: 8      lose cover RAM: 8M
[    0.000000]  gran_size: 16M     chunk_size: 128M     num_reg: 8      lose cover RAM: 8M
[    0.000000]  gran_size: 16M     chunk_size: 256M     num_reg: 8      lose cover RAM: 8M
[    0.000000]  gran_size: 16M     chunk_size: 512M     num_reg: 8      lose cover RAM: 8M
[    0.000000]  gran_size: 16M     chunk_size: 1G     num_reg: 8      lose cover RAM: 8M
[    0.000000] *BAD*gran_size: 16M     chunk_size: 2G     num_reg: 8      lose cover RAM: -1016M
[    0.000000]  gran_size: 32M     chunk_size: 32M     num_reg: 8      lose cover RAM: 8728M
[    0.000000]  gran_size: 32M     chunk_size: 64M     num_reg: 8      lose cover RAM: 24M
[    0.000000]  gran_size: 32M     chunk_size: 128M     num_reg: 8      lose cover RAM: 24M
[    0.000000]  gran_size: 32M     chunk_size: 256M     num_reg: 8      lose cover RAM: 24M
[    0.000000]  gran_size: 32M     chunk_size: 512M     num_reg: 8      lose cover RAM: 24M
[    0.000000]  gran_size: 32M     chunk_size: 1G     num_reg: 8      lose cover RAM: 24M
[    0.000000] *BAD*gran_size: 32M     chunk_size: 2G     num_reg: 8      lose cover RAM: -1000M
[    0.000000]  gran_size: 64M     chunk_size: 64M     num_reg: 8      lose cover RAM: 568M
[    0.000000]  gran_size: 64M     chunk_size: 128M     num_reg: 8      lose cover RAM: 56M
[    0.000000]  gran_size: 64M     chunk_size: 256M     num_reg: 8      lose cover RAM: 56M
[    0.000000]  gran_size: 64M     chunk_size: 512M     num_reg: 8      lose cover RAM: 56M
[    0.000000]  gran_size: 64M     chunk_size: 1G     num_reg: 8      lose cover RAM: 56M
[    0.000000] *BAD*gran_size: 64M     chunk_size: 2G     num_reg: 8      lose cover RAM: -968M
[    0.000000]  gran_size: 128M     chunk_size: 128M     num_reg: 8      lose cover RAM: 120M
[    0.000000]  gran_size: 128M     chunk_size: 256M     num_reg: 8      lose cover RAM: 120M
[    0.000000]  gran_size: 128M     chunk_size: 512M     num_reg: 8      lose cover RAM: 120M
[    0.000000]  gran_size: 128M     chunk_size: 1G     num_reg: 8      lose cover RAM: 120M
[    0.000000] *BAD*gran_size: 128M     chunk_size: 2G     num_reg: 8      lose cover RAM: -904M
[    0.000000]  gran_size: 256M     chunk_size: 256M     num_reg: 7      lose cover RAM: 248M
[    0.000000]  gran_size: 256M     chunk_size: 512M     num_reg: 8      lose cover RAM: 248M
[    0.000000]  gran_size: 256M     chunk_size: 1G     num_reg: 8      lose cover RAM: 248M
[    0.000000] *BAD*gran_size: 256M     chunk_size: 2G     num_reg: 8      lose cover RAM: -776M
[    0.000000]  gran_size: 512M     chunk_size: 512M     num_reg: 6      lose cover RAM: 504M
[    0.000000]  gran_size: 512M     chunk_size: 1G     num_reg: 7      lose cover RAM: 504M
[    0.000000]  gran_size: 512M     chunk_size: 2G     num_reg: 8      lose cover RAM: 504M
[    0.000000]  gran_size: 1G     chunk_size: 1G     num_reg: 5      lose cover RAM: 1016M
[    0.000000]  gran_size: 1G     chunk_size: 2G     num_reg: 5      lose cover RAM: 1016M
[    0.000000]  gran_size: 2G     chunk_size: 2G     num_reg: 4      lose cover RAM: 2040M
[    0.000000] mtrr_cleanup: can not find optimal value
[    0.000000] please specify mtrr_gran_size/mtrr_chunk_size
[    0.000000] e820 update range: 00000000df800000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xdf780 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Base memory trampoline at [ffff880000094000] 94000 size 20480
[    0.000000] init_memory_mapping: 0000000000000000-00000000df780000
[    0.000000]  0000000000 - 00df600000 page 2M
[    0.000000]  00df600000 - 00df780000 page 4k
[    0.000000] kernel direct mapping tables up to df780000 @ 1fffa000-20000000
[    0.000000] init_memory_mapping: 0000000100000000-0000000620000000
[    0.000000]  0100000000 - 0620000000 page 2M
[    0.000000] kernel direct mapping tables up to 620000000 @ df766000-df780000
[    0.000000] RAMDISK: 365ec000 - 372ee000
[    0.000000] ACPI: RSDP 00000000000faa70 00024 (v02 ACPIAM)
[    0.000000] ACPI: XSDT 00000000df790100 00074 (v01 SMCI            20100729 MSFT 00000097)
[    0.000000] ACPI: FACP 00000000df790290 000F4 (v03 072910 FACP2001 20100729 MSFT 00000097)
[    0.000000] ACPI: DSDT 00000000df790630 06761 (v01  1F580 1F580000 00000000 INTL 20051117)
[    0.000000] ACPI: FACS 00000000df79e000 00040
[    0.000000] ACPI: APIC 00000000df790390 000D2 (v01 072910 APIC2001 20100729 MSFT 00000097)
[    0.000000] ACPI: MCFG 00000000df790470 0003C (v01 072910 OEMMCFG  20100729 MSFT 00000097)
[    0.000000] ACPI: OEMB 00000000df79e040 0007B (v01 072910 OEMB2001 20100729 MSFT 00000097)
[    0.000000] ACPI: HPET 00000000df79a630 00038 (v01 072910 OEMHPET  20100729 MSFT 00000097)
[    0.000000] ACPI: SSDT 00000000df7a0b70 00363 (v01 DpgPmm    CpuPm 00000012 INTL 20051117)
[    0.000000] ACPI: EINJ 00000000df79a670 00130 (v01  AMIER AMI_EINJ 20100729 MSFT 00000097)
[    0.000000] ACPI: BERT 00000000df79a800 00030 (v01  AMIER AMI_BERT 20100729 MSFT 00000097)
[    0.000000] ACPI: ERST 00000000df79a830 001B0 (v01  AMIER AMI_ERST 20100729 MSFT 00000097)
[    0.000000] ACPI: HEST 00000000df79a9e0 000A8 (v01  AMIER ABC_HEST 20100729 MSFT 00000097)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000620000000
[    0.000000] Initmem setup node 0 0000000000000000-0000000620000000
[    0.000000]   NODE_DATA [000000061fffb000 - 000000061fffffff]
[    0.000000]  [ffffea0000000000-ffffea00157fffff] PMD -> [ffff880607600000-ffff88061c7fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00620000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x00000099
[    0.000000]     0: 0x00000100 -> 0x000df780
[    0.000000]     0: 0x00100000 -> 0x00620000
[    0.000000] On node 0 totalpages: 6289161
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 5 pages reserved
[    0.000000]   DMA zone: 3916 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 896952 pages, LIFO batch:31
[    0.000000]   Normal zone: 73472 pages used for memmap
[    0.000000]   Normal zone: 5300480 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x06] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x07] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x09] lapic_id[0x88] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0a] lapic_id[0x89] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0b] lapic_id[0x8a] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0c] lapic_id[0x8b] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0d] lapic_id[0x8c] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0e] lapic_id[0x8d] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0f] lapic_id[0x8e] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x10] lapic_id[0x8f] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x08] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 8, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a301 base: 0xfed00000
[    0.000000] SMP: Allowing 16 CPUs, 8 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 0000000000099000 - 000000000009a000
[    0.000000] PM: Registered nosave memory: 000000000009a000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000df780000 - 00000000df78e000
[    0.000000] PM: Registered nosave memory: 00000000df78e000 - 00000000df790000
[    0.000000] PM: Registered nosave memory: 00000000df790000 - 00000000df79e000
[    0.000000] PM: Registered nosave memory: 00000000df79e000 - 00000000df7d0000
[    0.000000] PM: Registered nosave memory: 00000000df7d0000 - 00000000df7e0000
[    0.000000] PM: Registered nosave memory: 00000000df7e0000 - 00000000df7ec000
[    0.000000] PM: Registered nosave memory: 00000000df7ec000 - 00000000f0000000
[    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffc00000
[    0.000000] PM: Registered nosave memory: 00000000ffc00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at f0000000 (gap: f0000000:ee00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:16 nr_node_ids:1
[    0.000000] PERCPU: Embedded 27 pages/cpu @ffff88061fc00000 s79616 r8192 d22784 u131072
[    0.000000] pcpu-alloc: s79616 r8192 d22784 u131072 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 00 01 02 03 04 05 06 07 08 09 10 11 12 13 14 15 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 6201348
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-17-server root=UUID=be36497e-8ebf-4b7c-aea9-79b6aa6530cb ro
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 24713604k/25690112k available (6222k kernel code, 533468k absent, 443040k reserved, 6902k data, 904k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=16, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:16640 nr_irqs:808 16
[    0.000000] Extended CMOS year: 2000
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 201326592 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.004000] Detected 3200.685 MHz processor.
[    0.000003] Calibrating delay loop (skipped), value calculated using timer frequency.. 6401.37 BogoMIPS (lpj=12802740)
[    0.000008] pid_max: default: 32768 minimum: 301
[    0.000029] Security Framework initialized
[    0.000040] AppArmor: AppArmor initialized
[    0.000043] Yama: becoming mindful.
[    0.002172] Dentry cache hash table entries: 4194304 (order: 13, 33554432 bytes)
[    0.007486] Inode-cache hash table entries: 2097152 (order: 12, 16777216 bytes)
[    0.009771] Mount-cache hash table entries: 256
[    0.009870] Initializing cgroup subsys cpuacct
[    0.009876] Initializing cgroup subsys memory
[    0.009883] Initializing cgroup subsys devices
[    0.009885] Initializing cgroup subsys freezer
[    0.009888] Initializing cgroup subsys net_cls
[    0.009890] Initializing cgroup subsys blkio
[    0.009896] Initializing cgroup subsys perf_event
[    0.009917] CPU: Physical Processor ID: 0
[    0.009920] CPU: Processor Core ID: 0
[    0.009925] mce: CPU supports 9 MCE banks
[    0.009934] CPU0: Thermal monitoring enabled (TM1)
[    0.009941] using mwait in idle threads.
[    0.011418] ACPI: Core revision 20110413
[    0.035865] ftrace: allocating 26099 entries in 103 pages
[    0.041439] Switched APIC routing to physical flat.
[    0.041825] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.081394] CPU0: Intel(R) Xeon(R) CPU           W3565  @ 3.20GHz stepping 05
[    0.188004] Performance Events: PEBS fmt1+, erratum AAJ80 worked around, Nehalem events, Intel PMU driver.
[    0.188011] ... version:                3
[    0.188013] ... bit width:              48
[    0.188015] ... generic registers:      4
[    0.188017] ... value mask:             0000ffffffffffff
[    0.188018] ... max period:             000000007fffffff
[    0.188020] ... fixed-purpose events:   3
[    0.188022] ... event mask:             000000070000000f
[    0.188298] Booting Node   0, Processors  #1
[    0.188301] smpboot cpu 1: start_ip = 94000
[    0.295827]  #2
[    0.295831] smpboot cpu 2: start_ip = 94000
[    0.403508]  #3
[    0.403511] smpboot cpu 3: start_ip = 94000
[    0.511084]  #4
[    0.511087] smpboot cpu 4: start_ip = 94000
[    0.618754]  #5
[    0.618757] smpboot cpu 5: start_ip = 94000
[    0.726435]  #6
[    0.726439] smpboot cpu 6: start_ip = 94000
[    0.834060]  #7
[    0.834063] smpboot cpu 7: start_ip = 94000
[    0.941680] Brought up 8 CPUs
[    0.941685] Total of 8 processors activated (51198.52 BogoMIPS).
[    0.945968] devtmpfs: initialized
[    0.947389] PM: Registering ACPI NVS region at df79e000 (204800 bytes)
[    0.948463] print_constraints: dummy: 
[    0.948487] Time:  7:15:31  Date: 03/30/12
[    0.948518] NET: Registered protocol family 16
[    0.948592] Trying to unpack rootfs image as initramfs...
[    0.948600] ACPI: bus type pci registered
[    0.948643] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.948647] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.972975] PCI: Using configuration type 1 for base access
[    0.973923] bio: create slab <bio-0> at 0
[    0.974725] ACPI: EC: Look up EC in DSDT
[    0.974962] \_SB_:_OSC evaluation returned wrong type
[    0.974963] _OSC request data:1 7 
[    0.975577] ACPI: Executed 1 blocks of module-level executable AML code
[    1.005427] ACPI: SSDT 00000000df79e0c0 0244C (v01 DpgPmm  P001Ist 00000011 INTL 20051117)
[    1.005682] ACPI: Dynamic OEM Table Load:
[    1.005685] ACPI: SSDT           (null) 0244C (v01 DpgPmm  P001Ist 00000011 INTL 20051117)
[    1.005759] ACPI: SSDT 00000000df7a0510 00659 (v01  PmRef  P001Cst 00003001 INTL 20051117)
[    1.005939] ACPI: Dynamic OEM Table Load:
[    1.005942] ACPI: SSDT           (null) 00659 (v01  PmRef  P001Cst 00003001 INTL 20051117)
[    1.006183] ACPI: Interpreter enabled
[    1.006187] ACPI: (supports S0 S1 S4 S5)
[    1.006200] ACPI: Using IOAPIC for interrupt routing
[    1.010608] ACPI: No dock devices found.
[    1.010628] HEST: Table parsing has been initialized.
[    1.010631] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    1.010689] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    1.010800] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    1.010803] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    1.010806] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    1.010809] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000dffff]
[    1.010812] pci_root PNP0A08:00: host bridge window [mem 0xf0000000-0xfed8ffff]
[    1.010826] pci 0000:00:00.0: [8086:3405] type 0 class 0x000600
[    1.010878] pci 0000:00:00.0: PME# supported from D0 D3hot D3cold
[    1.010881] pci 0000:00:00.0: PME# disabled
[    1.010901] pci 0000:00:01.0: [8086:3408] type 1 class 0x000604
[    1.010956] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    1.010959] pci 0000:00:01.0: PME# disabled
[    1.010978] pci 0000:00:03.0: [8086:340a] type 1 class 0x000604
[    1.011032] pci 0000:00:03.0: PME# supported from D0 D3hot D3cold
[    1.011035] pci 0000:00:03.0: PME# disabled
[    1.011055] pci 0000:00:05.0: [8086:340c] type 1 class 0x000604
[    1.011109] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
[    1.011112] pci 0000:00:05.0: PME# disabled
[    1.011131] pci 0000:00:07.0: [8086:340e] type 1 class 0x000604
[    1.011185] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
[    1.011188] pci 0000:00:07.0: PME# disabled
[    1.011207] pci 0000:00:09.0: [8086:3410] type 1 class 0x000604
[    1.011261] pci 0000:00:09.0: PME# supported from D0 D3hot D3cold
[    1.011264] pci 0000:00:09.0: PME# disabled
[    1.011285] pci 0000:00:14.0: [8086:342e] type 0 class 0x000800
[    1.011349] pci 0000:00:14.1: [8086:3422] type 0 class 0x000800
[    1.011412] pci 0000:00:14.2: [8086:3423] type 0 class 0x000800
[    1.011472] pci 0000:00:14.3: [8086:3438] type 0 class 0x000800
[    1.011527] pci 0000:00:16.0: [8086:3430] type 0 class 0x000880
[    1.011539] pci 0000:00:16.0: reg 10: [mem 0xfbef8000-0xfbefbfff 64bit]
[    1.011605] pci 0000:00:16.1: [8086:3431] type 0 class 0x000880
[    1.011616] pci 0000:00:16.1: reg 10: [mem 0xfbef4000-0xfbef7fff 64bit]
[    1.011681] pci 0000:00:16.2: [8086:3432] type 0 class 0x000880
[    1.011693] pci 0000:00:16.2: reg 10: [mem 0xfbef0000-0xfbef3fff 64bit]
[    1.011759] pci 0000:00:16.3: [8086:3433] type 0 class 0x000880
[    1.011770] pci 0000:00:16.3: reg 10: [mem 0xfbeec000-0xfbeeffff 64bit]
[    1.011836] pci 0000:00:16.4: [8086:3429] type 0 class 0x000880
[    1.011847] pci 0000:00:16.4: reg 10: [mem 0xfbee8000-0xfbeebfff 64bit]
[    1.011913] pci 0000:00:16.5: [8086:342a] type 0 class 0x000880
[    1.011924] pci 0000:00:16.5: reg 10: [mem 0xfbee4000-0xfbee7fff 64bit]
[    1.011991] pci 0000:00:16.6: [8086:342b] type 0 class 0x000880
[    1.012002] pci 0000:00:16.6: reg 10: [mem 0xfbee0000-0xfbee3fff 64bit]
[    1.012068] pci 0000:00:16.7: [8086:342c] type 0 class 0x000880
[    1.012079] pci 0000:00:16.7: reg 10: [mem 0xfbedc000-0xfbedffff 64bit]
[    1.012148] pci 0000:00:1a.0: [8086:3a37] type 0 class 0x000c03
[    1.012188] pci 0000:00:1a.0: reg 20: [io  0x8c00-0x8c1f]
[    1.012235] pci 0000:00:1a.1: [8086:3a38] type 0 class 0x000c03
[    1.012275] pci 0000:00:1a.1: reg 20: [io  0x8880-0x889f]
[    1.012322] pci 0000:00:1a.2: [8086:3a39] type 0 class 0x000c03
[    1.012362] pci 0000:00:1a.2: reg 20: [io  0x8800-0x881f]
[    1.012419] pci 0000:00:1a.7: [8086:3a3c] type 0 class 0x000c03
[    1.012438] pci 0000:00:1a.7: reg 10: [mem 0xfbeda000-0xfbeda3ff]
[    1.012524] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    1.012528] pci 0000:00:1a.7: PME# disabled
[    1.012546] pci 0000:00:1c.0: [8086:3a40] type 1 class 0x000604
[    1.012612] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    1.012615] pci 0000:00:1c.0: PME# disabled
[    1.012633] pci 0000:00:1c.1: [8086:3a42] type 1 class 0x000604
[    1.012699] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    1.012702] pci 0000:00:1c.1: PME# disabled
[    1.012728] pci 0000:00:1d.0: [8086:3a34] type 0 class 0x000c03
[    1.012768] pci 0000:00:1d.0: reg 20: [io  0x8480-0x849f]
[    1.012815] pci 0000:00:1d.1: [8086:3a35] type 0 class 0x000c03
[    1.012855] pci 0000:00:1d.1: reg 20: [io  0x8400-0x841f]
[    1.012903] pci 0000:00:1d.2: [8086:3a36] type 0 class 0x000c03
[    1.012943] pci 0000:00:1d.2: reg 20: [io  0x8080-0x809f]
[    1.012999] pci 0000:00:1d.7: [8086:3a3a] type 0 class 0x000c03
[    1.013019] pci 0000:00:1d.7: reg 10: [mem 0xfbed8000-0xfbed83ff]
[    1.013105] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    1.013108] pci 0000:00:1d.7: PME# disabled
[    1.013125] pci 0000:00:1e.0: [8086:244e] type 1 class 0x000604
[    1.013184] pci 0000:00:1f.0: [8086:3a16] type 0 class 0x000601
[    1.013260] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 4700 (mask 0097)
[    1.013265] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 03e8 (mask 000f)
[    1.013269] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 3 PIO at 1640 (mask 000f)
[    1.013274] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 4 PIO at 0ca0 (mask 000f)
[    1.013317] pci 0000:00:1f.2: [8086:3a20] type 0 class 0x000101
[    1.013331] pci 0000:00:1f.2: reg 10: [io  0x8000-0x8007]
[    1.013338] pci 0000:00:1f.2: reg 14: [io  0x7c00-0x7c03]
[    1.013345] pci 0000:00:1f.2: reg 18: [io  0x7880-0x7887]
[    1.013352] pci 0000:00:1f.2: reg 1c: [io  0x7800-0x7803]
[    1.013362] pci 0000:00:1f.2: reg 20: [io  0x7480-0x748f]
[    1.013369] pci 0000:00:1f.2: reg 24: [io  0x7400-0x740f]
[    1.013412] pci 0000:00:1f.3: [8086:3a30] type 0 class 0x000c05
[    1.013426] pci 0000:00:1f.3: reg 10: [mem 0xfbed6000-0xfbed60ff 64bit]
[    1.013446] pci 0000:00:1f.3: reg 20: [io  0x0400-0x041f]
[    1.013478] pci 0000:00:1f.5: [8086:3a26] type 0 class 0x000101
[    1.013492] pci 0000:00:1f.5: reg 10: [io  0x7000-0x7007]
[    1.013499] pci 0000:00:1f.5: reg 14: [io  0x6c00-0x6c03]
[    1.013506] pci 0000:00:1f.5: reg 18: [io  0x6880-0x6887]
[    1.013513] pci 0000:00:1f.5: reg 1c: [io  0x6800-0x6803]
[    1.013520] pci 0000:00:1f.5: reg 20: [io  0x6480-0x648f]
[    1.013527] pci 0000:00:1f.5: reg 24: [io  0x6400-0x640f]
[    1.013620] pci 0000:01:00.0: [8086:10d3] type 0 class 0x000200
[    1.013639] pci 0000:01:00.0: reg 10: [mem 0xfad20000-0xfad3ffff]
[    1.013653] pci 0000:01:00.0: reg 14: [mem 0xfad80000-0xfadfffff]
[    1.013667] pci 0000:01:00.0: reg 18: [io  0x9c00-0x9c1f]
[    1.013681] pci 0000:01:00.0: reg 1c: [mem 0xfad1c000-0xfad1ffff]
[    1.013721] pci 0000:01:00.0: reg 30: [mem 0xfad40000-0xfad7ffff pref]
[    1.013797] pci 0000:01:00.0: PME# supported from D0 D3hot D3cold
[    1.013802] pci 0000:01:00.0: PME# disabled
[    1.021348] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    1.021353] pci 0000:00:01.0:   bridge window [io  0x9000-0x9fff]
[    1.021355] pci 0000:00:01.0:   bridge window [mem 0xfad00000-0xfadfffff]
[    1.021360] pci 0000:00:01.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    1.021393] pci 0000:00:03.0: PCI bridge to [bus 02-02]
[    1.021398] pci 0000:00:03.0:   bridge window [io  0xf000-0x0000] (disabled)
[    1.021401] pci 0000:00:03.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    1.021405] pci 0000:00:03.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    1.021459] pci 0000:03:00.0: [8086:10d3] type 0 class 0x000200
[    1.021479] pci 0000:03:00.0: reg 10: [mem 0xfae20000-0xfae3ffff]
[    1.021494] pci 0000:03:00.0: reg 14: [mem 0xfae80000-0xfaefffff]
[    1.021508] pci 0000:03:00.0: reg 18: [io  0xac00-0xac1f]
[    1.021522] pci 0000:03:00.0: reg 1c: [mem 0xfae1c000-0xfae1ffff]
[    1.021562] pci 0000:03:00.0: reg 30: [mem 0xfae40000-0xfae7ffff pref]
[    1.021639] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
[    1.021644] pci 0000:03:00.0: PME# disabled
[    1.029322] pci 0000:00:05.0: PCI bridge to [bus 03-03]
[    1.029327] pci 0000:00:05.0:   bridge window [io  0xa000-0xafff]
[    1.029329] pci 0000:00:05.0:   bridge window [mem 0xfae00000-0xfaefffff]
[    1.029334] pci 0000:00:05.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    1.029389] pci 0000:04:00.0: [8086:10d3] type 0 class 0x000200
[    1.029409] pci 0000:04:00.0: reg 10: [mem 0xfb820000-0xfb83ffff]
[    1.029423] pci 0000:04:00.0: reg 14: [mem 0xfb880000-0xfb8fffff]
[    1.029438] pci 0000:04:00.0: reg 18: [io  0xbc00-0xbc1f]
[    1.029452] pci 0000:04:00.0: reg 1c: [mem 0xfb81c000-0xfb81ffff]
[    1.029492] pci 0000:04:00.0: reg 30: [mem 0xfb840000-0xfb87ffff pref]
[    1.029570] pci 0000:04:00.0: PME# supported from D0 D3hot D3cold
[    1.029575] pci 0000:04:00.0: PME# disabled
[    1.037296] pci 0000:00:07.0: PCI bridge to [bus 04-04]
[    1.037301] pci 0000:00:07.0:   bridge window [io  0xb000-0xbfff]
[    1.037303] pci 0000:00:07.0:   bridge window [mem 0xfb800000-0xfb8fffff]
[    1.037307] pci 0000:00:07.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    1.037351] pci 0000:05:00.0: [1000:0058] type 0 class 0x000100
[    1.037361] pci 0000:05:00.0: reg 10: [io  0xc000-0xc0ff]
[    1.037372] pci 0000:05:00.0: reg 14: [mem 0xfb9ec000-0xfb9effff 64bit]
[    1.037383] pci 0000:05:00.0: reg 1c: [mem 0xfb9f0000-0xfb9fffff 64bit]
[    1.037397] pci 0000:05:00.0: reg 30: [mem 0xfba00000-0xfbbfffff pref]
[    1.037435] pci 0000:05:00.0: supports D1 D2
[    1.037447] pci 0000:05:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    1.037456] pci 0000:00:09.0: PCI bridge to [bus 05-05]
[    1.037459] pci 0000:00:09.0:   bridge window [io  0xc000-0xcfff]
[    1.037462] pci 0000:00:09.0:   bridge window [mem 0xfb900000-0xfbbfffff]
[    1.037466] pci 0000:00:09.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    1.037528] pci 0000:06:00.0: [8086:10d3] type 0 class 0x000200
[    1.037551] pci 0000:06:00.0: reg 10: [mem 0xfbce0000-0xfbcfffff]
[    1.037582] pci 0000:06:00.0: reg 18: [io  0xdc00-0xdc1f]
[    1.037599] pci 0000:06:00.0: reg 1c: [mem 0xfbcdc000-0xfbcdffff]
[    1.037734] pci 0000:06:00.0: PME# supported from D0 D3hot D3cold
[    1.037740] pci 0000:06:00.0: PME# disabled
[    1.045271] pci 0000:00:1c.0: PCI bridge to [bus 06-06]
[    1.045276] pci 0000:00:1c.0:   bridge window [io  0xd000-0xdfff]
[    1.045279] pci 0000:00:1c.0:   bridge window [mem 0xfbc00000-0xfbcfffff]
[    1.045283] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    1.045345] pci 0000:07:00.0: [8086:10d3] type 0 class 0x000200
[    1.045368] pci 0000:07:00.0: reg 10: [mem 0xfbde0000-0xfbdfffff]
[    1.045400] pci 0000:07:00.0: reg 18: [io  0xec00-0xec1f]
[    1.045416] pci 0000:07:00.0: reg 1c: [mem 0xfbddc000-0xfbddffff]
[    1.045552] pci 0000:07:00.0: PME# supported from D0 D3hot D3cold
[    1.045557] pci 0000:07:00.0: PME# disabled
[    1.053247] pci 0000:00:1c.1: PCI bridge to [bus 07-07]
[    1.053252] pci 0000:00:1c.1:   bridge window [io  0xe000-0xefff]
[    1.053255] pci 0000:00:1c.1:   bridge window [mem 0xfbd00000-0xfbdfffff]
[    1.053260] pci 0000:00:1c.1:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    1.053294] pci 0000:08:04.0: [102b:0532] type 0 class 0x000300
[    1.053310] pci 0000:08:04.0: reg 10: [mem 0xf9000000-0xf9ffffff pref]
[    1.053319] pci 0000:08:04.0: reg 14: [mem 0xfaffc000-0xfaffffff]
[    1.053328] pci 0000:08:04.0: reg 18: [mem 0xfb000000-0xfb7fffff]
[    1.053420] pci 0000:00:1e.0: PCI bridge to [bus 08-08] (subtractive decode)
[    1.053424] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
[    1.053428] pci 0000:00:1e.0:   bridge window [mem 0xfaf00000-0xfb7fffff]
[    1.053432] pci 0000:00:1e.0:   bridge window [mem 0xf9000000-0xf9ffffff 64bit pref]
[    1.053434] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    1.053436] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    1.053437] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    1.053439] pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    1.053441] pci 0000:00:1e.0:   bridge window [mem 0xf0000000-0xfed8ffff] (subtractive decode)
[    1.053471] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    1.053626] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    1.053689] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    1.053707] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P5._PRT]
[    1.053731] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.NPE1._PRT]
[    1.053750] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.NPE3._PRT]
[    1.053770] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.NPE5._PRT]
[    1.053791] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.NPE7._PRT]
[    1.053810] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.NPE9._PRT]
[    1.053829]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    1.053832]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    1.053835] ACPI _OSC control for PCIe not granted, disabling ASPM
[    1.063720] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 10 *11 12 14 15)
[    1.063753] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 6 7 *10 11 12 14 15)
[    1.063784] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 11 12 14 *15)
[    1.063814] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 11 12 *14 15)
[    1.063847] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12 14 15) *0, disabled.
[    1.063879] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 *7 10 11 12 14 15)
[    1.063909] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 6 7 10 11 12 14 15) *0, disabled.
[    1.063941] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 6 7 *10 11 12 14 15)
[    1.064018] vgaarb: device added: PCI:0000:08:04.0,decodes=io+mem,owns=io+mem,locks=none
[    1.064022] vgaarb: loaded
[    1.064023] vgaarb: bridge control possible 0000:08:04.0
[    1.064137] SCSI subsystem initialized
[    1.064182] libata version 3.00 loaded.
[    1.064209] usbcore: registered new interface driver usbfs
[    1.064218] usbcore: registered new interface driver hub
[    1.064236] usbcore: registered new device driver usb
[    1.064295] PCI: Using ACPI for IRQ routing
[    1.070285] PCI: Discovered peer bus ff
[    1.070309] pci 0000:ff:00.0: [8086:2c41] type 0 class 0x000600
[    1.070324] pci 0000:ff:00.1: [8086:2c01] type 0 class 0x000600
[    1.070339] pci 0000:ff:02.0: [8086:2c10] type 0 class 0x000600
[    1.070352] pci 0000:ff:02.1: [8086:2c11] type 0 class 0x000600
[    1.070366] pci 0000:ff:03.0: [8086:2c18] type 0 class 0x000600
[    1.070379] pci 0000:ff:03.1: [8086:2c19] type 0 class 0x000600
[    1.070393] pci 0000:ff:03.4: [8086:2c1c] type 0 class 0x000600
[    1.070406] pci 0000:ff:04.0: [8086:2c20] type 0 class 0x000600
[    1.070419] pci 0000:ff:04.1: [8086:2c21] type 0 class 0x000600
[    1.070431] pci 0000:ff:04.2: [8086:2c22] type 0 class 0x000600
[    1.070444] pci 0000:ff:04.3: [8086:2c23] type 0 class 0x000600
[    1.070458] pci 0000:ff:05.0: [8086:2c28] type 0 class 0x000600
[    1.070470] pci 0000:ff:05.1: [8086:2c29] type 0 class 0x000600
[    1.070483] pci 0000:ff:05.2: [8086:2c2a] type 0 class 0x000600
[    1.070497] pci 0000:ff:05.3: [8086:2c2b] type 0 class 0x000600
[    1.070511] pci 0000:ff:06.0: [8086:2c30] type 0 class 0x000600
[    1.070523] pci 0000:ff:06.1: [8086:2c31] type 0 class 0x000600
[    1.070536] pci 0000:ff:06.2: [8086:2c32] type 0 class 0x000600
[    1.070548] pci 0000:ff:06.3: [8086:2c33] type 0 class 0x000600
[    1.070821] PCI: pci_cache_line_size set to 64 bytes
[    1.070949] reserve RAM buffer: 0000000000099800 - 000000000009ffff 
[    1.070951] reserve RAM buffer: 00000000df780000 - 00000000dfffffff 
[    1.071012] NetLabel: Initializing
[    1.071015] NetLabel:  domain hash size = 128
[    1.071016] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.071027] NetLabel:  unlabeled traffic allowed by default
[    1.071053] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    1.071059] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    1.071063] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    1.089243] Switching to clocksource hpet
[    1.093114] Switched to NOHz mode on CPU #0
[    1.093136] AppArmor: AppArmor Filesystem Enabled
[    1.093161] Switched to NOHz mode on CPU #3
[    1.093168] pnp: PnP ACPI init
[    1.093170] Switched to NOHz mode on CPU #4
[    1.093172] Switched to NOHz mode on CPU #6
[    1.093179] ACPI: bus type pnp registered
[    1.093197] Switched to NOHz mode on CPU #7
[    1.093202] Switched to NOHz mode on CPU #5
[    1.093211] Switched to NOHz mode on CPU #1
[    1.093235] Switched to NOHz mode on CPU #2
[    1.093274] pnp 00:00: [bus 00-ff]
[    1.093276] pnp 00:00: [io  0x0cf8-0x0cff]
[    1.093277] pnp 00:00: [io  0x0000-0x0cf7 window]
[    1.093278] pnp 00:00: [io  0x0d00-0xffff window]
[    1.093280] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    1.093281] pnp 00:00: [mem 0x000d0000-0x000dffff window]
[    1.093282] pnp 00:00: [mem 0xe0000000-0xdfffffff window disabled]
[    1.093284] pnp 00:00: [mem 0xf0000000-0xfed8ffff window]
[    1.093330] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    1.093337] pnp 00:01: [mem 0xfbf00000-0xfbffffff]
[    1.093338] pnp 00:01: [mem 0xfc000000-0xfcffffff]
[    1.093339] pnp 00:01: [mem 0xfd000000-0xfdffffff]
[    1.093340] pnp 00:01: [mem 0xfe000000-0xfebfffff]
[    1.093341] pnp 00:01: [mem 0xfec8a000-0xfec8afff]
[    1.093342] pnp 00:01: [mem 0xfed10000-0xfed10fff]
[    1.093391] system 00:01: [mem 0xfbf00000-0xfbffffff] has been reserved
[    1.093395] system 00:01: [mem 0xfc000000-0xfcffffff] has been reserved
[    1.093398] system 00:01: [mem 0xfd000000-0xfdffffff] has been reserved
[    1.093401] system 00:01: [mem 0xfe000000-0xfebfffff] has been reserved
[    1.093404] system 00:01: [mem 0xfec8a000-0xfec8afff] has been reserved
[    1.093407] system 00:01: [mem 0xfed10000-0xfed10fff] has been reserved
[    1.093410] system 00:01: Plug and Play ACPI device, IDs PNP0c01 (active)
[    1.093433] pnp 00:02: [dma 4]
[    1.093434] pnp 00:02: [io  0x0000-0x000f]
[    1.093435] pnp 00:02: [io  0x0081-0x0083]
[    1.093436] pnp 00:02: [io  0x0087]
[    1.093437] pnp 00:02: [io  0x0089-0x008b]
[    1.093438] pnp 00:02: [io  0x008f]
[    1.093439] pnp 00:02: [io  0x00c0-0x00df]
[    1.093454] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    1.093460] pnp 00:03: [io  0x0070-0x0071]
[    1.093468] pnp 00:03: [irq 8]
[    1.093482] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    1.093487] pnp 00:04: [io  0x0061]
[    1.093502] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
[    1.093507] pnp 00:05: [io  0x00f0-0x00ff]
[    1.093512] pnp 00:05: [irq 13]
[    1.093525] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
[    1.093679] pnp 00:06: [io  0x03f8-0x03ff]
[    1.093684] pnp 00:06: [irq 4]
[    1.093685] pnp 00:06: [dma 0 disabled]
[    1.093724] pnp 00:06: Plug and Play ACPI device, IDs PNP0501 (active)
[    1.093872] pnp 00:07: [io  0x02f8-0x02ff]
[    1.093877] pnp 00:07: [irq 3]
[    1.093878] pnp 00:07: [dma 0 disabled]
[    1.093928] pnp 00:07: Plug and Play ACPI device, IDs PNP0501 (active)
[    1.094104] pnp 00:08: [io  0x03f0-0x03f5]
[    1.094105] pnp 00:08: [io  0x03f7]
[    1.094109] pnp 00:08: [irq 6]
[    1.094111] pnp 00:08: [dma 2]
[    1.094144] pnp 00:08: Plug and Play ACPI device, IDs PNP0700 (active)
[    1.094336] pnp 00:09: [io  0x03e8-0x03ef]
[    1.094341] pnp 00:09: [irq 5]
[    1.094342] pnp 00:09: [dma 0 disabled]
[    1.094378] pnp 00:09: Plug and Play ACPI device, IDs PNP0501 (active)
[    1.094413] pnp 00:0a: [io  0x164e-0x164f]
[    1.094415] pnp 00:0a: [io  0x0000-0xffffffffffffffff disabled]
[    1.094451] system 00:0a: [io  0x164e-0x164f] has been reserved
[    1.094455] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.094529] pnp 00:0b: [io  0x0000-0xffffffffffffffff disabled]
[    1.094530] pnp 00:0b: [io  0x0a00-0x0a0f]
[    1.094531] pnp 00:0b: [io  0x0ca0-0x0caf]
[    1.094568] system 00:0b: [io  0x0a00-0x0a0f] has been reserved
[    1.094572] system 00:0b: [io  0x0ca0-0x0caf] has been reserved
[    1.094575] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.094645] pnp 00:0c: [io  0x0010-0x001f]
[    1.094646] pnp 00:0c: [io  0x0022-0x003f]
[    1.094648] pnp 00:0c: [io  0x0044-0x005f]
[    1.094649] pnp 00:0c: [io  0x0062-0x0063]
[    1.094650] pnp 00:0c: [io  0x0065-0x006f]
[    1.094651] pnp 00:0c: [io  0x0072-0x007f]
[    1.094652] pnp 00:0c: [io  0x0080]
[    1.094653] pnp 00:0c: [io  0x0084-0x0086]
[    1.094654] pnp 00:0c: [io  0x0088]
[    1.094655] pnp 00:0c: [io  0x008c-0x008e]
[    1.094656] pnp 00:0c: [io  0x0090-0x009f]
[    1.094657] pnp 00:0c: [io  0x00a2-0x00bf]
[    1.094658] pnp 00:0c: [io  0x00e0-0x00ef]
[    1.094659] pnp 00:0c: [io  0x04d0-0x04d1]
[    1.094660] pnp 00:0c: [io  0x0800-0x087f]
[    1.094663] pnp 00:0c: [io  0x0000-0xffffffffffffffff disabled]
[    1.094665] pnp 00:0c: [io  0x0500-0x057f]
[    1.094666] pnp 00:0c: [mem 0xfed1c000-0xfed1ffff]
[    1.094667] pnp 00:0c: [mem 0xfed20000-0xfed3ffff]
[    1.094668] pnp 00:0c: [mem 0xfed40000-0xfed8ffff]
[    1.094726] system 00:0c: [io  0x04d0-0x04d1] has been reserved
[    1.094729] system 00:0c: [io  0x0800-0x087f] has been reserved
[    1.094732] system 00:0c: [io  0x0500-0x057f] has been reserved
[    1.094735] system 00:0c: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    1.094738] system 00:0c: [mem 0xfed20000-0xfed3ffff] has been reserved
[    1.094741] system 00:0c: [mem 0xfed40000-0xfed8ffff] has been reserved
[    1.094745] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.094780] pnp 00:0d: [mem 0xfed00000-0xfed003ff]
[    1.094797] pnp 00:0d: Plug and Play ACPI device, IDs PNP0103 (active)
[    1.094843] pnp 00:0e: [io  0x0060]
[    1.094844] pnp 00:0e: [io  0x0064]
[    1.094845] pnp 00:0e: [mem 0xfec00000-0xfec00fff]
[    1.094846] pnp 00:0e: [mem 0xfee00000-0xfee00fff]
[    1.094886] system 00:0e: [mem 0xfec00000-0xfec00fff] could not be reserved
[    1.094890] system 00:0e: [mem 0xfee00000-0xfee00fff] has been reserved
[    1.094893] system 00:0e: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.094922] pnp 00:0f: [mem 0xe0000000-0xefffffff]
[    1.094959] system 00:0f: [mem 0xe0000000-0xefffffff] has been reserved
[    1.094963] system 00:0f: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.095071] pnp 00:10: [mem 0x00000000-0x0009ffff]
[    1.095072] pnp 00:10: [mem 0x000c0000-0x000cffff]
[    1.095073] pnp 00:10: [mem 0x000e0000-0x000fffff]
[    1.095074] pnp 00:10: [mem 0x00100000-0xdfffffff]
[    1.095076] pnp 00:10: [mem 0xfed90000-0xffffffff]
[    1.095120] system 00:10: [mem 0x00000000-0x0009ffff] could not be reserved
[    1.095124] system 00:10: [mem 0x000c0000-0x000cffff] could not be reserved
[    1.095127] system 00:10: [mem 0x000e0000-0x000fffff] could not be reserved
[    1.095130] system 00:10: [mem 0x00100000-0xdfffffff] could not be reserved
[    1.095133] system 00:10: [mem 0xfed90000-0xffffffff] could not be reserved
[    1.095136] system 00:10: Plug and Play ACPI device, IDs PNP0c01 (active)
[    1.095218] pnp: PnP ACPI: found 17 devices
[    1.095220] ACPI: ACPI bus type pnp unregistered
[    1.100566] PCI: max bus depth: 1 pci_try_num: 2
[    1.100617] pci 0000:00:1c.1: BAR 15: assigned [mem 0xf0000000-0xf01fffff 64bit pref]
[    1.100621] pci 0000:00:1c.0: BAR 15: assigned [mem 0xf0200000-0xf03fffff 64bit pref]
[    1.100625] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    1.100628] pci 0000:00:01.0:   bridge window [io  0x9000-0x9fff]
[    1.100633] pci 0000:00:01.0:   bridge window [mem 0xfad00000-0xfadfffff]
[    1.100637] pci 0000:00:01.0:   bridge window [mem pref disabled]
[    1.100642] pci 0000:00:03.0: PCI bridge to [bus 02-02]
[    1.100644] pci 0000:00:03.0:   bridge window [io  disabled]
[    1.100648] pci 0000:00:03.0:   bridge window [mem disabled]
[    1.100652] pci 0000:00:03.0:   bridge window [mem pref disabled]
[    1.100657] pci 0000:00:05.0: PCI bridge to [bus 03-03]
[    1.100660] pci 0000:00:05.0:   bridge window [io  0xa000-0xafff]
[    1.100665] pci 0000:00:05.0:   bridge window [mem 0xfae00000-0xfaefffff]
[    1.100668] pci 0000:00:05.0:   bridge window [mem pref disabled]
[    1.100674] pci 0000:00:07.0: PCI bridge to [bus 04-04]
[    1.100676] pci 0000:00:07.0:   bridge window [io  0xb000-0xbfff]
[    1.100681] pci 0000:00:07.0:   bridge window [mem 0xfb800000-0xfb8fffff]
[    1.100685] pci 0000:00:07.0:   bridge window [mem pref disabled]
[    1.100690] pci 0000:00:09.0: PCI bridge to [bus 05-05]
[    1.100693] pci 0000:00:09.0:   bridge window [io  0xc000-0xcfff]
[    1.100697] pci 0000:00:09.0:   bridge window [mem 0xfb900000-0xfbbfffff]
[    1.100701] pci 0000:00:09.0:   bridge window [mem pref disabled]
[    1.100706] pci 0000:00:1c.0: PCI bridge to [bus 06-06]
[    1.100709] pci 0000:00:1c.0:   bridge window [io  0xd000-0xdfff]
[    1.100714] pci 0000:00:1c.0:   bridge window [mem 0xfbc00000-0xfbcfffff]
[    1.100718] pci 0000:00:1c.0:   bridge window [mem 0xf0200000-0xf03fffff 64bit pref]
[    1.100725] pci 0000:00:1c.1: PCI bridge to [bus 07-07]
[    1.100728] pci 0000:00:1c.1:   bridge window [io  0xe000-0xefff]
[    1.100733] pci 0000:00:1c.1:   bridge window [mem 0xfbd00000-0xfbdfffff]
[    1.100737] pci 0000:00:1c.1:   bridge window [mem 0xf0000000-0xf01fffff 64bit pref]
[    1.100744] pci 0000:00:1e.0: PCI bridge to [bus 08-08]
[    1.100746] pci 0000:00:1e.0:   bridge window [io  disabled]
[    1.100751] pci 0000:00:1e.0:   bridge window [mem 0xfaf00000-0xfb7fffff]
[    1.100755] pci 0000:00:1e.0:   bridge window [mem 0xf9000000-0xf9ffffff 64bit pref]
[    1.100767] pci 0000:00:01.0: setting latency timer to 64
[    1.100772] pci 0000:00:03.0: setting latency timer to 64
[    1.100777] pci 0000:00:05.0: setting latency timer to 64
[    1.100782] pci 0000:00:07.0: setting latency timer to 64
[    1.100787] pci 0000:00:09.0: setting latency timer to 64
[    1.100798] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.100802] pci 0000:00:1c.0: setting latency timer to 64
[    1.100810] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    1.100814] pci 0000:00:1c.1: setting latency timer to 64
[    1.100819] pci 0000:00:1e.0: setting latency timer to 64
[    1.100822] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    1.100823] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    1.100825] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    1.100826] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    1.100827] pci_bus 0000:00: resource 8 [mem 0xf0000000-0xfed8ffff]
[    1.100829] pci_bus 0000:01: resource 0 [io  0x9000-0x9fff]
[    1.100830] pci_bus 0000:01: resource 1 [mem 0xfad00000-0xfadfffff]
[    1.100832] pci_bus 0000:03: resource 0 [io  0xa000-0xafff]
[    1.100833] pci_bus 0000:03: resource 1 [mem 0xfae00000-0xfaefffff]
[    1.100834] pci_bus 0000:04: resource 0 [io  0xb000-0xbfff]
[    1.100836] pci_bus 0000:04: resource 1 [mem 0xfb800000-0xfb8fffff]
[    1.100837] pci_bus 0000:05: resource 0 [io  0xc000-0xcfff]
[    1.100838] pci_bus 0000:05: resource 1 [mem 0xfb900000-0xfbbfffff]
[    1.100840] pci_bus 0000:06: resource 0 [io  0xd000-0xdfff]
[    1.100841] pci_bus 0000:06: resource 1 [mem 0xfbc00000-0xfbcfffff]
[    1.100843] pci_bus 0000:06: resource 2 [mem 0xf0200000-0xf03fffff 64bit pref]
[    1.100844] pci_bus 0000:07: resource 0 [io  0xe000-0xefff]
[    1.100846] pci_bus 0000:07: resource 1 [mem 0xfbd00000-0xfbdfffff]
[    1.100847] pci_bus 0000:07: resource 2 [mem 0xf0000000-0xf01fffff 64bit pref]
[    1.100849] pci_bus 0000:08: resource 1 [mem 0xfaf00000-0xfb7fffff]
[    1.100850] pci_bus 0000:08: resource 2 [mem 0xf9000000-0xf9ffffff 64bit pref]
[    1.100852] pci_bus 0000:08: resource 4 [io  0x0000-0x0cf7]
[    1.100853] pci_bus 0000:08: resource 5 [io  0x0d00-0xffff]
[    1.100854] pci_bus 0000:08: resource 6 [mem 0x000a0000-0x000bffff]
[    1.100856] pci_bus 0000:08: resource 7 [mem 0x000d0000-0x000dffff]
[    1.100857] pci_bus 0000:08: resource 8 [mem 0xf0000000-0xfed8ffff]
[    1.100858] pci_bus 0000:ff: resource 0 [io  0x0000-0xffff]
[    1.100860] pci_bus 0000:ff: resource 1 [mem 0x00000000-0xfffffffff]
[    1.100888] NET: Registered protocol family 2
[    1.101176] IP route cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    1.102218] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    1.103347] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    1.103484] TCP: Hash tables configured (established 524288 bind 65536)
[    1.103487] TCP reno registered
[    1.103523] UDP hash table entries: 16384 (order: 7, 524288 bytes)
[    1.103628] UDP-Lite hash table entries: 16384 (order: 7, 524288 bytes)
[    1.103796] NET: Registered protocol family 1
[    1.103989] pci 0000:08:04.0: Boot video device
[    1.104009] PCI: CLS 256 bytes, default 64
[    1.104011] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    1.104014] Placing 64MB software IO TLB between ffff8800db766000 - ffff8800df766000
[    1.104017] software IO TLB at phys 0xdb766000 - 0xdf766000
[    1.104440] audit: initializing netlink socket (disabled)
[    1.104447] type=2000 audit(1333091730.868:1): initialized
[    1.150079] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.210135] Freeing initrd memory: 13320k freed
[    1.210275] VFS: Disk quotas dquot_6.5.2
[    1.210318] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.210752] fuse init (API version 7.16)
[    1.210812] msgmni has been set to 32768
[    1.211106] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    1.211132] io scheduler noop registered
[    1.211135] io scheduler deadline registered (default)
[    1.211167] io scheduler cfq registered
[    1.211437] pcieport 0000:00:1c.0: setting latency timer to 64
[    1.211479] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    1.211528] pcieport 0000:00:1c.1: setting latency timer to 64
[    1.211562] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
[    1.211621] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.211637] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.211668] intel_idle: MWAIT substates: 0x1120
[    1.211678] intel_idle: v0.4 model 0x1A
[    1.211679] intel_idle: lapic_timer_reliable_states 0x2
[    1.211781] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    1.211787] ACPI: Power Button [PWRB]
[    1.211815] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    1.211819] ACPI: Power Button [PWRF]
[    1.211837] ACPI: acpi_idle yielding to intel_idle
[    1.213105] APEI: Can not request iomem region <00000000df7b4f0a-00000000df7b4f0c> for GARs.
[    1.213165] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.233475] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.300984] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.360797] serial8250: ttyS2 at I/O 0x3e8 (irq = 4) is a 16550A
[    1.452681] 00:06: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.473034] 00:07: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.493387] 00:09: ttyS2 at I/O 0x3e8 (irq = 5) is a 16550A
[    1.496214] Linux agpgart interface v0.103
[    1.496899] brd: module loaded
[    1.497202] loop: module loaded
[    1.497304] ata_piix 0000:00:1f.2: version 2.13
[    1.497317] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.497323] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    1.497353] ata_piix 0000:00:1f.2: setting latency timer to 64
[    1.497516] scsi0 : ata_piix
[    1.497571] scsi1 : ata_piix
[    1.498089] ata1: SATA max UDMA/133 cmd 0x8000 ctl 0x7c00 bmdma 0x7480 irq 19
[    1.498095] ata2: SATA max UDMA/133 cmd 0x7880 ctl 0x7800 bmdma 0x7488 irq 19
[    1.498109] ata_piix 0000:00:1f.5: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.498113] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
[    1.498140] ata_piix 0000:00:1f.5: setting latency timer to 64
[    1.498253] scsi2 : ata_piix
[    1.498297] scsi3 : ata_piix
[    1.498792] ata3: SATA max UDMA/133 cmd 0x7000 ctl 0x6c00 bmdma 0x6480 irq 19
[    1.498797] ata4: SATA max UDMA/133 cmd 0x6880 ctl 0x6800 bmdma 0x6488 irq 19
[    1.498978] Fixed MDIO Bus: probed
[    1.498992] PPP generic driver version 2.4.2
[    1.499015] tun: Universal TUN/TAP device driver, 1.6
[    1.499018] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.499065] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.499082] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.499102] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    1.499104] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    1.499128] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    1.499150] ehci_hcd 0000:00:1a.7: debug port 1
[    1.503031] ehci_hcd 0000:00:1a.7: cache line size of 256 is not supported
[    1.503043] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfbeda000
[    1.515960] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    1.516068] hub 1-0:1.0: USB hub found
[    1.516072] hub 1-0:1.0: 6 ports detected
[    1.516133] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.516144] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.516147] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.516169] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    1.516189] ehci_hcd 0000:00:1d.7: debug port 1
[    1.520067] ehci_hcd 0000:00:1d.7: cache line size of 256 is not supported
[    1.520077] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfbed8000
[    1.535897] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.535997] hub 2-0:1.0: USB hub found
[    1.536001] hub 2-0:1.0: 6 ports detected
[    1.536054] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.536064] uhci_hcd: USB Universal Host Controller Interface driver
[    1.536080] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.536087] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.536089] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    1.536113] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    1.536145] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00008c00
[    1.536215] hub 3-0:1.0: USB hub found
[    1.536219] hub 3-0:1.0: 2 ports detected
[    1.536269] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    1.536275] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    1.536277] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    1.536301] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    1.536332] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00008880
[    1.536403] hub 4-0:1.0: USB hub found
[    1.536407] hub 4-0:1.0: 2 ports detected
[    1.536451] uhci_hcd 0000:00:1a.2: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    1.536457] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    1.536460] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    1.536482] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    1.536505] uhci_hcd 0000:00:1a.2: irq 19, io base 0x00008800
[    1.536577] hub 5-0:1.0: USB hub found
[    1.536581] hub 5-0:1.0: 2 ports detected
[    1.536624] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.536630] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.536632] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.536654] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    1.536677] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00008480
[    1.536745] hub 6-0:1.0: USB hub found
[    1.536748] hub 6-0:1.0: 2 ports detected
[    1.536793] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.536799] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.536801] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.536824] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    1.536847] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00008400
[    1.536916] hub 7-0:1.0: USB hub found
[    1.536920] hub 7-0:1.0: 2 ports detected
[    1.536964] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.536970] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.536972] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.536997] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    1.537020] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00008080
[    1.537091] hub 8-0:1.0: USB hub found
[    1.537094] hub 8-0:1.0: 2 ports detected
[    1.537165] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    1.539834] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.539840] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.539894] mousedev: PS/2 mouse device common for all mice
[    1.539955] rtc_cmos 00:03: RTC can wake from S4
[    1.540029] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.540054] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.540122] device-mapper: uevent: version 1.0.3
[    1.540168] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: dm-devel@redhat.com
[    1.540279] cpuidle: using governor ladder
[    1.540460] cpuidle: using governor menu
[    1.540462] EFI Variables Facility v0.08 2004-May-17
[    1.540617] TCP cubic registered
[    1.540695] NET: Registered protocol family 10
[    1.541026] NET: Registered protocol family 17
[    1.541038] Registering the dns_resolver key type
[    1.541096] PM: Hibernation image not present or could not be loaded.
[    1.541103] registered taskstats version 1
[    1.577379]   Magic number: 4:695:269
[    1.577681] rtc_cmos 00:03: setting system clock to 2012-03-30 07:15:32 UTC (1333091732)
[    1.579794] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.579797] EDD information not available.
[    1.825967] ata3: SATA link down (SStatus 0 SControl 300)
[    1.836748] ata4: SATA link down (SStatus 0 SControl 300)
[    2.098340] Refined TSC clocksource calibration: 3199.999 MHz.
[    2.098349] Switching to clocksource tsc
[    2.130163] usb 3-2: new low speed USB device number 2 using uhci_hcd
[    2.145136] ata2.00: SATA link down (SStatus 0 SControl 300)
[    2.145151] ata2.01: SATA link down (SStatus 0 SControl 300)
[    2.155952] ata1.00: SATA link down (SStatus 0 SControl 300)
[    2.155968] ata1.01: SATA link down (SStatus 0 SControl 300)
[    2.157751] Freeing unused kernel memory: 904k freed
[    2.157852] Write protecting the kernel read-only data: 12288k
[    2.162717] Freeing unused kernel memory: 1952k freed
[    2.166096] Freeing unused kernel memory: 1360k freed
[    2.181181] udevd[112]: starting version 173
[    2.195836] Floppy drive(s): fd0 is 1.44M
[    2.198704] e1000e: Intel(R) PRO/1000 Network Driver - 1.3.10-k2
[    2.198710] e1000e: Copyright(c) 1999 - 2011 Intel Corporation.
[    2.198737] e1000e 0000:01:00.0: Disabling ASPM L0s 
[    2.198751] e1000e 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.198771] e1000e 0000:01:00.0: setting latency timer to 64
[    2.198948] e1000e 0000:01:00.0: irq 42 for MSI/MSI-X
[    2.198953] e1000e 0000:01:00.0: irq 43 for MSI/MSI-X
[    2.198961] e1000e 0000:01:00.0: irq 44 for MSI/MSI-X
[    2.199279] Fusion MPT base driver 3.04.19
[    2.199284] Copyright (c) 1999-2008 LSI Corporation
[    2.200050] Fusion MPT SAS Host driver 3.04.19
[    2.200076] mptsas 0000:05:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.200282] mptbase: ioc0: Initiating bringup
[    2.213486] FDC 0 is a post-1991 82077
[    2.304891] e1000e 0000:01:00.0: eth0: (PCI Express:2.5GT/s:Width x1) 68:05:ca:01:99:22
[    2.304895] e1000e 0000:01:00.0: eth0: Intel(R) PRO/1000 Network Connection
[    2.304907] e1000e 0000:01:00.0: eth0: MAC: 3, PHY: 8, PBA No: E46981-007
[    2.304914] e1000e 0000:03:00.0: Disabling ASPM L0s 
[    2.304926] e1000e 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.304943] e1000e 0000:03:00.0: setting latency timer to 64
[    2.305213] e1000e 0000:03:00.0: irq 45 for MSI/MSI-X
[    2.305217] e1000e 0000:03:00.0: irq 46 for MSI/MSI-X
[    2.305220] e1000e 0000:03:00.0: irq 47 for MSI/MSI-X
[    2.323927] input: Dell Dell USB Keyboard as /devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2:1.0/input/input2
[    2.324064] generic-usb 0003:413C:2003.0001: input,hidraw0: USB HID v1.10 Keyboard [Dell Dell USB Keyboard] on usb-0000:00:1a.0-2/input0
[    2.324075] usbcore: registered new interface driver usbhid
[    2.324077] usbhid: USB HID core driver
[    2.414410] e1000e 0000:03:00.0: eth1: (PCI Express:2.5GT/s:Width x1) 68:05:ca:01:9f:2b
[    2.414414] e1000e 0000:03:00.0: eth1: Intel(R) PRO/1000 Network Connection
[    2.414427] e1000e 0000:03:00.0: eth1: MAC: 3, PHY: 8, PBA No: E46981-007
[    2.414432] e1000e 0000:04:00.0: Disabling ASPM L0s 
[    2.414441] e1000e 0000:04:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.414455] e1000e 0000:04:00.0: setting latency timer to 64
[    2.414618] e1000e 0000:04:00.0: irq 48 for MSI/MSI-X
[    2.414622] e1000e 0000:04:00.0: irq 49 for MSI/MSI-X
[    2.414625] e1000e 0000:04:00.0: irq 50 for MSI/MSI-X
[    2.521996] e1000e 0000:04:00.0: eth2: (PCI Express:2.5GT/s:Width x1) 68:05:ca:01:99:4a
[    2.522000] e1000e 0000:04:00.0: eth2: Intel(R) PRO/1000 Network Connection
[    2.522012] e1000e 0000:04:00.0: eth2: MAC: 3, PHY: 8, PBA No: E46981-007
[    2.522019] e1000e 0000:06:00.0: Disabling ASPM L0s 
[    2.522028] e1000e 0000:06:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.522043] e1000e 0000:06:00.0: setting latency timer to 64
[    2.522209] e1000e 0000:06:00.0: irq 51 for MSI/MSI-X
[    2.522213] e1000e 0000:06:00.0: irq 52 for MSI/MSI-X
[    2.522216] e1000e 0000:06:00.0: irq 53 for MSI/MSI-X
[    2.544924] usb 5-2: new full speed USB device number 2 using uhci_hcd
[    2.641711] e1000e 0000:06:00.0: eth3: (PCI Express:2.5GT/s:Width x1) 00:25:90:71:6f:2e
[    2.641715] e1000e 0000:06:00.0: eth3: Intel(R) PRO/1000 Network Connection
[    2.641800] e1000e 0000:06:00.0: eth3: MAC: 3, PHY: 8, PBA No: 0101FF-0FF
[    2.641807] e1000e 0000:07:00.0: Disabling ASPM L0s 
[    2.641815] e1000e 0000:07:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.641830] e1000e 0000:07:00.0: setting latency timer to 64
[    2.641992] e1000e 0000:07:00.0: irq 54 for MSI/MSI-X
[    2.641996] e1000e 0000:07:00.0: irq 55 for MSI/MSI-X
[    2.642001] e1000e 0000:07:00.0: irq 56 for MSI/MSI-X
[    2.755901] input: American Megatrends Inc. Virtual Keyboard and Mouse as /devices/pci0000:00/0000:00:1a.2/usb5/5-2/5-2:1.0/input/input3
[    2.755943] generic-usb 0003:046B:FF10.0002: input,hidraw1: USB HID v1.10 Keyboard [American Megatrends Inc. Virtual Keyboard and Mouse] on usb-0000:00:1a.2-2/input0
[    2.757430] e1000e 0000:07:00.0: eth4: (PCI Express:2.5GT/s:Width x1) 00:25:90:71:6f:2f
[    2.757435] e1000e 0000:07:00.0: eth4: Intel(R) PRO/1000 Network Connection
[    2.757520] e1000e 0000:07:00.0: eth4: MAC: 3, PHY: 8, PBA No: 0101FF-0FF
[    2.772843] input: American Megatrends Inc. Virtual Keyboard and Mouse as /devices/pci0000:00/0000:00:1a.2/usb5/5-2/5-2:1.1/input/input4
[    2.772980] generic-usb 0003:046B:FF10.0003: input,hidraw2: USB HID v1.10 Mouse [American Megatrends Inc. Virtual Keyboard and Mouse] on usb-0000:00:1a.2-2/input1
[    2.907852] ioc0: LSISAS1068E B3: Capabilities={Initiator}
[    2.907870] mptsas 0000:05:00.0: setting latency timer to 64
[   15.103802] scsi4 : ioc0: LSISAS1068E B3, FwRev=01200000h, Ports=1, MaxQ=483, IRQ=16
[   15.140924] mptsas: ioc0: add expander: num_phys 30, sas_addr (0x500304800166aa7f)
[   15.241311] mptsas: ioc0: attaching sata device: fw_channel 0, fw_id 0, phy 12, sas_addr 0x500304800166aa6c
[   15.246370] scsi 4:0:0:0: Direct-Access     ATA      ST500DM002-1BD14 KC44 PQ: 0 ANSI: 5
[   15.248229] sd 4:0:0:0: Attached scsi generic sg0 type 0
[   15.250139] sd 4:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[   15.250811] mptsas: ioc0: attaching ssp device: fw_channel 0, fw_id 2, phy 28, sas_addr 0x500304800166aa7d
[   15.251436] scsi 4:0:1:0: Enclosure         LSI CORP SAS2X28          0717 PQ: 0 ANSI: 5
[   15.256761] scsi 4:0:1:0: Attached scsi generic sg1 type 13
[   15.296538] sd 4:0:0:0: [sda] Write Protect is off
[   15.296546] sd 4:0:0:0: [sda] Mode Sense: 73 00 00 08
[   15.346221] sd 4:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   15.455252]  sda: sda1 sda2 < sda5 >
[   15.527537] sd 4:0:0:0: [sda] Attached SCSI disk
[   15.580572] ses 4:0:1:0: Attached Enclosure device
[   16.331317] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   18.802492] udevd[385]: starting version 173
[   19.344654] lp: driver loaded but no devices found
[   19.391777] 802.1Q VLAN Support v1.8
[   19.469006] Adding 25154556k swap on /dev/sda5.  Priority:-1 extents:1 across:25154556k 
[   19.954649] [Firmware Warn]: GHES: Poll interval is 0 for generic hardware error source: 1, disabled.
[   19.964535] EDAC MC: Ver: 2.1.0
[   19.987554] dca service started, version 1.12.1
[   20.089507] EDAC MC0: Giving out device to 'i7core_edac.c' 'i7 core #0': DEV 0000:ff:03.0
[   20.089520] EDAC PCI0: Giving out device to module 'i7core_edac' controller 'EDAC PCI controller': DEV '0000:ff:03.0' (POLLED)
[   20.089522] EDAC i7core: Driver loaded.
[   20.141989] ioatdma: Intel(R) QuickData Technology Driver 4.00
[   20.142035] ioatdma 0000:00:16.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   20.142055] ioatdma 0000:00:16.0: setting latency timer to 64
[   20.142112] ioatdma 0000:00:16.0: irq 57 for MSI/MSI-X
[   20.142289] ioatdma 0000:00:16.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   20.142304] ioatdma 0000:00:16.1: setting latency timer to 64
[   20.142349] ioatdma 0000:00:16.1: irq 58 for MSI/MSI-X
[   20.142513] ioatdma 0000:00:16.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[   20.142525] ioatdma 0000:00:16.2: setting latency timer to 64
[   20.142568] ioatdma 0000:00:16.2: irq 59 for MSI/MSI-X
[   20.142725] ioatdma 0000:00:16.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[   20.142737] ioatdma 0000:00:16.3: setting latency timer to 64
[   20.142779] ioatdma 0000:00:16.3: irq 60 for MSI/MSI-X
[   20.142940] ioatdma 0000:00:16.4: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   20.142952] ioatdma 0000:00:16.4: setting latency timer to 64
[   20.142995] ioatdma 0000:00:16.4: irq 61 for MSI/MSI-X
[   20.143149] ioatdma 0000:00:16.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   20.143163] ioatdma 0000:00:16.5: setting latency timer to 64
[   20.143205] ioatdma 0000:00:16.5: irq 62 for MSI/MSI-X
[   20.143363] ioatdma 0000:00:16.6: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[   20.143375] ioatdma 0000:00:16.6: setting latency timer to 64
[   20.143417] ioatdma 0000:00:16.6: irq 63 for MSI/MSI-X
[   20.143574] ioatdma 0000:00:16.7: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[   20.143587] ioatdma 0000:00:16.7: setting latency timer to 64
[   20.143629] ioatdma 0000:00:16.7: irq 64 for MSI/MSI-X
[   20.875071] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.875074] 8021q: adding VLAN 0 to HW filter on device eth0
[   21.292745] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   21.573919] type=1400 audit(1333091752.558:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=866 comm="apparmor_parser"
[   21.573997] type=1400 audit(1333091752.558:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=863 comm="apparmor_parser"
[   21.574004] type=1400 audit(1333091752.558:4): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=867 comm="apparmor_parser"
[   21.574033] type=1400 audit(1333091752.558:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=861 comm="apparmor_parser"
[   21.574040] type=1400 audit(1333091752.558:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=862 comm="apparmor_parser"
[   21.574060] type=1400 audit(1333091752.558:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=864 comm="apparmor_parser"
[   21.574067] type=1400 audit(1333091752.558:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=865 comm="apparmor_parser"
[   21.574162] type=1400 audit(1333091752.558:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=866 comm="apparmor_parser"
[   21.574316] type=1400 audit(1333091752.558:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=866 comm="apparmor_parser"
[   21.574338] type=1400 audit(1333091752.558:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=867 comm="apparmor_parser"
[   21.594992] ADDRCONF(NETDEV_UP): eth0.17: link is not ready
[   22.240638] init: failsafe main process (999) killed by TERM signal
[   23.962742] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: None
[   23.963771] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   23.964744] ADDRCONF(NETDEV_CHANGE): eth0.17: link becomes ready
[   24.193441] vesafb: mode is 1280x1024x32, linelength=5120, pages=0
[   24.193442] vesafb: scrolling: redraw
[   24.193444] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[   24.193448] mtrr: type mismatch for f9000000,800000 old: write-back new: write-combining
[   24.193450] mtrr: type mismatch for f9000000,400000 old: write-back new: write-combining
[   24.193452] mtrr: type mismatch for f9000000,200000 old: write-back new: write-combining
[   24.193453] mtrr: type mismatch for f9000000,100000 old: write-back new: write-combining
[   24.193455] mtrr: type mismatch for f9000000,80000 old: write-back new: write-combining
[   24.193457] mtrr: type mismatch for f9000000,40000 old: write-back new: write-combining
[   24.193458] mtrr: type mismatch for f9000000,20000 old: write-back new: write-combining
[   24.193460] mtrr: type mismatch for f9000000,10000 old: write-back new: write-combining
[   24.193461] mtrr: type mismatch for f9000000,8000 old: write-back new: write-combining
[   24.193463] mtrr: type mismatch for f9000000,4000 old: write-back new: write-combining
[   24.193465] mtrr: type mismatch for f9000000,2000 old: write-back new: write-combining
[   24.193466] mtrr: type mismatch for f9000000,1000 old: write-back new: write-combining
[   24.194033] vesafb: framebuffer at 0xf9000000, mapped to 0xffffc90014600000, using 5120k, total 5120k
[   24.194229] Console: switching to colour frame buffer device 160x64
[   24.309762] fb0: VESA VGA frame buffer device
[   24.491847] init: apport pre-start process (1143) terminated with status 1
[   24.493653] init: apport post-stop process (1156) terminated with status 1
[   26.956434] CE: hpet increased min_delta_ns to 20113 nsec
[   34.715903] eth0: no IPv6 routers present
[   34.939210] eth0.17: no IPv6 routers present
[  108.148945] mptsas: ioc0: attaching sata device: fw_channel 0, fw_id 11, phy 21, sas_addr 0x500304800166aa75
[  108.154010] scsi 4:0:2:0: Direct-Access     ATA      Hitachi HDS72303 A580 PQ: 0 ANSI: 5
[  108.155953] sd 4:0:2:0: Attached scsi generic sg2 type 0
[  108.161286] sd 4:0:2:0: [sdb] 4294967294 512-byte logical blocks: (2.19 TB/1.99 TiB)
[  108.343248] sd 4:0:2:0: [sdb] Write Protect is off
[  108.343252] sd 4:0:2:0: [sdb] Mode Sense: 73 00 00 08
[  108.347214] sd 4:0:2:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  108.552122]  sdb: AHDI sdb1 sdb2
[  108.552169] sdb: p2 size 4294967295 extends beyond EOD, enabling native capacity
[  108.776362]  sdb: AHDI sdb1 sdb2
[  108.776409] sdb: p2 size 4294967295 extends beyond EOD, truncated
[  108.997074] sd 4:0:2:0: [sdb] Attached SCSI disk
[  391.347221] EXT3-fs (sdb1): error: can't find ext3 filesystem on dev sdb1.
[  391.397908] EXT2-fs (sdb1): error: can't find an ext2 filesystem on dev sdb1.
[  391.437948] EXT4-fs (sdb1): VFS: Can't find ext4 filesystem
[  403.906959] EXT3-fs (sdb1): error: can't find ext3 filesystem on dev sdb1.
[  403.954599] EXT2-fs (sdb1): error: can't find an ext2 filesystem on dev sdb1.
[  403.994593] EXT4-fs (sdb1): VFS: Can't find ext4 filesystem
[  417.263370] EXT4-fs (sdb1): VFS: Can't find ext4 filesystem
[ 4753.720509] init: tty1 main process (1239) killed by INT signal
[ 4753.720539] init: tty1 main process ended, respawning
[ 4775.023854] mptsas: ioc0: attaching sata device: fw_channel 0, fw_id 8, phy 17, sas_addr 0x500304800166aa71
[ 4775.033840] scsi 4:0:3:0: Direct-Access     ATA      WDC WD30EZRX-00M 0A80 PQ: 0 ANSI: 5
[ 4775.035830] sd 4:0:3:0: Attached scsi generic sg3 type 0
[ 4775.046417] sd 4:0:3:0: [sdc] 4294967294 512-byte logical blocks: (2.19 TB/1.99 TiB)
[ 4775.082632] sd 4:0:3:0: [sdc] Write Protect is off
[ 4775.082637] sd 4:0:3:0: [sdc] Mode Sense: 73 00 00 08
[ 4775.092174] sd 4:0:3:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 4775.149014]  sdc: unknown partition table
[ 4775.231614] sd 4:0:3:0: [sdc] Attached SCSI disk
[ 5544.130494] EXT3-fs (sdb1): error: can't find ext3 filesystem on dev sdb1.
[ 5544.171241] EXT2-fs (sdb1): error: can't find an ext2 filesystem on dev sdb1.
[ 5544.211050] EXT4-fs (sdb1): VFS: Can't find ext4 filesystem
[ 5547.047524] EXT3-fs (sdb2): error: can't find ext3 filesystem on dev sdb2.
[ 5547.093953] EXT2-fs (sdb2): error: can't find an ext2 filesystem on dev sdb2.
[ 5547.114012] EXT4-fs (sdb2): VFS: Can't find ext4 filesystem
[ 6656.021333] EXT3-fs (sdc): error: can't find ext3 filesystem on dev sdc.
[ 6656.069108] EXT2-fs (sdc): error: can't find an ext2 filesystem on dev sdc.
[ 6656.109109] EXT4-fs (sdc): VFS: Can't find ext4 filesystem
```and here is the output from **fdisk -l**


```
WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00093025

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   926459903   463228928   83  Linux
/dev/sda2       926461950   976771071    25154561    5  Extended
/dev/sda5       926461952   976771071    25154560   82  Linux swap / Solaris

Disk /dev/sdb: 2199.0 GB, 2199023254528 bytes
255 heads, 63 sectors/track, 267349 cylinders, total 4294967294 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          33          16+  ee  GPT
/dev/sdb2   *          34  4294967328  2147483647+   7  HPFS/NTFS/exFAT

Disk /dev/sdc: 2199.0 GB, 2199023254528 bytes
256 heads, 63 sectors/track, 266305 cylinders, total 4294967294 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9bf278fe

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1  4294967295  2147483647+  ee  GPT


```and here is the output from **parted -l **


```


Model: ATA ST500DM002-1BD14 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  474GB  474GB   primary   ext4            boot
 2      474GB   500GB  25.8GB  extended
 5      474GB   500GB  25.8GB  logical   linux-swap(v1)


Error: Invalid argument during seek for read on /dev/sdb                  
Retry/Ignore/Cancel? I                                                    
Error: The backup GPT table is corrupt, but the primary appears OK, so that will be used.
OK/Cancel? Ok                                                             
Backtrace has 8 calls on stack:
  8: /lib/libparted.so.0(ped_assert+0x2e) [0x7f9769cc639e]
  7: /lib/libparted.so.0(+0x4095c) [0x7f9769cf795c]
  6: /lib/libparted.so.0(ped_disk_new+0x58) [0x7f9769ccc588]
  5: parted() [0x406cb1]
  4: parted() [0x407a7a]
  3: parted(main+0x1483) [0x406403]
  2: /lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xed) [0x7f97694ce30d]
  1: parted() [0x406451]
                                                                          

You found a bug in GNU Parted! Here's what you have to do:

Don't panic! The bug has most likely not affected any of your data.
Help us to fix this bug by doing the following:

Check whether the bug has already been fixed by checking
the last version of GNU Parted that you can find at:

    http://ftp.gnu.org/gnu/parted/

Please check this version prior to bug reporting.

If this has not been fixed yet or if you don't know how to check,
please visit the GNU Parted website:

       http://www.gnu.org/software/parted

for further information.

Your report should contain the version of this release (2.3)
along with the error message below, the output of

      parted DEVICE unit co print unit s print

and the following history of commands you entered.
Also include any additional information about your setup you
consider important.

Assertion (last_usable <= disk->dev->length) at ../../../libparted/labels/gpt.c:934 in function _parse_header() failed.

Aborted

```Have googled around without any success. 


Thanks!

---

### Post by darkod on 2012-03-30
10.04 might be mounting them, but both disks look strange. It might be just because fdisk doesn't understand gpt properly, but look at your fdisk results:
For /dev/sdb the sdb2 partition End sector is outside of the disk. It is higher than total number of sectors. On top of that sdb1 is type GPT and sdb2 is reported as type NTFS. For a true GPT disk fdisk should report the whole disk as single gpt type partition.
For /dev/sdc for example, it reports a single gpt partition on the whole disk, but again the End sector is higher (by 1) than the total number of sectors.

Sometimes errors in the partition table can happen depending what program you use to partition. For example, it seems fdisk has some bugs and it is not advised to create partitions with fdisk even if we are talking about msdos disk. you better use cfdisk or parted.

For your GPT disks, parted seems a good choice for creating partitions.

If you have no data on these disks, and you don't mind starting from scratch, you can create new gpt table with:
```
sudo parted /dev/sdb
mklabel gpt
exit
```Do the same for /dev/sdc.

If you are creating partitions with parted too, it's best to use it in sectors, not KBs, or cylinders. It's more precise. You can change the unit with 'unit s'. Simply create single partition from sector 1 to the last sector, and exit parted.

Then create the filesystem with mkfs to the one you want to use.

---

### Post by oldfred on 2012-03-30
Are you booting with BIOS or UEFI. I do not see either a bios_grub or efi partition.

Another poster said he used gpt with MBR and had it work without a bios_grub until the recent version. But I have always used a bios_grub and grub installs without issue.

In a GPT partition map, the 31 kiB area after Master Boot Record where GRUB is usually embedded to, does not exist. When GRUB can't be embedded, its only option is to use blocklists, which are unreliable and discouraged.
However, in the GPT setup, there is no space following the 512-byte MBR for embedding the "second stage" core.img. Thus, you must make a separate "BIOS boot partition" to hold core.img. BIOS Boot Partition only needs to be about 32 KiB in size, although in most cases make it 1 MiB because of partition alignment issues

You can also use gdisk which is a gpt version of fdisk. It is in the repository, but you may want to download the newest version from the rodsbooks site.

repair gpt:
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)

GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)
[http://www.rodsbooks.com/gdisk/download.html#obs](http://www.rodsbooks.com/gdisk/download.html#obs)

---

### Post by darkod on 2012-03-30
> **oldfred said:**
> Are you booting with BIOS or UEFI. I do not see either a bios_grub or efi partition.


If I underastand it correctly the boot is on sda which has msdos table and the boot flag on the root partition sda1.

sdb and sdc are only data disks, with gpt because of their large capacity.

---

### Post by oldfred on 2012-03-30
Sorry, missed the MBR drive. So all the info on bios_grub is not necessary. 

But you still may need gdisk or fixparts to work on the gpt drives. fdisk is only good on the MBR drive.

---

