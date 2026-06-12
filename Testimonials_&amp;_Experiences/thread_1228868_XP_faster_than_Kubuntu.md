---
title: "XP faster than Kubuntu?"
date: 2009-08-01
forum: Testimonials &amp; Experiences
---

### Post by DylanH on 2009-08-01
Just wiped drive and now dual-booting a modified (some components removed) version of XP Pro SP3 and Kubuntu 9.04.

I ran some completely non-scientific tests to test boot up and shut down speed and found that XP was significantly faster in both respects. Starting at the boot menu, the time it took to log in and load Firefox: 56 seconds for Kubuntu and only 41 seconds for XP. Shutdown - same trend: 13 seconds for XP and 28 seconds for Kubuntu. What gives?

One notable feature of the Kubuntu startup/shutdown process (on my machine at any rate), is a black screen that lasts for 20 seconds. Perhaps this is the culprit? I don't recall seeing anything like this when I was booting Ubuntu or Xubuntu.

Assuming this is the problem that is causing Kubuntu to be so much slower than XP, can anyone help me figure out a solution? Please let me know what information would be of use and I'll provide it ASAP!

Please help!

:confused:

-----

[edit: below is the output of dmesg]

```
[    0.000000] BIOS EBDA/lowmem at: 0009fc00/0009fc00
[    0.000000] Initializing cgroup subsys cpuset     
[    0.000000] Initializing cgroup subsys cpu        
[    0.000000] Linux version 2.6.28-11-generic (buildd@palmer) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 (Ubuntu 2.6.28-11.42-generic)                                                                           
[    0.000000] KERNEL supported cpus:                                                                                           
[    0.000000]   Intel GenuineIntel                                                                                             
[    0.000000]   AMD AuthenticAMD                                                                                               
[    0.000000]   NSC Geode by NSC                                                                                               
[    0.000000]   Cyrix CyrixInstead                                                                                             
[    0.000000]   Centaur CentaurHauls                                                                                           
[    0.000000]   Transmeta GenuineTMx86                                                                                         
[    0.000000]   Transmeta TransmetaCPU                                                                                         
[    0.000000]   UMC UMC UMC UMC                                                                                                
[    0.000000] BIOS-provided physical RAM map:                                                                                  
[    0.000000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)                                                         
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)                                                       
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fe74000 (usable)                                                         
[    0.000000]  BIOS-e820: 000000003fe74000 - 000000003fe76000 (ACPI NVS)                                                       
[    0.000000]  BIOS-e820: 000000003fe76000 - 000000003fe97000 (ACPI data)                                                      
[    0.000000]  BIOS-e820: 000000003fe97000 - 000000003ff00000 (reserved)                                                       
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)                                                       
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)                                                       
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)                                                       
[    0.000000] DMI 2.3 present.                                                                                                 
[    0.000000] last_pfn = 0x3fe74 max_arch_pfn = 0x100000                                                                       
[    0.000000] Scanning 2 areas for low memory corruption                                                                       
[    0.000000] modified physical RAM map:                                                                                       
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)                                                          
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)                                                        
[    0.000000]  modified: 0000000000006000 - 0000000000007000 (usable)                                                          
[    0.000000]  modified: 0000000000007000 - 0000000000010000 (reserved)                                                        
[    0.000000]  modified: 0000000000010000 - 0000000000093000 (usable)                                                          
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)                                                        
[    0.000000]  modified: 0000000000100000 - 000000003fe74000 (usable)                                                          
[    0.000000]  modified: 000000003fe74000 - 000000003fe76000 (ACPI NVS)                                                        
[    0.000000]  modified: 000000003fe76000 - 000000003fe97000 (ACPI data)                                                       
[    0.000000]  modified: 000000003fe97000 - 000000003ff00000 (reserved)                                                        
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)                                                        
[    0.000000]  modified: 00000000fee00000 - 00000000fee10000 (reserved)                                                        
[    0.000000]  modified: 00000000ffb00000 - 0000000100000000 (reserved)                                                        
[    0.000000] kernel direct mapping tables up to 373fe000 @ 10000-16000                                                        
[    0.000000] RAMDISK: 378bf000 - 37fef253                                                                                     
[    0.000000] Allocated new RAMDISK: 00881000 - 00fb1253                                                                       
[    0.000000] Move RAMDISK from 00000000378bf000 - 0000000037fef252 to 00881000 - 00fb1252                                     
[    0.000000] ACPI: RSDP 000FEB80, 0014 (r0 DELL  )                                                                            
[    0.000000] ACPI: RSDT 000FD22A, 0034 (r1 DELL    2400           7 ASL        61)                                            
[    0.000000] ACPI: FACP 000FD25E, 0074 (r1 DELL    2400           7 ASL        61)                                            
[    0.000000] ACPI: DSDT FFFCC0F1, 2404 (r1   DELL    dt_ex     1000 MSFT  100000D)                                            
[    0.000000] ACPI: FACS 3FE74000, 0040                                                                                        
[    0.000000] ACPI: SSDT FFFCE632, 00BA (r1   DELL    st_ex     1000 MSFT  100000D)                                            
[    0.000000] ACPI: APIC 000FD2D2, 006C (r1 DELL    2400           7 ASL        61)                                            
[    0.000000] ACPI: BOOT 000FD33E, 0028 (r1 DELL    2400           7 ASL        61)                                            
[    0.000000] ACPI: Local APIC address 0xfee00000                                                                              
[    0.000000] 138MB HIGHMEM available.                                                                                         
[    0.000000] 883MB LOWMEM available.                                                                                          
[    0.000000]   mapped low ram: 0 - 373fe000                                                                                   
[    0.000000]   low ram: 00000000 - 373fe000                                                                                   
[    0.000000]   bootmap 00012000 - 00018e80                                                                                    
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00373fe000]                                                     
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]                                    
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]                                    
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]                                    
[    0.000000]   #3 [0000100000 - 000087c52c]    TEXT DATA BSS ==> [0000100000 - 000087c52c]                                    
[    0.000000]   #4 [000087d000 - 0000881000]    INIT_PG_TABLE ==> [000087d000 - 0000881000]                                    
[    0.000000]   #5 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]                                    
[    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]                                    
[    0.000000]   #7 [0000881000 - 0000fb1253]      NEW RAMDISK ==> [0000881000 - 0000fb1253]                                    
[    0.000000]   #8 [0000012000 - 0000019000]          BOOTMAP ==> [0000012000 - 0000019000]                                    
[    0.000000] found SMP MP-table at [c00fe710] 000fe710                                                                        
[    0.000000] Zone PFN ranges:                                                                                                 
[    0.000000]   DMA      0x00000000 -> 0x00001000                                                                              
[    0.000000]   Normal   0x00001000 -> 0x000373fe                                                                              
[    0.000000]   HighMem  0x000373fe -> 0x0003fe74                                                                              
[    0.000000] Movable zone start PFN for each node                                                                             
[    0.000000] early_node_map[4] active PFN ranges                                                                              
[    0.000000]     0: 0x00000000 -> 0x00000002                                                                                  
[    0.000000]     0: 0x00000006 -> 0x00000007                                                                                  
[    0.000000]     0: 0x00000010 -> 0x00000093                                                                                  
[    0.000000]     0: 0x00000100 -> 0x0003fe74                                                                                  
[    0.000000] On node 0 totalpages: 261626                                                                                     
[    0.000000] free_area_init_node: node 0, pgdat c06d0f80, node_mem_map c1000000                                               
[    0.000000]   DMA zone: 32 pages used for memmap                                                                             
[    0.000000]   DMA zone: 0 pages reserved                                                                                     
[    0.000000]   DMA zone: 3942 pages, LIFO batch:0                                                                             
[    0.000000]   Normal zone: 1736 pages used for memmap                                                                        
[    0.000000]   Normal zone: 220470 pages, LIFO batch:31                                                                       
[    0.000000]   HighMem zone: 277 pages used for memmap                                                                        
[    0.000000]   HighMem zone: 35169 pages, LIFO batch:7                                                                        
[    0.000000]   Movable zone: 0 pages used for memmap                                                                          
[    0.000000] ACPI: PM-Timer IO Port: 0x808                                                                                    
[    0.000000] ACPI: Local APIC address 0xfee00000                                                                              
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)                                                               
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] disabled)                                                              
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] disabled)                                                              
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] disabled)                                                              
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])                                                          
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23                                                   
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)                                                         
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)                                                      
[    0.000000] ACPI: IRQ0 used by override.                                                                                     
[    0.000000] ACPI: IRQ2 used by override.                                                                                     
[    0.000000] ACPI: IRQ9 used by override.                                                                                     
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs                                                                    
[    0.000000] Using ACPI (MADT) for SMP configuration information                                                              
[    0.000000] SMP: Allowing 4 CPUs, 3 hotplug CPUs                                                                             
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000                                                
[    0.000000] PM: Registered nosave memory: 0000000000007000 - 0000000000010000                                                
[    0.000000] PM: Registered nosave memory: 0000000000093000 - 00000000000f0000                                                
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000                                                
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 3ff00000:bed00000)                                           
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data                                                                   
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1                                                                        
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 259581                                      
[    0.000000] Kernel command line: root=UUID=c9352583-3e64-4fd5-8229-912314373bde ro quiet splash                              
[    0.000000] Enabling fast FPU save and restore... done.                                                                      
[    0.000000] Enabling unmasked SIMD FPU exception support... done.                                                            
[    0.000000] Initializing CPU#0                                                                                               
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)                                                            
[    0.000000] TSC: PIT calibration matches PMTIMER. 1 loops                                                                    
[    0.000000] Detected 2392.220 MHz processor.                                                                                 
[    0.004000] Console: colour VGA+ 80x25                                                                                       
[    0.004000] console [tty0] enabled                                                                                           
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)                                                 
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)                                                   
[    0.004000] allocated 5234960 bytes of page_cgroup                                                                           
[    0.004000] please try cgroup_disable=memory option if you don't want                                                        
[    0.004000] Scanning for low memory corruption every 60 seconds                                                              
[    0.004000] Memory: 1016800k/1046992k available (4126k kernel code, 29380k reserved, 2208k data, 532k init, 141784k highmem) 
[    0.004000] virtual kernel memory layout:                                                                                    
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)                                                                
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)                                                                
[    0.004000]     vmalloc : 0xf7bfe000 - 0xff3fe000   ( 120 MB)                                                                
[    0.004000]     lowmem  : 0xc0000000 - 0xf73fe000   ( 883 MB)                                                                
[    0.004000]       .init : 0xc0737000 - 0xc07bc000   ( 532 kB)                                                                
[    0.004000]       .data : 0xc0507a6f - 0xc072fe60   (2208 kB)                                                                
[    0.004000]       .text : 0xc0100000 - 0xc0507a6f   (4126 kB)                                                                
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.                                      
[    0.004000] SLUB: Genslabs=12, HWalign=128, Order=0-3, MinObjects=0, CPUs=4, Nodes=1                                         
[    0.004020] Calibrating delay loop (skipped), value calculated using timer frequency.. 4784.44 BogoMIPS (lpj=9568880)        
[    0.004056] Security Framework initialized                                                                                   
[    0.004073] SELinux:  Disabled at boot.                                                                                      
[    0.004108] AppArmor: AppArmor initialized                                                                                   
[    0.004132] Mount-cache hash table entries: 512                                                                              
[    0.004412] Initializing cgroup subsys ns                                                                                    
[    0.004424] Initializing cgroup subsys cpuacct                                                                               
[    0.004431] Initializing cgroup subsys memory                                                                                
[    0.004441] Initializing cgroup subsys freezer                                                                               
[    0.004472] CPU: Trace cache: 12K uops, L1 D cache: 8K                                                                       
[    0.004479] CPU: L2 cache: 128K                                                                                              
[    0.004485] CPU: Hyper-Threading is disabled                                                                                 
[    0.004514] Checking 'hlt' instruction... OK.                                                                                
[    0.020911] SMP alternatives: switching to UP code                                                                           
[    0.212041] ACPI: Core revision 20080926                                                                                     
[    0.227662] ACPI: Checking initramfs for custom DSDT                                                                         
[    0.598198] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1                                                             
[    0.637896] CPU0: Intel(R) Celeron(R) CPU 2.40GHz stepping 09                                                                
[    0.640002] Brought up 1 CPUs                                                                                                
[    0.640002] Total of 1 processors activated (4784.44 BogoMIPS).                                                              
[    0.640002] CPU0 attaching NULL sched-domain.                                                                                
[    0.640002] net_namespace: 776 bytes                                                                                         
[    0.640002] Booting paravirtualized kernel on bare hardware                                                                  
[    0.640002] Time: 11:08:15  Date: 08/01/09                                                                                   
[    0.640002] regulator: core version 0.5                                                                                      
[    0.640002] NET: Registered protocol family 16                                                                               
[    0.640002] EISA bus registered                                                                                              
[    0.640002] ACPI: bus type pci registered                                                                                    
[    0.640002] PCI: PCI BIOS revision 2.10 entry at 0xfbbbf, last bus=1                                                         
[    0.640002] PCI: Using configuration type 1 for base access                                                                  
[    0.641960] ACPI: EC: Look up EC in DSDT                                                                                     
[    0.672452] ACPI: Interpreter enabled                                                                                        
[    0.672463] ACPI: (supports S0 S1 S3 S4 S5)                                                                                  
[    0.672496] ACPI: Using IOAPIC for interrupt routing                                                                         
[    0.708108] ACPI: No dock devices found.                                                                                     
[    0.708134] ACPI: PCI Root Bridge [PCI0] (0000:00)                                                                           
[    0.708224] pci 0000:00:00.0: reg 10 32bit mmio: [0xf0000000-0xf7ffffff]                                                     
[    0.708305] pci 0000:00:02.0: reg 10 32bit mmio: [0xe8000000-0xefffffff]                                                     
[    0.708314] pci 0000:00:02.0: reg 14 32bit mmio: [0xfeb80000-0xfebfffff]                                                     
[    0.708430] pci 0000:00:1d.0: reg 20 io port: [0xff80-0xff9f]                                                                
[    0.708488] pci 0000:00:1d.1: reg 20 io port: [0xff60-0xff7f]                                                                
[    0.708546] pci 0000:00:1d.2: reg 20 io port: [0xff40-0xff5f]                                                                
[    0.708613] pci 0000:00:1d.7: reg 10 32bit mmio: [0xffa80800-0xffa80bff]                                                     
[    0.708663] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold                                                            
[    0.708669] pci 0000:00:1d.7: PME# disabled                                                                                  
[    0.708723] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,                                               
[    0.708724] * this clock source is slow. If you are sure your timer does not have                                            
[    0.708727] * this bug, please use "acpi_pm_good" to disable the workaround                                                  
[    0.708772] HPET not enabled in BIOS. You might try hpet=force boot option                                                   
[    0.708782] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO                                          
[    0.708787] pci 0000:00:1f.0: quirk: region 0880-08bf claimed by ICH4 GPIO                                                   
[    0.708811] pci 0000:00:1f.1: reg 10 io port: [0x1f0-0x1f7]                                                                  
[    0.708821] pci 0000:00:1f.1: reg 14 io port: [0x3f4-0x3f7]                                                                  
[    0.708829] pci 0000:00:1f.1: reg 18 io port: [0x170-0x177]                                                                  
[    0.708837] pci 0000:00:1f.1: reg 1c io port: [0x374-0x377]                                                                  
[    0.708845] pci 0000:00:1f.1: reg 20 io port: [0xffa0-0xffaf]                                                                
[    0.708854] pci 0000:00:1f.1: reg 24 32bit mmio: [0xfeb7fc00-0xfeb7ffff]                                                     
[    0.708911] pci 0000:00:1f.3: reg 20 io port: [0xeda0-0xedbf]                                                                
[    0.708961] pci 0000:00:1f.5: reg 10 io port: [0xee00-0xeeff]                                                                
[    0.708969] pci 0000:00:1f.5: reg 14 io port: [0xedc0-0xedff]                                                                
[    0.708977] pci 0000:00:1f.5: reg 18 32bit mmio: [0xfeb7fa00-0xfeb7fbff]                                                     
[    0.708986] pci 0000:00:1f.5: reg 1c 32bit mmio: [0xfeb7f900-0xfeb7f9ff]                                                     
[    0.709012] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold                                                            
[    0.709017] pci 0000:00:1f.5: PME# disabled                                                                                  
[    0.709080] pci 0000:01:04.0: reg 10 32bit mmio: [0xfe9f0000-0xfe9fffff]                                                     
[    0.709161] pci 0000:01:09.0: reg 10 32bit mmio: [0xfe9ee000-0xfe9effff]                                                     
[    0.709193] pci 0000:01:09.0: reg 30 32bit mmio: [0xfea00000-0xfea03fff]                                                     
[    0.709204] pci 0000:01:09.0: supports D1 D2                                                                                 
[    0.709207] pci 0000:01:09.0: PME# supported from D0 D1 D2 D3hot D3cold                                                      
[    0.709212] pci 0000:01:09.0: PME# disabled                                                                                  
[    0.709248] pci 0000:00:1e.0: transparent bridge                                                                             
[    0.709257] pci 0000:00:1e.0: bridge 32bit mmio: [0xfe900000-0xfeafffff]                                                     
[    0.709271] bus 00 -> node 0                                                                                                 
[    0.709290] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]                                                              
[    0.709901] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]                                                         
[    0.876593] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 15)                                                  
[    0.876977] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 7 9 10 11 12 15)                                                  
[    0.877363] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 15)                                                  
[    0.877740] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 *10 11 12 15)                                                  
[    0.878129] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.                                     
[    0.878513] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.                                     
[    0.878896] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.                                     
[    0.879286] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 9 10 11 12 15)                                                  
[    0.879556] ACPI: WMI: Mapper loaded                                                                                         
[    0.879995] SCSI subsystem initialized                                                                                       
[    0.880139] libata version 3.00 loaded.                                                                                      
[    0.880284] usbcore: registered new interface driver usbfs                                                                   
[    0.880325] usbcore: registered new interface driver hub                                                                     
[    0.880426] usbcore: registered new device driver usb                                                                        
[    0.880779] PCI: Using ACPI for IRQ routing                                                                                  
[    0.880942] Bluetooth: Core ver 2.13                                                                                         
[    0.880942] NET: Registered protocol family 31                                                                               
[    0.880942] Bluetooth: HCI device and connection manager initialized                                                         
[    0.880942] Bluetooth: HCI socket layer initialized                                                                          
[    0.880942] NET: Registered protocol family 8                                                                                
[    0.880942] NET: Registered protocol family 20                                                                               
[    0.880942] NetLabel: Initializing                                                                                           
[    0.880942] NetLabel:  domain hash size = 128                                                                                
[    0.880942] NetLabel:  protocols = UNLABELED CIPSOv4                                                                         
[    0.880942] NetLabel:  unlabeled traffic allowed by default                                                                  
[    0.880942] AppArmor: AppArmor Filesystem Enabled                                                                            
[    0.880942] pnp: PnP ACPI init                                                                                               
[    0.880942] ACPI: bus type pnp registered                                                                                    
[    0.904968] pnp 00:09: io resource (0x800-0x85f) overlaps 0000:00:1f.0 BAR 7 (0x800-0x87f), disabling                        
[    0.904975] pnp 00:09: io resource (0x860-0x8ff) overlaps 0000:00:1f.0 BAR 7 (0x800-0x87f), disabling                        
[    0.905865] pnp: PnP ACPI: found 10 devices                                                                                  
[    0.905871] ACPI: ACPI bus type pnp unregistered                                                                             
[    0.905878] PnPBIOS: Disabled by ACPI PNP                                                                                    
[    0.905903] system 00:00: iomem range 0x0-0x9ffff could not be reserved                                                      
[    0.905908] system 00:00: iomem range 0x100000-0xffffff could not be reserved                                                
[    0.905912] system 00:00: iomem range 0x1000000-0x3fe73fff could not be reserved                                             
[    0.905916] system 00:00: iomem range 0xc0000-0xfffff could not be reserved                                                  
[    0.905921] system 00:00: iomem range 0xfec00000-0xfec0ffff has been reserved                                                
[    0.905925] system 00:00: iomem range 0xfee00000-0xfee0ffff has been reserved                                                
[    0.905929] system 00:00: iomem range 0xfecf0000-0xfecf0fff has been reserved                                                
[    0.905933] system 00:00: iomem range 0xffb00000-0xffbfffff has been reserved                                                
[    0.905937] system 00:00: iomem range 0xffc00000-0xffffffff has been reserved                                                
[    0.905956] system 00:09: ioport range 0xc00-0xc7f has been reserved                                                         
[    0.940950] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:01                                                              
[    0.940954] pci 0000:00:1e.0:   IO window: disabled                                                                          
[    0.940961] pci 0000:00:1e.0:   MEM window: 0xfe900000-0xfeafffff                                                            
[    0.940967] pci 0000:00:1e.0:   PREFETCH window: 0x00000040000000-0x000000400fffff                                           
[    0.940988] pci 0000:00:1e.0: setting latency timer to 64                                                                    
[    0.940994] bus: 00 index 0 io port: [0x00-0xffff]                                                                           
[    0.940998] bus: 00 index 1 mmio: [0x000000-0xffffffff]                                                                      
[    0.941001] bus: 01 index 0 mmio: [0x0-0x0]                                                                                  
[    0.941004] bus: 01 index 1 mmio: [0xfe900000-0xfeafffff]                                                                    
[    0.941007] bus: 01 index 2 mmio: [0x40000000-0x400fffff]                                                                    
[    0.941010] bus: 01 index 3 io port: [0x00-0xffff]                                                                           
[    0.941014] bus: 01 index 4 mmio: [0x000000-0xffffffff]                                                                      
[    0.941041] NET: Registered protocol family 2                                                                                
[    0.941259] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)                                                
[    0.941789] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)                                             
[    0.943420] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)                                                      
[    0.944234] TCP: Hash tables configured (established 131072 bind 65536)                                                      
[    0.944241] TCP reno registered                                                                                              
[    0.944502] NET: Registered protocol family 1                                                                                
[    0.944710] checking if image is initramfs... it is                                                                          
[    1.444059] Switched to high resolution mode on CPU 0                                                                        
[    1.727514] Freeing initrd memory: 7360k freed                                                                               
[    1.727593] Simple Boot Flag value 0x87 read from CMOS RAM was invalid                                                       
[    1.727597] Simple Boot Flag at 0x7a set to 0x1                                                                              
[    1.727647] cpufreq: No nForce2 chipset.                                                                                     
[    1.727933] audit: initializing netlink socket (disabled)                                                                    
[    1.727961] type=2000 audit(1249124895.724:1): initialized                                                                   
[    1.735556] highmem bounce pool size: 64 pages                                                                               
[    1.735568] HugeTLB registered 4 MB page size, pre-allocated 0 pages                                                         
[    1.737560] VFS: Disk quotas dquot_6.5.1                                                                                     
[    1.737693] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)                                                       
[    1.739002] fuse init (API version 7.10)                                                                                     
[    1.739224] msgmni has been set to 1724                                                                                      
[    1.739654] alg: No test for stdrng (krng)                                                                                   
[    1.739705] io scheduler noop registered                                                                                     
[    1.739709] io scheduler anticipatory registered                                                                             
[    1.739711] io scheduler deadline registered                                                                                 
[    1.739768] io scheduler cfq registered (default)                                                                            
[    1.739791] pci 0000:00:02.0: Boot video device                                                                              
[    1.759761] pci_hotplug: PCI Hot Plug PCI Core version: 0.5                                                                  
[    1.759780] pciehp: PCI Express Hot Plug Controller Driver version: 0.4                                                      
[    1.760041] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0                                        
[    1.760047] ACPI: Power Button (FF) [PWRF]                                                                                   
[    1.760139] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1                               
[    1.760150] ACPI: Power Button (CM) [VBTN]                                                                                   
[    1.760615] processor ACPI_CPU:00: registered as cooling_device0                                                             
[    1.786445] isapnp: Scanning for PnP cards...                                                                                
[    2.140441] isapnp: No Plug & Play device found                                                                              
[    2.143466] Serial: 8250/16550 driver4 ports, IRQ sharing enabled                                                            
[    2.143596] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A                                                             
[    2.144229] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A                                                                  
[    2.146047] brd: module loaded                                                                                               
[    2.146976] loop: module loaded                                                                                              
[    2.147196] Fixed MDIO Bus: probed                                                                                           
[    2.147207] PPP generic driver version 2.4.2                                                                                 
[    2.147344] input: Macintosh mouse button emulation as /devices/virtual/input/input2                                         
[    2.147411] Driver 'sd' needs updating - please use bus_type methods                                                         
[    2.147433] Driver 'sr' needs updating - please use bus_type methods                                                         
[    2.147592] ata_piix 0000:00:1f.1: version 2.12                                                                              
[    2.147621] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18                                                
[    2.147696] ata_piix 0000:00:1f.1: setting latency timer to 64                                                               
[    2.147890] scsi0 : ata_piix                                                                                                 
[    2.148174] scsi1 : ata_piix                                                                                                 
[    2.148275] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14                                                  
[    2.148280] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15                                                  
[    2.320630] ata1.00: ATA-6: HDS722540VLAT20, V31OA69A, max UDMA/100                                                          
[    2.320636] ata1.00: 78125000 sectors, multi 8: LBA48                                                                        
[    2.344619] ata1.00: configured for UDMA/100                                                                                 
[    2.508763] ata2.00: ATAPI: GCR-8483B, 1.05, max UDMA/33                                                                     
[    2.524770] ata2.00: configured for UDMA/33                                                                                  
[    2.525160] scsi 0:0:0:0: Direct-Access     ATA      HDS722540VLAT20  V31O PQ: 0 ANSI: 5                                     
[    2.525450] sd 0:0:0:0: [sda] 78125000 512-byte hardware sectors: (40.0 GB/37.2 GiB)                                         
[    2.525519] sd 0:0:0:0: [sda] Write Protect is off                                                                           
[    2.525523] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00                                                                        
[    2.525629] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA                          
[    2.525828] sd 0:0:0:0: [sda] 78125000 512-byte hardware sectors: (40.0 GB/37.2 GiB)                                         
[    2.525894] sd 0:0:0:0: [sda] Write Protect is off                                                                           
[    2.525898] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00                                                                        
[    2.526003] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA                          
[    2.526014]  sda: sda1 sda2 sda3 < sda5 sda6 >                                                                               
[    2.576850] sd 0:0:0:0: [sda] Attached SCSI disk                                                                             
[    2.576985] sd 0:0:0:0: Attached scsi generic sg0 type 0                                                                     
[    2.579728] scsi 1:0:0:0: CD-ROM            HL-DT-ST CD-ROM GCR-8483B 1.05 PQ: 0 ANSI: 5                                     
[    2.585673] sr0: scsi3-mmc drive: 48x/48x cd/rw xa/form2 cdda tray                                                           
[    2.585681] Uniform CD-ROM driver Revision: 3.20                                                                             
[    2.585895] sr 1:0:0:0: Attached scsi CD-ROM sr0                                                                             
[    2.586031] sr 1:0:0:0: Attached scsi generic sg1 type 5                                                                     
[    2.587528] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver                                                       
[    2.587591] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23                                                
[    2.587634] ehci_hcd 0000:00:1d.7: setting latency timer to 64                                                               
[    2.587641] ehci_hcd 0000:00:1d.7: EHCI Host Controller                                                                      
[    2.587812] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1                                             
[    2.591767] ehci_hcd 0000:00:1d.7: debug port 1                                                                              
[    2.591777] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported                                                   
[    2.591806] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xffa80800                                                                 
[    2.604021] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00                                                                
[    2.604191] usb usb1: configuration #1 chosen from 1 choice                                                                  
[    2.604253] hub 1-0:1.0: USB hub found                                                                                       
[    2.604275] hub 1-0:1.0: 6 ports detected                                                                                    
[    2.604547] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver                                                           
[    2.604596] uhci_hcd: USB Universal Host Controller Interface driver                                                         
[    2.604693] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16                                                
[    2.604710] uhci_hcd 0000:00:1d.0: setting latency timer to 64                                                               
[    2.604716] uhci_hcd 0000:00:1d.0: UHCI Host Controller                                                                      
[    2.604852] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2                                             
[    2.604900] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000ff80                                                                
[    2.605076] usb usb2: configuration #1 chosen from 1 choice                                                                  
[    2.605136] hub 2-0:1.0: USB hub found                                                                                       
[    2.605156] hub 2-0:1.0: 2 ports detected                                                                                    
[    2.605384] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19                                                
[    2.605399] uhci_hcd 0000:00:1d.1: setting latency timer to 64                                                               
[    2.605405] uhci_hcd 0000:00:1d.1: UHCI Host Controller                                                                      
[    2.605530] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3                                             
[    2.605584] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000ff60                                                                
[    2.605750] usb usb3: configuration #1 chosen from 1 choice                                                                  
[    2.605807] hub 3-0:1.0: USB hub found                                                                                       
[    2.605828] hub 3-0:1.0: 2 ports detected                                                                                    
[    2.606050] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18                                                
[    2.606064] uhci_hcd 0000:00:1d.2: setting latency timer to 64                                                               
[    2.606069] uhci_hcd 0000:00:1d.2: UHCI Host Controller                                                                      
[    2.606196] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4                                             
[    2.606245] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000ff40                                                                
[    2.606409] usb usb4: configuration #1 chosen from 1 choice                                                                  
[    2.606479] hub 4-0:1.0: USB hub found                                                                                       
[    2.606501] hub 4-0:1.0: 2 ports detected                                                                                    
[    2.606791] usbcore: registered new interface driver libusual                                                                
[    2.606880] usbcore: registered new interface driver usbserial                                                               
[    2.606904] USB Serial support registered for generic                                                                        
[    2.606936] usbcore: registered new interface driver usbserial_generic                                                       
[    2.606940] usbserial: USB Serial Driver core                                                                                
[    2.607033] PNP: No PS/2 controller found. Probing ports directly.                                                           
[    2.610050] serio: i8042 KBD port at 0x60,0x64 irq 1                                                                         
[    2.610064] serio: i8042 AUX port at 0x60,0x64 irq 12                                                                        
[    2.610397] mice: PS/2 mouse device common for all mice                                                                      
[    2.610777] rtc_cmos 00:05: RTC can wake from S4                                                                             
[    2.610881] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0                                                            
[    2.610915] rtc0: alarms up to one day, 242 bytes nvram                                                                      
[    2.611064] device-mapper: uevent: version 1.0.3                                                                             
[    2.611391] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]                                 
[    2.611575] device-mapper: multipath: version 1.0.5 loaded                                                                   
[    2.611582] device-mapper: multipath round-robin: version 1.0.0 loaded                                                       
[    2.611846] EISA: Probing bus 0 at eisa.0                                                                                    
[    2.611888] EISA: Detected 0 cards.                                                                                          
[    2.611986] cpuidle: using governor ladder                                                                                   
[    2.611990] cpuidle: using governor menu                                                                                     
[    2.612786] TCP cubic registered                                                                                             
[    2.612963] NET: Registered protocol family 10                                                                               
[    2.613677] lo: Disabled Privacy Extensions                                                                                  
[    2.614134] NET: Registered protocol family 17                                                                               
[    2.614203] Bluetooth: L2CAP ver 2.11                                                                                        
[    2.614206] Bluetooth: L2CAP socket layer initialized                                                                        
[    2.614211] Bluetooth: SCO (Voice Link) ver 0.6                                                                              
[    2.614214] Bluetooth: SCO socket layer initialized                                                                          
[    2.614323] Bluetooth: RFCOMM socket layer initialized                                                                       
[    2.614348] Bluetooth: RFCOMM TTY layer initialized                                                                          
[    2.614351] Bluetooth: RFCOMM ver 1.10                                                                                       
[    2.614467] Using IPI No-Shortcut mode                                                                                       
[    2.614693] registered taskstats version 1                                                                                   
[    2.614875]   Magic number: 5:316:124                                                                                        
[    2.614982] rtc_cmos 00:05: setting system clock to 2009-08-01 11:08:17 UTC (1249124897)                                     
[    2.614988] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found                                                             
[    2.614990] EDD information not available.                                                                                   
[    2.615888] Freeing unused kernel memory: 532k freed                                                                         
[    2.616097] Write protecting the kernel text: 4128k                                                                          
[    2.616147] Write protecting the kernel read-only data: 1532k                                                                
[    2.916048] usb 1-3: new high speed USB device using ehci_hcd and address 2                                                  
[    3.065037] usb 1-3: configuration #1 chosen from 1 choice                                                                   
[    3.091594] Initializing USB Mass Storage driver...                                                                          
[    3.099339] scsi2 : SCSI emulation for USB Mass Storage devices                                                              
[    3.118729] usbcore: registered new interface driver usb-storage                                                             
[    3.118737] USB Mass Storage support registered.                                                                             
[    3.118951] usb-storage: device found at 2                                                                                   
[    3.118956] usb-storage: waiting for device to settle before scanning                                                        
[    3.200130] usb 1-5: new high speed USB device using ehci_hcd and address 3                                                  
[    3.303870] FDC 0 is a post-1991 82077                                                                                       
[    3.334764] usb 1-5: configuration #1 chosen from 1 choice                                                                   
[    3.340533] scsi3 : SCSI emulation for USB Mass Storage devices                                                              
[    3.349301] usb-storage: device found at 3                                                                                   
[    3.349306] usb-storage: waiting for device to settle before scanning                                                        
[    3.644072] usb 4-2: new low speed USB device using uhci_hcd and address 2                                                   
[    3.718783] b44 0000:01:09.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17                                                     
[    3.780163] ssb: Sonics Silicon Backplane found on PCI device 0000:01:09.0                                                   
[    3.780215] b44.c:v2.0                                                                                                       
[    3.801029] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:0f:1f:7b:ce:1a                                                  
[    3.909267] usb 4-2: configuration #1 chosen from 1 choice                                                                   
[    5.628915] usbcore: registered new interface driver hiddev                                                                  
[    5.673413] input: BTC USB Multimedia Cordless Kit as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.0/input/input3         
[    5.756208] generic-usb 0003:046E:5520.0001: input,hidraw0: USB HID v1.10 Keyboard [BTC USB Multimedia Cordless Kit] on usb-0000:00:1d.2-2/input0                                                                                                            
[    5.790303] input: BTC USB Multimedia Cordless Kit as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.1/input/input4         
[    5.836212] generic-usb 0003:046E:5520.0002: input,hidraw1: USB HID v1.10 Mouse [BTC USB Multimedia Cordless Kit] on usb-0000:00:1d.2-2/input1                                                                                                               
[    5.973925] input: BTC USB Multimedia Cordless Kit as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.2/input/input5         
[    6.036196] generic-usb 0003:046E:5520.0003: input,hidraw2: USB HID v1.10 Device [BTC USB Multimedia Cordless Kit] on usb-0000:00:1d.2-2/input2                                                                                                              
[    6.036235] usbcore: registered new interface driver usbhid                                                                  
[    6.036242] usbhid: v2.6:USB HID core driver                                                                                 
[    6.477063] PM: Starting manual resume from disk                                                                             
[    6.477070] PM: Resume from partition 8:6                                                                                    
[    6.477072] PM: Checking hibernation image.                                                                                  
[    6.477320] PM: Resume from disk failed.                                                                                     
[    6.556050] kjournald starting.  Commit interval 5 seconds                                                                   
[    6.556079] EXT3-fs: mounted filesystem with ordered data mode.                                                              
[    8.116355] usb-storage: device scan complete                                                                                
[    8.116916] scsi 2:0:0:0: Direct-Access     SAMSUNG  HD502IJ               PQ: 0 ANSI: 2 CCS                                 
[    8.118521] sd 2:0:0:0: [sdb] 976773168 512-byte hardware sectors: (500 GB/465 GiB)                                          
[    8.119390] sd 2:0:0:0: [sdb] Write Protect is off                                                                           
[    8.119396] sd 2:0:0:0: [sdb] Mode Sense: 34 00 00 00                                                                        
[    8.119399] sd 2:0:0:0: [sdb] Assuming drive cache: write through                                                            
[    8.120143] sd 2:0:0:0: [sdb] 976773168 512-byte hardware sectors: (500 GB/465 GiB)                                          
[    8.121012] sd 2:0:0:0: [sdb] Write Protect is off                                                                           
[    8.121017] sd 2:0:0:0: [sdb] Mode Sense: 34 00 00 00                                                                        
[    8.121020] sd 2:0:0:0: [sdb] Assuming drive cache: write through                                                            
[    8.121031]  sdb: sdb1                                                                                                       
[    8.121921] sd 2:0:0:0: [sdb] Attached SCSI disk                                                                             
[    8.122079] sd 2:0:0:0: Attached scsi generic sg2 type 0                                                                     
[    8.363410] usb-storage: device scan complete                                                                                
[    8.364037] scsi 3:0:0:0: Direct-Access     Kingston DataTraveler 2.0 1.00 PQ: 0 ANSI: 2                                     
[    8.365736] sd 3:0:0:0: [sdc] 1994752 512-byte hardware sectors: (1.02 GB/974 MiB)                                           
[    8.366350] sd 3:0:0:0: [sdc] Write Protect is off                                                                           
[    8.366356] sd 3:0:0:0: [sdc] Mode Sense: 23 00 00 00                                                                        
[    8.366359] sd 3:0:0:0: [sdc] Assuming drive cache: write through                                                            
[    8.367983] sd 3:0:0:0: [sdc] 1994752 512-byte hardware sectors: (1.02 GB/974 MiB)                                           
[    8.368605] sd 3:0:0:0: [sdc] Write Protect is off                                                                           
[    8.368610] sd 3:0:0:0: [sdc] Mode Sense: 23 00 00 00                                                                        
[    8.368613] sd 3:0:0:0: [sdc] Assuming drive cache: write through                                                            
[    8.368626]  sdc:                                                                                                            
[    8.369546] sd 3:0:0:0: [sdc] Attached SCSI removable disk                                                                   
[    8.369695] sd 3:0:0:0: Attached scsi generic sg3 type 0                                                                     
[   12.353829] udev: starting version 141                                                                                       
[   12.829305] parport_pc 00:08: reported by Plug and Play ACPI                                                                 
[   12.829363] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]                               
[   12.989769] Linux agpgart interface v0.103                                                                                   
[   12.995529] agpgart-intel 0000:00:00.0: Intel 830M Chipset                                                                   
[   12.995879] agpgart-intel 0000:00:00.0: detected 892K stolen memory                                                          
[   12.998544] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xe8000000                                                    
[   13.722633] intel_rng: FWH not detected                                                                                      
[   13.735180] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4                                                     
[   13.762437] iTCO_vendor_support: vendor-support=0                                                                            
[   13.765186] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05                                                                  
[   13.765521] iTCO_wdt: Found a ICH4 TCO device (Version=1, TCOBASE=0x0860)                                                    
[   13.765734] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)                                                             
[   13.824168] cfg80211: Calling CRDA to update world regulatory domain                                                         
[   14.102655] ath5k_pci 0000:01:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16                                               
[   14.102859] ath5k_pci 0000:01:04.0: registered as 'phy0'                                                                     
[   14.264762] phy0: Selected rate control algorithm 'pid'                                                                      
[   14.277070] input: PC Speaker as /devices/platform/pcspkr/input/input6                                                       
[   14.490304] ath5k phy0: Atheros AR2413 chip found (MAC: 0x78, PHY: 0x45)                                                     
[   15.146022] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17                                               
[   15.146305] Intel ICH 0000:00:1f.5: setting latency timer to 64                                                              
[   15.190244] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)                                           
[   15.568083] intel8x0_measure_ac97_clock: measured 54807 usecs                                                                
[   15.568088] intel8x0: clocking to 48000                                                                                      
[   16.130096] ppdev: user-space parallel port driver                                                                           
[   16.392421] cfg80211: World regulatory domain updated:                                                                       
[   16.392429]  (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)                                               
[   16.392433]  (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)                                                    
[   16.392436]  (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)                                                    
[   16.392439]  (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)                                                    
[   16.392442]  (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)                                                    
[   16.392445]  (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)                                                    
[   17.491660] lp0: using parport0 (interrupt-driven).                                                                          
[   18.292521] Adding 1630556k swap on /dev/sda6.  Priority:-1 extents:1 across:1630556k                                        
[   19.204838] EXT3 FS on sda2, internal journal                                                                                
[   26.822713] type=1505 audit(1249139321.705:2): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2079
[   26.823047] type=1505 audit(1249139321.705:3): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2079      
[   26.823237] type=1505 audit(1249139321.705:4): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action"name2="default" pid=2079
[   26.823395] type=1505 audit(1249139321.705:5): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2079
[   27.055498] type=1505 audit(1249139321.937:6): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2084
[   27.055991] type=1505 audit(1249139321.937:7): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2084
[   27.109675] type=1505 audit(1249139321.993:8): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2088
[   30.487197] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   30.487202] Bluetooth: BNEP filters: protocol multicast
[   30.511995] Bridge firewalling registered
[   32.559405] [drm] Initialized drm 1.1.0 20060810
[   32.571527] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   32.571539] pci 0000:00:02.0: setting latency timer to 64
[   32.571903] [drm] Initialized i915 1.6.0 20080730 on minor 0
[   32.698832] [drm:i915_setparam] *ERROR* unknown parameter 4
[   32.698926] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   33.480624] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   35.119861] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   35.160404] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   37.023607] wlan0: authenticate with AP 00:21:29:b5:7e:38
[   37.025640] wlan0: authenticated
[   37.025649] wlan0: associate with AP 00:21:29:b5:7e:38
[   37.027874] wlan0: RX AssocResp from 00:21:29:b5:7e:38 (capab=0x401 status=0 aid=1)
[   37.027878] wlan0: associated
[   37.030634] wlan0: disassociating by local choice (reason=3)
```

---

### Post by bashirchacha on 2009-08-01
I think Windows 7 faster than any OS

---

### Post by LowSky on 2009-08-01
what format is the Kubuntu partition, EXT3 or EXT4, because EXT4 is much faster at data retrieval making boot times quicker.

---

### Post by DylanH on 2009-08-01
I formatted the partition to be EXT3 (I'm new at this.) 

I'd imagine that the only way to adjust that would be to reinstall Kubuntu? I might not mind reinstalling if it would translate into a significant increase in performance - what sort of speed difference are we talking here?

---

### Post by zerhacke on 2009-08-01
> **bashirchacha said:**
> I think Windows 7 faster than any OS

I can't stop laughing at this.

---

### Post by SuperSonic4 on 2009-08-01
> **DylanH said:**
> I formatted the partition to be EXT3 (I'm new at this.) 

I'd imagine that the only way to adjust that would be to reinstall Kubuntu? I might not mind reinstalling if it would translate into a significant increase in performance - what sort of speed difference are we talking here?

For me it is largely negligible

---

### Post by Durden on 2009-08-01
An OS that is 7-8 years old which was based on technology even older is going to probably be faster than Kubuntu on newer, faster hardware. Kubuntu is loading KDE which, to me, is still beta software and probably will be for several more years.

I personally don't get the KDE 4 craze. It's slow, buggy and the developers are more interested in showing off than producing anything really usable. To each their own but I'll be sticking to gnome until the bitter taste KDE 4.0 left in my mouth is washed away.

---

### Post by DylanH on 2009-08-01
> **SuperSonic4 said:**
> For me it is largely negligible

Thank you - I'll leave it as ext3 then.

---

### Post by DylanH on 2009-08-01
> **Durden said:**
> An OS that is 7-8 years old which was based on technology even older is going to probably be faster than Kubuntu on newer, faster hardware. Kubuntu is loading KDE which, to me, is still beta software and probably will be for several more years.

I personally don't get the KDE 4 craze. It's slow, buggy and the developers are more interested in showing off than producing anything really usable. To each their own but I'll be sticking to gnome until the bitter taste KDE 4.0 left in my mouth is washed away.

To its credit, the interface looks quite snazzy. But I suppose this will have varying degrees of value depending on how much weight the user places on aesthetics.

---

### Post by moster on 2009-08-01
I know from before that win7 and xp was little slow on copy small files from USB. I today was coping around 7000 pictures for my father on win7... here is what I got.

USB stick corsair voyager GT (on large files he is very fast in any os, around 20 MB/s)

winXP: 1:27 minutes
Win7: do not really know time, but it was 1-2 MB/s very slow, feels slower then XP
Ubuntu: 9.4 x86 : 31 sec (speed was around 18/MB/s)

I think anybody can check that. It was 7000 jpgs around 50 kb each, 500 MB all

---

### Post by DylanH on 2009-08-01
So, to summarize what has been suggested by others in this thread:

A clean install of XP probably has a faster startup time than Kubuntu 9.04 so I shouldn't be surprised if this is the case on my computer.

I'll assume this position is correct unless someone provides evidence to the contrary.

---

### Post by moster on 2009-08-01
It is faster. I had in virtual XP in virtualbox that could load in 25-30 sec. But after I enable internet and install little programs on it, it wait something on boot and starting to drag even when boot is complete. It is known that windows is slower with age and amout of installed programs, I am not sure how come you not see that for yourself.

---

### Post by HavocXphere on 2009-08-01
> can anyone help me figure out a solution?
I wouldn't bother trying to fix the boot times. Maybe throw out some of the services starting. You can also plot the boot on a graph...forgot the name of that app...boot something. It will take ~30 minutes to gain a few seconds. Just not worth it.

Regarding the FF boot time, you can try to use something like preload. Or investigate the database backend. Clearing out the history & cache and compacting the DB has yielded some improvements for some.

Not sure why boot-up and shutdown times are frequently brought in (Not just here, every damn review seems to have them).:confused: I boot up once per day, so whether it takes 1 or 2 mins doesn't matter.

Boot-up times largely depend on how much stuff is loaded. The OSs take very different approaches and individual configs are very different. e.g. Vista and Win& just delay some stuff and load it in the first few minutes while the user is already using the PC.

e.g. I've got an external drive which takes up ~5 sec to spin up which delays the process.

---

### Post by DylanH on 2009-08-01
> **HavocXphere said:**
>  Not sure why boot-up and shutdown times are frequently brought in (Not just here, every damn review seems to have them).:confused: I boot up once per day, so whether it takes 1 or 2 mins doesn't matter.

Boot-up times largely depend on how much stuff is loaded. The OSs take very different approaches and individual configs are very different. e.g. Vista and Win& just delay some stuff and load it in the first few minutes while the user is already using the PC.

I think these are good points to make.

---

### Post by dE_logics on 2009-08-01
> **bashirchacha said:**
> I think Windows 7 faster than any OS

There's a reason why we have a different 'league' of Linux or at least Unix type users.


Anyway, Windows 7 is of real concern to Linux...this time, responding to the competition by Linux it IS at least 'comparable'.

---

### Post by Jerry N on 2009-08-01
In my highly subjective observations, I find Win XP, Win 7 RC and Ubuntu 9.04 to be roughly equivalent to each other in speed, except for boot time where Win 7 beats the socks off both of them.  I have never used Vista so I can't compare it to the others.  My test computer is an Athlon 2400+ with 1GB RAM, Geforce 5500 AGP video, and removeable IDE drives.  Fancy video effects and "eye candy" annoy me and are turned OFF in all these operating systems.  I tried the Compiz-Fusion (confused-fission?) thing a year or so back and found it to be a real resource hog.  

Jerry

---

### Post by Durden on 2009-08-01
I'm fairly happy with my Win 7 release candidate install. It's boot time etc is pretty bad but once it's running it's fairly "out of my way" and just does what I want it to. My only complaint with Win 7 is the new taskbar which I absolutely loathe.

---

### Post by powel212 on 2009-08-01
My experience is that Kubuntu is the slowest of ubuntus to boot. But is a nice interface and highly configurable and as with all linux installs once it is booted it does not need to be shut down. Just let it run and forget about boot times.

If you just want to boot fast try Ubuntu Server.

Powel

---

### Post by jacklinux on 2009-08-01
> **bashirchacha said:**
> I think Windows 7 faster than any OS
Made me die a little inside.

---

### Post by jacklinux on 2009-08-01
> **Durden said:**
> I'm fairly happy with my Win 7 release candidate install. It's boot time etc is pretty bad but once it's running it's fairly "out of my way" and just does what I want it to. My only complaint with Win 7 is the new taskbar which I absolutely loathe.
Yeah. Also did they base 7 off of NE ir Vista?

---

### Post by Merk42 on 2009-08-01
> **Durden said:**
> I personally don't get the KDE 4 craze. It's slow, buggy and the developers are more interested in showing off than producing anything really usable. To each their own but I'll be sticking to gnome until the bitter taste KDE 4.0 left in my mouth is washed away.
> **Durden said:**
> My only complaint with Win 7 is the new taskbar which I absolutely loathe.

Seems like you don't care for change in your interface.  What are you going to do when GNOME Shell gets released?

> **jacklinux said:**
> Yeah. Also did they base 7 off of NE ir Vista?

There is no NE, there was ME, which was the last of the 95, 98 etc line. There's NT, which is the basis of NT, 2000, XP, Vista and 7.

---

### Post by Durden on 2009-08-01
> **Merk42 said:**
> Seems like you don't care for change in your interface.  What are you going to do when GNOME Shell gets released?


You extrapolate that from one post on a message forum? If you came here to troll, piss off.

---

### Post by Tamlynmac on 2009-08-01
> [zerhacke]("http://ubuntuforums.org/member.php?u=29937")
                     Originally Posted by **bashirchacha**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=7716192#post7716192")                 
                 [I]I think Windows 7 faster than any OS

[/I]
                                 I can't stop laughing at this.Why, didn't you know Windows 7 is not an OS? It's just smoke & mirrors. :P
I'm glad we have windows or the house would get real stuffy. :D

---

### Post by lancest on 2009-08-01
Wait until XP and Win 7 get the software kludge. They will be a lot slower to boot. Performance degradation is part of the MS experience.

---

### Post by 3rdalbum on 2009-08-02
If you start really using XP heavily, your startup and shutdown times will get longer. With Ubuntu and Kubuntu, you do generally get your system starting up and shutting down in the same amount of time, every time.

---

### Post by jrusso2 on 2009-08-03
Start up and shut down times are only two minor measures of system performace.

In order to really know what performs better you need to do benchmarks.

A lot of people talk about how fast windows 7 is but I have read benchmarks that only show a 5% improvement over Vista which is barely in the range of being noticble.

---

### Post by Chronon on 2009-08-03
> **moster said:**
> It is faster. I had in virtual XP in virtualbox that could load in 25-30 sec. But after I enable internet and install little programs on it, it wait something on boot and starting to drag even when boot is complete. It is known that windows is slower with age and amout of installed programs, I am not sure how come you not see that for yourself.

Booting from a VM is usually faster than booting on real hardware too (at least in my experience).

---

### Post by Tamlynmac on 2009-08-04
> jrusso2
In order to really know what performs better you need to do benchmarks.

+1

They almost never publish benchmarks and rarely perform a true analysis. Establishing benchmarks and testing systems based on hardware compatibility in an controlled environment, is (IMHO) complicated. I've read few if any reports that actually have performed an analysis (true quantitative comparison) between Windows & Ubuntu/Linux, based on multiple machines designed for each OS.

Many of the reports (I've read) were based on 2 identical machines. Instead of performing the comparison on two machines that are uniquely designed for each OS, while endeavoring to maintain machine equality. This aspect alone, would probably open the analysis to argument. Maintaining machine equality may sound simple, I suspect it could prove extremely complex. Not to mention the potential that either machine may have an unnoticed mfg flaw. Any true analysis must be the product of multiple machines.

When considering any analysis, one must not forget the human aspect - which often impacts the interruption of data. As with any analysis, the results can be skewed in an effort to advance one product over another.

When put in perspective, the majority of home desktops sold are designed specifically for Windows. Thus, purchasing two identical machines for test purposes and establishing benchmarks based on these machines is fundamentally flawed. I suspect the test results would be as expected, if not one can always skew the data. :D

Just my $0.02

---

### Post by Hallvor on 2009-08-04
> **jrusso2 said:**
> Start up and shut down times are only two minor measures of system performace.

In order to really know what performs better you need to do benchmarks.

A lot of people talk about how fast windows 7 is but I have read benchmarks that only show a 5% improvement over Vista which is barely in the range of being noticble.

QFT! :popcorn:

---

### Post by windows-killer on 2009-08-04
> **DylanH said:**
> Just wiped drive and now dual-booting a modified (some components removed) version of XP Pro SP3 and Kubuntu 9.04.

I ran some completely non-scientific tests to test boot up and shut down speed and found that XP was significantly faster in both respects. Starting at the boot menu, the time it took to log in and load Firefox: 56 seconds for Kubuntu and only 41 seconds for XP. Shutdown - same trend: 13 seconds for XP and 28 seconds for Kubuntu. What gives?

One notable feature of the Kubuntu startup/shutdown process (on my machine at any rate), is a black screen that lasts for 20 seconds. Perhaps this is the culprit? I don't recall seeing anything like this when I was booting Ubuntu or Xubuntu.

Assuming this is the problem that is causing Kubuntu to be so much slower than XP, can anyone help me figure out a solution? Please let me know what information would be of use and I'll provide it ASAP!

Please help!

:confused:

-----

[edit: below is the output of dmesg]

```
[    0.000000] BIOS EBDA/lowmem at: 0009fc00/0009fc00
[    0.000000] Initializing cgroup subsys cpuset     
[    0.000000] Initializing cgroup subsys cpu        
[    0.000000] Linux version 2.6.28-11-generic (buildd@palmer) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 (Ubuntu 2.6.28-11.42-generic)                                                                           
[    0.000000] KERNEL supported cpus:                                                                                           
[    0.000000]   Intel GenuineIntel                                                                                             
[    0.000000]   AMD AuthenticAMD                                                                                               
[    0.000000]   NSC Geode by NSC                                                                                               
[    0.000000]   Cyrix CyrixInstead                                                                                             
[    0.000000]   Centaur CentaurHauls                                                                                           
[    0.000000]   Transmeta GenuineTMx86                                                                                         
[    0.000000]   Transmeta TransmetaCPU                                                                                         
[    0.000000]   UMC UMC UMC UMC                                                                                                
[    0.000000] BIOS-provided physical RAM map:                                                                                  
[    0.000000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)                                                         
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)                                                       
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fe74000 (usable)                                                         
[    0.000000]  BIOS-e820: 000000003fe74000 - 000000003fe76000 (ACPI NVS)                                                       
[    0.000000]  BIOS-e820: 000000003fe76000 - 000000003fe97000 (ACPI data)                                                      
[    0.000000]  BIOS-e820: 000000003fe97000 - 000000003ff00000 (reserved)                                                       
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)                                                       
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)                                                       
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)                                                       
[    0.000000] DMI 2.3 present.                                                                                                 
[    0.000000] last_pfn = 0x3fe74 max_arch_pfn = 0x100000                                                                       
[    0.000000] Scanning 2 areas for low memory corruption                                                                       
[    0.000000] modified physical RAM map:                                                                                       
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)                                                          
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)                                                        
[    0.000000]  modified: 0000000000006000 - 0000000000007000 (usable)                                                          
[    0.000000]  modified: 0000000000007000 - 0000000000010000 (reserved)                                                        
[    0.000000]  modified: 0000000000010000 - 0000000000093000 (usable)                                                          
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)                                                        
[    0.000000]  modified: 0000000000100000 - 000000003fe74000 (usable)                                                          
[    0.000000]  modified: 000000003fe74000 - 000000003fe76000 (ACPI NVS)                                                        
[    0.000000]  modified: 000000003fe76000 - 000000003fe97000 (ACPI data)                                                       
[    0.000000]  modified: 000000003fe97000 - 000000003ff00000 (reserved)                                                        
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)                                                        
[    0.000000]  modified: 00000000fee00000 - 00000000fee10000 (reserved)                                                        
[    0.000000]  modified: 00000000ffb00000 - 0000000100000000 (reserved)                                                        
[    0.000000] kernel direct mapping tables up to 373fe000 @ 10000-16000                                                        
[    0.000000] RAMDISK: 378bf000 - 37fef253                                                                                     
[    0.000000] Allocated new RAMDISK: 00881000 - 00fb1253                                                                       
[    0.000000] Move RAMDISK from 00000000378bf000 - 0000000037fef252 to 00881000 - 00fb1252                                     
[    0.000000] ACPI: RSDP 000FEB80, 0014 (r0 DELL  )                                                                            
[    0.000000] ACPI: RSDT 000FD22A, 0034 (r1 DELL    2400           7 ASL        61)                                            
[    0.000000] ACPI: FACP 000FD25E, 0074 (r1 DELL    2400           7 ASL        61)                                            
[    0.000000] ACPI: DSDT FFFCC0F1, 2404 (r1   DELL    dt_ex     1000 MSFT  100000D)                                            
[    0.000000] ACPI: FACS 3FE74000, 0040                                                                                        
[    0.000000] ACPI: SSDT FFFCE632, 00BA (r1   DELL    st_ex     1000 MSFT  100000D)                                            
[    0.000000] ACPI: APIC 000FD2D2, 006C (r1 DELL    2400           7 ASL        61)                                            
[    0.000000] ACPI: BOOT 000FD33E, 0028 (r1 DELL    2400           7 ASL        61)                                            
[    0.000000] ACPI: Local APIC address 0xfee00000                                                                              
[    0.000000] 138MB HIGHMEM available.                                                                                         
[    0.000000] 883MB LOWMEM available.                                                                                          
[    0.000000]   mapped low ram: 0 - 373fe000                                                                                   
[    0.000000]   low ram: 00000000 - 373fe000                                                                                   
[    0.000000]   bootmap 00012000 - 00018e80                                                                                    
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00373fe000]                                                     
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]                                    
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]                                    
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]                                    
[    0.000000]   #3 [0000100000 - 000087c52c]    TEXT DATA BSS ==> [0000100000 - 000087c52c]                                    
[    0.000000]   #4 [000087d000 - 0000881000]    INIT_PG_TABLE ==> [000087d000 - 0000881000]                                    
[    0.000000]   #5 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]                                    
[    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]                                    
[    0.000000]   #7 [0000881000 - 0000fb1253]      NEW RAMDISK ==> [0000881000 - 0000fb1253]                                    
[    0.000000]   #8 [0000012000 - 0000019000]          BOOTMAP ==> [0000012000 - 0000019000]                                    
[    0.000000] found SMP MP-table at [c00fe710] 000fe710                                                                        
[    0.000000] Zone PFN ranges:                                                                                                 
[    0.000000]   DMA      0x00000000 -> 0x00001000                                                                              
[    0.000000]   Normal   0x00001000 -> 0x000373fe                                                                              
[    0.000000]   HighMem  0x000373fe -> 0x0003fe74                                                                              
[    0.000000] Movable zone start PFN for each node                                                                             
[    0.000000] early_node_map[4] active PFN ranges                                                                              
[    0.000000]     0: 0x00000000 -> 0x00000002                                                                                  
[    0.000000]     0: 0x00000006 -> 0x00000007                                                                                  
[    0.000000]     0: 0x00000010 -> 0x00000093                                                                                  
[    0.000000]     0: 0x00000100 -> 0x0003fe74                                                                                  
[    0.000000] On node 0 totalpages: 261626                                                                                     
[    0.000000] free_area_init_node: node 0, pgdat c06d0f80, node_mem_map c1000000                                               
[    0.000000]   DMA zone: 32 pages used for memmap                                                                             
[    0.000000]   DMA zone: 0 pages reserved                                                                                     
[    0.000000]   DMA zone: 3942 pages, LIFO batch:0                                                                             
[    0.000000]   Normal zone: 1736 pages used for memmap                                                                        
[    0.000000]   Normal zone: 220470 pages, LIFO batch:31                                                                       
[    0.000000]   HighMem zone: 277 pages used for memmap                                                                        
[    0.000000]   HighMem zone: 35169 pages, LIFO batch:7                                                                        
[    0.000000]   Movable zone: 0 pages used for memmap                                                                          
[    0.000000] ACPI: PM-Timer IO Port: 0x808                                                                                    
[    0.000000] ACPI: Local APIC address 0xfee00000                                                                              
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)                                                               
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] disabled)                                                              
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] disabled)                                                              
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] disabled)                                                              
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])                                                          
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23                                                   
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)                                                         
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)                                                      
[    0.000000] ACPI: IRQ0 used by override.                                                                                     
[    0.000000] ACPI: IRQ2 used by override.                                                                                     
[    0.000000] ACPI: IRQ9 used by override.                                                                                     
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs                                                                    
[    0.000000] Using ACPI (MADT) for SMP configuration information                                                              
[    0.000000] SMP: Allowing 4 CPUs, 3 hotplug CPUs                                                                             
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000                                                
[    0.000000] PM: Registered nosave memory: 0000000000007000 - 0000000000010000                                                
[    0.000000] PM: Registered nosave memory: 0000000000093000 - 00000000000f0000                                                
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000                                                
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 3ff00000:bed00000)                                           
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data                                                                   
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1                                                                        
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 259581                                      
[    0.000000] Kernel command line: root=UUID=c9352583-3e64-4fd5-8229-912314373bde ro quiet splash                              
[    0.000000] Enabling fast FPU save and restore... done.                                                                      
[    0.000000] Enabling unmasked SIMD FPU exception support... done.                                                            
[    0.000000] Initializing CPU#0                                                                                               
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)                                                            
[    0.000000] TSC: PIT calibration matches PMTIMER. 1 loops                                                                    
[    0.000000] Detected 2392.220 MHz processor.                                                                                 
[    0.004000] Console: colour VGA+ 80x25                                                                                       
[    0.004000] console [tty0] enabled                                                                                           
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)                                                 
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)                                                   
[    0.004000] allocated 5234960 bytes of page_cgroup                                                                           
[    0.004000] please try cgroup_disable=memory option if you don't want                                                        
[    0.004000] Scanning for low memory corruption every 60 seconds                                                              
[    0.004000] Memory: 1016800k/1046992k available (4126k kernel code, 29380k reserved, 2208k data, 532k init, 141784k highmem) 
[    0.004000] virtual kernel memory layout:                                                                                    
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)                                                                
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)                                                                
[    0.004000]     vmalloc : 0xf7bfe000 - 0xff3fe000   ( 120 MB)                                                                
[    0.004000]     lowmem  : 0xc0000000 - 0xf73fe000   ( 883 MB)                                                                
[    0.004000]       .init : 0xc0737000 - 0xc07bc000   ( 532 kB)                                                                
[    0.004000]       .data : 0xc0507a6f - 0xc072fe60   (2208 kB)                                                                
[    0.004000]       .text : 0xc0100000 - 0xc0507a6f   (4126 kB)                                                                
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.                                      
[    0.004000] SLUB: Genslabs=12, HWalign=128, Order=0-3, MinObjects=0, CPUs=4, Nodes=1                                         
[    0.004020] Calibrating delay loop (skipped), value calculated using timer frequency.. 4784.44 BogoMIPS (lpj=9568880)        
[    0.004056] Security Framework initialized                                                                                   
[    0.004073] SELinux:  Disabled at boot.                                                                                      
[    0.004108] AppArmor: AppArmor initialized                                                                                   
[    0.004132] Mount-cache hash table entries: 512                                                                              
[    0.004412] Initializing cgroup subsys ns                                                                                    
[    0.004424] Initializing cgroup subsys cpuacct                                                                               
[    0.004431] Initializing cgroup subsys memory                                                                                
[    0.004441] Initializing cgroup subsys freezer                                                                               
[    0.004472] CPU: Trace cache: 12K uops, L1 D cache: 8K                                                                       
[    0.004479] CPU: L2 cache: 128K                                                                                              
[    0.004485] CPU: Hyper-Threading is disabled                                                                                 
[    0.004514] Checking 'hlt' instruction... OK.                                                                                
[    0.020911] SMP alternatives: switching to UP code                                                                           
[    0.212041] ACPI: Core revision 20080926                                                                                     
[    0.227662] ACPI: Checking initramfs for custom DSDT                                                                         
[    0.598198] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1                                                             
[    0.637896] CPU0: Intel(R) Celeron(R) CPU 2.40GHz stepping 09                                                                
[    0.640002] Brought up 1 CPUs                                                                                                
[    0.640002] Total of 1 processors activated (4784.44 BogoMIPS).                                                              
[    0.640002] CPU0 attaching NULL sched-domain.                                                                                
[    0.640002] net_namespace: 776 bytes                                                                                         
[    0.640002] Booting paravirtualized kernel on bare hardware                                                                  
[    0.640002] Time: 11:08:15  Date: 08/01/09                                                                                   
[    0.640002] regulator: core version 0.5                                                                                      
[    0.640002] NET: Registered protocol family 16                                                                               
[    0.640002] EISA bus registered                                                                                              
[    0.640002] ACPI: bus type pci registered                                                                                    
[    0.640002] PCI: PCI BIOS revision 2.10 entry at 0xfbbbf, last bus=1                                                         
[    0.640002] PCI: Using configuration type 1 for base access                                                                  
[    0.641960] ACPI: EC: Look up EC in DSDT                                                                                     
[    0.672452] ACPI: Interpreter enabled                                                                                        
[    0.672463] ACPI: (supports S0 S1 S3 S4 S5)                                                                                  
[    0.672496] ACPI: Using IOAPIC for interrupt routing                                                                         
[    0.708108] ACPI: No dock devices found.                                                                                     
[    0.708134] ACPI: PCI Root Bridge [PCI0] (0000:00)                                                                           
[    0.708224] pci 0000:00:00.0: reg 10 32bit mmio: [0xf0000000-0xf7ffffff]                                                     
[    0.708305] pci 0000:00:02.0: reg 10 32bit mmio: [0xe8000000-0xefffffff]                                                     
[    0.708314] pci 0000:00:02.0: reg 14 32bit mmio: [0xfeb80000-0xfebfffff]                                                     
[    0.708430] pci 0000:00:1d.0: reg 20 io port: [0xff80-0xff9f]                                                                
[    0.708488] pci 0000:00:1d.1: reg 20 io port: [0xff60-0xff7f]                                                                
[    0.708546] pci 0000:00:1d.2: reg 20 io port: [0xff40-0xff5f]                                                                
[    0.708613] pci 0000:00:1d.7: reg 10 32bit mmio: [0xffa80800-0xffa80bff]                                                     
[    0.708663] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold                                                            
[    0.708669] pci 0000:00:1d.7: PME# disabled                                                                                  
[    0.708723] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,                                               
[    0.708724] * this clock source is slow. If you are sure your timer does not have                                            
[    0.708727] * this bug, please use "acpi_pm_good" to disable the workaround                                                  
[    0.708772] HPET not enabled in BIOS. You might try hpet=force boot option                                                   
[    0.708782] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO                                          
[    0.708787] pci 0000:00:1f.0: quirk: region 0880-08bf claimed by ICH4 GPIO                                                   
[    0.708811] pci 0000:00:1f.1: reg 10 io port: [0x1f0-0x1f7]                                                                  
[    0.708821] pci 0000:00:1f.1: reg 14 io port: [0x3f4-0x3f7]                                                                  
[    0.708829] pci 0000:00:1f.1: reg 18 io port: [0x170-0x177]                                                                  
[    0.708837] pci 0000:00:1f.1: reg 1c io port: [0x374-0x377]                                                                  
[    0.708845] pci 0000:00:1f.1: reg 20 io port: [0xffa0-0xffaf]                                                                
[    0.708854] pci 0000:00:1f.1: reg 24 32bit mmio: [0xfeb7fc00-0xfeb7ffff]                                                     
[    0.708911] pci 0000:00:1f.3: reg 20 io port: [0xeda0-0xedbf]                                                                
[    0.708961] pci 0000:00:1f.5: reg 10 io port: [0xee00-0xeeff]                                                                
[    0.708969] pci 0000:00:1f.5: reg 14 io port: [0xedc0-0xedff]                                                                
[    0.708977] pci 0000:00:1f.5: reg 18 32bit mmio: [0xfeb7fa00-0xfeb7fbff]                                                     
[    0.708986] pci 0000:00:1f.5: reg 1c 32bit mmio: [0xfeb7f900-0xfeb7f9ff]                                                     
[    0.709012] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold                                                            
[    0.709017] pci 0000:00:1f.5: PME# disabled                                                                                  
[    0.709080] pci 0000:01:04.0: reg 10 32bit mmio: [0xfe9f0000-0xfe9fffff]                                                     
[    0.709161] pci 0000:01:09.0: reg 10 32bit mmio: [0xfe9ee000-0xfe9effff]                                                     
[    0.709193] pci 0000:01:09.0: reg 30 32bit mmio: [0xfea00000-0xfea03fff]                                                     
[    0.709204] pci 0000:01:09.0: supports D1 D2                                                                                 
[    0.709207] pci 0000:01:09.0: PME# supported from D0 D1 D2 D3hot D3cold                                                      
[    0.709212] pci 0000:01:09.0: PME# disabled                                                                                  
[    0.709248] pci 0000:00:1e.0: transparent bridge                                                                             
[    0.709257] pci 0000:00:1e.0: bridge 32bit mmio: [0xfe900000-0xfeafffff]                                                     
[    0.709271] bus 00 -> node 0                                                                                                 
[    0.709290] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]                                                              
[    0.709901] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]                                                         
[    0.876593] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 15)                                                  
[    0.876977] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 7 9 10 11 12 15)                                                  
[    0.877363] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 15)                                                  
[    0.877740] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 *10 11 12 15)                                                  
[    0.878129] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.                                     
[    0.878513] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.                                     
[    0.878896] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.                                     
[    0.879286] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 9 10 11 12 15)                                                  
[    0.879556] ACPI: WMI: Mapper loaded                                                                                         
[    0.879995] SCSI subsystem initialized                                                                                       
[    0.880139] libata version 3.00 loaded.                                                                                      
[    0.880284] usbcore: registered new interface driver usbfs                                                                   
[    0.880325] usbcore: registered new interface driver hub                                                                     
[    0.880426] usbcore: registered new device driver usb                                                                        
[    0.880779] PCI: Using ACPI for IRQ routing                                                                                  
[    0.880942] Bluetooth: Core ver 2.13                                                                                         
[    0.880942] NET: Registered protocol family 31                                                                               
[    0.880942] Bluetooth: HCI device and connection manager initialized                                                         
[    0.880942] Bluetooth: HCI socket layer initialized                                                                          
[    0.880942] NET: Registered protocol family 8                                                                                
[    0.880942] NET: Registered protocol family 20                                                                               
[    0.880942] NetLabel: Initializing                                                                                           
[    0.880942] NetLabel:  domain hash size = 128                                                                                
[    0.880942] NetLabel:  protocols = UNLABELED CIPSOv4                                                                         
[    0.880942] NetLabel:  unlabeled traffic allowed by default                                                                  
[    0.880942] AppArmor: AppArmor Filesystem Enabled                                                                            
[    0.880942] pnp: PnP ACPI init                                                                                               
[    0.880942] ACPI: bus type pnp registered                                                                                    
[    0.904968] pnp 00:09: io resource (0x800-0x85f) overlaps 0000:00:1f.0 BAR 7 (0x800-0x87f), disabling                        
[    0.904975] pnp 00:09: io resource (0x860-0x8ff) overlaps 0000:00:1f.0 BAR 7 (0x800-0x87f), disabling                        
[    0.905865] pnp: PnP ACPI: found 10 devices                                                                                  
[    0.905871] ACPI: ACPI bus type pnp unregistered                                                                             
[    0.905878] PnPBIOS: Disabled by ACPI PNP                                                                                    
[    0.905903] system 00:00: iomem range 0x0-0x9ffff could not be reserved                                                      
[    0.905908] system 00:00: iomem range 0x100000-0xffffff could not be reserved                                                
[    0.905912] system 00:00: iomem range 0x1000000-0x3fe73fff could not be reserved                                             
[    0.905916] system 00:00: iomem range 0xc0000-0xfffff could not be reserved                                                  
[    0.905921] system 00:00: iomem range 0xfec00000-0xfec0ffff has been reserved                                                
[    0.905925] system 00:00: iomem range 0xfee00000-0xfee0ffff has been reserved                                                
[    0.905929] system 00:00: iomem range 0xfecf0000-0xfecf0fff has been reserved                                                
[    0.905933] system 00:00: iomem range 0xffb00000-0xffbfffff has been reserved                                                
[    0.905937] system 00:00: iomem range 0xffc00000-0xffffffff has been reserved                                                
[    0.905956] system 00:09: ioport range 0xc00-0xc7f has been reserved                                                         
[    0.940950] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:01                                                              
[    0.940954] pci 0000:00:1e.0:   IO window: disabled                                                                          
[    0.940961] pci 0000:00:1e.0:   MEM window: 0xfe900000-0xfeafffff                                                            
[    0.940967] pci 0000:00:1e.0:   PREFETCH window: 0x00000040000000-0x000000400fffff                                           
[    0.940988] pci 0000:00:1e.0: setting latency timer to 64                                                                    
[    0.940994] bus: 00 index 0 io port: [0x00-0xffff]                                                                           
[    0.940998] bus: 00 index 1 mmio: [0x000000-0xffffffff]                                                                      
[    0.941001] bus: 01 index 0 mmio: [0x0-0x0]                                                                                  
[    0.941004] bus: 01 index 1 mmio: [0xfe900000-0xfeafffff]                                                                    
[    0.941007] bus: 01 index 2 mmio: [0x40000000-0x400fffff]                                                                    
[    0.941010] bus: 01 index 3 io port: [0x00-0xffff]                                                                           
[    0.941014] bus: 01 index 4 mmio: [0x000000-0xffffffff]                                                                      
[    0.941041] NET: Registered protocol family 2                                                                                
[    0.941259] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)                                                
[    0.941789] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)                                             
[    0.943420] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)                                                      
[    0.944234] TCP: Hash tables configured (established 131072 bind 65536)                                                      
[    0.944241] TCP reno registered                                                                                              
[    0.944502] NET: Registered protocol family 1                                                                                
[    0.944710] checking if image is initramfs... it is                                                                          
[    1.444059] Switched to high resolution mode on CPU 0                                                                        
[    1.727514] Freeing initrd memory: 7360k freed                                                                               
[    1.727593] Simple Boot Flag value 0x87 read from CMOS RAM was invalid                                                       
[    1.727597] Simple Boot Flag at 0x7a set to 0x1                                                                              
[    1.727647] cpufreq: No nForce2 chipset.                                                                                     
[    1.727933] audit: initializing netlink socket (disabled)                                                                    
[    1.727961] type=2000 audit(1249124895.724:1): initialized                                                                   
[    1.735556] highmem bounce pool size: 64 pages                                                                               
[    1.735568] HugeTLB registered 4 MB page size, pre-allocated 0 pages                                                         
[    1.737560] VFS: Disk quotas dquot_6.5.1                                                                                     
[    1.737693] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)                                                       
[    1.739002] fuse init (API version 7.10)                                                                                     
[    1.739224] msgmni has been set to 1724                                                                                      
[    1.739654] alg: No test for stdrng (krng)                                                                                   
[    1.739705] io scheduler noop registered                                                                                     
[    1.739709] io scheduler anticipatory registered                                                                             
[    1.739711] io scheduler deadline registered                                                                                 
[    1.739768] io scheduler cfq registered (default)                                                                            
[    1.739791] pci 0000:00:02.0: Boot video device                                                                              
[    1.759761] pci_hotplug: PCI Hot Plug PCI Core version: 0.5                                                                  
[    1.759780] pciehp: PCI Express Hot Plug Controller Driver version: 0.4                                                      
[    1.760041] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0                                        
[    1.760047] ACPI: Power Button (FF) [PWRF]                                                                                   
[    1.760139] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1                               
[    1.760150] ACPI: Power Button (CM) [VBTN]                                                                                   
[    1.760615] processor ACPI_CPU:00: registered as cooling_device0                                                             
[    1.786445] isapnp: Scanning for PnP cards...                                                                                
[    2.140441] isapnp: No Plug & Play device found                                                                              
[    2.143466] Serial: 8250/16550 driver4 ports, IRQ sharing enabled                                                            
[    2.143596] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A                                                             
[    2.144229] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A                                                                  
[    2.146047] brd: module loaded                                                                                               
[    2.146976] loop: module loaded                                                                                              
[    2.147196] Fixed MDIO Bus: probed                                                                                           
[    2.147207] PPP generic driver version 2.4.2                                                                                 
[    2.147344] input: Macintosh mouse button emulation as /devices/virtual/input/input2                                         
[    2.147411] Driver 'sd' needs updating - please use bus_type methods                                                         
[    2.147433] Driver 'sr' needs updating - please use bus_type methods                                                         
[    2.147592] ata_piix 0000:00:1f.1: version 2.12                                                                              
[    2.147621] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18                                                
[    2.147696] ata_piix 0000:00:1f.1: setting latency timer to 64                                                               
[    2.147890] scsi0 : ata_piix                                                                                                 
[    2.148174] scsi1 : ata_piix                                                                                                 
[    2.148275] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14                                                  
[    2.148280] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15                                                  
[    2.320630] ata1.00: ATA-6: HDS722540VLAT20, V31OA69A, max UDMA/100                                                          
[    2.320636] ata1.00: 78125000 sectors, multi 8: LBA48                                                                        
[    2.344619] ata1.00: configured for UDMA/100                                                                                 
[    2.508763] ata2.00: ATAPI: GCR-8483B, 1.05, max UDMA/33                                                                     
[    2.524770] ata2.00: configured for UDMA/33                                                                                  
[    2.525160] scsi 0:0:0:0: Direct-Access     ATA      HDS722540VLAT20  V31O PQ: 0 ANSI: 5                                     
[    2.525450] sd 0:0:0:0: [sda] 78125000 512-byte hardware sectors: (40.0 GB/37.2 GiB)                                         
[    2.525519] sd 0:0:0:0: [sda] Write Protect is off                                                                           
[    2.525523] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00                                                                        
[    2.525629] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA                          
[    2.525828] sd 0:0:0:0: [sda] 78125000 512-byte hardware sectors: (40.0 GB/37.2 GiB)                                         
[    2.525894] sd 0:0:0:0: [sda] Write Protect is off                                                                           
[    2.525898] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00                                                                        
[    2.526003] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA                          
[    2.526014]  sda: sda1 sda2 sda3 < sda5 sda6 >                                                                               
[    2.576850] sd 0:0:0:0: [sda] Attached SCSI disk                                                                             
[    2.576985] sd 0:0:0:0: Attached scsi generic sg0 type 0                                                                     
[    2.579728] scsi 1:0:0:0: CD-ROM            HL-DT-ST CD-ROM GCR-8483B 1.05 PQ: 0 ANSI: 5                                     
[    2.585673] sr0: scsi3-mmc drive: 48x/48x cd/rw xa/form2 cdda tray                                                           
[    2.585681] Uniform CD-ROM driver Revision: 3.20                                                                             
[    2.585895] sr 1:0:0:0: Attached scsi CD-ROM sr0                                                                             
[    2.586031] sr 1:0:0:0: Attached scsi generic sg1 type 5                                                                     
[    2.587528] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver                                                       
[    2.587591] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23                                                
[    2.587634] ehci_hcd 0000:00:1d.7: setting latency timer to 64                                                               
[    2.587641] ehci_hcd 0000:00:1d.7: EHCI Host Controller                                                                      
[    2.587812] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1                                             
[    2.591767] ehci_hcd 0000:00:1d.7: debug port 1                                                                              
[    2.591777] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported                                                   
[    2.591806] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xffa80800                                                                 
[    2.604021] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00                                                                
[    2.604191] usb usb1: configuration #1 chosen from 1 choice                                                                  
[    2.604253] hub 1-0:1.0: USB hub found                                                                                       
[    2.604275] hub 1-0:1.0: 6 ports detected                                                                                    
[    2.604547] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver                                                           
[    2.604596] uhci_hcd: USB Universal Host Controller Interface driver                                                         
[    2.604693] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16                                                
[    2.604710] uhci_hcd 0000:00:1d.0: setting latency timer to 64                                                               
[    2.604716] uhci_hcd 0000:00:1d.0: UHCI Host Controller                                                                      
[    2.604852] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2                                             
[    2.604900] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000ff80                                                                
[    2.605076] usb usb2: configuration #1 chosen from 1 choice                                                                  
[    2.605136] hub 2-0:1.0: USB hub found                                                                                       
[    2.605156] hub 2-0:1.0: 2 ports detected                                                                                    
[    2.605384] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19                                                
[    2.605399] uhci_hcd 0000:00:1d.1: setting latency timer to 64                                                               
[    2.605405] uhci_hcd 0000:00:1d.1: UHCI Host Controller                                                                      
[    2.605530] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3                                             
[    2.605584] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000ff60                                                                
[    2.605750] usb usb3: configuration #1 chosen from 1 choice                                                                  
[    2.605807] hub 3-0:1.0: USB hub found                                                                                       
[    2.605828] hub 3-0:1.0: 2 ports detected                                                                                    
[    2.606050] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18                                                
[    2.606064] uhci_hcd 0000:00:1d.2: setting latency timer to 64                                                               
[    2.606069] uhci_hcd 0000:00:1d.2: UHCI Host Controller                                                                      
[    2.606196] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4                                             
[    2.606245] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000ff40                                                                
[    2.606409] usb usb4: configuration #1 chosen from 1 choice                                                                  
[    2.606479] hub 4-0:1.0: USB hub found                                                                                       
[    2.606501] hub 4-0:1.0: 2 ports detected                                                                                    
[    2.606791] usbcore: registered new interface driver libusual                                                                
[    2.606880] usbcore: registered new interface driver usbserial                                                               
[    2.606904] USB Serial support registered for generic                                                                        
[    2.606936] usbcore: registered new interface driver usbserial_generic                                                       
[    2.606940] usbserial: USB Serial Driver core                                                                                
[    2.607033] PNP: No PS/2 controller found. Probing ports directly.                                                           
[    2.610050] serio: i8042 KBD port at 0x60,0x64 irq 1                                                                         
[    2.610064] serio: i8042 AUX port at 0x60,0x64 irq 12                                                                        
[    2.610397] mice: PS/2 mouse device common for all mice                                                                      
[    2.610777] rtc_cmos 00:05: RTC can wake from S4                                                                             
[    2.610881] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0                                                            
[    2.610915] rtc0: alarms up to one day, 242 bytes nvram                                                                      
[    2.611064] device-mapper: uevent: version 1.0.3                                                                             
[    2.611391] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]                                 
[    2.611575] device-mapper: multipath: version 1.0.5 loaded                                                                   
[    2.611582] device-mapper: multipath round-robin: version 1.0.0 loaded                                                       
[    2.611846] EISA: Probing bus 0 at eisa.0                                                                                    
[    2.611888] EISA: Detected 0 cards.                                                                                          
[    2.611986] cpuidle: using governor ladder                                                                                   
[    2.611990] cpuidle: using governor menu                                                                                     
[    2.612786] TCP cubic registered                                                                                             
[    2.612963] NET: Registered protocol family 10                                                                               
[    2.613677] lo: Disabled Privacy Extensions                                                                                  
[    2.614134] NET: Registered protocol family 17                                                                               
[    2.614203] Bluetooth: L2CAP ver 2.11                                                                                        
[    2.614206] Bluetooth: L2CAP socket layer initialized                                                                        
[    2.614211] Bluetooth: SCO (Voice Link) ver 0.6                                                                              
[    2.614214] Bluetooth: SCO socket layer initialized                                                                          
[    2.614323] Bluetooth: RFCOMM socket layer initialized                                                                       
[    2.614348] Bluetooth: RFCOMM TTY layer initialized                                                                          
[    2.614351] Bluetooth: RFCOMM ver 1.10                                                                                       
[    2.614467] Using IPI No-Shortcut mode                                                                                       
[    2.614693] registered taskstats version 1                                                                                   
[    2.614875]   Magic number: 5:316:124                                                                                        
[    2.614982] rtc_cmos 00:05: setting system clock to 2009-08-01 11:08:17 UTC (1249124897)                                     
[    2.614988] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found                                                             
[    2.614990] EDD information not available.                                                                                   
[    2.615888] Freeing unused kernel memory: 532k freed                                                                         
[    2.616097] Write protecting the kernel text: 4128k                                                                          
[    2.616147] Write protecting the kernel read-only data: 1532k                                                                
[    2.916048] usb 1-3: new high speed USB device using ehci_hcd and address 2                                                  
[    3.065037] usb 1-3: configuration #1 chosen from 1 choice                                                                   
[    3.091594] Initializing USB Mass Storage driver...                                                                          
[    3.099339] scsi2 : SCSI emulation for USB Mass Storage devices                                                              
[    3.118729] usbcore: registered new interface driver usb-storage                                                             
[    3.118737] USB Mass Storage support registered.                                                                             
[    3.118951] usb-storage: device found at 2                                                                                   
[    3.118956] usb-storage: waiting for device to settle before scanning                                                        
[    3.200130] usb 1-5: new high speed USB device using ehci_hcd and address 3                                                  
[    3.303870] FDC 0 is a post-1991 82077                                                                                       
[    3.334764] usb 1-5: configuration #1 chosen from 1 choice                                                                   
[    3.340533] scsi3 : SCSI emulation for USB Mass Storage devices                                                              
[    3.349301] usb-storage: device found at 3                                                                                   
[    3.349306] usb-storage: waiting for device to settle before scanning                                                        
[    3.644072] usb 4-2: new low speed USB device using uhci_hcd and address 2                                                   
[    3.718783] b44 0000:01:09.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17                                                     
[    3.780163] ssb: Sonics Silicon Backplane found on PCI device 0000:01:09.0                                                   
[    3.780215] b44.c:v2.0                                                                                                       
[    3.801029] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:0f:1f:7b:ce:1a                                                  
[    3.909267] usb 4-2: configuration #1 chosen from 1 choice                                                                   
[    5.628915] usbcore: registered new interface driver hiddev                                                                  
[    5.673413] input: BTC USB Multimedia Cordless Kit as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.0/input/input3         
[    5.756208] generic-usb 0003:046E:5520.0001: input,hidraw0: USB HID v1.10 Keyboard [BTC USB Multimedia Cordless Kit] on usb-0000:00:1d.2-2/input0                                                                                                            
[    5.790303] input: BTC USB Multimedia Cordless Kit as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.1/input/input4         
[    5.836212] generic-usb 0003:046E:5520.0002: input,hidraw1: USB HID v1.10 Mouse [BTC USB Multimedia Cordless Kit] on usb-0000:00:1d.2-2/input1                                                                                                               
[    5.973925] input: BTC USB Multimedia Cordless Kit as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.2/input/input5         
[    6.036196] generic-usb 0003:046E:5520.0003: input,hidraw2: USB HID v1.10 Device [BTC USB Multimedia Cordless Kit] on usb-0000:00:1d.2-2/input2                                                                                                              
[    6.036235] usbcore: registered new interface driver usbhid                                                                  
[    6.036242] usbhid: v2.6:USB HID core driver                                                                                 
[    6.477063] PM: Starting manual resume from disk                                                                             
[    6.477070] PM: Resume from partition 8:6                                                                                    
[    6.477072] PM: Checking hibernation image.                                                                                  
[    6.477320] PM: Resume from disk failed.                                                                                     
[    6.556050] kjournald starting.  Commit interval 5 seconds                                                                   
[    6.556079] EXT3-fs: mounted filesystem with ordered data mode.                                                              
[    8.116355] usb-storage: device scan complete                                                                                
[    8.116916] scsi 2:0:0:0: Direct-Access     SAMSUNG  HD502IJ               PQ: 0 ANSI: 2 CCS                                 
[    8.118521] sd 2:0:0:0: [sdb] 976773168 512-byte hardware sectors: (500 GB/465 GiB)                                          
[    8.119390] sd 2:0:0:0: [sdb] Write Protect is off                                                                           
[    8.119396] sd 2:0:0:0: [sdb] Mode Sense: 34 00 00 00                                                                        
[    8.119399] sd 2:0:0:0: [sdb] Assuming drive cache: write through                                                            
[    8.120143] sd 2:0:0:0: [sdb] 976773168 512-byte hardware sectors: (500 GB/465 GiB)                                          
[    8.121012] sd 2:0:0:0: [sdb] Write Protect is off                                                                           
[    8.121017] sd 2:0:0:0: [sdb] Mode Sense: 34 00 00 00                                                                        
[    8.121020] sd 2:0:0:0: [sdb] Assuming drive cache: write through                                                            
[    8.121031]  sdb: sdb1                                                                                                       
[    8.121921] sd 2:0:0:0: [sdb] Attached SCSI disk                                                                             
[    8.122079] sd 2:0:0:0: Attached scsi generic sg2 type 0                                                                     
[    8.363410] usb-storage: device scan complete                                                                                
[    8.364037] scsi 3:0:0:0: Direct-Access     Kingston DataTraveler 2.0 1.00 PQ: 0 ANSI: 2                                     
[    8.365736] sd 3:0:0:0: [sdc] 1994752 512-byte hardware sectors: (1.02 GB/974 MiB)                                           
[    8.366350] sd 3:0:0:0: [sdc] Write Protect is off                                                                           
[    8.366356] sd 3:0:0:0: [sdc] Mode Sense: 23 00 00 00                                                                        
[    8.366359] sd 3:0:0:0: [sdc] Assuming drive cache: write through                                                            
[    8.367983] sd 3:0:0:0: [sdc] 1994752 512-byte hardware sectors: (1.02 GB/974 MiB)                                           
[    8.368605] sd 3:0:0:0: [sdc] Write Protect is off                                                                           
[    8.368610] sd 3:0:0:0: [sdc] Mode Sense: 23 00 00 00                                                                        
[    8.368613] sd 3:0:0:0: [sdc] Assuming drive cache: write through                                                            
[    8.368626]  sdc:                                                                                                            
[    8.369546] sd 3:0:0:0: [sdc] Attached SCSI removable disk                                                                   
[    8.369695] sd 3:0:0:0: Attached scsi generic sg3 type 0                                                                     
[   12.353829] udev: starting version 141                                                                                       
[   12.829305] parport_pc 00:08: reported by Plug and Play ACPI                                                                 
[   12.829363] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]                               
[   12.989769] Linux agpgart interface v0.103                                                                                   
[   12.995529] agpgart-intel 0000:00:00.0: Intel 830M Chipset                                                                   
[   12.995879] agpgart-intel 0000:00:00.0: detected 892K stolen memory                                                          
[   12.998544] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xe8000000                                                    
[   13.722633] intel_rng: FWH not detected                                                                                      
[   13.735180] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4                                                     
[   13.762437] iTCO_vendor_support: vendor-support=0                                                                            
[   13.765186] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05                                                                  
[   13.765521] iTCO_wdt: Found a ICH4 TCO device (Version=1, TCOBASE=0x0860)                                                    
[   13.765734] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)                                                             
[   13.824168] cfg80211: Calling CRDA to update world regulatory domain                                                         
[   14.102655] ath5k_pci 0000:01:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16                                               
[   14.102859] ath5k_pci 0000:01:04.0: registered as 'phy0'                                                                     
[   14.264762] phy0: Selected rate control algorithm 'pid'                                                                      
[   14.277070] input: PC Speaker as /devices/platform/pcspkr/input/input6                                                       
[   14.490304] ath5k phy0: Atheros AR2413 chip found (MAC: 0x78, PHY: 0x45)                                                     
[   15.146022] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17                                               
[   15.146305] Intel ICH 0000:00:1f.5: setting latency timer to 64                                                              
[   15.190244] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)                                           
[   15.568083] intel8x0_measure_ac97_clock: measured 54807 usecs                                                                
[   15.568088] intel8x0: clocking to 48000                                                                                      
[   16.130096] ppdev: user-space parallel port driver                                                                           
[   16.392421] cfg80211: World regulatory domain updated:                                                                       
[   16.392429]  (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)                                               
[   16.392433]  (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)                                                    
[   16.392436]  (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)                                                    
[   16.392439]  (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)                                                    
[   16.392442]  (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)                                                    
[   16.392445]  (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)                                                    
[   17.491660] lp0: using parport0 (interrupt-driven).                                                                          
[   18.292521] Adding 1630556k swap on /dev/sda6.  Priority:-1 extents:1 across:1630556k                                        
[   19.204838] EXT3 FS on sda2, internal journal                                                                                
[   26.822713] type=1505 audit(1249139321.705:2): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2079
[   26.823047] type=1505 audit(1249139321.705:3): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2079      
[   26.823237] type=1505 audit(1249139321.705:4): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action"name2="default" pid=2079
[   26.823395] type=1505 audit(1249139321.705:5): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2079
[   27.055498] type=1505 audit(1249139321.937:6): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2084
[   27.055991] type=1505 audit(1249139321.937:7): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2084
[   27.109675] type=1505 audit(1249139321.993:8): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2088
[   30.487197] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   30.487202] Bluetooth: BNEP filters: protocol multicast
[   30.511995] Bridge firewalling registered
[   32.559405] [drm] Initialized drm 1.1.0 20060810
[   32.571527] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   32.571539] pci 0000:00:02.0: setting latency timer to 64
[   32.571903] [drm] Initialized i915 1.6.0 20080730 on minor 0
[   32.698832] [drm:i915_setparam] *ERROR* unknown parameter 4
[   32.698926] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   33.480624] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   35.119861] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   35.160404] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   37.023607] wlan0: authenticate with AP 00:21:29:b5:7e:38
[   37.025640] wlan0: authenticated
[   37.025649] wlan0: associate with AP 00:21:29:b5:7e:38
[   37.027874] wlan0: RX AssocResp from 00:21:29:b5:7e:38 (capab=0x401 status=0 aid=1)
[   37.027878] wlan0: associated
[   37.030634] wlan0: disassociating by local choice (reason=3)
```


Windows xp is faster than kubunutu because KDE looks beatiful and heavy on machines. xp is very light, and its even faster than windows 7

---

### Post by Arup on 2009-08-04
> **zerhacke said:**
> I can't stop laughing at this.

Me too, come back after one year of Win7 install and service packs, then we will talk.

---

### Post by solwic on 2009-08-04
> **Durden said:**
> I'm fairly happy with my Win 7 release candidate install. It's boot time etc is pretty bad but once it's running it's fairly "out of my way" and just does what I want it to. My only complaint with Win 7 is the new taskbar which I absolutely loathe.

I gave up comparing Windows to Linux a long time ago.  For me, Ubuntu does what I want it to do, and I find no need to spend money on an OS when I can get one that works for nothing.  

Personally, I think we can stuff the philosophical and ideological discussions on this topic.  There's one area where Linux will always beat Windows:  price.  

Good enough for me.  :)

EDIT:  And please spare me that tired old argument of "Ubuntu costs time (to learn, fix, whatever)".  What else are you going to do with your time?  Knit doilies?  Play WoW?  Find yet *another* version of a Matrix screen saver?  Honestly....

---

### Post by solwic on 2009-08-04
> **Arup said:**
> Me too, come back after one year of Win7 install and service packs, then we will talk.

Likely wouldn't take a year.  Six months, probably.  If that....

---

### Post by realzippy on 2009-08-04
Who cares about boottime?
My system never crashes... ;-)

---

### Post by DracoMoye on 2009-08-05
I test loading mozilla from win7 and ubuntu and it load faster on ubuntu for the first load after that it like 1 or 2 seconde faster on win7.

> I gave up comparing Windows to Linux a long time ago. For me, Ubuntu does what I want it to do, and I find no need to spend money on an OS when I can get one that works for nothing. 

Personally, I think we can stuff the philosophical and ideological discussions on this topic. There's one area where Linux will always beat Windows: price.

In the reality windows is pirated for many people so the price is not an argument.

---

### Post by kaptain0 on 2009-08-05
Yeah my computer is dual boot xp (10 years old) and ubuntu.
 
Mine does crash alot, but that's cuz the hardware's old. I used to have to restart it 6 times for it to boot up all the way, but its fine now.

---

### Post by mdsmedia on 2009-08-06
> **iRun said:**
> Likely wouldn't take a year.  Six months, probably.  If that....

That's about exactly what it took to make my brand new XP slow to a crawl, and then I discovered Ubuntu :).

---

### Post by konqui on 2009-08-06
Reinstall Kubuntu, using the ALTERNATE cd. Install on Ext4.

If you have multiple core CPU, do this.

Alt + F2 
type: kdesu kate /etc/init.d/rc

---

### Post by solwic on 2009-08-06
> **mdsmedia said:**
> That's about exactly what it took to make my brand new XP slow to a crawl, and then I discovered Ubuntu :).

Amen.  Once you use Ubuntu for a while, without reformatting two dozen times, you start to see how much Windows does slow down over time.  

Lucky us, though.  We've got Linux. :)

---

### Post by Tamlynmac on 2009-08-06
> mdsmedia
That's about exactly what it took to make my brand new XP slow to a crawl, and then I discovered Ubuntu :smile:. 	

+1

IMHO, knowledge and experience are indispensable when making a decision. You and iRun again display a propensity for both. ;)

When first installing Ubuntu 3 years ago, I was somewhat apprehensive. Now, after three years of rock solid stability and no Internet maleware - I can say without hesitation it was one of the best computing decision I've ever made.

I still consider myself an Ubuntu/Linux noob. Fortunately, Ubuntu is intuitive enough to have made the transition simple, for even one as ignorant as myself. For a modest investment (learning), the rewards have been phenomenal.

---

### Post by TurboRush on 2009-08-06
I guess I am with a few others here and I am not quite sure where bootup and shutdown time matters.

Assuming all else equal from a performance perspective and looking at the big picture, once I boot Ubuntu I never need to reboot and my system has been up for months at a time with a power outage being the culprit to reboot. On the other hand, my XP device needs to get restarted at least once a week because something goes haywire.

So, in the big picture ubuntu comes out ahead because after 2 reboots of XP its longer... :D

---

### Post by kaptain0 on 2009-08-06
> **konqui said:**
> Reinstall Kubuntu, using the ALTERNATE cd. Install on Ext4.
 
If you have multiple core CPU, do this.
 
Alt + F2 
type: kdesu kate /etc/init.d/rc
 
Forgive my ignorance. What does it do?

---

### Post by hellmet on 2009-08-06
> **bashirchacha said:**
> I think Windows 7 faster than any OS
It is probably faster than .. oh never mind.

And hey, who needs to boot? I can make changes to almost anything and I don't have to restart Ubuntu. 
Oops, sorry for going really off-topic.

---

### Post by khelben1979 on 2009-08-06
> **bashirchacha said:**
> I think Windows 7 faster than any OS

If it's that fast, how come you can't run it on a 386 processor? :-\"

AmigaOS has been the most efficient operating system I've ever seen when it comes to how little memory and cpu power it needs. Now, that's a fast operating system! I'm going to install and begin running it together with UAE in the future. I haven't done it in ages. Too much focus on Linux.

---

### Post by running_rabbit07 on 2009-08-06
Are these times on XP taken with automatic updates turned on and anti-virus installed? When I boot it takes forever to do anything because of the Live Updates and anti-virus. From what I am reading I should probably not waste the disk I was getting ready to use to get a taste of KDE just to see what it looks like.

As far as Windows 7 being fast, I have not tried it yet but for the price people are paying for it, it better be fast. 

I love Ubuntu. Turn on the machine, seconds later, sign in, and seconds later I am checking the mail and surfing the net.

---

### Post by Mike_IronFist on 2009-08-08
> **bashirchacha said:**
> I think Windows 7 faster than any OS

Excuse me for saying this, but you're out of your mind. Windows 7 is barely even faster than Windows Vista, as benchmark tests prove.

Anyway, there's no doubt that XP is faster than Kubuntu. Kubuntu has more demanding system requirements and the KDE desktop in general is more taxing on hardware than either XP or the Gnome desktop environment.

In short, yes XP is faster than Kubuntu, but regular, Gnome-desktop Ubuntu is faster than XP in my experience.

---

### Post by Durden on 2009-08-09
I'm finding KDE faster than Gnome these days. KDE 4.3 is pretty damn quick. Of course, this is with desktop effects on both setups. 

Gnome is feeling very dated now and seems to get bloated as it goes while simultaneously losing features. It's a complete paradox.

---

### Post by khelben1979 on 2009-08-09
> **Durden said:**
> I'm finding KDE faster than Gnome these days. KDE 4.3 is pretty damn quick. Of course, this is with desktop effects on both setups. 

Gnome is feeling very dated now and seems to get bloated as it goes while simultaneously losing features. It's a complete paradox.

I've read that Gnome is more stable than KDE and I think they are right (especially if you're looking at KDE 4.x). I don't think that Gnome has been much of a desktop enviroment for speed.

---

