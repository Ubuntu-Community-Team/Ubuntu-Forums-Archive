---
title: "No SSH-Connection"
date: 2011-03-03
forum: Ubuntu Cloud and Juju
---

### Post by haukman on 2011-03-03
Hi Guys,
 
i installed a UEC from the 10.10 image.
I am able to start instanzes and they also get an IP form our local DHCP-server.
I can ping the machine, but i am not able to log in using ssh.
 
> RESERVATION r-385A0786 hxxx default
INSTANCE i-2F1305B5 emi-3EE1164E 16.xx.xx.xx 16.xx.xx.xx running 0 m1.small 2011-03-03T10:49:08.59Z cluster1 eki-927D1B51
 
Here the ssh-result:
 
> ssh: connect to host 16.xx.xx.xx port 22: Connection refused

 
I also tried to start an instanze with a key attached to it, but it doesnt work either...
Do have any ideas what maybe wrong??
 
The other Problem i have has to deal with hybridfox. It cant connect to my Cloud...
([http://16.x.x.x:8773/services/Eucalyptus](http://16.x.x.x:8773/services/Eucalyptus))
I get an error message with no content in...if i type it in my browser i get: "Internal Server Error"
 
Any Ideas?!?
Thank you :)

---

### Post by raymdt on 2011-03-03
Hey and welcome,
you should first check if your instances boot correctly( running state doesn't meant that every things is ok) and if your private key is ok.
So post the output of
```

euca-get-console-output  i-xxxxx(your instance id )

```

And check the content of your mykey.priv file
post
```

cat  ~/.euca/mykey.priv (dont forget to hide a part of the output)

```

---

### Post by haukman on 2011-03-03
here the first output:
 
```
i-3B9A07E2
2011-03-03T12:01:08.025Z
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-28-server (buildd@allspice) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #55-Ubuntu SMP Mon Jan 10 23:57:16 UTC 2011 (Ubuntu 2.6.32-28.55-server 2.6.32.27+drm33.12)
[    0.000000] Command line: root=/dev/sda1 console=ttyS0
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
[    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000000bffd000 (usable)
[    0.000000]  BIOS-e820: 000000000bffd000 - 000000000c000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fffbc000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.4 present.
[    0.000000] last_pfn = 0xbffd max_arch_pfn = 0x400000000
[    0.000000] PAT not supported by CPU.
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000001000 (usable)
[    0.000000]  modified: 0000000000001000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009f400 (usable)
[    0.000000]  modified: 000000000009f400 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000000bffd000 (usable)
[    0.000000]  modified: 000000000bffd000 - 000000000c000000 (reserved)
[    0.000000]  modified: 00000000fffbc000 - 0000000100000000 (reserved)
[    0.000000] init_memory_mapping: 0000000000000000-000000000bffd000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] ACPI: RSDP 00000000000fdb70 00014 (v00 BOCHS )
[    0.000000] ACPI: RSDT 000000000bffde30 00034 (v01 BOCHS  BXPCRSDT 00000001 BXPC 00000001)
[    0.000000] ACPI: FACP 000000000bfffe70 00074 (v01 BOCHS  BXPCFACP 00000001 BXPC 00000001)
[    0.000000] ACPI: DSDT 000000000bffdfd0 01E22 (v01   BXPC   BXDSDT 00000001 INTL 20090123)
[    0.000000] ACPI: FACS 000000000bfffe00 00040
[    0.000000] ACPI: SSDT 000000000bffdf90 00037 (v01 BOCHS  BXPCSSDT 00000001 BXPC 00000001)
[    0.000000] ACPI: APIC 000000000bffdeb0 00072 (v01 BOCHS  BXPCAPIC 00000001 BXPC 00000001)
[    0.000000] ACPI: HPET 000000000bffde70 00038 (v01 BOCHS  BXPCHPET 00000001 BXPC 00000001)
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000000bffd000
[    0.000000] Bootmem setup node 0 0000000000000000-000000000bffd000
[    0.000000]   NODE_DATA [0000000000009000 - 000000000000dfff]
[    0.000000]   bootmap [000000000000e000 -  000000000000f7ff] pages 2
[    0.000000] (6 early reservations) ==> bootmem [0000000000 - 000bffd000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0001000000 - 0001a4faa4]    TEXT DATA BSS ==> [0001000000 - 0001a4faa4]
[    0.000000]   #3 [000009f400 - 0000100000]    BIOS reserved ==> [000009f400 - 0000100000]
[    0.000000]   #4 [0001a50000 - 0001a50071]              BRK ==> [0001a50000 - 0001a50071]
[    0.000000]   #5 [0000008000 - 0000009000]          PGTABLE ==> [0000008000 - 0000009000]
[    0.000000] found SMP MP-table at [ffff8800000fdbc0] fdbc0
[    0.000000] kvm-clock: cpu 0, msr 0:187eb41, boot clock
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00100000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000001
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0000bffd
[    0.000000] ACPI: PM-Timer IO Port: 0xb008
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 5 global_irq 5 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 10 global_irq 10 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 11 global_irq 11 high level)
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 0000000000001000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at c000000 (gap: c000000:f3fbc000)
[    0.000000] Booting paravirtualized kernel on KVM
[    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880001c00000 s91544 r8192 d23144 u2097152
[    0.000000] pcpu-alloc: s91544 r8192 d23144 u2097152 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] kvm-clock: cpu 0, msr 0:1c15b41, primary cpu clock
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 48275
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: root=/dev/sda1 console=ttyS0
[    0.000000] PID hash table entries: 1024 (order: 1, 8192 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Memory: 181120k/196596k available (5515k kernel code, 408k absent, 15068k reserved, 3090k data, 800k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:4352 nr_irqs:256
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [ttyS0] enabled
[    0.000000] allocated 2621440 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.000000] Detected 2264.020 MHz processor.
[    0.050000] Calibrating delay loop (skipped) preset value.. 4528.04 BogoMIPS (lpj=22640200)
[    0.050000] Security Framework initialized
[    0.050000] AppArmor: AppArmor initialized
[    0.050000] Dentry cache hash table entries: 32768 (order: 6, 262144 bytes)
[    0.050000] Inode-cache hash table entries: 16384 (order: 5, 131072 bytes)
[    0.050000] Mount-cache hash table entries: 256
[    0.050000] Initializing cgroup subsys ns
[    0.050000] Initializing cgroup subsys cpuacct
[    0.050000] Initializing cgroup subsys memory
[    0.050000] Initializing cgroup subsys devices
[    0.050000] Initializing cgroup subsys freezer
[    0.050000] Initializing cgroup subsys net_cls
[    0.050070] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.050708] CPU: L2 cache: 4096K
[    0.051142] CPU 0/0x0 -> Node 0
[    0.051561] mce: CPU supports 10 MCE banks
[    0.052156] Performance Events: unsupported p6 CPU model 2 no PMU driver, software events only.
[    0.053311] SMP alternatives: switching to UP code
[    0.080056] Freeing SMP alternatives: 40k freed
[    0.080713] ACPI: Core revision 20090903
[    0.081949] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.082698] ftrace: allocating 22837 entries in 90 pages
[    0.090138] Setting APIC routing to flat
[    0.091961] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.092811] CPU0: Intel QEMU Virtual CPU version 0.12.5 stepping 03
[    0.110000] Brought up 1 CPUs
[    0.110000] Total of 1 processors activated (4528.04 BogoMIPS).
[    0.110000] devtmpfs: initialized
[    0.110000] regulator: core version 0.5
[    0.110000] Time: 10:34:15  Date: 03/03/11
[    0.110000] NET: Registered protocol family 16
[    0.110000] ACPI: bus type pci registered
[    0.110000] PCI: Using configuration type 1 for base access
[    0.110000] bio: create slab <bio-0> at 0
[    0.111929] ACPI: Interpreter enabled
[    0.112443] ACPI: (supports S0 S3 S4 S5)
[    0.113072] ACPI: Using IOAPIC for interrupt routing
[    0.116435] ACPI: No dock devices found.
[    0.117018] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.119059] pci 0000:00:01.3: quirk: region b000-b03f claimed by PIIX4 ACPI
[    0.120033] pci 0000:00:01.3: quirk: region b100-b10f claimed by PIIX4 SMB
[    0.124931] ACPI: PCI Interrupt Link [LNKA] (IRQs 5 *10 11)
[    0.125860] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 *10 11)
[    0.126788] ACPI: PCI Interrupt Link [LNKC] (IRQs 5 10 *11)
[    0.127719] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 10 *11)
[    0.128646] vgaarb: loaded
[    0.129161] SCSI subsystem initialized
[    0.129895] usbcore: registered new interface driver usbfs
[    0.130018] usbcore: registered new interface driver hub
[    0.130801] usbcore: registered new device driver usb
[    0.131667] ACPI: WMI: Mapper loaded
[    0.132173] PCI: Using ACPI for IRQ routing
[    0.132992] NetLabel: Initializing
[    0.133470] NetLabel:  domain hash size = 128
[    0.134060] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.134782] NetLabel:  unlabeled traffic allowed by default
[    0.135598] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.136329] hpet0: 3 comparators, 64-bit 100.000000 MHz counter
[    0.150034] Switching to clocksource kvm-clock
[    0.152858] AppArmor: AppArmor Filesystem Enabled
[    0.153533] pnp: PnP ACPI init
[    0.153966] ACPI: bus type pnp registered
[    0.155165] pnp: PnP ACPI: found 6 devices
[    0.155736] ACPI: ACPI bus type pnp unregistered
[    0.160476] NET: Registered protocol family 2
[    0.161142] IP route cache hash table entries: 2048 (order: 2, 16384 bytes)
[    0.162381] TCP established hash table entries: 8192 (order: 5, 131072 bytes)
[    0.163545] TCP bind hash table entries: 8192 (order: 5, 131072 bytes)
[    0.164596] TCP: Hash tables configured (established 8192 bind 8192)
[    0.165467] TCP reno registered
[    0.165950] NET: Registered protocol family 1
[    0.166578] pci 0000:00:00.0: Limiting direct PCI/PCI transfers
[    0.167387] pci 0000:00:01.0: PIIX3: Enabling Passive Release
[    0.168168] pci 0000:00:01.0: Activating ISA DMA hang workarounds
[    0.169226] Scanning for low memory corruption every 60 seconds
[    0.170231] audit: initializing netlink socket (disabled)
[    0.170985] type=2000 audit(1299148457.170:1): initialized
[    0.181188] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.183412] VFS: Disk quotas dquot_6.5.2
[    0.184031] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.185600] fuse init (API version 7.13)
[    0.186248] msgmni has been set to 353
[    0.187075] alg: No test for stdrng (krng)
[    0.187707] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.188725] io scheduler noop registered
[    0.189270] io scheduler anticipatory registered
[    0.189905] io scheduler deadline registered (default)
[    0.190675] io scheduler cfq registered
[    0.191268] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.192047] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.193031] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.194051] ACPI: Power Button [PWRF]
[    0.194918] processor LNXCPU:00: registered as cooling_device0
[    0.196564] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[    0.197380] virtio-pci 0000:00:04.0: PCI INT A -> Link[LNKD] -> GSI 11 (level, high) -> IRQ 11
[    0.199874] Linux agpgart interface v0.103
[    0.200512] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.201595] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.203636] brd: module loaded
[    0.204689] loop: module loaded
[    0.205228] input: Macintosh mouse button emulation as /devices/virtual/input/input1
[    0.206475] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10
[    0.207279] sym53c8xx 0000:00:03.0: PCI INT A -> Link[LNKC] -> GSI 10 (level, high) -> IRQ 10
[    0.209712] sym0: <895a> rev 0x0 at pci 0000:00:03.0 irq 10
[    0.212629] sym0: No NVRAM, ID 7, Fast-40, LVD, parity checking
[    0.220476] sym0: SCSI BUS has been reset.
[    0.222454] scsi0 : sym-2.2.3
[    0.223374] scsi1 : ata_piix
[    0.223844] scsi2 : ata_piix
[    0.224297] ata1: PATA max MWDMA2 cmd 0x1f0 ctl 0x3f6 bmdma 0xc000 irq 14
[    0.225221] ata2: PATA max MWDMA2 cmd 0x170 ctl 0x376 bmdma 0xc008 irq 15
[    0.226419] Fixed MDIO Bus: probed
[    0.226933] PPP generic driver version 2.4.2
[    0.227559] tun: Universal TUN/TAP device driver, 1.6
[    0.228246] tun: (C) 1999-2004 Max Krasnyansky <[EMAIL="maxk@qualcomm.com"]maxk@qualcomm.com[/EMAIL]>
[    0.229191] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.230131] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.230979] uhci_hcd: USB Universal Host Controller Interface driver
[    0.231870] uhci_hcd 0000:00:01.2: PCI INT D -> Link[LNKD] -> GSI 11 (level, high) -> IRQ 11
[    0.233033] uhci_hcd 0000:00:01.2: UHCI Host Controller
[    0.233778] uhci_hcd 0000:00:01.2: new USB bus registered, assigned bus number 1
[    0.234998] uhci_hcd 0000:00:01.2: irq 11, io base 0x0000c020
[    0.235920] usb usb1: configuration #1 chosen from 1 choice
[    0.236799] hub 1-0:1.0: USB hub found
[    0.237377] hub 1-0:1.0: 2 ports detected
[    0.238083] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[    0.240232] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.240976] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.241827] mice: PS/2 mouse device common for all mice
[    0.242790] rtc_cmos 00:01: rtc core: registered rtc_cmos as rtc0
[    0.243811] rtc0: alarms up to one day, 114 bytes nvram, hpet irqs
[    0.244917] device-mapper: uevent: version 1.0.3
[    0.245953] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    0.248243] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    0.249578] device-mapper: multipath: version 1.1.0 loaded
[    0.250404] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.251604] cpuidle: using governor ladder
[    0.252233] cpuidle: using governor menu
[    0.253144] TCP cubic registered
[    0.253787] NET: Registered protocol family 10
[    0.254954] lo: Disabled Privacy Extensions
[    0.255793] NET: Registered protocol family 17
[    0.256588] registered taskstats version 1
[    0.257424]   Magic number: 3:294:577
[    0.257988] scsi: waiting for bus probes to complete ...
[    3.230358] scsi 0:0:0:0: Direct-Access     QEMU     QEMU HARDDISK    0.12 PQ: 0 ANSI: 3
[    3.231468] scsi target0:0:0: tagged command queuing enabled, command queue depth 16.
[    3.232526] scsi target0:0:0: Beginning Domain Validation
[    3.233628] scsi target0:0:0: Domain Validation skipping write tests
[    3.234489] scsi target0:0:0: Ending Domain Validation
[    3.237531] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.238442] rtc_cmos 00:01: setting system clock to 2011-03-03 10:34:18 UTC (1299148458)
[    3.239939] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    3.240792] EDD information not available.
[    3.241527] sd 0:0:0:0: [sda] 4259840 512-byte logical blocks: (2.18 GB/2.03 GiB)
[    3.242600] sd 0:0:0:0: [sda] Write Protect is off
[    3.243381] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[    3.244914]  sda: sda1 sda2 sda3
[    3.246829] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.247509] md: Waiting for all devices to be available before autodetect
[    3.248494] md: If you don't use raid, use raid=noautodetect
[    3.249380] md: Autodetecting RAID arrays.
[    3.249963] md: Scanned 0 and added 0 devices.
[    3.250606] md: autorun ...
[    3.250997] md: ... autorun DONE.
[    3.253249] kjournald starting.  Commit interval 5 seconds
[    3.254021] EXT3-fs: mounted filesystem with ordered data mode.
[    3.254837] VFS: Mounted root (ext3 filesystem) readonly on device 8:1.
[    3.256426] devtmpfs: mounted
[    3.256869] Freeing unused kernel memory: 800k freed
[    3.257827] Write protecting the kernel read-only data: 7808k
init: plymouth main process (51) killed by SEGV signal
init: plymouth-splash main process (320) terminated with status 2
cloud-init running: Thu, 03 Mar 2011 10:34:29 +0000. up 14.57 seconds
waiting for metadata service at [http://169.254.169.254/2009-04-04/meta-data/instance-id](http://169.254.169.254/2009-04-04/meta-data/instance-id)
  10:34:31 [ 1/100]: url error [timed out]
  10:34:34 [ 2/100]: url error [timed out]
  10:34:37 [ 3/100]: url error [timed out]
  10:34:40 [ 4/100]: url error [timed out]
  10:34:43 [ 5/100]: url error [timed out]
  10:34:46 [ 6/100]: url error [timed out]
  10:34:50 [ 7/100]: url error [timed out]
  10:34:54 [ 8/100]: url error [timed out]
  10:34:58 [ 9/100]: url error [timed out]
  10:35:02 [10/100]: url error [timed out]
  10:35:06 [11/100]: url error [timed out]
  10:35:11 [12/100]: url error [timed out]
  10:35:16 [13/100]: url error [timed out]
  10:35:21 [14/100]: url error [timed out]
  10:35:26 [15/100]: url error [timed out]
  10:35:31 [16/100]: url error [timed out]
  10:35:37 [17/100]: url error [timed out]
  10:35:43 [18/100]: url error [timed out]
  10:35:49 [19/100]: url error [timed out]
  10:35:55 [20/100]: url error [timed out]
  10:36:01 [21/100]: url error [timed out]
  10:36:08 [22/100]: url error [timed out]
  10:36:23 [23/100]: url error [timed out]
  10:36:30 [24/100]: url error [timed out]
  10:36:37 [25/100]: url error [timed out]
  10:36:44 [26/100]: url error [timed out]
  10:36:52 [27/100]: url error [timed out]
  10:37:00 [28/100]: url error [timed out]
  10:37:08 [29/100]: url error [timed out]
  10:37:16 [30/100]: url error [timed out]
  10:37:24 [31/100]: url error [timed out]
  10:37:33 [32/100]: url error [timed out]
  10:37:42 [33/100]: url error [timed out]
  10:37:51 [34/100]: url error [timed out]
  10:38:00 [35/100]: url error [timed out]
  10:38:09 [36/100]: url error [timed out]
  10:38:19 [37/100]: url error [timed out]
  10:38:29 [38/100]: url error [timed out]
  10:38:39 [39/100]: url error [timed out]
  10:38:49 [40/100]: url error [timed out]
  10:38:59 [41/100]: url error [timed out]
  10:39:10 [42/100]: url error [timed out]
  10:39:21 [43/100]: url error [timed out]
  10:39:32 [44/100]: url error [timed out]
  10:39:43 [45/100]: url error [timed out]
  10:39:54 [46/100]: url error [timed out]
  10:40:06 [47/100]: url error [timed out]
  10:40:18 [48/100]: url error [timed out]
  10:40:30 [49/100]: url error [timed out]
  10:40:42 [50/100]: url error [timed out]
  10:40:54 [51/100]: url error [timed out]
  10:41:07 [52/100]: url error [timed out]
  10:41:20 [53/100]: url error [timed out]
  10:41:33 [54/100]: url error [timed out]
  10:41:46 [55/100]: url error [timed out]
  10:41:59 [56/100]: url error [timed out]
  10:42:13 [57/100]: url error [timed out]
  10:42:27 [58/100]: url error [timed out]
  10:42:41 [59/100]: url error [timed out]
  10:42:55 [60/100]: url error [timed out]
  10:43:09 [61/100]: url error [timed out]
  10:43:24 [62/100]: url error [timed out]
  10:43:39 [63/100]: url error [timed out]
  10:43:54 [64/100]: url error [timed out]
  10:44:09 [65/100]: url error [timed out]
  10:44:24 [66/100]: url error [timed out]
  10:44:40 [67/100]: url error [timed out]
  10:44:56 [68/100]: url error [timed out]
  10:45:12 [69/100]: url error [timed out]
  10:45:28 [70/100]: url error [timed out]
  10:45:44 [71/100]: url error [timed out]
  10:46:01 [72/100]: url error [timed out]
  10:46:18 [73/100]: url error [timed out]
  10:46:35 [74/100]: url error [timed out]
  10:46:52 [75/100]: url error [timed out]
  10:47:09 [76/100]: url error [timed out]
  10:47:27 [77/100]: url error [timed out]
  10:47:45 [78/100]: url error [timed out]
  10:48:03 [79/100]: url error [timed out]
  10:48:21 [80/100]: url error [timed out]
  10:48:40 [81/100]: url error [timed out]
  10:48:59 [82/100]: url error [timed out]
  10:49:18 [83/100]: url error [timed out]
  10:49:37 [84/100]: url error [timed out]
  10:49:56 [85/100]: url error [timed out]
  10:50:15 [86/100]: url error [timed out]
  10:50:35 [87/100]: url error [timed out]
  10:50:55 [88/100]: url error [timed out]
  10:51:15 [89/100]: url error [timed out]
  10:51:35 [90/100]: url error [timed out]
  10:51:55 [91/100]: url error [timed out]
  10:52:16 [92/100]: url error [timed out]
  10:52:37 [93/100]: url error [timed out]
  10:52:58 [94/100]: url error [timed out]
  10:53:19 [95/100]: url error [timed out]
  10:53:40 [96/100]: url error [timed out]
  10:54:02 [97/100]: url error [timed out]
  10:54:24 [98/100]: url error [timed out]
  10:54:46 [99/100]: url error [timed out]
  10:55:08 [100/100]: url error [timed out]
giving up on md after 1258 seconds
Could not find data source
Failed to get instance data
init: cloud-init main process (368) terminated with status 1
mountall: Event failed
init: plymouth-log main process (399) terminated with status 1
 * Starting AppArmor profiles       [80G Traceback (most recent call last):
  File "/usr/bin/cloud-init-cfg", line 56, in <module>
    main()
  File "/usr/bin/cloud-init-cfg", line 43, in main
    cc = cloudinit.CloudConfig.CloudConfig(cfg_path)
  File "/usr/lib/python2.6/dist-packages/cloudinit/CloudConfig.py", line 42, in __init__
Traceback (most recent call last):
  File "/usr/bin/cloud-init-cfg", line 56, in <module>
    main()
  File "/usr/bin/cloud-init-cfg", line 43, in main
    cc = cloudinit.CloudConfig.CloudConfig(cfg_path)
  File "/usr/lib/python2.6/dist-packages/cloudinit/CloudConfig.py", line 42, in __init__
    self.cfg = self.get_config_obj(cfgfile)
  File "/usr/lib/python2.6/dist-packages/cloudinit/CloudConfig.py", line 53, in get_config_obj
    f=file(cfgfile)
IOError: [Errno 2] No such file or directory: '/var/lib/cloud/data/cloud-config.txt'
    self.cfg = self.get_config_obj(cfgfile)
  File "/usr/lib/python2.6/dist-packages/cloudinit/CloudConfig.py", line 53, in get_config_obj
    f=file(cfgfile)
IOError: [Errno 2] No such file or directory: '/var/lib/cloud/data/cloud-config.txt'
Traceback (most recent call last):
  File "/usr/bin/cloud-init-cfg", line 56, in <module>
    main()
  File "/usr/bin/cloud-init-cfg", line 43, in main
    cc = cloudinit.CloudConfig.CloudConfig(cfg_path)
  File "/usr/lib/python2.6/dist-packages/cloudinit/CloudConfig.py", line 42, in __init__
    self.cfg = self.get_config_obj(cfgfile)
  File "/usr/lib/python2.6/dist-packages/cloudinit/CloudConfig.py", line 53, in get_config_obj
    f=file(cfgfile)
IOError: [Errno 2] No such file or directory: '/var/lib/cloud/data/cloud-config.txt'
Traceback (most recent call last):
  File "/usr/bin/cloud-init-cfg", line 56, in <module>
    main()
  File "/usr/bin/cloud-init-cfg", line 43, in main
    cc = cloudinit.CloudConfig.CloudConfig(cfg_path)
  File "/usr/lib/python2.6/dist-packages/cloudinit/CloudConfig.py", line 42, in __init__
    self.cfg = self.get_config_obj(cfgfile)
  File "/usr/lib/python2.6/dist-packages/cloudinit/CloudConfig.py", line 53, in get_config_obj
    f=file(cfgfile)
IOError: [Errno 2] No such file or directory: '/var/lib/cloud/data/cloud-config.txt'Traceback (most recent call last):
  File "/usr/bin/cloud-init-cfg", line 56, in <module>
    main()
  File "/usr/bin/cloud-init-cfg", line 43, in main
    cc = cloudinit.CloudConfig.CloudConfig(cfg_path)
  File "/usr/lib/python2.6/dist-packages/cloudinit/CloudConfig.py", line 42, in __init__
    self.cfg = self.get_config_obj(cfgfile)
  File "/usr/lib/python2.6/dist-packages/cloudinit/CloudConfig.py", line 53, in get_config_obj
    f=file(cfgfile)
IOError: [Errno 2] No such file or directory: '/var/lib/cloud/data/cloud-config.txt'
init: cloud-disable-ec2-metadata main process (402) terminated with status 1
init: cloud-config-ssh main process (398) terminated with status 1
init: cloud-config-mounts main process (401) terminated with status 1
init: cloud-apt-update-upgrade main process (405) terminated with status 1
[74G[ OK ]
init: cloud-config-misc main process (406) terminated with status 1
init: apport pre-start process (454) terminated with status 1
init: apport post-stop process (465) terminated with status 1
Traceback (most recent call last):
  File "/usr/bin/cloud-init-cfg", line 56, in <module>
    main()
  File "/usr/bin/cloud-init-cfg", line 43, in main
    cc = cloudinit.CloudConfig.CloudConfig(cfg_path)
  File "/usr/lib/python2.6/dist-packages/cloudinit/CloudConfig.py", line 42, in __init__
    self.cfg = self.get_config_obj(cfgfile)
  File "/usr/lib/python2.6/dist-packages/cloudinit/CloudConfig.py", line 53, in get_config_obj
    f=file(cfgfile)
IOError: [Errno 2] No such file or directory: '/var/lib/cloud/data/cloud-config.txt'
init: cloud-config-puppet main process (443) terminated with status 1
landscape-client is not configured, please run landscape-config.

```
 
And my private Key :)
```
----BEGIN RSA PRIVATE KEY-----
MIIEpQIBAAKCAQEA18QSwhJ62qhiI+Z0ow/MX8bhFXFYvG8X10CTYL4ci4cNvuoQ
hKCnFtVmO0RpnInOFExtiFOH624oAb63hdiQaj4CgExji3O0K60KA/nWN8DdDspm
VSDdNcQP5Nzt679h6ucp1PW2JNJozbn2biRec/kcHmgoLC3x2O8AaVCV6A9vrrz1
9qB4G2/FMsManxQ7PJpK5AdD9yDl0PcojnR6ZQ+PpGZm+NjhHetW423W4WfOWm5x
zY/GRBldQxRmSbKWujOOund4NzRLOrNFyuNlnbMaKDp1NhkQUh3WDAZabVhHpEwb
QOcN/MMkMZ0LJJ67xW9YHVhZbuQUBcmckAZLmQIDAQABAoIBAQDRpvOTH+HAFV1H
BObQislLRzPuYfSXJFtGDLknh5K1AMWafFUQignRZgmwDQmR0VUs5BaKIKAxYxf8
mhQ5OfUZRqengpI3LnYi+kCBHIHKKtyhQomsrgJD+/51ozaLm6rJVVSQWTBjFxA+
1jNdUnl0ttlbsllWlE4rPBBqRKNkl9Fcvd/UwNAdfVQXrSjOUUxY8HIXocddQTSZ
K0YUaBOvbYhi+NMSPLP2PWe8/9bqkzTbbiJ3hvoyynFahgPQzCIkAs8M4qgooz6V
8C42+s/wgj6B+A3UCDzcg+cL7ITQGUhJySqk+hNo0/xIPRwep4VJVPrWDnSQ9n1z
QL3nJKsBAoGBAPu+jcXOKNKLwQA4HhZV7q7OeJMtCXQ1CSFXcv69+e+YGohpifrH
Go4OxZlsbvcw542kRrFS4YOEnck6gohak6DAoDSaMjKcz3en6gF5vK3yOzXL3pn1
vHZaXRD5L5hZXQR/nBv9RNTz3DkXycW+kUBTV2UO62ZKVF/DrOQsEyTzAoGBANtp
....
-----END RSA PRIVATE KEY-----

```
 
Thanks again :)

---

### Post by kim0 on 2011-03-04
Are you using a non-default networking mode? If so, I'd strongly recommend reverting to MANAGED_NOVLAN (default setting for UEC). Other modes do not get much testing and are known broken in certain situations

---

