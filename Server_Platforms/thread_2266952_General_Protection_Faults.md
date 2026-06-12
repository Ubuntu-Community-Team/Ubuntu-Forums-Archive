---
title: "General Protection Faults"
date: 2015-02-26
forum: Server Platforms
---

### Post by bsntech on 2015-02-26
Ubuntu running kernel 3.2.0-60.

Two days ago, early in the morning, the load average of the machine started going on a constant uphill line. CPU usage very low with about 85% idle. Memory usage low as well with only about 2 MB of swap showed as used.

My first thought was because those two items were OK - that it must have been a problem with the hard drive and that the hard drive was inaccessible for reading/writing.

Number of processes are around 185 on a regular basis. After about five hours, the load was up to over 400 - and the number of processes was up to almost 900. As cron jobs ran or other processes, they just kept adding on.

When the load was about 180, I was able to ssh into the machine and run top to watch processes. The machine was still responding to DNS queries as well and ping was working. This was around 8:30 AM.

The syslog runs up until about 8:16 AM before it stops. The next log line is from when the machine was rebooted (about 1:10 PM).

When I attempted to do a reboot or shutdown command, I received a response of 'segmentation fault'.

In the Syslog, there are thousands of General Protection Faults. They all have different process IDs and different executables. But one thing seems to stay the same across all of them - CPU 3. The second line of the errors all say CPU 3. Here are some example lines:

Example 1:

```
Feb 24 06:26:19 arcola-d kernel: [827037.628738] general protection fault: 0000 [#6] SMP
Feb 24 06:26:19 arcola-d kernel: [827037.632707] CPU 3
Feb 24 06:26:19 arcola-d kernel: [827037.632707] Modules linked in: pci_stub vboxpci(O) vboxnetadp(O) vboxnetflt(O) vboxdrv(O) xt_state xt_tcpudp xt_connlimit xt_owner iptable_nat ipt_REDIRECT nf_nat iptable_mangle nf_conntrack_ftp nf_conntrack_ipv4 nf_defrag_ipv4 xt_conntrack nf_conntrack ipt_REJECT ipt_LOG xt_limit iptable_filter ip_tables xt_multiport x_tables dm_crypt eeepc_wmi asus_wmi sparse_keymap mac_hid psmouse serio_raw edac_core edac_mce_amd fam15h_power k10temp lp parport sp5100_tco i2c_piix4 radeon mxm_wmi ttm drm_kms_helper drm i2c_algo_bit r8169 wmi
Feb 24 06:26:19 arcola-d kernel: [827037.632707]
Feb 24 06:26:19 arcola-d kernel: [827037.632707] Pid: 895, comm: apache2 Tainted: G    B D    O 3.2.0-60-generic #91-Ubuntu To be filled by O.E.M. To be filled by O.E.M./M5A97 LE R2.0
Feb 24 06:26:19 arcola-d kernel: [827037.632707] RIP: 0010:[<ffffffff81166e6a>]  [<ffffffff81166e6a>] kmem_cache_alloc+0x5a/0x140
Feb 24 06:26:19 arcola-d kernel: [827037.632707] RSP: 0018:ffff880261bf9de8  EFLAGS: 00010282
Feb 24 06:26:19 arcola-d kernel: [827037.632707] RAX: 0000000000000000 RBX: ffff88034ed95160 RCX: 0000000005992ad7
Feb 24 06:26:19 arcola-d kernel: [827037.632707] RDX: 0000000005992ad6 RSI: 0000000000016e30 RDI: ffff88042e006d00
Feb 24 06:26:19 arcola-d kernel: [827037.632707] RBP: ffff880261bf9e38 R08: ffff88043ecd6e30 R09: 0000000000000001
Feb 24 06:26:19 arcola-d kernel: [827037.632707] R10: 00007fce3a348000 R11: 0000000000000001 R12: ffff88042e006d00
Feb 24 06:26:19 arcola-d kernel: [827037.632707] R13: 80000001bdf57067 R14: ffffffff81144b47 R15: 00000000000000d0
Feb 24 06:26:19 arcola-d kernel: [827037.632707] FS:  00007fce3799e740(0000) GS:ffff88043ecc0000(0000) knlGS:0000000000000000
Feb 24 06:26:19 arcola-d kernel: [827037.632707] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Feb 24 06:26:19 arcola-d kernel: [827037.632707] CR2: 0000000001d00000 CR3: 0000000258121000 CR4: 00000000000406e0
Feb 24 06:26:19 arcola-d kernel: [827037.632707] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Feb 24 06:26:19 arcola-d kernel: [827037.632707] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Feb 24 06:26:19 arcola-d kernel: [827037.632707] Process apache2 (pid: 895, threadinfo ffff880261bf8000, task ffff88042454dc00)
Feb 24 06:26:19 arcola-d kernel: [827037.632707] Stack:
Feb 24 06:26:19 arcola-d kernel: [827037.632707]  ffff880261bf9df8 ffffffff81661fb5 ffff880261bf9e98 ffffffff8165fc5d
Feb 24 06:26:19 arcola-d kernel: [827037.632707]  ffff880261bf9eb8 ffff88034ed95160 ffff88034ed95160 ffff880261bf9f20
Feb 24 06:26:19 arcola-d kernel: [827037.632707]  00007fce3a347000 ffff88041f8bec80 ffff880261bf9e88 ffffffff81144b47
Feb 24 06:26:19 arcola-d kernel: [827037.632707] Call Trace:
Feb 24 06:26:19 arcola-d kernel: [827037.632707]  [<ffffffff81661fb5>] ? _raw_spin_lock_irq+0x15/0x20
Feb 24 06:26:19 arcola-d kernel: [827037.632707]  [<ffffffff8165fc5d>] ? wait_for_common+0x13d/0x180
Feb 24 06:26:19 arcola-d kernel: [827037.632707]  [<ffffffff81144b47>] __split_vma+0x77/0x270
Feb 24 06:26:19 arcola-d kernel: [827037.632707]  [<ffffffff81146a60>] split_vma+0x20/0x30
Feb 24 06:26:19 arcola-d kernel: [827037.632707]  [<ffffffff81143379>] mlock_fixup+0x159/0x1a0
Feb 24 06:26:19 arcola-d kernel: [827037.632707]  [<ffffffff811434ff>] do_mlock+0x9f/0xf0
Feb 24 06:26:19 arcola-d kernel: [827037.632707]  [<ffffffff81143637>] sys_mlock+0xe7/0x130
Feb 24 06:26:19 arcola-d kernel: [827037.632707]  [<ffffffff8166a302>] system_call_fastpath+0x16/0x1b
Feb 24 06:26:19 arcola-d kernel: [827037.632707] Code: 00 4d 8b 04 24 65 4c 03 04 25 50 da 00 00 49 8b 50 08 4d 8b 28 4d 85 ed 0f 84 d8 00 00 00 49 63 44 24 20 49 8b 34 24 48 8d 4a 01 <49> 8b 5c 05 00 4c 89 e8 65 48 0f c7 0e 0f 94 c0 84 c0 74 c2 4d
Feb 24 06:26:19 arcola-d kernel: [827037.632707] RIP  [<ffffffff81166e6a>] kmem_cache_alloc+0x5a/0x140
Feb 24 06:26:19 arcola-d kernel: [827037.632707]  RSP <ffff880261bf9de8>
Feb 24 06:26:19 arcola-d kernel: [827039.363308] ---[ end trace 2e7855ad3e8edeb1 ]---
```

Example 2:

```
Feb 24 06:27:18 arcola-d kernel: [827096.812472] general protection fault: 0000 [#11] SMP
Feb 24 06:27:18 arcola-d kernel: [827096.816440] CPU 3
Feb 24 06:27:18 arcola-d kernel: [827096.816440] Modules linked in: pci_stub vboxpci(O) vboxnetadp(O) vboxnetflt(O) vboxdrv(O) xt_state xt_tcpudp xt_connlimit xt_owner iptable_nat ipt_REDIRECT nf_nat iptable_mangle nf_conntrack_ftp nf_conntrack_ipv4 nf_defrag_ipv4 xt_conntrack nf_conntrack ipt_REJECT ipt_LOG xt_limit iptable_filter ip_tables xt_multiport x_tables dm_crypt eeepc_wmi asus_wmi sparse_keymap mac_hid psmouse serio_raw edac_core edac_mce_amd fam15h_power k10temp lp parport sp5100_tco i2c_piix4 radeon mxm_wmi ttm drm_kms_helper drm i2c_algo_bit r8169 wmi
Feb 24 06:27:18 arcola-d kernel: [827096.867994]
Feb 24 06:27:18 arcola-d kernel: [827096.867994] Pid: 1308, comm: console-kit-dae Tainted: G    B D    O 3.2.0-60-generic #91-Ubuntu To be filled by O.E.M. To be filled by O.E.M./M5A97 LE R2.0
Feb 24 06:27:18 arcola-d kernel: [827096.867994] RIP: 0010:[<ffffffff81166e6a>]  [<ffffffff81166e6a>] kmem_cache_alloc+0x5a/0x140
Feb 24 06:27:18 arcola-d kernel: [827096.867994] RSP: 0018:ffff88025801fdd8  EFLAGS: 00010282
Feb 24 06:27:18 arcola-d kernel: [827096.867994] RAX: 0000000000000000 RBX: ffff88041f864980 RCX: 0000000005992ad7
Feb 24 06:27:18 arcola-d kernel: [827096.867994] RDX: 0000000005992ad6 RSI: 0000000000016e30 RDI: ffff88042e006d00
Feb 24 06:27:18 arcola-d kernel: [827096.867994] RBP: ffff88025801fe28 R08: ffff88043ecd6e30 R09: 000000000001e3e1
Feb 24 06:27:18 arcola-d kernel: [827096.867994] R10: ffffea0008db9040 R11: 0000000000000000 R12: ffff88042e006d00
Feb 24 06:27:18 arcola-d kernel: [827096.867994] R13: 80000001bdf57067 R14: ffffffff81180f9c R15: 00000000000080d0
Feb 24 06:27:18 arcola-d kernel: [827096.867994] FS:  00007f837d6067c0(0000) GS:ffff88043ecc0000(0000) knlGS:0000000000000000
Feb 24 06:27:18 arcola-d kernel: [827096.867994] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Feb 24 06:27:18 arcola-d kernel: [827096.867994] CR2: 0000000001d00000 CR3: 000000023bb6a000 CR4: 00000000000406e0
Feb 24 06:27:18 arcola-d kernel: [827096.867994] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Feb 24 06:27:18 arcola-d kernel: [827096.867994] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Feb 24 06:27:18 arcola-d kernel: [827096.867994] Process console-kit-dae (pid: 1308, threadinfo ffff88025801e000, task ffff88041ff5ae00)
Feb 24 06:27:18 arcola-d kernel: [827096.867994] Stack:
Feb 24 06:27:18 arcola-d kernel: [827096.867994]  ffff88041f864980 ffff88034eee2700 ffff88025801ff58 00007fffac42e040
Feb 24 06:27:18 arcola-d kernel: [827096.867994]  ffff88025801fe08 ffff88041f864980 ffff88034eee2700 ffff88041f864980
Feb 24 06:27:18 arcola-d kernel: [827096.867994]  ffff88025801ff58 00007fffac42e040 ffff88025801fe68 ffffffff81180f9c
Feb 24 06:27:18 arcola-d kernel: [827096.867994] Call Trace:
Feb 24 06:27:18 arcola-d kernel: [827096.867994]  [<ffffffff81180f9c>] __bprm_mm_init+0x3c/0x170
Feb 24 06:27:18 arcola-d kernel: [827096.867994]  [<ffffffff811829b8>] bprm_mm_init+0x78/0x90
Feb 24 06:27:18 arcola-d kernel: [827096.867994]  [<ffffffff81182ddd>] do_execve_common.isra.26+0x16d/0x340
Feb 24 06:27:18 arcola-d kernel: [827096.867994]  [<ffffffff81182fcb>] do_execve+0x1b/0x20
Feb 24 06:27:18 arcola-d kernel: [827096.867994]  [<ffffffff8101d637>] sys_execve+0x47/0x70
Feb 24 06:27:18 arcola-d kernel: [827096.867994]  [<ffffffff8166a75c>] stub_execve+0x6c/0xc0
Feb 24 06:27:18 arcola-d kernel: [827096.867994] Code: 00 4d 8b 04 24 65 4c 03 04 25 50 da 00 00 49 8b 50 08 4d 8b 28 4d 85 ed 0f 84 d8 00 00 00 49 63 44 24 20 49 8b 34 24 48 8d 4a 01 <49> 8b 5c 05 00 4c 89 e8 65 48 0f c7 0e 0f 94 c0 84 c0 74 c2 4d
Feb 24 06:27:18 arcola-d kernel: [827096.867994] RIP  [<ffffffff81166e6a>] kmem_cache_alloc+0x5a/0x140
Feb 24 06:27:18 arcola-d kernel: [827096.867994]  RSP <ffff88025801fdd8>
Feb 24 06:27:18 arcola-d kernel: [827098.481648] ---[ end trace 2e7855ad3e8edeb6 ]---
```

Example 3:

```
Feb 24 06:29:02 arcola-d kernel: [827201.686003] general protection fault: 0000 [#18] SMP
Feb 24 06:29:02 arcola-d kernel: [827201.689880] CPU 3
Feb 24 06:29:02 arcola-d kernel: [827201.689880] Modules linked in: pci_stub vboxpci(O) vboxnetadp(O) vboxnetflt(O) vboxdrv(O) xt_state xt_tcpudp xt_connlimit xt_owner iptable_nat ipt_REDIRECT nf_nat iptable_mangle nf_conntrack_ftp nf_conntrack_ipv4 nf_defrag_ipv4 xt_conntrack nf_conntrack ipt_REJECT ipt_LOG xt_limit iptable_filter ip_tables xt_multiport x_tables dm_crypt eeepc_wmi asus_wmi sparse_keymap mac_hid psmouse serio_raw edac_core edac_mce_amd fam15h_power k10temp lp parport sp5100_tco i2c_piix4 radeon mxm_wmi ttm drm_kms_helper drm i2c_algo_bit r8169 wmi
Feb 24 06:29:02 arcola-d kernel: [827201.689880]
Feb 24 06:29:02 arcola-d kernel: [827201.689880] Pid: 1348, comm: cron Tainted: G    B D    O 3.2.0-60-generic #91-Ubuntu To be filled by O.E.M. To be filled by O.E.M./M5A97 LE R2.0
Feb 24 06:29:02 arcola-d kernel: [827201.689880] RIP: 0010:[<ffffffff81166e6a>]  [<ffffffff81166e6a>] kmem_cache_alloc+0x5a/0x140
Feb 24 06:29:02 arcola-d kernel: [827201.689880] RSP: 0018:ffff88042055fe58  EFLAGS: 00010282
Feb 24 06:29:02 arcola-d kernel: [827201.689880] RAX: 0000000000000000 RBX: ffff88041f8ba300 RCX: 0000000005992ad7
Feb 24 06:29:02 arcola-d kernel: [827201.689880] RDX: 0000000005992ad6 RSI: 0000000000016e30 RDI: ffff88042e006d00
Feb 24 06:29:02 arcola-d kernel: [827201.689880] RBP: ffff88042055fea8 R08: ffff88043ecd6e30 R09: 00000000ffffffff
Feb 24 06:29:02 arcola-d kernel: [827201.689880] R10: 00007fed58315a90 R11: 0000000000000206 R12: ffff88042e006d00
Feb 24 06:29:02 arcola-d kernel: [827201.689880] R13: 80000001bdf57067 R14: ffffffff81144b47 R15: 00000000000000d0
Feb 24 06:29:02 arcola-d kernel: [827201.689880] FS:  00007fed583157c0(0000) GS:ffff88043ecc0000(0000) knlGS:0000000000000000
Feb 24 06:29:02 arcola-d kernel: [827201.689880] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Feb 24 06:29:02 arcola-d kernel: [827201.689880] CR2: 00007fed57a087d0 CR3: 000000034ea21000 CR4: 00000000000406e0
Feb 24 06:29:02 arcola-d kernel: [827201.689880] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Feb 24 06:29:02 arcola-d kernel: [827201.689880] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Feb 24 06:29:02 arcola-d kernel: [827201.689880] Process cron (pid: 1348, threadinfo ffff88042055e000, task ffff88034e9d8000)
Feb 24 06:29:02 arcola-d kernel: [827201.689880] Stack:
Feb 24 06:29:02 arcola-d kernel: [827201.689880]  0000000000000014 00007fed57a087d0 0000000000000003 0000000000000000
Feb 24 06:29:02 arcola-d kernel: [827201.689880]  ffff88042055ff48 ffff88041f8ba300 ffff88041fed1630 ffff88041fed1630
Feb 24 06:29:02 arcola-d kernel: [827201.689880]  00007fed58326000 ffff88041f8ba300 ffff88042055fef8 ffffffff81144b47
Feb 24 06:29:02 arcola-d kernel: [827201.689880] Call Trace:
Feb 24 06:29:02 arcola-d kernel: [827201.689880]  [<ffffffff81144b47>] __split_vma+0x77/0x270
Feb 24 06:29:02 arcola-d kernel: [827201.689880]  [<ffffffff8114540b>] do_munmap+0x2cb/0x2f0
Feb 24 06:29:02 arcola-d kernel: [827201.689880]  [<ffffffff81146ac3>] sys_munmap+0x53/0x80
Feb 24 06:29:02 arcola-d kernel: [827201.689880]  [<ffffffff8166a302>] system_call_fastpath+0x16/0x1b
Feb 24 06:29:02 arcola-d kernel: [827201.689880] Code: 00 4d 8b 04 24 65 4c 03 04 25 50 da 00 00 49 8b 50 08 4d 8b 28 4d 85 ed 0f 84 d8 00 00 00 49 63 44 24 20 49 8b 34 24 48 8d 4a 01 <49> 8b 5c 05 00 4c 89 e8 65 48 0f c7 0e 0f 94 c0 84 c0 74 c2 4d
Feb 24 06:29:02 arcola-d kernel: [827201.689880] RIP  [<ffffffff81166e6a>] kmem_cache_alloc+0x5a/0x140
Feb 24 06:29:02 arcola-d kernel: [827201.689880]  RSP <ffff88042055fe58>
Feb 24 06:29:02 arcola-d kernel: [827203.262637] ---[ end trace 2e7855ad3e8edebd ]---
```

Would anyone else be able to provide some of their thoughts/feedback as what they believe it could be? The fact that all of the lines were written shows that the hard drive was accessible and writable.

---

### Post by sandyd on 2015-03-01
```
general protection fault: 0000 [#6] SMP
```
and
```
kmem_cache_alloc
```

Possibly a memory allocation error.

Have you checked the RAM on the server?
Do a few memtests and see if anything shows up

---

### Post by tgalati4 on 2015-03-01
Because it was specific to CPU3 several times, it's possible that you have CPU problem.  I would dismantle the machine, clean it out, clean off the old paste, reseat the CPU's (assuming they are in sockets), inspect the motherboard for bad capacitors, and then rebuild.  Run memtest for 30 complete cycles.

There's a way to disable a specific CPU, but I don't know it off hand.  You could do that and see if stability improves, but a hardware problem requires immediate action.

Run the manufacturer's diagnostic suite, that might catch the specific hardware problem, but I'm going to bet a heat sink/heat paste problem causing a CPU fault.  It may be fixable, but it may also be retirement time.

How long has the server been running 24/7?

---

