---
title: "XEN Crashing on Opteron CPUs"
date: 2012-03-24
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by AdrianSt on 2012-03-24
Hello,

I experienced core dumps (Illegal Instruction) on 2 new Opteron 2-way 6274 systems while using XEN 4.1.2.

I could make following observations in different configurations:
2x Opteron 6274: Ubuntu Precise w/o XEN = WORKING
2x Opteron 6274: Ubuntu Precise + XEN 4.1.2 = NOT working
2x Opteron 6274: Ubuntu Oneiric + XEN 4.1.1 = WORKING
2x Opteron 6274: Fedora 16 + XEN 4.1.2 + Kernel 3.1 = WORKING
2x Opteron 6274: Fedora 16 + XEN 4.1.2 + Kernel 3.2 = NOT working
2x Opteron 6274: Debian Testing (wheezy) + XEN 4.1.2 + Kernel 3.2.0-2 = WORKING
2x Xeon E5520: Ubuntu Precise + XEN 4.1.2 = WORKING

The only bug I came across is this here: [https://bugzilla.redhat.com/show_bug.cgi?id=802407](https://bugzilla.redhat.com/show_bug.cgi?id=802407)

Here is what 'dmesg' gave me with Opteron 6274+Ubuntu Precise+XEN since even the bug reporting tools aren't working at all:

[    7.646652] XENBUS: Unable to read cpu state
[    7.646819] XENBUS: Unable to read cpu state
[    7.646961] XENBUS: Unable to read cpu state
[    7.647104] XENBUS: Unable to read cpu state
[    7.647279] XENBUS: Unable to read cpu state
[    7.647444] XENBUS: Unable to read cpu state
[    7.647577] XENBUS: Unable to read cpu state
[    7.647740] XENBUS: Unable to read cpu state
[    7.647897] XENBUS: Unable to read cpu state
[    7.648381] XENBUS: Unable to read cpu state
[    7.648519] XENBUS: Unable to read cpu state
[    7.648690] XENBUS: Unable to read cpu state
[    7.746468] Process 1242(apport) has RLIMIT_CORE set to 1
[    7.746474] Aborting core
[    7.864390] Process 1244(apport) has RLIMIT_CORE set to 1
[    7.864396] Aborting core
[   17.836071] eth0: no IPv6 routers present
[  104.758221] do_trap: 16 callbacks suppressed
[  104.758229] landscape-sysin[1369] trap invalid opcode ip:7f0c026e25fc sp:7fff04960670 error:0 in libm-2.15.so[7f0c026a0000+f9000]
[  104.801393] apport[1370] trap invalid opcode ip:7f99e46325fc sp:7ffffaa65150 error:0 in libm-2.15.so[7f99e45f0000+f9000]
[  104.801422] Process 1370(apport) has RLIMIT_CORE set to 1
[  104.801426] Aborting core
[  106.347313] xm[1537] trap invalid opcode ip:7fe8b9d425fc sp:7fff5311b070 error:0 in libm-2.15.so[7fe8b9d00000+f9000]
[  106.390681] apport[1549] trap invalid opcode ip:7f789132a5fc sp:7fff4c8878b0 error:0 in libm-2.15.so[7f78912e8000+f9000]
[  106.390710] Process 1549(apport) has RLIMIT_CORE set to 1
[  106.390714] Aborting core
[  216.122619] landscape-sysin[1568] trap invalid opcode ip:7ffeee0525fc sp:7fffa8bd1c50 error:0 in libm-2.15.so[7ffeee010000+f9000]
[  216.165290] apport[1569] trap invalid opcode ip:7f75907ba5fc sp:7fffd174a970 error:0 in libm-2.15.so[7f7590778000+f9000]
[  216.165319] Process 1569(apport) has RLIMIT_CORE set to 1
[  216.165323] Aborting core
[  219.885725] python[1737] trap invalid opcode ip:7faa42cc25fc sp:7fff7aa3cdb0 error:0 in libm-2.15.so[7faa42c80000+f9000]
[  219.928920] apport[1738] trap invalid opcode ip:7f3fa98325fc sp:7fffde9cc030 error:0 in libm-2.15.so[7f3fa97f0000+f9000]
[  219.928948] Process 1738(apport) has RLIMIT_CORE set to 1
[  219.928952] Aborting core

Hoping for a fix as LTS is the way to go on servers and opterons just work fine with oneiric.

---

### Post by dcstar on 2012-03-25
> **AdrianSt said:**
> Hello,

I experienced core dumps (Illegal Instruction) on 2 new Opteron 2-way 6274 systems while using XEN 4.1.2.
..........
Hoping for a fix as LTS is the way to go on servers and opterons just work fine with oneiric.

So what is the Launchpad bug **you **have reported?

---

### Post by AdrianSt on 2012-03-25
I filed it under eglibc as the debugging messages are hinting to it.

[https://bugs.launchpad.net/bugs/956051](https://bugs.launchpad.net/bugs/956051)

---

### Post by AdrianSt on 2012-03-30
Another observation:
Different Opteron CPU (6128) - dom0 booting fine, xm tools working, but the domU is crashing.

```

[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.2.0-20-generic (buildd@allspice) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu3) ) #33-Ubuntu SMP Tue Mar 27 16:42:26 UTC 2012 (Ubuntu 3.2.0-20.33-generic 3.2.12)
[    0.000000] Command line: root=/dev/xvda2 ro xencons=tty console=tty1 console=hvc0
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] ACPI in unprivileged domain disabled
[    0.000000] Released 0 pages of unused memory
[    0.000000] Set 0 page(s) to 1-1 mapping
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  Xen: 0000000000000000 - 00000000000a0000 (usable)
[    0.000000]  Xen: 00000000000a0000 - 0000000000100000 (reserved)
[    0.000000]  Xen: 0000000000100000 - 0000000080800000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI not present or invalid.
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x80800 max_arch_pfn = 0x400000000
[    0.000000] init_memory_mapping: 0000000000000000-0000000080800000
[    0.000000] RAMDISK: 02060000 - 0477c000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000080800000
[    0.000000] Initmem setup node 0 0000000000000000-0000000080800000
[    0.000000]   NODE_DATA [000000007fffb000 - 000000007fffffff]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   empty
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x000000a0
[    0.000000]     0: 0x00000100 -> 0x00080800
[    0.000000] SFI: Simple Firmware Interface v0.81 http://simplefirmware.org
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] No local APIC present
[    0.000000] APIC: disable apic facility
[    0.000000] APIC: switched to apic NOOP
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80800000 (gap: 80800000:7f800000)
[    0.000000] Booting paravirtualized kernel on Xen
[    0.000000] Xen version: 4.1.2 (preserve-AD)
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88007ff53000 s83072 r8192 d23424 u114688
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 517009
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: root=/dev/xvda2 ro xencons=tty console=tty1 console=hvc0
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Memory: 1997192k/2105344k available (6565k kernel code, 448k absent, 107704k reserved, 6639k data, 920k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:16640 nr_irqs:304 16
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] console [hvc0] enabled
[    0.000000] allocated 17825792 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] installing Xen timer for CPU 0
[    0.000000] Detected 2000.176 MHz processor.
[    0.000000] Marking TSC unstable due to TSCs unsynchronized
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 4000.35 BogoMIPS (lpj=8000704)
[    0.004000] pid_max: default: 32768 minimum: 301
[    0.004000] Security Framework initialized
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Yama: becoming mindful.
[    0.004000] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.004000] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.004000] Mount-cache hash table entries: 256
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] Initializing cgroup subsys devices
[    0.004000] Initializing cgroup subsys freezer
[    0.004000] Initializing cgroup subsys blkio
[    0.004000] Initializing cgroup subsys perf_event
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 5
[    0.004000] SMP alternatives: switching to UP code
[    0.004000] ftrace: allocating 27049 entries in 107 pages
[    0.004099] cpu 0 spinlock event irq 17
[    0.004154] Performance Events: 
[    0.004161] no APIC, boot with the "lapic" boot parameter to force-enable it.
[    0.004169] no hardware sampling interrupt available.
[    0.004187] Broken PMU hardware detected, using software events only.
[    0.004378] NMI watchdog disabled (cpu0): hardware events not enabled
[    0.004499] installing Xen timer for CPU 1
[    0.004519] cpu 1 spinlock event irq 23
[    0.004555] SMP alternatives: switching to SMP code
[    0.008122] NMI watchdog disabled (cpu1): hardware events not enabled
[    0.008289] installing Xen timer for CPU 2
[    0.008320] cpu 2 spinlock event irq 29
[    0.008475] NMI watchdog disabled (cpu2): hardware events not enabled
[    0.008581] installing Xen timer for CPU 3
[    0.008598] cpu 3 spinlock event irq 35
[    0.008739] NMI watchdog disabled (cpu3): hardware events not enabled
[    0.008774] Brought up 4 CPUs
[    0.008939] devtmpfs: initialized
[    0.009628] EVM: security.selinux
[    0.009634] EVM: security.SMACK64
[    0.009639] EVM: security.capability
[    0.009701] Grant table initialized
[    0.009701] print_constraints: dummy: 
[    0.031425] RTC time: 165:165:165, date: 165/165/65
[    0.031498] NET: Registered protocol family 16
[    0.031652] Trying to unpack rootfs image as initramfs...
[    0.044361] Extended Config Space enabled on 0 nodes
[    0.045393] PCI: setting up Xen PCI frontend stub
[    0.056234] bio: create slab <bio-0> at 0
[    0.056377] ACPI: Interpreter disabled.
[    0.057111] xen/balloon: Initialising balloon driver.
[    0.058426] xen-balloon: Initialising balloon driver.
[    0.058672] vgaarb: loaded
[    0.058799] i2c-core: driver [aat2870] using legacy suspend method
[    0.058806] i2c-core: driver [aat2870] using legacy resume method
[    0.058895] SCSI subsystem initialized
[    0.059022] usbcore: registered new interface driver usbfs
[    0.059039] usbcore: registered new interface driver hub
[    0.059096] usbcore: registered new device driver usb
[    0.059232] PCI: System does not support PCI
[    0.059239] PCI: System does not support PCI
[    0.059354] NetLabel: Initializing
[    0.059360] NetLabel:  domain hash size = 128
[    0.059366] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.059388] NetLabel:  unlabeled traffic allowed by default
[    0.059455] Switching to clocksource xen
[    0.064624] AppArmor: AppArmor Filesystem Enabled
[    0.064659] pnp: PnP ACPI: disabled
[    0.068125] NET: Registered protocol family 2
[    0.068396] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[    0.070223] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    0.093934] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.094261] TCP: Hash tables configured (established 262144 bind 65536)
[    0.094272] TCP reno registered
[    0.094296] UDP hash table entries: 1024 (order: 3, 32768 bytes)
[    0.094330] UDP-Lite hash table entries: 1024 (order: 3, 32768 bytes)
[    0.094452] NET: Registered protocol family 1
[    0.094588] platform rtc_cmos: registered platform RTC device (no PNP device found)
[    0.094996] audit: initializing netlink socket (disabled)
[    0.095014] type=2000 audit(1333099671.473:1): initialized
[    0.096806] Freeing initrd memory: 40048k freed
[    0.127151] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.129157] VFS: Disk quotas dquot_6.5.2
[    0.129235] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.129884] fuse init (API version 7.17)
[    0.130013] msgmni has been set to 3978
[    0.130686] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.130747] io scheduler noop registered
[    0.130755] io scheduler deadline registered
[    0.130796] io scheduler cfq registered (default)
[    0.130897] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.130931] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.131517] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.376381] Linux agpgart interface v0.103
[    0.378197] brd: module loaded
[    0.379134] loop: module loaded
[    0.382645] blkfront device/vbd/51714 num-ring-pages 1 nr_ents 32.
[    0.383471] Fixed MDIO Bus: probed
[    0.383505] tun: Universal TUN/TAP device driver, 1.6
[    0.383512] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.383587] PPP generic driver version 2.4.2
[    0.383650] Initialising Xen virtual ethernet driver.
[    0.386195] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.386219] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.386237] uhci_hcd: USB Universal Host Controller Interface driver
[    0.386282] usbcore: registered new interface driver libusual
[    0.386313] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    0.387131] i8042: No controller found
[    0.387242] mousedev: PS/2 mouse device common for all mice
[    0.396355] blkfront: xvda2: barrier or flush: disabled
[    0.427209] rtc_cmos rtc_cmos: rtc core: registered rtc_cmos as rtc0
[    0.427290] rtc_cmos: probe of rtc_cmos failed with error -38
[    0.427398] device-mapper: uevent: version 1.0.3
[    0.427603] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    0.427621] EFI Variables Facility v0.08 2004-May-17
[    0.427965] TCP cubic registered
[    0.428128] NET: Registered protocol family 10
[    0.429062] NET: Registered protocol family 17
[    0.429094] Registering the dns_resolver key type
[    0.429312] registered taskstats version 1
[    0.443855] XENBUS: Device with no driver: device/console/0
[    0.443878]   Magic number: 1:252:3141
[    0.443917] /build/buildd/linux-3.2.0/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[    0.443980] powernow-k8: Found 1 AMD Opteron(tm) Processor 6128 (4 cpu cores) (version 2.20.00)
[    0.444000] [Firmware Bug]: powernow-k8: No compatible ACPI _PSS objects found.
[    0.444002] [Firmware Bug]: powernow-k8: Try again with latest BIOS.
[    0.444015] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.444021] EDD information not available.
[    0.444605] Freeing unused kernel memory: 920k freed
[    0.444882] Write protecting the kernel read-only data: 12288k
[    0.451931] Freeing unused kernel memory: 1608k freed
[    0.453010] Freeing unused kernel memory: 1200k freed
Loading, please wait...
[    0.514704] udevd[94]: starting version 175
Begin: Loading essential drivers ... done.
Begin: Running /scripts/init-premount ... done.
Begin: Mounting root file system ... Begin: Running /scripts/local-top ... done.
Begin: Running /scripts/local-premount ... done.
[    5.645183] EXT4-fs (xvda2): mounted filesystem with ordered data mode. Opts: (null)
Begin: Running /scripts/local-bottom ... done.
done.
Begin: Running /scripts/init-bottom ... done.
[    5.928404] init[1] general protection ip:7fde99d09262 sp:7fffa6932230 error:0 in libc-2.7.so[7fde99ceb000+158000]
[    5.928682] Kernel panic - not syncing: Attempted to kill init!
[    5.928694] Pid: 1, comm: init Not tainted 3.2.0-20-generic #33-Ubuntu
[    5.928702] Call Trace:
[    5.928718]  [<ffffffff816438d3>] panic+0x91/0x1a7
[    5.928729]  [<ffffffff8106b2b5>] forget_original_parent+0x245/0x250
[    5.928739]  [<ffffffff8106b2d7>] exit_notify+0x17/0x160
[    5.928749]  [<ffffffff8106bbb3>] do_exit+0x1f3/0x420
[    5.928757]  [<ffffffff8106bf84>] do_group_exit+0x44/0xa0
[    5.928766]  [<ffffffff8107ce0c>] get_signal_to_deliver+0x21c/0x420
[    5.928776]  [<ffffffff81013865>] do_signal+0x45/0x130
[    5.928786]  [<ffffffff8100aa6f>] ? xen_restore_fl_direct_reloc+0x4/0x4
[    5.928796]  [<ffffffff8165c0fe>] ? _raw_spin_unlock_irqrestore+0x1e/0x30
[    5.928806]  [<ffffffff8107beab>] ? force_sig_info+0xdb/0x100
[    5.928815]  [<ffffffff81013b15>] do_notify_resume+0x65/0x80
[    5.928824]  [<ffffffff8165c4bc>] retint_signal+0x48/0x8c

```

---

