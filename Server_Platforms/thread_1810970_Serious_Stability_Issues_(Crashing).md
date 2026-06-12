---
title: "Serious Stability Issues (Crashing)"
date: 2011-07-24
forum: Server Platforms
---

### Post by searing on 2011-07-24
My fileserver, which is running Ubuntu Server 11.04, seems to crash on a regular basis.  When it crashes, no SSH connections can be made and it stops responding to all file transfers.  It appears to crash most often while I'm in the middle of a large-ish transfer.

The most recent time it crashed, it never got around to writing anything to syslog.  However, yesterday when it crashed (it does this almost every day), I got a nasty CPU dump and an attempt at a stacktrace:

```
Jul 22 13:58:33 titanium kernel: [ 6294.257421] general protection fault: 0000 [#1] SMP
Jul 22 13:58:33 titanium kernel: [ 6294.257446] last sysfs file: /sys/devices/system/cpu/cpu3/cpufreq/scaling_governor
Jul 22 13:58:33 titanium kernel: [ 6294.257459] CPU 1
Jul 22 13:58:33 titanium kernel: [ 6294.257465] Modules linked in: xfs exportfs snd_hda_codec_realtek nouveau snd_hda_intel snd_hda_codec ttm snd_hwdep drm_kms_helper snd_pcm snd_timer drm snd soundcore snd_page_alloc i2c_algo_bit lp ppd
ev serio_raw video parport_pc parport raid10 raid456 async_pq async_xor xor async_memcpy async_raid6_recov e1000 e1000e r8169 ahci libahci xhci_hcd pata_jmicron raid6_pq async_tx raid1 raid0 multipath linear
Jul 22 13:58:33 titanium kernel: [ 6294.257621]
Jul 22 13:58:33 titanium kernel: [ 6294.257628] Pid: 1266, comm: smbd Not tainted 2.6.38-10-server #46-Ubuntu Gigabyte Technology Co., Ltd. P55-USB3/P55-USB3
Jul 22 13:58:33 titanium kernel: [ 6294.257656] RIP: 0010:[<ffffffff811551e8>]  [<ffffffff811551e8>] kmem_cache_alloc+0x58/0x110
Jul 22 13:58:33 titanium kernel: [ 6294.257681] RSP: 0018:ffff8801933b5948  EFLAGS: 00010082
Jul 22 13:58:33 titanium kernel: [ 6294.257691] RAX: 0000000000000230 RBX: ffff88019f8050c0 RCX: ffffffff812dec49
Jul 22 13:58:33 titanium kernel: [ 6294.257704] RDX: 000000000000000a RSI: 00000000000000d0 RDI: ffff88019f8050c0
Jul 22 13:58:33 titanium kernel: [ 6294.257717] RBP: ffff8801933b5988 R08: ffff8800df856d90 R09: 0000000000001000
Jul 22 13:58:33 titanium kernel: [ 6294.257729] R10: ffff8801926d1300 R11: 0000000000000000 R12: fffd880186e5ee98
Jul 22 13:58:33 titanium kernel: [ 6294.257741] R13: 0000000000000286 R14: 00000000000e3301 R15: 00000000000000d0
Jul 22 13:58:33 titanium kernel: [ 6294.257754] FS:  00007f76ce6d6740(0000) GS:ffff8800df840000(0000) knlGS:0000000000000000
Jul 22 13:58:33 titanium kernel: [ 6294.257768] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Jul 22 13:58:33 titanium kernel: [ 6294.257778] CR2: 00007f76ce816d80 CR3: 0000000190493000 CR4: 00000000000006e0
Jul 22 13:58:33 titanium kernel: [ 6294.257790] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Jul 22 13:58:33 titanium kernel: [ 6294.257802] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Jul 22 13:58:33 titanium kernel: [ 6294.257815] Process smbd (pid: 1266, threadinfo ffff8801933b4000, task ffff88018f5e16e0)
Jul 22 13:58:33 titanium kernel: [ 6294.257827] Stack:
```As you may notice, it never got around to printing out the stack - that's all that was written to syslog.

I used to run 10.04 LTS, but I had similar issues.  I was told that upgrading to the newest version may help.  It has not seemed to fix the problem at all.

For more background, my server has 8 hard drives in a raid6 array with mdadm, with XFS on top of the array.  None of the hard drives are defective (I've checked!).  Also, my RAM is not defective.

If anyone has any idea as to what the problem is, I would be very grateful.  I've had this issue for a while now, and I'm afraid I may have to leave Ubuntu behind if I can't manage to fix this (which is a shame, because I really like it better than FreeBSD).

---

### Post by ian dobson on 2011-07-24
Hi,

Looking at the stack trace it looks as if your hitting a bug in the fs. It maybe not be a bug directly, rather file system corruption which is causing a gpf.

Try running a full file system check on all your file systems.

Also is the last sys file always scaling_governor? If yes try disabling the cpu scaling. I can't imagine what could  cause such a problem but......

Regards
Ian Dobson

---

### Post by searing on 2011-07-24
I ran xfs_check on my XFS filesystem.  It returned with no output, which means it found nothing wrong (according to the man page).  My root filesystem is using ext4, not XFS.  I have no other XFS filesystems.

I dug back and found another CPU dump (most of the time, the system crashes before the log is written).  This other one included a call trace.  However, it is from before I upgraded from 10.04 LTS to 11.04, so perhaps it's a different bug (although it posed the same symptoms).

```
Jul  8 20:23:58 titanium kernel: [ 6131.317334] general protection fault: 0000 [#1] SMP
Jul  8 20:23:58 titanium kernel: [ 6131.317714] last sysfs file: /sys/devices/pci0000:00/0000:00:1e.0/0000:06:04.0/irq
Jul  8 20:23:58 titanium kernel: [ 6131.318060] CPU 0
Jul  8 20:23:58 titanium kernel: [ 6131.318252] Modules linked in: xfs exportfs fbcon tileblit font bitblit softcursor vga16fb vgastate snd_hda_codec_realtek nouveau snd_hda_intel ttm drm_kms_helper ppdev snd_hda_codec snd_hwdep parport_
pc snd_pcm snd_timer serio_raw xhci intel_agp drm i2c_algo_bit snd soundcore snd_page_alloc lp parport raid10 raid456 async_pq async_xor xor async_memcpy async_raid6_recov raid6_pq async_tx raid1 raid0 multipath pata_jmicron e1000 e1000e
 ahci linear r8169 mii
Jul  8 20:23:58 titanium kernel: [ 6131.324237] Pid: 1466, comm: flush-9:0 Not tainted 2.6.32-32-server #62-Ubuntu P55-USB3
Jul  8 20:23:58 titanium kernel: [ 6131.324608] RIP: 0010:[<ffffffff810f616f>]  [<ffffffff810f616f>] find_get_pages+0x5f/0xf0
Jul  8 20:23:58 titanium kernel: [ 6131.325081] RSP: 0018:ffff88018fcf57a0  EFLAGS: 00010293
Jul  8 20:23:58 titanium kernel: [ 6131.325327] RAX: ffff8800cfc9c6b0 RBX: ffff88018fcf5880 RCX: 0000000000000000
Jul  8 20:23:58 titanium kernel: [ 6131.325628] RDX: 0000000000000000 RSI: 000000000000000e RDI: fffdea0002d39900
Jul  8 20:23:58 titanium kernel: [ 6131.325924] RBP: ffff88018fcf57f0 R08: ffff88018fcf5760 R09: 000000000000000e
Jul  8 20:23:58 titanium kernel: [ 6131.326221] R10: 000000000000000d R11: ffff8800cfc9c718 R12: ffff880180dceab8
Jul  8 20:23:58 titanium kernel: [ 6131.326518] R13: 000000000000000e R14: 000000000001e741 R15: ffff88018fcf5880
Jul  8 20:23:58 titanium kernel: [ 6131.326815] FS:  0000000000000000(0000) GS:ffff880007400000(0000) knlGS:0000000000000000
Jul  8 20:23:58 titanium kernel: [ 6131.327188] CS:  0010 DS: 0018 ES: 0018 CR0: 000000008005003b
Jul  8 20:23:58 titanium kernel: [ 6131.327447] CR2: 00007f45a4a07dd8 CR3: 0000000196a5d000 CR4: 00000000000006f0
Jul  8 20:23:58 titanium kernel: [ 6131.327749] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Jul  8 20:23:58 titanium kernel: [ 6131.328049] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Jul  8 20:23:58 titanium kernel: [ 6131.328340] Process flush-9:0 (pid: 1466, threadinfo ffff88018fcf4000, task ffff8801907f8000)
Jul  8 20:23:58 titanium kernel: [ 6131.355455] Stack:
Jul  8 20:23:58 titanium kernel: [ 6131.368991]  ffff88018fcf59e8 ffff880180dce990 0000000c00000000 ffff88018fcf5d40
Jul  8 20:23:58 titanium kernel: [ 6131.382751] <0> 0000000000023d30 ffff88018fcf5870 ffff88018fcf5801 000000000001e741
Jul  8 20:23:58 titanium kernel: [ 6131.410012] <0> 0000000000000001 0000000000000000 ffff88018fcf5810 ffffffff81100a52
Jul  8 20:23:58 titanium kernel: [ 6131.451359] Call Trace:
Jul  8 20:23:58 titanium kernel: [ 6131.464850]  [<ffffffff81100a52>] pagevec_lookup+0x22/0x30
Jul  8 20:23:58 titanium kernel: [ 6131.478286]  [<ffffffffa03443b4>] xfs_cluster_write+0xb4/0x190 [xfs]
Jul  8 20:23:58 titanium kernel: [ 6131.491577]  [<ffffffffa0344a4d>] xfs_page_state_convert+0x5bd/0x720 [xfs]
Jul  8 20:23:58 titanium kernel: [ 6131.504938]  [<ffffffffa0344d0a>] xfs_vm_writepage+0x7a/0x130 [xfs]
Jul  8 20:23:58 titanium kernel: [ 6131.518146]  [<ffffffff8110f91e>] ? __dec_zone_page_state+0x2e/0x30
Jul  8 20:23:58 titanium kernel: [ 6131.531096]  [<ffffffff810fe7e7>] __writepage+0x17/0x40
Jul  8 20:23:58 titanium kernel: [ 6131.543827]  [<ffffffff810ff967>] write_cache_pages+0x1d7/0x3e0
Jul  8 20:23:58 titanium kernel: [ 6131.556415]  [<ffffffff810fe7d0>] ? __writepage+0x0/0x40
Jul  8 20:23:58 titanium kernel: [ 6131.568882]  [<ffffffff810ffb94>] generic_writepages+0x24/0x30
Jul  8 20:23:58 titanium kernel: [ 6131.581255]  [<ffffffffa0343afd>] xfs_vm_writepages+0x5d/0x80 [xfs]
Jul  8 20:23:58 titanium kernel: [ 6131.593276]  [<ffffffff810ffbc1>] do_writepages+0x21/0x40
Jul  8 20:23:58 titanium kernel: [ 6131.605006]  [<ffffffff81168db6>] writeback_single_inode+0xf6/0x3d0
Jul  8 20:23:58 titanium kernel: [ 6131.616310]  [<ffffffff811694e5>] writeback_sb_inodes+0x195/0x280
Jul  8 20:23:58 titanium kernel: [ 6131.627362]  [<ffffffff81169d00>] writeback_inodes_wb+0xa0/0x1b0
Jul  8 20:23:58 titanium kernel: [ 6131.638338]  [<ffffffff8116a04b>] wb_writeback+0x23b/0x2a0
Jul  8 20:23:58 titanium kernel: [ 6131.649166]  [<ffffffff81077bec>] ? lock_timer_base+0x3c/0x70
Jul  8 20:23:58 titanium kernel: [ 6131.659779]  [<ffffffff81078732>] ? del_timer_sync+0x22/0x30
Jul  8 20:23:58 titanium kernel: [ 6131.670119]  [<ffffffff8116a159>] wb_do_writeback+0xa9/0x190
Jul  8 20:23:58 titanium kernel: [ 6131.680121]  [<ffffffff81077d00>] ? process_timeout+0x0/0x10
Jul  8 20:23:58 titanium kernel: [ 6131.690126]  [<ffffffff8116a293>] bdi_writeback_task+0x53/0xf0
Jul  8 20:23:58 titanium kernel: [ 6131.699887]  [<ffffffff81111636>] bdi_start_fn+0x86/0x100
Jul  8 20:23:58 titanium kernel: [ 6131.709332]  [<ffffffff811115b0>] ? bdi_start_fn+0x0/0x100
Jul  8 20:23:58 titanium kernel: [ 6131.718923]  [<ffffffff81085d16>] kthread+0x96/0xa0
Jul  8 20:23:58 titanium kernel: [ 6131.728354]  [<ffffffff810141ea>] child_rip+0xa/0x20
Jul  8 20:23:58 titanium kernel: [ 6131.737607]  [<ffffffff81085c80>] ? kthread+0x0/0xa0
Jul  8 20:23:58 titanium kernel: [ 6131.746739]  [<ffffffff810141e0>] ? child_rip+0x0/0x20
Jul  8 20:23:58 titanium kernel: [ 6131.755612] Code: 85 c0 89 c6 0f 84 91 00 00 00 49 89 df 31 d2 31 c9 0f 1f 00 49 8b 07 48 8b 38 40 f6 c7 01 75 cf 48 85 ff 74 3c 48 83 ff ff 74 c4 <44> 8b 47 08 45 85 c0 74 e3 45 8d 48 01 49 63 c0 4c 8d 57 08 4d
Jul  8 20:23:58 titanium kernel: [ 6131.789764] RIP  [<ffffffff810f616f>] find_get_pages+0x5f/0xf0
Jul  8 20:23:58 titanium kernel: [ 6131.799952]  RSP <ffff88018fcf57a0>
Jul  8 20:23:58 titanium kernel: [ 6131.817783] ---[ end trace 7678b2036fe20b91 ]---
```I hope this can give you more information.

Edit:  This call trace seems to reinforce my suspicion that it was related to writes.  I'm going to see if I can dig back farther to find another intact CPU dump.

Edit 2:  I found another dump, this one includes two cores.

```
Jun 25 11:16:35 titanium kernel: [59480.737150] CPU 2
Jun 25 11:16:35 titanium kernel: [59480.737329] Modules linked in: xfs exportfs fbcon tileblit font bitblit softcursor vga16fb vgastate snd_hda_codec_realtek snd_hda_intel nouveau snd_hda_codec snd_hwdep ttm drm_kms_helper snd_pcm ppdev
snd_timer serio_raw parport_pc intel_agp drm i2c_algo_bit xhci snd soundcore snd_page_alloc lp parport raid10 raid456 async_pq async_xor xor async_memcpy async_raid6_recov raid6_pq async_tx raid1 r8169 raid0 mii e1000 multipath e1000e pa
ta_jmicron ahci linear
Jun 25 11:16:35 titanium kernel: [59480.743069] Pid: 1977, comm: flush-9:0 Not tainted 2.6.32-32-server #62-Ubuntu P55-USB3
Jun 25 11:16:35 titanium kernel: [59480.743420] RIP: 0010:[<ffffffffa034a8f5>]  [<ffffffffa034a8f5>] xfs_submit_ioend+0x65/0xf0 [xfs]
Jun 25 11:16:35 titanium kernel: [59480.743909] RSP: 0018:ffff880159d978f0  EFLAGS: 00010202
Jun 25 11:16:35 titanium kernel: [59480.744143] RAX: 0000000000001000 RBX: fffd8800c84dd4d0 RCX: 000000000000001d
Jun 25 11:16:35 titanium kernel: [59480.744426] RDX: 00000000c50b2000 RSI: 0000000000000000 RDI: 0000000000001000
Jun 25 11:16:35 titanium kernel: [59480.744711] RBP: ffff880159d97920 R08: 00000000000000e0 R09: 00000001cdf0a900
Jun 25 11:16:35 titanium kernel: [59480.744994] R10: 0000000000000000 R11: 0000000000000002 R12: ffff880159e68b40
Jun 25 11:16:35 titanium kernel: [59480.745279] R13: ffff8800df43c960 R14: 0000000000000000 R15: 0000000039be153d
Jun 25 11:16:35 titanium kernel: [59480.745566] FS:  0000000000000000(0000) GS:ffff880007480000(0000) knlGS:0000000000000000
Jun 25 11:16:35 titanium kernel: [59480.745920] CS:  0010 DS: 0018 ES: 0018 CR0: 000000008005003b
Jun 25 11:16:35 titanium kernel: [59480.746166] CR2: 00007f1b6e9ec8b4 CR3: 0000000001001000 CR4: 00000000000006e0
Jun 25 11:16:35 titanium kernel: [59480.746449] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Jun 25 11:16:35 titanium kernel: [59480.746733] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Jun 25 11:16:35 titanium kernel: [59480.747025] Process flush-9:0 (pid: 1977, threadinfo ffff880159d96000, task ffff8801967cae00)
Jun 25 11:16:35 titanium kernel: [59480.786950]  ffff8800df43c960 0000000000005d04 0000000000000001 00000000017e7000
Jun 25 11:16:35 titanium kernel: [59480.800633] <0> ffff8800df43c960 ffffea0002b55a58 ffff880159d97a20 ffffffffa034b82f
Jun 25 11:16:35 titanium kernel: [59480.827794] <0> ffff880100000000 0000000000005d04 0000000000000001 0000000000000004
Jun 25 11:16:35 titanium kernel: [59480.882779]  [<ffffffffa034b82f>] xfs_page_state_convert+0x39f/0x720 [xfs]
Jun 25 11:16:35 titanium kernel: [59480.896449]  [<ffffffffa034bd0a>] xfs_vm_writepage+0x7a/0x130 [xfs]
Jun 25 11:16:35 titanium kernel: [59480.909971]  [<ffffffff8110f91e>] ? __dec_zone_page_state+0x2e/0x30
Jun 25 11:16:35 titanium kernel: [59480.923366]  [<ffffffff810fe7e7>] __writepage+0x17/0x40
Jun 25 11:16:35 titanium kernel: [59480.936605]  [<ffffffff810ff967>] write_cache_pages+0x1d7/0x3e0
Jun 25 11:16:35 titanium kernel: [59480.949508]  [<ffffffff810fe7d0>] ? __writepage+0x0/0x40
Jun 25 11:16:35 titanium kernel: [59480.962245]  [<ffffffff810ffb94>] generic_writepages+0x24/0x30
Jun 25 11:16:35 titanium kernel: [59480.974876]  [<ffffffffa034aafd>] xfs_vm_writepages+0x5d/0x80 [xfs]
Jun 25 11:16:35 titanium kernel: [59480.987385]  [<ffffffff810ffbc1>] do_writepages+0x21/0x40
Jun 25 11:16:35 titanium kernel: [59480.999744]  [<ffffffff81168db6>] writeback_single_inode+0xf6/0x3d0
Jun 25 11:16:35 titanium kernel: [59481.011861]  [<ffffffff811694e5>] writeback_sb_inodes+0x195/0x280
Jun 25 11:16:35 titanium kernel: [59481.023761]  [<ffffffff81169d00>] writeback_inodes_wb+0xa0/0x1b0
Jun 25 11:16:35 titanium kernel: [59481.035403]  [<ffffffff8116a04b>] wb_writeback+0x23b/0x2a0
Jun 25 11:16:35 titanium kernel: [59481.046763]  [<ffffffff81077bec>] ? lock_timer_base+0x3c/0x70
Jun 25 11:16:35 titanium kernel: [59481.057945]  [<ffffffff81078732>] ? del_timer_sync+0x22/0x30
Jun 25 11:16:35 titanium kernel: [59481.068887]  [<ffffffff8116a159>] wb_do_writeback+0xa9/0x190
Jun 25 11:16:35 titanium kernel: [59481.079519]  [<ffffffff81077d00>] ? process_timeout+0x0/0x10
Jun 25 11:16:35 titanium kernel: [59481.089876]  [<ffffffff8116a293>] bdi_writeback_task+0x53/0xf0
Jun 25 11:16:35 titanium kernel: [59481.099957]  [<ffffffff81111636>] bdi_start_fn+0x86/0x100
Jun 25 11:16:35 titanium kernel: [59481.109944]  [<ffffffff811115b0>] ? bdi_start_fn+0x0/0x100
Jun 25 11:16:35 titanium kernel: [59481.119804]  [<ffffffff81085d16>] kthread+0x96/0xa0
Jun 25 11:16:35 titanium kernel: [59481.129299]  [<ffffffff810141ea>] child_rip+0xa/0x20
Jun 25 11:16:35 titanium kernel: [59481.138902]  [<ffffffff81085c80>] ? kthread+0x0/0xa0
Jun 25 11:16:35 titanium kernel: [59481.148345]  [<ffffffff810141e0>] ? child_rip+0x0/0x20
Jun 25 11:16:35 titanium kernel: [59481.203395]  RSP <ffff880159d978f0>
Jun 25 11:16:35 titanium kernel: [59481.222015] ---[ end trace 85bba6ef59ec74e3 ]---
Jun 25 11:16:35 titanium kernel: [59481.238975] SMP
Jun 25 11:16:35 titanium kernel: [59481.238982] CPU 0
Jun 25 11:16:35 titanium kernel: [59481.238983] Modules linked in: xfs exportfs fbcon tileblit font bitblit softcursor vga16fb vgastate snd_hda_codec_realtek snd_hda_intel nouveau snd_hda_codec snd_hwdep ttm drm_kms_helper snd_pcm ppdev
snd_timer serio_raw parport_pc intel_agp drm i2c_algo_bit xhci snd soundcore snd_page_alloc lp parport raid10 raid456 async_pq async_xor xor async_memcpy async_raid6_recov raid6_pq async_tx raid1 r8169 raid0 mii e1000 multipath e1000e pa
ta_jmicron ahci linear
Jun 25 11:16:35 titanium kernel: [59481.239005] Pid: 985, comm: md0_raid6 Tainted: G      D    2.6.32-32-server #62-Ubuntu P55-USB3
Jun 25 11:16:35 titanium kernel: [59481.239006] RIP: 0010:[<ffffffff812bfa4b>]  [<ffffffff812bfa4b>] memcpy_c+0xb/0x20
Jun 25 11:16:35 titanium kernel: [59481.239013] RSP: 0018:ffff88019015fb68  EFLAGS: 00010246
Jun 25 11:16:35 titanium kernel: [59481.239015] RAX: ffff880190730000 RBX: ffff88019015e000 RCX: 0000000000000200
Jun 25 11:16:35 titanium kernel: [59481.239016] RDX: 0000000000000000 RSI: 23ff8800c508b000 RDI: ffff880190730000
Jun 25 11:16:35 titanium kernel: [59481.239017] RBP: ffff88019015fbd0 R08: 0000000000001000 R09: ffff88019015fbf0
Jun 25 11:16:35 titanium kernel: [59481.239019] R10: 0000000000000000 R11: 0000000000000000 R12: ffff88019015fbf0
Jun 25 11:16:35 titanium kernel: [59481.239020] R13: 0000000000001000 R14: 0000000000000000 R15: 0000000000000000
Jun 25 11:16:35 titanium kernel: [59481.239022] FS:  0000000000000000(0000) GS:ffff880007400000(0000) knlGS:0000000000000000
Jun 25 11:16:35 titanium kernel: [59481.239024] CS:  0010 DS: 0018 ES: 0018 CR0: 000000008005003b
Jun 25 11:16:35 titanium kernel: [59481.239025] CR2: 00007f4111adb000 CR3: 0000000198b7b000 CR4: 00000000000006f0
Jun 25 11:16:35 titanium kernel: [59481.239026] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Jun 25 11:16:35 titanium kernel: [59481.239028] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Jun 25 11:16:35 titanium kernel: [59481.239030] Process md0_raid6 (pid: 985, threadinfo ffff88019015e000, task ffff880195e85c00)
Jun 25 11:16:35 titanium kernel: [59481.239032]  ffffffffa00bc0e7 0000000000000000 0000000000000000 0000000000000000
Jun 25 11:16:35 titanium kernel: [59481.239034] <0> fffdea0002b19e68 ffffea0005799280 0000000000001000 0000000000000286
Jun 25 11:16:35 titanium kernel: [59481.239036] <0> 0000000000001000 0000000000000015 0000000000001000 0000000000001000
Jun 25 11:16:35 titanium kernel: [59481.239044]  [<ffffffffa00bc0e7>] ? async_memcpy+0xe7/0x25c [async_memcpy]
Jun 25 11:16:35 titanium kernel: [59481.239050]  [<ffffffffa00d7ff5>] async_copy_data+0x85/0x130 [raid456]
Jun 25 11:16:35 titanium kernel: [59481.239054]  [<ffffffffa00d899e>] __raid_run_ops+0x35e/0x7d0 [raid456]
Jun 25 11:16:35 titanium kernel: [59481.239058]  [<ffffffff81061b70>] ? load_balance_newidle+0xc0/0x350
Jun 25 11:16:35 titanium kernel: [59481.239062]  [<ffffffffa00d6ca0>] ? ops_complete_reconstruct+0x0/0xa0 [raid456]
Jun 25 11:16:35 titanium kernel: [59481.239065]  [<ffffffffa00da368>] handle_stripe6+0x828/0xb40 [raid456]
Jun 25 11:16:35 titanium kernel: [59481.239068]  [<ffffffffa00d694c>] ? __release_stripe+0xcc/0x1c0 [raid456]
Jun 25 11:16:35 titanium kernel: [59481.239072]  [<ffffffffa00db045>] handle_stripe+0x25/0x30 [raid456]
Jun 25 11:16:35 titanium kernel: [59481.239075]  [<ffffffffa00db442>] raid5d+0x202/0x320 [raid456]
Jun 25 11:16:35 titanium kernel: [59481.239079]  [<ffffffff81559ff9>] ? _spin_unlock_irqrestore+0x19/0x30
Jun 25 11:16:35 titanium kernel: [59481.239084]  [<ffffffff8142ca6c>] md_thread+0x5c/0x130
Jun 25 11:16:35 titanium kernel: [59481.239088]  [<ffffffff81086090>] ? autoremove_wake_function+0x0/0x40
Jun 25 11:16:35 titanium kernel: [59481.239091]  [<ffffffff8142ca10>] ? md_thread+0x0/0x130
Jun 25 11:16:35 titanium kernel: [59481.239092]  [<ffffffff81085d16>] kthread+0x96/0xa0
Jun 25 11:16:35 titanium kernel: [59481.239096]  [<ffffffff810141ea>] child_rip+0xa/0x20
Jun 25 11:16:35 titanium kernel: [59481.239098]  [<ffffffff81085c80>] ? kthread+0x0/0xa0
Jun 25 11:16:35 titanium kernel: [59481.239100]  [<ffffffff810141e0>] ? child_rip+0x0/0x20
Jun 25 11:16:35 titanium kernel: [59481.239116]  RSP <ffff88019015fb68>
Jun 25 11:16:35 titanium kernel: [59481.239144] ---[ end trace 85bba6ef59ec74e4 ]---
```

---

### Post by ian dobson on 2011-07-24
Hi,

OK the crash is comming from xfs filesystem drivers (kmem_cache_alloc /pagevec_lookup xfs_cluster_write).

Sorry but I can't say much more than this, I've only ever used ext file system on normal pc's and squashfs/jffs on embeded boxes.

Regards
Ian Dobson

---

### Post by searing on 2011-07-24
Alright, thanks for helping me pinpoint the issue.  I guess I'll prepare and submit a bug report to those developing XFS and see where that takes me.

Edit:  I've been doing quite a bit of reading, and I'm going to try a few things - I'll edit this again if any of them work, so others can benefit.

---

### Post by ian dobson on 2011-07-24
Hi,

Can I ask why your using xfs? I've been running ext4 for about 18months now on my large (now 8Tb) video storage, and haven't seen any problems up till now.

I'm just asking as I've seen alot of threads on various forums that are alot like yours (Kernel panic/oops pointing to xfs/xfs caching threads).

Regards
Ian Dobson

---

### Post by searing on 2011-07-24
Well, I had a longer post typed out, but the forum system here screwed it up ("token has expired" o.o).

Anyways, I was under the impression that XFS performed better with large files, which is mostly what I'm dealing with.  I suppose I could switch to ext4, but I would have to back up all the data on my server to delete everything and start again.

Is there a way around this?  Can I shrink my XFS to half my raid array (since I"m only using about 1/4 of it right now), make an ext4 FS on the other half, copy my data over, and then expand my ext4 FS to fit the rest of the array?

---

### Post by ian dobson on 2011-07-24
Hi,

From what I've heard you can't shrink xfs. I've heard of convertfs, but have never used it myself.

Another solution would be to buy afew 2tb drives and backup you data onto them, wd 2tb green drives are so cheap these days (I purchased 2 afew days ago for less than 150$)

Regards
Ian Dobson

---

### Post by Cappientes on 2011-08-08
> **searing said:**
> Alright, thanks for helping me pinpoint the issue.  I guess I'll prepare and submit a bug report to those developing XFS and see where that takes me.

Edit:  I've been doing quite a bit of reading, and I'm going to try a few things - I'll edit this again if any of them work, so others can benefit.

Hi,

We're having problems similar to you, have you got a link to the bug you reported so we can follow it too?

Cheers,

C

---

