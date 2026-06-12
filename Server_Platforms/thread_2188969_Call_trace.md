---
title: "Call trace"
date: 2013-11-20
forum: Server Platforms
---

### Post by alessandro-macuz on 2013-11-20
Hi all,

I hope this is the right forum where to post my issue and have comments of the developers. It's about a call trace. No crash but a slow down of the CPU.
It started from CPU number 2. Here below the call trace

History:
as soon as I started a process where bzip2 was involved messages about power limitation like the following started to be logged

Nov 18 21:54:28 server02 kernel: [6171200.759011] CPU4: Core power limit notification (total events = 1)[COLOR=#000000][FONT=Arial]
[/FONT][/COLOR]
with the counter total events starting indeed from 1.

then a hour later

[COLOR=#000000][FONT=Arial]Nov 18 23:01:43 grpnas02 kernel: [6175233.904302] INFO: rcu_bh detected stall on CPU 2 (t=0 jiffies) [/FONT][/COLOR]

and the call traces for all the CPUs. Here below the trace for the CPU 2 (sorry for the length)

[COLOR=#000000][FONT=Arial]Nov 18 23:01:43 grpnas02 kernel: [6175234.021894] NMI backtrace for cpu 2 [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Nov 18 23:01:43 grpnas02 kernel: [6175234.021933] CPU 2 [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Nov 18 23:01:43 grpnas02 kernel: [6175234.021935] Modules linked in: des_generic md4 nls_utf8 cifs iscsi_scst(O) scst_vdisk(O) scst(O) libcrc32c ipmi_devintf ipmi_si ipmi_msghandler parport_pc ppdev nfsd nfs lockd fscache auth_rpcgss nfs_acl sunrpc joydev lp 8021q garp stp sb_edac edac_core shpchp dcdbas ses mac_hid enclosure parport wmi acpi_power_meter mei(C) zfs(P) zcommon(P) znvpair(P) zavl(P) zunicode(P) spl(O) zlib_deflate usbhid hid dm_mirror dm_region_hash dm_log usb_storage mpt2sas scsi_transport_sas tg3 raid_class [last unloaded: scst] [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Nov 18 23:01:43 grpnas02 kernel: [6175234.024334] [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Nov 18 23:01:43 grpnas02 kernel: [6175234.024376] Pid: 13562, comm: z_fr_iss_0/2 Tainted: P C O 3.2.0-53-generic #81-Ubuntu Dell Inc. PowerEdge R420/072XWF [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Nov 18 23:01:43 grpnas02 kernel: [6175234.024456] RIP: 0010:[<ffffffff8101c2e1>] [<ffffffff8101c2e1>] native_read_tsc+0x1/0x20 [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Nov 18 23:01:43 grpnas02 kernel: [6175234.024895] RSP: 0018:ffff8817df243ce8 EFLAGS: 00000887 [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Nov 18 23:01:43 grpnas02 kernel: [6175234.025094] RAX: 000000008b96afc0 RBX: 00000000000003e9 RCX: 000000000118c0bc [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Nov 18 23:01:43 grpnas02 kernel: [6175234.025254] RDX: 0000000000037b3a RSI: 0000000000000100 RDI: 0000000000037b3b [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Nov 18 23:01:43 grpnas02 kernel: [6175234.025414] RBP: ffff8817df243d18 R08: ffffffff81cdf140 R09: 0000000000000000 [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Nov 18 23:01:43 grpnas02 kernel: [6175234.025574] R10: 0000000000000000 R11: 0000000000000000 R12: 0000000000001000 [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Nov 18 23:01:43 grpnas02 kernel: [6175234.025734] R13: 0000000000000002 R14: 0000000000037b3b R15: 0000000000000092 [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Nov 18 23:01:43 grpnas02 kernel: [6175234.025895] FS: 0000000000000000(0000) GS:ffff8817df240000(0000) knlGS:0000000000000000 [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Nov 18 23:01:43 grpnas02 kernel: [6175234.026095] CS: 0010 DS: 0000 ES: 0000 CR0: 000000008005003b [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Nov 18 23:01:43 grpnas02 kernel: [6175234.026254] CR2: 00007faa5fc60000 CR3: 0000000001c05000 CR4: 00000000000406e0 [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Nov 18 23:01:43 grpnas02 kernel: [6175234.026414] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000 [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Nov 18 23:01:43 grpnas02 kernel: [6175234.026574] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400 [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Nov 18 23:01:43 grpnas02 kernel: [6175234.026735] Process z_fr_iss_0/2 (pid: 13562, threadinfo ffff88176250a000, task ffff881762502e00)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Nov 18 23:01:43 grpnas02 kernel: [6175234.026934] Stack: [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Nov 18 23:01:43 grpnas02 kernel: [6175234.029656] ffff8817df243d18 ffffffff8131ae77 00000000000003e9 0000000000001000 [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Nov 18 23:01:43 grpnas02 kernel: [6175234.029738] ffffffff81cdf140 0000000000000400 ffff8817df243d28 ffffffff8131adcc [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Nov 18 23:01:43 grpnas02 kernel: [6175234.029818] ffff8817df243d48 ffffffff81032452 0000000000000002 000000000000da82 [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Nov 18 23:01:43 grpnas02 kernel: [6175234.029934] Call Trace: [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Nov 18 23:01:43 grpnas02 kernel: [6175234.033137] <IRQ> [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Nov 18 23:01:43 grpnas02 kernel: [6175234.036218] [<ffffffff8131ae77>] ? delay_tsc+0x27/0x80 [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Nov 18 23:01:43 grpnas02 kernel: [6175234.036298] [<ffffffff8131adcc>] __const_udelay+0x2c/0x30 [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Nov 18 23:01:43 grpnas02 kernel: [6175234.036379] [<ffffffff81032452>] native_safe_apic_wait_icr_idle+0x22/0x50 [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Nov 18 23:01:43 grpnas02 kernel: [6175234.036458] [<ffffffff8103359f>] default_send_IPI_mask_sequence_phys+0xcf/0xe0 [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Nov 18 23:01:43 grpnas02 kernel: [6175234.036537] [<ffffffff81037ff7>] physflat_send_IPI_all+0x17/0x20 [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Nov 18 23:01:43 grpnas02 kernel: [6175234.036615] [<ffffffff81033731>] arch_trigger_all_cpu_backtrace+0x61/0xa0 [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Nov 18 23:01:43 grpnas02 kernel: [6175234.036659] [<ffffffff810e1f07>] check_cpu_stall.isra.35+0x97/0xf0 [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Nov 18 23:01:43 grpnas02 kernel: [6175234.036736] [<ffffffff810e1f98>] __rcu_pending+0x38/0x1d0 [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Nov 18 23:01:43 grpnas02 kernel: [6175234.036778] [<ffffffff810e257b>] rcu_check_callbacks+0x1cb/0x1e0 [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Nov 18 23:01:43 grpnas02 kernel: [6175234.036859] [<ffffffff810799f8>] update_process_times+0x48/0x90 [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Nov 18 23:01:43 grpnas02 kernel: [6175234.036938] [<ffffffff8109d784>] tick_sched_timer+0x64/0xc0 [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Nov 18 23:01:43 grpnas02 kernel: [6175234.037017] [<ffffffff8108fda8>] __run_hrtimer+0x78/0x1f0 [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Nov 18 23:01:43 grpnas02 kernel: [6175234.037059] [<ffffffff8109d720>] ? tick_nohz_handler+0x100/0x100 [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Nov 18 23:01:43 grpnas02 kernel: [6175234.037138] [<ffffffff810906d7>] hrtimer_interrupt+0xf7/0x240 [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Nov 18 23:01:43 grpnas02 kernel: [6175234.037699] [<ffffffffa0226590>] ? zio_taskq_member.isra.5+0xb0/0xb0 [zfs] [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Nov 18 23:01:43 grpnas02 kernel: [6175234.037777] [<ffffffff8166bf19>] smp_apic_timer_interrupt+0x69/0x99 [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Nov 18 23:01:43 grpnas02 kernel: [6175234.037856] [<ffffffff81669dde>] apic_timer_interrupt+0x6e/0x80 [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Nov 18 23:01:43 grpnas02 kernel: [6175234.037859] <EOI> [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Nov 18 23:01:43 grpnas02 kernel: [6175234.040897] [<ffffffff81660cf9>] ? _raw_spin_unlock_irqrestore+0x19/0x30 [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Nov 18 23:01:43 grpnas02 kernel: [6175234.041058] [<ffffffffa00d5637>] taskq_dispatch_ent+0x77/0x1d0 [spl] [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Nov 18 23:01:43 grpnas02 kernel: [6175234.041539] [<ffffffffa0226590>] ? zio_taskq_member.isra.5+0xb0/0xb0 [zfs] [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Nov 18 23:01:43 grpnas02 kernel: [6175234.042019] [<ffffffffa01d493b>] spa_taskq_dispatch_ent+0x6b/0xa0 [zfs] [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Nov 18 23:01:43 grpnas02 kernel: [6175234.042498] [<ffffffffa0225599>] zio_taskq_dispatch+0x99/0xb0 [zfs] [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Nov 18 23:01:43 grpnas02 kernel: [6175234.042940] [<ffffffffa02255c2>] zio_issue_async+0x12/0x20 [zfs] [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Nov 18 23:01:43 grpnas02 kernel: [6175234.043380] [<ffffffffa022664a>] zio_execute+0xba/0x160 [zfs] [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Nov 18 23:01:43 grpnas02 kernel: [6175234.043539] [<ffffffffa00d6626>] taskq_thread+0x236/0x4b0 [spl] [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Nov 18 23:01:43 grpnas02 kernel: [6175234.043619] [<ffffffff810608e0>] ? try_to_wake_up+0x200/0x200 [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Nov 18 23:01:43 grpnas02 kernel: [6175234.043740] [<ffffffffa00d63f0>] ? task_done+0x160/0x160 [spl] [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Nov 18 23:01:43 grpnas02 kernel: [6175234.043819] [<ffffffff8108b64c>] kthread+0x8c/0xa0 [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Nov 18 23:01:43 grpnas02 kernel: [6175234.043898] [<ffffffff8166b474>] kernel_thread_helper+0x4/0x10 [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Nov 18 23:01:43 grpnas02 kernel: [6175234.043941] [<ffffffff8108b5c0>] ? flush_kthread_worker+0xa0/0xa0 [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Nov 18 23:01:43 grpnas02 kernel: [6175234.044020] [<ffffffff8166b470>] ? gs_change+0x13/0x13 [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Nov 18 23:01:43 grpnas02 kernel: [6175234.044059] Code: e6 ea 2f 00 5d c3 90 90 90 90 55 89 f8 48 89 e5 e6 70 e4 71 5d c3 0f 1f 40 00 55 89 f0 48 89 e5 e6 70 89 f8 e6 71 5d c3 66 90 55 <48> 89 e5 0f 31 89 c1 48 89 d0 48 c1 e0 20 48 09 c8 5d c3 66 66 [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Nov 18 23:01:43 grpnas02 kernel: [6175234.075427] Call Trace: [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Nov 18 23:01:43 grpnas02 kernel: [6175234.075466] <IRQ> [<ffffffff8131ae77>] ? delay_tsc+0x27/0x80 [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Nov 18 23:01:43 grpnas02 kernel: [6175234.075588] [<ffffffff8131adcc>] __const_udelay+0x2c/0x30 [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Nov 18 23:01:43 grpnas02 kernel: [6175234.075666] [<ffffffff81032452>] native_safe_apic_wait_icr_idle+0x22/0x50 [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Nov 18 23:01:43 grpnas02 kernel: [6175234.075709] [<ffffffff8103359f>] default_send_IPI_mask_sequence_phys+0xcf/0xe0 [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Nov 18 23:01:43 grpnas02 kernel: [6175234.075787] [<ffffffff81037ff7>] physflat_send_IPI_all+0x17/0x20 [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Nov 18 23:01:43 grpnas02 kernel: [6175234.075830] [<ffffffff81033731>] arch_trigger_all_cpu_backtrace+0x61/0xa0 [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Nov 18 23:01:43 grpnas02 kernel: [6175234.075908] [<ffffffff810e1f07>] check_cpu_stall.isra.35+0x97/0xf0 [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Nov 18 23:01:43 grpnas02 kernel: [6175234.075949] [<ffffffff810e1f98>] __rcu_pending+0x38/0x1d0 [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Nov 18 23:01:43 grpnas02 kernel: [6175234.076026] [<ffffffff810e257b>] rcu_check_callbacks+0x1cb/0x1e0 [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Nov 18 23:01:43 grpnas02 kernel: [6175234.076106] [<ffffffff810799f8>] update_process_times+0x48/0x90 [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Nov 18 23:01:43 grpnas02 kernel: [6175234.076149] [<ffffffff8109d784>] tick_sched_timer+0x64/0xc0 [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Nov 18 23:01:43 grpnas02 kernel: [6175234.076228] [<ffffffff8108fda8>] __run_hrtimer+0x78/0x1f0 [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Nov 18 23:01:43 grpnas02 kernel: [6175234.076270] [<ffffffff8109d720>] ? tick_nohz_handler+0x100/0x100 [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Nov 18 23:01:43 grpnas02 kernel: [6175234.076349] [<ffffffff810906d7>] hrtimer_interrupt+0xf7/0x240 [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Nov 18 23:01:43 grpnas02 kernel: [6175234.076908] [<ffffffffa0226590>] ? zio_taskq_member.isra.5+0xb0/0xb0 [zfs] [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Nov 18 23:01:43 grpnas02 kernel: [6175234.076950] [<ffffffff8166bf19>] smp_apic_timer_interrupt+0x69/0x99 [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Nov 18 23:01:43 grpnas02 kernel: [6175234.077028] [<ffffffff81669dde>] apic_timer_interrupt+0x6e/0x80 [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Nov 18 23:01:43 grpnas02 kernel: [6175234.077067] <EOI> [<ffffffff81660cf9>] ? _raw_spin_unlock_irqrestore+0x19/0x30 [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Nov 18 23:01:43 grpnas02 kernel: [6175234.077268] [<ffffffffa00d5637>] taskq_dispatch_ent+0x77/0x1d0 [spl] [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Nov 18 23:01:43 grpnas02 kernel: [6175234.077709] [<ffffffffa0226590>] ? zio_taskq_member.isra.5+0xb0/0xb0 [zfs] [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Nov 18 23:01:43 grpnas02 kernel: [6175234.078188] [<ffffffffa01d493b>] spa_taskq_dispatch_ent+0x6b/0xa0 [zfs] [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Nov 18 23:01:43 grpnas02 kernel: [6175234.078630] [<ffffffffa0225599>] zio_taskq_dispatch+0x99/0xb0 [zfs] [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Nov 18 23:01:43 grpnas02 kernel: [6175234.079070] [<ffffffffa02255c2>] zio_issue_async+0x12/0x20 [zfs] [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Nov 18 23:01:43 grpnas02 kernel: [6175234.079509] [<ffffffffa022664a>] zio_execute+0xba/0x160 [zfs] [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Nov 18 23:01:43 grpnas02 kernel: [6175234.079668] [<ffffffffa00d6626>] taskq_thread+0x236/0x4b0 [spl] [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Nov 18 23:01:43 grpnas02 kernel: [6175234.079748] [<ffffffff810608e0>] ? try_to_wake_up+0x200/0x200 [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Nov 18 23:01:43 grpnas02 kernel: [6175234.079869] [<ffffffffa00d63f0>] ? task_done+0x160/0x160 [spl] [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Nov 18 23:01:43 grpnas02 kernel: [6175234.079947] [<ffffffff8108b64c>] kthread+0x8c/0xa0 [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Nov 18 23:01:43 grpnas02 kernel: [6175234.080027] [<ffffffff8166b474>] kernel_thread_helper+0x4/0x10 [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Nov 18 23:01:43 grpnas02 kernel: [6175234.080069] [<ffffffff8108b5c0>] ? flush_kthread_worker+0xa0/0xa0 [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Nov 18 23:01:43 grpnas02 kernel: [6175234.080148] [<ffffffff8166b470>] ? gs_change+0x13/0x13 


The message about the power limitation led me to the issue about especially the mei module

[/FONT][/COLOR]http://en.community.dell.com/techcenter/b/techcenter/archive/2012/08/27/ubuntu-on-dell-12g-poweredge-servers.aspx

and the call trace led me to this web page

[https://groups.google.com/forum/#!msg/linux.kernel/v7qFGJ0SO5Q/wyYMj7vIxEUJ](https://groups.google.com/forum/#!msg/linux.kernel/v7qFGJ0SO5Q/wyYMj7vIxEUJ) (pattern from IRQ to EOI matches the one for CPU number 8)

for the Linux kernel.

the kernel image I'm using is 

root@server02:/var/log$ uname -a
Linux server02 3.2.0-53-generic #81-Ubuntu SMP Thu Aug 22 21:01:03 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 12.04.3 LTS
Release:        12.04
Codename:       precise


For the moment I'm going to blacklist the mei module (and all the others mentioned in the dell community) but I wonder which kernel has this fixed.

Thanks,

Alex

---

### Post by alessandro-macuz on 2013-11-20
Is there a way to discuss this with developers? Just to understand a bit more if there is a fix and as of which version.

---

