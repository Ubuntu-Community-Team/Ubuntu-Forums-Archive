---
title: "cant access my running instance"
date: 2013-01-18
forum: Ubuntu Cloud and Juju
---

### Post by asraa on 2013-01-18
i cant login to my running instance when i try to connect to it using command:
ssh -i ~/.ssh/eucakey admin@192.168.1.120 (eucakey is the keypair i used to run the image)

the following out appear: 

Read from socket failed: Connection reset by peer

please help

---

### Post by asraa on 2013-01-18
this is the output of  instance console :

freqtok = self.datasource.get_instance_id()
  File "/usr/lib/python2.6/dist-packages/cloudinit/DataSourceEc2.py", line 64, in get_instance_id
    return(self.metadata['instance-id'])
KeyError: 'instance-id'
init: cloud-init main process (574) terminated with status 1
mountall: Event failed
 * Starting AppArmor profiles       
[80G Traceback (most recent call last):
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
[74G[ OK ]
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
  File "/usr/bin/landscape-is-cloud-managed", line 12, in <module>
    sys.exit(not is_cloud_managed())
  File "/usr/lib/python2.6/dist-packages/landscape/broker/registration.py", line 397, in is_cloud_managed
    raw_user_data, int(launch_index))
ValueError: invalid literal for int() with base 10: ''
landscape-client is not configured, please run landscape-config.

---

### Post by asraa on 2013-01-18
this is the output of   ssh -i ~/.ssh/eucakey -vvv admin@192.168.1.120 :

OpenSSH_5.8p1 Debian-1ubuntu3, OpenSSL 0.9.8o 01 Jun 2010
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 192.168.1.120 [192.168.1.120] port 22.
debug1: Connection established.
debug3: Incorrect RSA1 identifier
debug3: Could not load "/home/asraa/.ssh/eucakey" as a RSA1 public key
debug3: key_read: missing whitespace
debug2: key_type_from_name: unknown key type '-----BEGIN'
debug3: key_read: missing keytype
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug2: key_type_from_name: unknown key type '-----END'
debug3: key_read: missing keytype
debug1: identity file /home/asraa/.ssh/eucakey type -1
debug1: identity file /home/asraa/.ssh/eucakey-cert type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.3p1 Debian-3ubuntu3
debug1: match: OpenSSH_5.3p1 Debian-3ubuntu3 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.8p1 Debian-1ubuntu3
debug2: fd 3 setting O_NONBLOCK
debug3: load_hostkeys: loading entries for host "192.168.1.120" from file "/home/asraa/.ssh/known_hosts"
debug3: load_hostkeys: found key type RSA in file /home/asraa/.ssh/known_hosts:3
debug3: load_hostkeys: loaded 1 keys
debug3: load_hostkeys: loading entries for host "192.168.1.120" from file "/etc/ssh/ssh_known_hosts"
debug3: load_hostkeys: loaded 0 keys
debug3: order_hostkeyalgs: prefer hostkeyalgs: [email]ssh-rsa-cert-v01@openssh.com,ssh-rsa-cert-v00@openssh.com[/email],ssh-rsa
debug1: SSH2_MSG_KEXINIT sent
Read from socket failed: Connection reset by peer


please help :confused:

---

### Post by asraa on 2013-01-23
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-21-generic-pae (buildd@rothera) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #32-Ubuntu SMP Fri Apr 16 09:39:35 UTC 2010 (Ubuntu 2.6.32-21.32-generic-pae 2.6.32.11+drm33.2)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000000bffd000 (usable)
[    0.000000]  BIOS-e820: 000000000bffd000 - 000000000c000000 (reserved)
[    0.000000]  BIOS-e820: 00000000feffc000 - 00000000ff000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fffc0000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.4 present.
[    0.000000] last_pfn = 0xbffd max_arch_pfn = 0x1000000
[    0.000000] PAT not supported by CPU.
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000000bffd000 (usable)
[    0.000000]  modified: 000000000bffd000 - 000000000c000000 (reserved)
[    0.000000]  modified: 00000000feffc000 - 00000000ff000000 (reserved)
[    0.000000]  modified: 00000000fffc0000 - 0000000100000000 (reserved)
[    0.000000] init_memory_mapping: 0000000000000000-000000000bffd000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] RAMDISK: 0bc38000 - 0bfefe9b
[    0.000000] ACPI: RSDP 000fd740 00014 (v00 BOCHS )
[    0.000000] ACPI: RSDT 0bffdc40 00034 (v01 BOCHS  BXPCRSDT 00000001 BXPC 00000001)
[    0.000000] ACPI: FACP 0bfffe70 00074 (v01 BOCHS  BXPCFACP 00000001 BXPC 00000001)
[    0.000000] ACPI: DSDT 0bffde40 01FB7 (v01   BXPC   BXDSDT 00000001 INTL 20090123)
[    0.000000] ACPI: FACS 0bfffe00 00040
[    0.000000] ACPI: SSDT 0bffdda0 0009E (v01 BOCHS  BXPCSSDT 00000001 BXPC 00000001)
[    0.000000] ACPI: APIC 0bffdcc0 00072 (v01 BOCHS  BXPCAPIC 00000001 BXPC 00000001)
[    0.000000] ACPI: HPET 0bffdc80 00038 (v01 BOCHS  BXPCHPET 00000001 BXPC 00000001)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 191MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 0bffd000
[    0.000000]   low ram: 0 - 0bffd000
[    0.000000]   node 0 low ram: 00000000 - 0bffd000
[    0.000000]   node 0 bootmap 00009000 - 0000a800
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 000bffd000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 000092f7d8]    TEXT DATA BSS ==> [0000100000 - 000092f7d8]
[    0.000000]   #4 [000bc38000 - 000bfefe9b]          RAMDISK ==> [000bc38000 - 000bfefe9b]
[    0.000000]   #5 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #6 [0000930000 - 0000937071]              BRK ==> [0000930000 - 0000937071]
[    0.000000]   #7 [0000007000 - 0000009000]          PGTABLE ==> [0000007000 - 0000009000]
[    0.000000]   #8 [0000009000 - 000000b000]          BOOTMAP ==> [0000009000 - 000000b000]
[    0.000000] found SMP MP-table at [c00fd790] fd790
[    0.000000] kvm-clock: cpu 0, msr 0:887461, boot clock
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0000bffd
[    0.000000]   HighMem  0x0000bffd -> 0x0000bffd
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0000bffd
[    0.000000] Using APIC driver default
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
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at c000000 (gap: c000000:f2ffc000)
[    0.000000] Booting paravirtualized kernel on KVM
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 15 pages/cpu @c1200000 s39448 r0 d21992 u2097152
[    0.000000] pcpu-alloc: s39448 r0 d21992 u2097152 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] kvm-clock: cpu 0, msr 0:1209461, primary cpu clock
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 48664
[    0.000000] Kernel command line: root=/dev/sda1 console=ttyS0
[    0.000000] PID hash table entries: 1024 (order: 0, 4096 bytes)
[    0.000000] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.000000] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 982980 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00000000:00000000)
[    0.000000] Memory: 180996k/196596k available (4826k kernel code, 15032k reserved, 2211k data, 672k init, 0k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xffa00000 - 0xffc00000   (2048 kB)
[    0.000000]     vmalloc : 0xcc7fd000 - 0xff9fe000   ( 818 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xcbffd000   ( 191 MB)
[    0.000000]       .init : 0xc07e0000 - 0xc0888000   ( 672 kB)
[    0.000000]       .data : 0xc05b6a1b - 0xc07df7a8   (2211 kB)
[    0.000000]       .text : 0xc0100000 - 0xc05b6a1b   (4826 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:256
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [ttyS0] enabled
[    0.000000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.000000] Detected 2394.562 MHz processor.
[    0.008000] Calibrating delay loop (skipped) preset value.. 4789.12 BogoMIPS (lpj=9578248)
[    0.008000] Security Framework initialized
[    0.008000] AppArmor: AppArmor initialized
[    0.008000] Mount-cache hash table entries: 512
[    0.008000] Initializing cgroup subsys ns
[    0.008000] Initializing cgroup subsys cpuacct
[    0.008000] Initializing cgroup subsys memory
[    0.008000] Initializing cgroup subsys devices
[    0.008005] Initializing cgroup subsys freezer
[    0.008402] Initializing cgroup subsys net_cls
[    0.008785] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.009178] CPU: L2 cache: 4096K
[    0.009443] mce: CPU supports 10 MCE banks
[    0.009817] Performance Events: unsupported p6 CPU model 2 no PMU driver, software events only.
[    0.012982] SMP alternatives: switching to UP code
[    0.028564] Freeing SMP alternatives: 19k freed
[    0.028946] ACPI: Core revision 20090903
[    0.029799] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.030264] ftrace: allocating 22402 entries in 44 pages
[    0.032102] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.033544] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.034089] CPU0: Intel QEMU Virtual CPU version 0.14.0 stepping 03
[    0.040001] Brought up 1 CPUs
[    0.040001] Total of 1 processors activated (4789.12 BogoMIPS).
[    0.040001] devtmpfs: initialized
[    0.040001] regulator: core version 0.5
[    0.040001] Time: 14:17:40  Date: 01/23/13
[    0.040001] NET: Registered protocol family 16
[    0.040001] EISA bus registered
[    0.040001] ACPI: bus type pci registered
[    0.040004] PCI: PCI BIOS revision 2.10 entry at 0xfc566, last bus=0
[    0.040579] PCI: Using configuration type 1 for base access
[    0.041621] bio: create slab <bio-0> at 0
[    0.043401] ACPI: Interpreter enabled
[    0.043745] ACPI: (supports S0 S3 S4 S5)
[    0.044150] ACPI: Using IOAPIC for interrupt routing
[    0.046146] ACPI: No dock devices found.
[    0.046524] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.047689] pci 0000:00:01.3: quirk: region b000-b03f claimed by PIIX4 ACPI
[    0.048009] pci 0000:00:01.3: quirk: region b100-b10f claimed by PIIX4 SMB
[    0.051037] ACPI: PCI Interrupt Link [LNKA] (IRQs 5 *10 11)
[    0.052081] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 *10 11)
[    0.052687] ACPI: PCI Interrupt Link [LNKC] (IRQs 5 10 *11)
[    0.053297] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 10 *11)
[    0.053902] ACPI: PCI Interrupt Link [LNKS] (IRQs 9) *0
[    0.054522] vgaarb: loaded
[    0.054894] SCSI subsystem initialized
[    0.055355] usbcore: registered new interface driver usbfs
[    0.055868] usbcore: registered new interface driver hub
[    0.056028] usbcore: registered new device driver usb
[    0.056589] ACPI: WMI: Mapper loaded
[    0.056924] PCI: Using ACPI for IRQ routing
[    0.057494] NetLabel: Initializing
[    0.057813] NetLabel:  domain hash size = 128
[    0.058211] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.058677] NetLabel:  unlabeled traffic allowed by default
[    0.059223] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.060064] hpet0: 3 comparators, 64-bit 100.000000 MHz counter
[    0.064028] Switching to clocksource kvm-clock
[    0.066104] AppArmor: AppArmor Filesystem Enabled
[    0.066611] pnp: PnP ACPI init
[    0.066916] ACPI: bus type pnp registered
[    0.067715] pnp: PnP ACPI: found 6 devices
[    0.068001] ACPI: ACPI bus type pnp unregistered
[    0.068022] PnPBIOS: Disabled
[    0.103003] NET: Registered protocol family 2
[    0.103454] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[    0.104289] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[    0.104998] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.105641] TCP: Hash tables configured (established 8192 bind 8192)
[    0.106222] TCP reno registered
[    0.106546] NET: Registered protocol family 1
[    0.106962] pci 0000:00:00.0: Limiting direct PCI/PCI transfers
[    0.107511] pci 0000:00:01.0: PIIX3: Enabling Passive Release
[    0.108062] pci 0000:00:01.0: Activating ISA DMA hang workarounds
[    0.108755] cpufreq-nforce2: No nForce2 chipset.
[    0.109207] Scanning for low memory corruption every 60 seconds
[    0.109811] audit: initializing netlink socket (disabled)
[    0.110319] type=2000 audit(1358950662.108:1): initialized
[    0.116695] Trying to unpack rootfs image as initramfs...
[    0.128065] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.129534] VFS: Disk quotas dquot_6.5.2
[    0.129937] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.130920] fuse init (API version 7.13)
[    0.131342] msgmni has been set to 353
[    0.136115] alg: No test for stdrng (krng)
[    0.136552] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.137221] io scheduler noop registered
[    0.137578] io scheduler anticipatory registered
[    0.138011] io scheduler deadline registered
[    0.138434] io scheduler cfq registered (default)
[    0.138913] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.139461] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.144202] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.144888] ACPI: Power Button [PWRF]
[    0.145514] processor LNXCPU:00: registered as cooling_device0
[    0.147441] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.148177] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.149507] brd: module loaded
[    0.150101] loop: module loaded
[    0.150454] input: Macintosh mouse button emulation as /devices/virtual/input/input1
[    0.151272] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[    0.151850] sym53c8xx 0000:00:03.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, high) -> IRQ 11
[    0.156042] isapnp: Scanning for PnP cards...
[    0.165081] sym0: <895a> rev 0x0 at pci 0000:00:03.0 irq 11
[    0.170271] sym0: No NVRAM, ID 7, Fast-40, LVD, parity checking
[    0.172014] sym0: SCSI BUS has been reset.
[    0.180945] scsi0 : sym-2.2.3
[    0.240525] scsi1 : ata_piix
[    0.240882] scsi2 : ata_piix
[    0.241174] ata1: PATA max MWDMA2 cmd 0x1f0 ctl 0x3f6 bmdma 0xc000 irq 14
[    0.241788] ata2: PATA max MWDMA2 cmd 0x170 ctl 0x376 bmdma 0xc008 irq 15
[    0.242625] Fixed MDIO Bus: probed
[    0.242970] PPP generic driver version 2.4.2
[    0.243411] tun: Universal TUN/TAP device driver, 1.6
[    0.243897] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.248411] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.249026] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.249599] uhci_hcd: USB Universal Host Controller Interface driver
[    0.250289] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 10
[    0.250825] uhci_hcd 0000:00:01.2: PCI INT D -> Link[LNKD] -> GSI 10 (level, high) -> IRQ 10
[    0.251600] uhci_hcd 0000:00:01.2: UHCI Host Controller
[    0.256254] uhci_hcd 0000:00:01.2: new USB bus registered, assigned bus number 1
[    0.257027] uhci_hcd 0000:00:01.2: irq 10, io base 0x0000c020
[    0.257669] usb usb1: configuration #1 chosen from 1 choice
[    0.264097] hub 1-0:1.0: USB hub found
[    0.264574] hub 1-0:1.0: 2 ports detected
[    0.265163] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[    0.266611] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.267224] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.272111] mice: PS/2 mouse device common for all mice
[    0.273058] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    0.274272] rtc_cmos 00:01: rtc core: registered rtc_cmos as rtc0
[    0.274942] rtc0: alarms up to one day, 114 bytes nvram, hpet irqs
[    0.275617] device-mapper: uevent: version 1.0.3
[    0.280188] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    0.281056] device-mapper: multipath: version 1.1.0 loaded
[    0.281587] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.284183] EISA: Probing bus 0 at eisa.0
[    0.284649] EISA: Detected 0 cards.
[    0.288126] cpuidle: using governor ladder
[    0.288536] cpuidle: using governor menu
[    0.288944] virtio-pci 0000:00:04.0: PCI INT A -> Link[LNKD] -> GSI 10 (level, high) -> IRQ 10
[    0.290014] TCP cubic registered
[    0.290408] NET: Registered protocol family 10
[    0.291128] lo: Disabled Privacy Extensions
[    0.291694] NET: Registered protocol family 17
[    0.292184] Using IPI No-Shortcut mode
[    0.292630] registered taskstats version 1
[    0.293143]   Magic number: 13:899:283
[    0.293520] scsi: waiting for bus probes to complete ...
[    0.294960] Freeing initrd memory: 3807k freed
[    0.603308] isapnp: No Plug & Play device found
[    3.180486] sym0: unknown interrupt(s) ignored, ISTAT=0x5 DSTAT=0x80 SIST=0x0
[    3.182861] scsi 0:0:0:0: Direct-Access     QEMU     QEMU HARDDISK    0.14 PQ: 0 ANSI: 5
[    3.185507] scsi target0:0:0: tagged command queuing enabled, command queue depth 16.
[    3.187934] scsi target0:0:0: Beginning Domain Validation
[    3.190497] scsi target0:0:0: Domain Validation skipping write tests
[    3.192549] scsi target0:0:0: Ending Domain Validation
[    3.195700] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.196282] rtc_cmos 00:01: setting system clock to 2013-01-23 14:17:43 UTC (1358950663)
[    3.197020] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    3.197562] EDD information not available.
[    3.198073] sd 0:0:0:0: [sda] 4253696 512-byte logical blocks: (2.17 GB/2.02 GiB)
[    3.199010] sd 0:0:0:0: [sda] Write Protect is off
[    3.199518] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[    3.200657]  sda: sda1 sda2 sda3
[    3.202222] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.202669] Freeing unused kernel memory: 672k freed
[    3.203280] Write protecting the kernel text: 4828k
[    3.203779] Write protecting the kernel read-only data: 1876k
Loading, please wait...
Begin: Loading essential drivers... ...
Done.
[    3.216299] udev: starting version 151
Begin: Running /scripts/init-premount ...
Done.
Begin: Mounting root file system... ...
Begin: Running /scripts/local-top ...
Done.
[    3.316434] Intel(R) PRO/1000 Network Driver - version 7.3.21-k5-NAPI
[    3.317038] Copyright (c) 1999-2006 Intel Corporation.
[    3.317619] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[    3.318148] e1000 0000:00:02.0: PCI INT A -> Link[LNKB] -> GSI 10 (level, high) -> IRQ 10
[    3.320278] FDC 0 is a S82078B
Begin: Running /scripts/local-premount ...
Done.
[    3.592861] e1000: 0000:00:02.0: e1000_probe: (PCI:33MHz:32-bit) d0:0d:46:61:08:6d
[    3.595778] kjournald starting.  Commit interval 5 seconds
[    3.596310] EXT3-fs: mounted filesystem with ordered data mode.
Begin: Running /scripts/local-bottom ...
Done.
Done.
Begin: Running /scripts/init-bottom ...
Done.
[    3.632251] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
consuming user data failed!
Traceback (most recent call last):
  File "/usr/bin/cloud-init", line 90, in <module>
    main()
  File "/usr/bin/cloud-init", line 47, in main
    cloud.consume_userdata,[],False)
  File "/usr/lib/python2.6/dist-packages/cloudinit/__init__.py", line 215, in sem_and_run
    if self.sem_has_run(semname,freq): return
  File "/usr/lib/python2.6/dist-packages/cloudinit/__init__.py", line 173, in sem_has_run
    semfile = self.sem_getpath(name,freq)
  File "/usr/lib/python2.6/dist-packages/cloudinit/__init__.py", line 167, in sem_getpath
    freqtok = self.datasource.get_instance_id()
  File "/usr/lib/python2.6/dist-packages/cloudinit/DataSourceEc2.py", line 64, in get_instance_id
    return(self.metadata['instance-id'])
KeyError: 'instance-id'
init: cloud-init main process (575) terminated with status 1
mountall: Event failed
 * Starting AppArmor profiles       
[80G Traceback (most recent call last):
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
[74G[ OK ]
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
  File "/usr/bin/landscape-is-cloud-managed", line 12, in <module>
    sys.exit(not is_cloud_managed())
  File "/usr/lib/python2.6/dist-packages/landscape/broker/registration.py", line 397, in is_cloud_managed
    raw_user_data, int(launch_index))
ValueError: invalid literal for int() with base 10: ''
landscape-client is not configured, please run landscape-config.

---

