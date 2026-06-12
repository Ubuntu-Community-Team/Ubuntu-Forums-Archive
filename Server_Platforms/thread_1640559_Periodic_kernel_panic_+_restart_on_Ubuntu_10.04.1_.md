---
title: "Periodic kernel panic + restart on Ubuntu 10.04.1 LTS"
date: 2010-12-07
forum: Server Platforms
---

### Post by realmike on 2010-12-07
Hi,

I am running Ubuntu 10.04.1 LTS on Amazon EC2 c1.xlarge instance store based instances with several EBS volumes mounted and having XFS on them.
For time to time - i.e. almost once per week server is automatically restarted due to a kernel fault. Any ideas what that can be or how to solve it ?
Below is the console output for the init sequence followed by output during 4 occasions causing a restart.
Any help is welcome.

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-309-ec2 (buildd@yellow) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #18-Ubuntu SMP Mon Oct 18 21:00:50 UTC 2010 (Ubuntu 2.6.32-309.18-ec2 2.6.32.21+drm33.7)
[    0.000000] Command line:  root=/dev/sda1 ro 4
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] Xen-provided physical RAM map:
[    0.000000]  Xen: 0000000000000000 - 00000001c0800000 (usable)
[    0.000000] last_pfn = 0x1c0800 max_arch_pfn = 0x80000000
[    0.000000] last_pfn = 0x100000 max_arch_pfn = 0x80000000
[    0.000000] init_memory_mapping: 0000000000000000-0000000100000000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] init_memory_mapping: 0000000100000000-00000001c0800000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] (4 early reservations) ==> bootmem [0000000000 - 01c0000000]
[    0.000000]   #0 [0001842000 - 000265c000]     Xen provided ==> [0001842000 - 000265c000]
[    0.000000]   #1 [0001000000 - 0001821778]    TEXT DATA BSS ==> [0001000000 - 0001821778]
[    0.000000]   #2 [000265c000 - 0002e61000]          PGTABLE ==> [000265c000 - 0002e61000]
[    0.000000]   #3 [0002e61000 - 0003469000]          PGTABLE ==> [0002e61000 - 0003469000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x001c0800
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x001c0000
[    0.000000]     0: 0x001c0800 -> 0x001c0800
[    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 18 pages/cpu @ffff88000184e000 s44248 r8192 d21288 u73728
[    0.000000] pcpu-alloc: s44248 r8192 d21288 u73728 alloc=18*4096
[    0.000000] pcpu-alloc: [0] 0 [0] 1 [0] 2 [0] 3 [0] 4 [0] 5 [0] 6 [0] 7
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1809892
[    0.000000] Kernel command line:  root=/dev/sda1 ro 4
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.000000] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 73482240 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Software IO TLB disabled
[    0.000000] Memory: 7116800k/7348224k available (4831k kernel code, 8192k absent, 222552k reserved, 2081k data, 228k init)
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:96
[    0.000000] Xen reported: 2327.494 MHz processor.
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] console [tty-1] enabled
[    0.280002] Calibrating delay using timer specific routine.. 4657.34 BogoMIPS (lpj=23286723)
[    0.280051] Security Framework initialized
[    0.280069] AppArmor: AppArmor initialized
[    0.280090] Mount-cache hash table entries: 256
[    0.280209] Initializing cgroup subsys ns
[    0.280216] Initializing cgroup subsys cpuacct
[    0.280221] Initializing cgroup subsys memory
[    0.280233] Initializing cgroup subsys devices
[    0.280237] Initializing cgroup subsys freezer
[    0.280271] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.280277] CPU: L2 cache: 6144K
[    0.280290] SMP alternatives: switching to UP code
[    0.309108] Brought up 1 CPUs
[    0.309209] devtmpfs: initialized
[    0.309676] NET: Registered protocol family 16
[    0.310523] SMP alternatives: switching to SMP code
[    0.338724] Initializing CPU#1
[    0.338724] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.338724] CPU: L2 cache: 6144K
[    0.640447] Initializing CPU#2
[    0.640450] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.640450] CPU: L2 cache: 6144K
[    0.960457] Initializing CPU#3
[    0.960457] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.960457] CPU: L2 cache: 6144K
[    1.360512] Initializing CPU#4
[    1.360512] CPU: L1 I cache: 32K, L1 D cache: 32K
[    1.360512] CPU: L2 cache: 6144K
[    1.840476] Initializing CPU#5
[    1.840476] CPU: L1 I cache: 32K, L1 D cache: 32K
[    1.840476] CPU: L2 cache: 6144K
[    2.350507] Initializing CPU#6
[    2.350507] CPU: L1 I cache: 32K, L1 D cache: 32K
[    2.350507] CPU: L2 cache: 6144K
[    2.950470] Initializing CPU#7
[    2.950470] CPU: L1 I cache: 32K, L1 D cache: 32K
[    2.950470] CPU: L2 cache: 6144K
[    3.630165] Brought up 8 CPUs
[    3.630183] PCI: Fatal: No config space access function found
[    3.630187] PCI: setting up Xen PCI frontend stub
[    3.631122] bio: create slab <bio-0> at 0
[    3.631618] vgaarb: loaded
[    3.631817] suspend: event channel 51
[    3.632193] xen_mem: Initialising balloon driver.
[    3.633258] PCI: System does not support PCI
[    3.633258] PCI: System does not support PCI
[    3.633258] NET: Registered protocol family 8
[    3.633258] NET: Registered protocol family 20
[    3.633258] NetLabel: Initializing
[    3.633258] NetLabel:  domain hash size = 128
[    3.633258] NetLabel:  protocols = UNLABELED CIPSOv4
[    3.633258] NetLabel:  unlabeled traffic allowed by default
[    3.633258] Switching to clocksource xen
[    3.633275] AppArmor: AppArmor Filesystem Enabled
[    3.633275] NET: Registered protocol family 2
[    3.633275] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    3.633521] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    3.634960] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    3.635355] TCP: Hash tables configured (established 262144 bind 65536)
[    3.635362] TCP reno registered
[    3.635546] NET: Registered protocol family 1
[    3.635647] platform rtc_cmos: registered platform RTC device (no PNP device found)
[    3.636065] audit: initializing netlink socket (disabled)
[    3.636082] type=2000 audit(1289889206.004:1): initialized
[    3.642797] VFS: Disk quotas dquot_6.5.2
[    3.642850] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    3.643012] DLM (built Oct 18 2010 21:03:05) installed
[    3.643512] JFS: nTxBlock = 8192, nTxLock = 65536
[    3.646646] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
[    3.647919] SGI XFS Quota Management subsystem
[    3.648644] Slow work thread pool: Starting up
[    3.648788] Slow work thread pool: Ready
[    3.648788] GFS2 (built Oct 18 2010 21:04:10) installed
[    3.648788] msgmni has been set to 14336
[    3.649346] alg: No test for stdrng (krng)
[    3.649356] io scheduler noop registered
[    3.649356] io scheduler anticipatory registered
[    3.649356] io scheduler deadline registered (default)
[    3.649356] io scheduler cfq registered
[    3.662218] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    3.663210] brd: module loaded
[    3.663611] loop: module loaded
[    3.666039] Xen virtual console successfully installed as tty1
[    3.666090] Event-channel device installed.
[    3.681340] netfront: Initialising virtual ethernet driver.
[    3.682843] xen-vbd: registered block device major 8
[    3.683551]  sdb: unknown partition table
[    3.708059]  sdc: unknown partition table
[    3.708876]  sdd: unknown partition table
[    3.709781]  sde: unknown partition table
[    3.711062] PPP generic driver version 2.4.2
[    3.711761] Equalizer2002: Simon Janes (simon@ncm.com) and David S. Miller (davem@redhat.com)
[    3.711952] tun: Universal TUN/TAP device driver, 1.6
[    3.711957] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    3.712858] i8042.c: No controller found.
[    3.712924] mice: PS/2 mouse device common for all mice
[    3.712999] rtc_cmos rtc_cmos: rtc core: registered rtc_cmos as rtc0
[    3.713059] Driver for 1-wire Dallas network protocol.
[    3.713221] device-mapper: uevent: version 1.0.3
[    3.713331] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    3.713701] NET: Registered protocol family 17
[    3.713833] registered taskstats version 1
[    3.816134] /build/buildd/linux-ec2-2.6.32/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[    3.874505] kjournald starting.  Commit interval 5 seconds
[    3.874514] EXT3-fs: mounted filesystem with writeback data mode.
[    3.874532] VFS: Mounted root (ext3 filesystem) readonly on device 8:1.
[    3.907603] devtmpfs: mounted
[    3.907693] Freeing unused kernel memory: 228k freed
[    3.907818] Write protecting the kernel read-only data: 6484k

----------------------------------------------------

First restart:

[1765182.703661] BUG: unable to handle kernel NULL pointer dereference at (null)
[1765182.703679] IP: [<(null)>] (null)
[1765182.703685] PGD 0
[1765182.703690] Oops: 0010 [#1] SMP
[1765182.703696] last sysfs file: /sys/devices/xen/vbd-2289/block/sdp1/stat
[1765182.703701] CPU 5
[1765182.703705] Modules linked in: nfsd nfs lockd nfs_acl auth_rpcgss ipv6 sunrpc
[1765182.703720] Pid: 31, comm: ksoftirqd/5 Not tainted 2.6.32-309-ec2 #18-Ubuntu
[1765182.703725] RIP: e030:[<0000000000000000>]  [<(null)>] (null)
[1765182.703731] RSP: e02b:ffff8800018abeb0  EFLAGS: 00010202
[1765182.703735] RAX: 0000000000000003 RBX: ffffffff8166e3c0 RCX: 0000000000000000
[1765182.703740] RDX: ffffffffff5fc000 RSI: 0000000000000000 RDI: ffff8800dfb9dd00
[1765182.703745] RBP: ffff8800018abef8 R08: 4000000000000080 R09: 0000000000000001
[1765182.703751] R10: 0000000000000000 R11: 0000000000000000 R12: ffff8800018aff20
[1765182.703755] R13: ffff8800dfb9dd00 R14: 0000000000000004 R15: 0000000000000000
[1765182.703763] FS:  00007f4a1b3f37c0(0000) GS:ffff8800018a8000(0000) knlGS:0000000000000000
[1765182.703769] CS:  e033 DS: 0000 ES: 0000 CR0: 000000008005003b
[1765182.703774] CR2: 0000000000000000 CR3: 0000000001001000 CR4: 0000000000002660
[1765182.703779] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[1765182.703785] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000000
[1765182.703791] Process ksoftirqd/5 (pid: 31, threadinfo ffff8801bf99a000, task ffff8801bf998940)
[1765182.703796] Stack:
[1765182.703800]  ffffffff81090587 ffff8800018aff50 ffff88009ca31a00 0000000000007c20
[1765182.703809] <0> ffffffff8166e3c0 ffff8800018aff20 0000000000000100 0000000000000009
[1765182.703818] <0> ffff8801bf99bfd8 ffff8800018abf28 ffffffff81091180 0000000000000048
[1765182.703829] Call Trace:
[1765182.703833]  <IRQ>
[1765182.703843]  [<ffffffff81090587>] ? rcu_do_batch+0xe7/0x310
[1765182.703849]  [<ffffffff81091180>] __rcu_process_callbacks+0x90/0x190
[1765182.703854]  [<ffffffff810912a6>] rcu_process_callbacks+0x26/0x50
[1765182.703862]  [<ffffffff81043f05>] __do_softirq+0xd5/0x220
[1765182.703869]  [<ffffffff813a14a4>] ? evtchn_do_upcall+0x224/0x250
[1765182.703876]  [<ffffffff8100a80c>] call_softirq+0x1c/0x30
[1765182.703880]  <EOI>
[1765182.703884]  [<ffffffff8100ba85>] do_softirq+0xb5/0xf0
[1765182.703889]  [<ffffffff810439d0>] ksoftirqd+0x70/0x100
[1765182.703894]  [<ffffffff81043960>] ? ksoftirqd+0x0/0x100
[1765182.703899]  [<ffffffff81059a8e>] kthread+0x8e/0xa0
[1765182.703904]  [<ffffffff8100a70a>] child_rip+0xa/0x20
[1765182.703909]  [<ffffffff81059a00>] ? kthread+0x0/0xa0
[1765182.703914]  [<ffffffff8100a700>] ? child_rip+0x0/0x20
[1765182.703918] Code:  Bad RIP value.
[1765182.703927] RIP  [<(null)>] (null)
[1765182.703931]  RSP <ffff8800018abeb0>
[1765182.703934] CR2: 0000000000000000
[1765182.703940] ---[ end trace ab5156132ffc16af ]---
[1765182.703944] Kernel panic - not syncing: Fatal exception in interrupt
[1765182.703950] Pid: 31, comm: ksoftirqd/5 Tainted: G      D    2.6.32-309-ec2 #18-Ubuntu
[1765182.703954] Call Trace:
[1765182.703957]  <IRQ>  [<ffffffff814ad4cc>] panic+0x73/0x148
[1765182.703967]  [<ffffffff814b178e>] oops_end+0xee/0xf0
[1765182.703974]  [<ffffffff8101805b>] no_context+0xeb/0x180
[1765182.703979]  [<ffffffff8101823d>] __bad_area_nosemaphore+0x14d/0x200
[1765182.703985]  [<ffffffff810e30fe>] ? slab_destroy+0x2e/0x80
[1765182.703991]  [<ffffffff810182fe>] bad_area_nosemaphore+0xe/0x10
[1765182.703996]  [<ffffffff814b2fcc>] do_page_fault+0x2cc/0x390
[1765182.704001]  [<ffffffff814b0c78>] page_fault+0x28/0x30
[1765182.704006]  [<ffffffff81090587>] ? rcu_do_batch+0xe7/0x310
[1765182.704012]  [<ffffffff81091180>] __rcu_process_callbacks+0x90/0x190
[1765182.704017]  [<ffffffff810912a6>] rcu_process_callbacks+0x26/0x50
[1765182.704022]  [<ffffffff81043f05>] __do_softirq+0xd5/0x220
[1765182.704027]  [<ffffffff813a14a4>] ? evtchn_do_upcall+0x224/0x250
[1765182.704033]  [<ffffffff8100a80c>] call_softirq+0x1c/0x30
[1765182.704037]  <EOI>  [<ffffffff8100ba85>] do_softirq+0xb5/0xf0
[1765182.704045]  [<ffffffff810439d0>] ksoftirqd+0x70/0x100
[1765182.704049]  [<ffffffff81043960>] ? ksoftirqd+0x0/0x100
[1765182.704054]  [<ffffffff81059a8e>] kthread+0x8e/0xa0
[1765182.704059]  [<ffffffff8100a70a>] child_rip+0xa/0x20
[1765182.704064]  [<ffffffff81059a00>] ? kthread+0x0/0xa0
[1765182.704068]  [<ffffffff8100a700>] ? child_rip+0x0/0x20

------------------------------------------------

Second restart several days later:

[117749.429421] BUG: unable to handle kernel NULL pointer dereference at (null)
[117749.429439] IP: [<(null)>] (null)
[117749.429445] PGD 3cca3067 PUD 5723f067 PMD 0
[117749.429457] Oops: 0010 [#1] SMP
[117749.429463] last sysfs file: /sys/devices/xen/vbd-2289/block/sdp1/stat
[117749.429468] CPU 2
[117749.429472] Modules linked in: nfsd nfs lockd nfs_acl auth_rpcgss ipv6 sunrpc
[117749.429491] Pid: 30900, comm: stat Not tainted 2.6.32-309-ec2 #18-Ubuntu
[117749.429496] RIP: e030:[<0000000000000000>]  [<(null)>] (null)
[117749.429501] RSP: e02b:ffff880001875e08  EFLAGS: 00010202
[117749.429505] RAX: 0000000000000003 RBX: ffffffff8166e3c0 RCX: 0000000000000000
[117749.429510] RDX: ffffffffff5fc000 RSI: 0000000000000000 RDI: ffff8801b7fca280
[117749.429515] RBP: ffff880001875e50 R08: 0000000000000120 R09: 0000000000000001
[117749.429520] R10: 0000000000000000 R11: 0000000000000000 R12: ffff880001879f20
[117749.429524] R13: ffff8801b7fca280 R14: 0000000000000004 R15: 0000000000000000
[117749.429532] FS:  00007f2e9303e700(0000) GS:ffff880001872000(0000) knlGS:0000000000000000
[117749.429537] CS:  e033 DS: 0000 ES: 0000 CR0: 000000008005003b
[117749.429541] CR2: 0000000000000000 CR3: 000000009321f000 CR4: 0000000000002660
[117749.429546] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[117749.429551] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000000
[117749.429558] Process stat (pid: 30900, threadinfo ffff8800a9c8c000, task ffff8800e2160940)
[117749.429562] Stack:
[117749.429565]  ffffffff81090587 ffff880001879f50 ffff880045e90d20 ffff8801bf915820
[117749.429574] <0> ffffffff8166e3c0 ffff880001879f20 0000000000000100 0000000000000009
[117749.429582] <0> ffff8800a9c8dfd8 ffff880001875e80 ffffffff81091180 0000000000000048
[117749.429592] Call Trace:
[117749.429595]  <IRQ>
[117749.429605]  [<ffffffff81090587>] ? rcu_do_batch+0xe7/0x310
[117749.429613]  [<ffffffff81091180>] __rcu_process_callbacks+0x90/0x190
[117749.429618]  [<ffffffff810912a6>] rcu_proces

---------------------------------------

In addition to these I have also observed such messages prior to restart:

[262780.847239] ------------[ cut here ]------------
[262780.847254] kernel BUG at /build/buildd/linux-ec2-2.6.32/kernel/cred.c:101!
[262780.847260] invalid opcode: 0000 [#1] SMP
[262780.847266] last sysfs file: /sys/devices/xen/vbd-2289/block/sdp1/stat
[262780.847271] CPU 2
[262780.847275] Modules linked in: nfsd nfs lockd nfs_acl auth_rpcgss ipv6 sunrpc
[262780.847289] Pid: 19, comm: ksoftirqd/2 Not tainted 2.6.32-309-ec2 #18-Ubuntu
[262780.847295] RIP: e030:[<ffffffff8105fba4>]  [<ffffffff8105fba4>] release_tgcred_rcu+0x44/0x50
[262780.847309] RSP: e02b:ffff880001875e98  EFLAGS: 00010286
[262780.847315] RAX: 00000000ffffffff RBX: ffff88008d761460 RCX: ffffffffff5fc000
[262780.847322] RDX: ffffffffff5fc000 RSI: 0000000000000000 RDI: ffff88008d761460
[262780.847329] RBP: ffff880001875ea8 R08: ffff8801bf936000 R09: 0000000000000000
[262780.847345] R10: 0000000000000000 R11: 0000000000000000 R12: ffff88008d761440
[262780.847351] R13: ffff88008d761460 R14: 0000000000000003 R15: ffff8801ba82e980
[262780.847361] FS:  00007fd58fa7c700(0000) GS:ffff880001872000(0000) knlGS:0000000000000000
[262780.847368] CS:  e033 DS: 0000 ES: 0000 CR0: 000000008005003b
[262780.847373] CR2: 00007f063aa64740 CR3: 00000001be142000 CR4: 0000000000002660
[262780.847379] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[262780.847385] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000000
[262780.847393] Process ksoftirqd/2 (pid: 19, threadinfo ffff8801bf936000, task ffff8801bf934640)
[262780.847399] Stack:
[262780.847402]  ffffffff8166e3c0 ffff880001879f20 ffff880001875ef8 ffffffff81090587
[262780.847410] <0> ffff880001879f50 ffff88000ff5c860 0000000000007c20 ffffffff8166e3c0
[262780.847420] <0> ffff880001879f20 ffffffff8166e3c0 00000000004c6a9d ffff8801bf937fd8
[262780.847430] Call Trace:
[262780.847434]  <IRQ>
[262780.847441]  [<ffffffff81090587>] rcu_do_batch+0xe7/0x310
[262780.847447]  [<ffffffff81091180>] __rcu_process_callbacks+0x90/0x190
[262780.847452]  [<ffffffff810912a6>] rcu_process_callbacks+0x26/0x50
[262780.847458]  [<ffffffff81043f05>] __do_softirq+0xd5/0x220
[262780.847465]  [<ffffffff813a14a4>] ? evtchn_do_upcall+0x224/0x250
[262780.847472]  [<ffffffff8100a80c>] call_softirq+0x1c/0x30
[262780.847476]  <EOI>
[262780.847480]  [<ffffffff8100ba85>] do_softirq+0xb5/0xf0
[262780.847485]  [<ffffffff810439d0>] ksoftirqd+0x70/0x100
[262780.847490]  [<ffffffff81043960>] ? ksoftirqd+0x0/0x100
[262780.847496]  [<ffffffff81059a8e>] kthread+0x8e/0xa0
[262780.847501]  [<ffffffff8100a70a>] child_rip+0xa/0x20
[262780.847506]  [<ffffffff81059a00>] ? kthread+0x0/0xa0
[262780.847511]  [<ffffffff8100a700>] ? child_rip+0x0/0x20
[262780.847514] Code: 67 e0 85 c0 75 25 48 8b 7f f0 e8 78 5f 27 00 48 8b 7b f8 e8 6f 5f 27 00 4c 89 e7 e8 c7 32 08 00 48 8b 1c 24 4c 8b 64 24 08 c9 c3 <0f> 0b eb fe 0f 1f 84 00 00 00 00 00 55 48 89 e5 41 54 49 89 fc
[262780.847580] RIP  [<ffffffff8105fba4>] release_tgcred_rcu+0x44/0x50
[262780.847587]  RSP <ffff880001875e98>
[262780.847593] ---[ end trace e6539ab6d8ea7470 ]---
[262780.847597] Kernel panic - not syncing: Fatal exception in interrupt
[262780.847603] Pid: 19, comm: ksoftirqd/2 Tainted: G      D    2.6.32-309-ec2 #18-Ubuntu
[262780.847608] Call Trace:
[262780.847610]  <IRQ>  [<ffffffff814ad4cc>] panic+0x73/0x148
[262780.847621]  [<ffffffff814b178e>] oops_end+0xee/0xf0
[262780.847626]  [<ffffffff8100dbd6>] die+0x56/0x90
[262780.847630]  [<ffffffff814b0e74>] do_trap+0xc4/0x170
[262780.847636]  [<ffffffff8100b3a0>] do_invalid_op+0xb0/0xd0
[262780.847640]  [<ffffffff8105fba4>] ? release_tgcred_rcu+0x44/0x50
[262780.847647]  [<ffffffff8103430a>] ? enqueue_entity+0x11a/0x1a0
[262780.847652]  [<ffffffff810343cb>] ? enqueue_task_fair+0x3b/0x50
[262780.847657]  [<ffffffff8100a495>] invalid_op+0x25/0x30
[262780.847662]  [<ffffffff8105fba4>] ? release_tgcred_rcu+0x44/0x50
[262780.847669]  [<ffffffff810eefbe>] ? file_free_rcu+0x2e/0x40
[262780.847674]  [<ffffffff81090587>] rcu_do_batch+0xe7/0x310
[262780.847680]  [<ffffffff81091180>] __rcu_process_callbacks+0x90/0x190
[262780.847685]  [<ffffffff810912a6>] rcu_process_callbacks+0x26/0x50
[262780.847691]  [<ffffffff81043f05>] __do_softirq+0xd5/0x220
[262780.847696]  [<ffffffff813a14a4>] ? evtchn_do_upcall+0x224/0x250
[262780.847702]  [<ffffffff8100a80c>] call_softirq+0x1c/0x30
[262780.847705]  <EOI>  [<ffffffff8100ba85>] do_softirq+0xb5/0xf0
[262780.847712]  [<ffffffff810439d0>] ksoftirqd+0x70/0x100
[262780.847717]  [<ffffffff81043960>] ? ksoftirqd+0x0/0x100
[262780.847722]  [<ffffffff81059a8e>] kthread+0x8e/0xa0
[262780.847727]  [<ffffffff8100a70a>] child_rip+0xa/0x20
[262780.847732]  [<ffffffff81059a00>] ? kthread+0x0/0xa0
[262780.847737]  [<ffffffff8100a700>] ? child_rip+0x0/0x20

-------------------------------

On another occasion:

[171745.019775] kernel tried to execute NX-protected page - exploit attempt? (uid: 0)
[171745.019789] BUG: unable to handle kernel paging request at ffff8801b2f0ecc0

------------------------------

Looking forward to any leads that can help with this.

Best regards,
Mike.

---

