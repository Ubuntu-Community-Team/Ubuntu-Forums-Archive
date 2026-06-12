---
title: "mdadm serious data corruption"
date: 2011-08-13
forum: Server Platforms
---

### Post by searing on 2011-08-13
I've been using Ubuntu on my fileserver for quite a while now, and I've always really had this problem, but I want to finally address it and get it fixed.

At seemingly random points (when my fileserver is under stress - typically while I'm writing lots of data to it), my fileserver will crash.  It generally completely crashes, not responding to any further file requests or any of my SSH commands, and must be reset hard (typically by flipping the power switch).  After such an occasion, I end up with some corrupted files.  It seems to corrupt a large array of files (it's not an isolated issue - for example, it corrupts files that were not being accessed anywhere near the time it crashed, including files that had never been accessed during that period of uptime).  The files don't get completely smashed, but they're definitely corrupted (artifacts in images, skips in audio and video files, often complete failure of binary files such as virtual hard drives or disc images).

I'm using Ubuntu Server 11.04, but similar issues to this happened for me in 10.04 LTS (in fact, I upgraded to try to solve them).  I'm using mdadm to create an 8-drive raid6 array.  The drives are 1.5 TB each, mostly Samsung HD154UI, but with a WD drive in there too (sorry, I can't find the model number at the moment).  The hard drives themselves appear to be working fine - SMART reports no issues with any of them, mdadm says they're all up, and I have no reason to believe that the drives are at fault here (although I can conduct further tests if necessary).

I've posted about this problem before [here]("http://ubuntuforums.org/showthread.php?t=1790667") and [here]("http://ubuntuforums.org/showthread.php?t=1810970").  In these cases, the issues seemed to be with XFS - in fact, I switched from XFS to ext4 on my RAID array because I simply believed XFS to be unstable.  Unfortunately, this issue occurs with ext4 as well, so I'm fairly certain it's an mdadm issue.

Here is the output of "cat /proc/mdstat", for those interested:
```
md127 : active raid6 sdi[7] sdh[6] sdc[1] sdb[0] sdg[5] sdf[4] sdd[2] sde[3]
      8790822912 blocks super 1.2 level 6, 512k chunk, algorithm 2 [8/8] [UUUUUUUU]
```This has only happened twice so far with ext4 for me.  I'm not sure if the second time incurred corruption, because my files were already corrupted from the first time.  Here are some stack traces from syslog:

First:
```
Aug 12 23:14:14 titanium kernel: [38176.570325] general protection fault: 0000 [#1] SMP
Aug 12 23:14:14 titanium kernel: [38176.570343] last sysfs file: /sys/devices/system/cpu/cpu3/cpufreq/scaling_governor
Aug 12 23:14:14 titanium kernel: [38176.570349] CPU 2
Aug 12 23:14:14 titanium kernel: [38176.570351] Modules linked in: nfsd lockd nfs_acl auth_rpcgss sunrpc exportfs snd_hda_codec_realtek ppdev nouveau snd_hda_intel serio_raw snd_hda_codec ttm snd_hwdep parport_pc snd_pcm drm_kms_helper drm snd_timer snd i2c_algo_bit video soundcore lp snd_page_alloc parport raid10 raid456 async_pq async_xor xor async_memcpy async_raid6_recov e1000 ahci r8169 e1000e xhci_hcd pata_jmicron raid6_pq libahci async_tx raid1 raid0 multipath linear
Aug 12 23:14:14 titanium kernel: [38176.570429]
Aug 12 23:14:14 titanium kernel: [38176.570432] Pid: 1258, comm: jbd2/md127-8 Not tainted 2.6.38-10-server #46-Ubuntu Gigabyte Technology Co., Ltd. P55-USB3/P55-USB3
Aug 12 23:14:14 titanium kernel: [38176.570445] RIP: 0010:[<ffffffff8110ba89>]  [<ffffffff8110ba89>] find_get_pages_tag+0x69/0x120
Aug 12 23:14:14 titanium kernel: [38176.570459] RSP: 0018:ffff88018878dad0  EFLAGS: 00010246
Aug 12 23:14:14 titanium kernel: [38176.570464] RAX: ffff8800caffd190 RBX: ffff88018878dbb0 RCX: 0000000000000001
Aug 12 23:14:14 titanium kernel: [38176.570469] RDX: ffff88018878dbb8 RSI: 000000000000000e RDI: fffdea0002a318c0
Aug 12 23:14:14 titanium kernel: [38176.570474] RBP: ffff88018878db20 R08: 0000000000000002 R09: 0000000000000002
Aug 12 23:14:14 titanium kernel: [38176.570479] R10: ffffea0002a31890 R11: 0000000000000000 R12: ffff88018878dc28
Aug 12 23:14:14 titanium kernel: [38176.570484] R13: 0000000000000002 R14: 000000000000000e R15: 0000000000000001
Aug 12 23:14:14 titanium kernel: [38176.570490] FS:  0000000000000000(0000) GS:ffff8800df880000(0000) knlGS:0000000000000000
Aug 12 23:14:14 titanium kernel: [38176.570495] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
Aug 12 23:14:14 titanium kernel: [38176.570500] CR2: 00007fc8df9cf000 CR3: 0000000001a03000 CR4: 00000000000006e0
Aug 12 23:14:14 titanium kernel: [38176.570505] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Aug 12 23:14:14 titanium kernel: [38176.570510] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Aug 12 23:14:14 titanium kernel: [38176.570516] Process jbd2/md127-8 (pid: 1258, threadinfo ffff88018878c000, task ffff880186685b80)
Aug 12 23:14:14 titanium kernel: [38176.570521] Stack:
Aug 12 23:14:14 titanium kernel: [38176.570524]  ffff88018878db20 ffffffff81204a33 a8000a952bc00000 ffff880165fe1b60
Aug 12 23:14:14 titanium kernel: [38176.570533]  0000000000000000 ffff88018878dba0 ffff880165fe1b58 0000000000000001
Aug 12 23:14:14 titanium kernel: [38176.570542]  0000000000000000 ffff88018878dc20 ffff88018878db40 ffffffff81117275
Aug 12 23:14:14 titanium kernel: [38176.570550] Call Trace:
Aug 12 23:14:14 titanium kernel: [38176.570557]  [<ffffffff81204a33>] ? ext4_writepage+0x183/0x220
Aug 12 23:14:14 titanium kernel: [38176.570563]  [<ffffffff81117275>] pagevec_lookup_tag+0x25/0x40
Aug 12 23:14:14 titanium kernel: [38176.570568]  [<ffffffff8111548c>] write_cache_pages+0xfc/0x460
Aug 12 23:14:14 titanium kernel: [38176.570576]  [<ffffffff8105824d>] ? enqueue_entity+0x14d/0x2a0
Aug 12 23:14:14 titanium kernel: [38176.570582]  [<ffffffff81114ef0>] ? __writepage+0x0/0x40
Aug 12 23:14:14 titanium kernel: [38176.570587]  [<ffffffff81115814>] generic_writepages+0x24/0x30
Aug 12 23:14:14 titanium kernel: [38176.570594]  [<ffffffff812421b4>] journal_submit_data_buffers+0xb4/0x190
Aug 12 23:14:14 titanium kernel: [38176.570600]  [<ffffffff81242708>] jbd2_journal_commit_transaction+0x308/0x1180
Aug 12 23:14:14 titanium kernel: [38176.570609]  [<ffffffff8100a6e0>] ? __switch_to+0xc0/0x2f0
Aug 12 23:14:14 titanium kernel: [38176.570616]  [<ffffffff815d7c0e>] ? _raw_spin_lock+0xe/0x20
Aug 12 23:14:14 titanium kernel: [38176.570622]  [<ffffffff81074d4b>] ? lock_timer_base.clone.20+0x3b/0x70
Aug 12 23:14:14 titanium kernel: [38176.570630]  [<ffffffff810879c0>] ? autoremove_wake_function+0x0/0x40
Aug 12 23:14:14 titanium kernel: [38176.570636]  [<ffffffff812476db>] kjournald2+0xbb/0x220
Aug 12 23:14:14 titanium kernel: [38176.570641]  [<ffffffff810879c0>] ? autoremove_wake_function+0x0/0x40
Aug 12 23:14:14 titanium kernel: [38176.570646]  [<ffffffff81247620>] ? kjournald2+0x0/0x220
Aug 12 23:14:14 titanium kernel: [38176.570651]  [<ffffffff81087276>] kthread+0x96/0xa0
Aug 12 23:14:14 titanium kernel: [38176.570656]  [<ffffffff8100cde4>] kernel_thread_helper+0x4/0x10
Aug 12 23:14:14 titanium kernel: [38176.570995]  [<ffffffff810871e0>] ? kthread+0x0/0xa0
Aug 12 23:14:14 titanium kernel: [38176.571388]  [<ffffffff8100cde0>] ? kernel_thread_helper+0x0/0x10
Aug 12 23:14:14 titanium kernel: [38176.571781] Code: 1d 00 85 c0 89 c6 0f 84 ab 00 00 00 48 89 da 45 31 ff 31 c9 66 0f 1f 44 00 00 48 8b 02 48 8b 38 48 85 ff 74 3e 40 f6 c7 01 75 c1 <44> 8b 47 08 4c 8d 57 08 45 85 c0 74 e5 45 8d 48 01 44 89 c0 f0
Aug 12 23:14:14 titanium kernel: [38176.572653] RIP  [<ffffffff8110ba89>] find_get_pages_tag+0x69/0x120
Aug 12 23:14:14 titanium kernel: [38176.573055]  RSP <ffff88018878dad0>
Aug 12 23:14:14 titanium kernel: [38176.575218] ---[ end trace c246b6438e1a5d28 ]---
Aug 12 23:14:20 titanium kernel: [38182.957934] general protection fault: 0000 [#2] SMP
Aug 12 23:14:20 titanium kernel: [38182.958576] last sysfs file: /sys/devices/system/cpu/cpu3/cpufreq/scaling_governor
Aug 12 23:14:20 titanium kernel: [38182.959206] CPU 2
Aug 12 23:14:20 titanium kernel: [38182.959217] Modules linked in: nfsd lockd nfs_acl auth_rpcgss sunrpc exportfs snd_hda_codec_realtek ppdev nouveau snd_hda_intel serio_raw snd_hda_codec ttm snd_hwdep parport_pc snd_pcm drm_kms_helper drm snd_timer snd i2c_algo_bit video soundcore lp snd_page_alloc parport raid10 raid456 async_pq async_xor xor async_memcpy async_raid6_recov e1000 ahci r8169 e1000e xhci_hcd pata_jmicron raid6_pq libahci async_tx raid1 raid0 multipath linear
Aug 12 23:14:20 titanium kernel: [38182.962351]
Aug 12 23:14:20 titanium kernel: [38182.962769] Pid: 1566, comm: flush-9:127 Tainted: G      D     2.6.38-10-server #46-Ubuntu Gigabyte Technology Co., Ltd. P55-USB3/P55-USB3
Aug 12 23:14:20 titanium kernel: [38182.964016] RIP: 0010:[<ffffffff812024c0>]  [<ffffffff812024c0>] ext4_num_dirty_pages.clone.38+0x150/0x2d0
Aug 12 23:14:20 titanium kernel: [38182.964691] RSP: 0018:ffff880036ca9a00  EFLAGS: 00010206
Aug 12 23:14:20 titanium kernel: [38182.965179] RAX: 000000000000000e RBX: 000000000001232c RCX: 000000000001232c
Aug 12 23:14:20 titanium kernel: [38182.965625] RDX: 000000000000232c RSI: ffff880036ca9a40 RDI: fffd8800cac5d478
Aug 12 23:14:20 titanium kernel: [38182.966266] RBP: ffff880036ca9ae0 R08: 0000000000000223 R09: ffff8800cac5d478
Aug 12 23:14:20 titanium kernel: [38182.966900] R10: a8000af4c9e00000 R11: 57ffdf0b38dd3278 R12: ffff880165fe1b58
Aug 12 23:14:20 titanium kernel: [38182.967554] R13: 000000000000232a R14: 0000000000008000 R15: ffffea0002bd4040
Aug 12 23:14:20 titanium kernel: [38182.968001] FS:  0000000000000000(0000) GS:ffff8800df880000(0000) knlGS:0000000000000000
Aug 12 23:14:20 titanium kernel: [38182.968603] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
Aug 12 23:14:20 titanium kernel: [38182.969248] CR2: 00007fc8df9cf000 CR3: 0000000001a03000 CR4: 00000000000006e0
Aug 12 23:14:20 titanium kernel: [38182.969908] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Aug 12 23:14:20 titanium kernel: [38182.970403] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Aug 12 23:14:20 titanium kernel: [38182.970844] Process flush-9:127 (pid: 1566, threadinfo ffff880036ca8000, task ffff88018fd016e0)
Aug 12 23:14:20 titanium kernel: [38182.971282] Stack:
Aug 12 23:14:20 titanium kernel: [38182.971748]  ffff880036ca9a38 ffffffff0000000e 000000000001232b 000000000000232b
Aug 12 23:14:20 titanium kernel: [38182.972431]  000000000000000e 0000000000000000 ffffea0002bd3240 ffffea0002bd3278
Aug 12 23:14:20 titanium kernel: [38182.972895]  ffffea0002bd4040 ffffea0002bd4078 ffffea0002bd40b0 ffffea0002bd40e8
Aug 12 23:14:20 titanium kernel: [38182.973358] Call Trace:
Aug 12 23:14:20 titanium kernel: [38182.973829]  [<ffffffff812093c5>] ext4_da_writepages+0x5d5/0x630
Aug 12 23:14:20 titanium kernel: [38182.974468]  [<ffffffff811167d1>] do_writepages+0x21/0x40
Aug 12 23:14:20 titanium kernel: [38182.975079]  [<ffffffff8118b7df>] writeback_single_inode+0x9f/0x240
Aug 12 23:14:20 titanium kernel: [38182.975538]  [<ffffffff8118bbbb>] writeback_sb_inodes+0xcb/0x160
Aug 12 23:14:20 titanium kernel: [38182.976102]  [<ffffffff811038b1>] ? __perf_event_task_sched_out+0x31/0x40
Aug 12 23:14:20 titanium kernel: [38182.976654]  [<ffffffff8118be0b>] writeback_inodes_wb+0x10b/0x1c0
Aug 12 23:14:20 titanium kernel: [38182.977107]  [<ffffffff8118c23e>] wb_writeback+0x37e/0x490
Aug 12 23:14:20 titanium kernel: [38182.977571]  [<ffffffff815d7dbf>] ? _raw_spin_lock_irqsave+0x2f/0x40
Aug 12 23:14:20 titanium kernel: [38182.978025]  [<ffffffff81074d4b>] ? lock_timer_base.clone.20+0x3b/0x70
Aug 12 23:14:20 titanium kernel: [38182.978493]  [<ffffffff8118c571>] wb_do_writeback+0x221/0x230
Aug 12 23:14:20 titanium kernel: [38182.978947]  [<ffffffff8118c602>] bdi_writeback_thread+0x82/0x260
Aug 12 23:14:20 titanium kernel: [38182.979576]  [<ffffffff8118c580>] ? bdi_writeback_thread+0x0/0x260
Aug 12 23:14:20 titanium kernel: [38182.980231]  [<ffffffff81087276>] kthread+0x96/0xa0
Aug 12 23:14:20 titanium kernel: [38182.980687]  [<ffffffff8100cde4>] kernel_thread_helper+0x4/0x10
Aug 12 23:14:20 titanium kernel: [38182.981224]  [<ffffffff810871e0>] ? kthread+0x0/0xa0
Aug 12 23:14:20 titanium kernel: [38182.981768]  [<ffffffff8100cde0>] ? kernel_thread_helper+0x0/0x10
Aug 12 23:14:20 titanium kernel: [38182.982180] Code: 39 cb 0f 85 f3 00 00 00 49 8b 3f f7 c7 00 08 00 00 74 78 49 8b 3f f7 c7 00 08 00 00 0f 84 40 01 00 00 4d 8b 4f 10 4c 89 cf 66 90 <4c> 8b 07 41 f7 c0 00 02 00 00 0f 84 e8 fe ff ff 48 8b 7f 08 49
Aug 12 23:14:20 titanium kernel: [38182.983407] RIP  [<ffffffff812024c0>] ext4_num_dirty_pages.clone.38+0x150/0x2d0
Aug 12 23:14:20 titanium kernel: [38182.984049]  RSP <ffff880036ca9a00>
Aug 12 23:14:20 titanium kernel: [38182.984807] ---[ end trace c246b6438e1a5d29 ]---
```Second:
```
Aug 13 17:36:37 titanium kernel: [104256.110617] general protection fault: 0000 [#3] SMP
Aug 13 17:36:37 titanium kernel: [104256.110988] last sysfs file: /sys/devices/system/cpu/cpu3/cpufreq/scaling_governor
Aug 13 17:36:37 titanium kernel: [104256.111342] CPU 2
Aug 13 17:36:37 titanium kernel: [104256.111347] Modules linked in: nfsd lockd nfs_acl auth_rpcgss sunrpc exportfs snd_hda_codec_realtek ppdev nouveau snd_hda_intel serio_raw snd_hda_codec ttm snd_hwdep parport_pc snd_pcm drm_kms_helper drm snd_timer snd i2c_algo_bit video soundcore lp snd_page_alloc parport raid10 raid456 async_pq async_xor xor async_memcpy async_raid6_recov e1000 ahci r8169 e1000e xhci_hcd pata_jmicron raid6_pq libahci async_tx raid1 raid0 multipath linear
Aug 13 17:36:37 titanium kernel: [104256.113383]
Aug 13 17:36:37 titanium kernel: [104256.113800] Pid: 3730, comm: bash Tainted: G      D     2.6.38-10-server #46-Ubuntu Gigabyte Technology Co., Ltd. P55-USB3/P55-USB3
Aug 13 17:36:37 titanium kernel: [104256.114668] RIP: 0010:[<ffffffff811551e8>]  [<ffffffff811551e8>] kmem_cache_alloc+0x58/0x110
Aug 13 17:36:37 titanium kernel: [104256.115110] RSP: 0018:ffff8800ce20fd10  EFLAGS: 00010082
Aug 13 17:36:37 titanium kernel: [104256.115540] RAX: 0000000000000000 RBX: ffff88019f805780 RCX: ffffffff8106322c
Aug 13 17:36:37 titanium kernel: [104256.115974] RDX: 00000000001c9223 RSI: 00000000000000d0 RDI: ffff88019f805780
Aug 13 17:36:37 titanium kernel: [104256.116415] RBP: ffff8800ce20fd50 R08: ffff8800df896fe0 R09: 00007f271256f000
Aug 13 17:36:37 titanium kernel: [104256.116861] R10: ffff8800ce218000 R11: ffff88019fffb000 R12: fffd8800ce3fcc38
Aug 13 17:36:37 titanium kernel: [104256.117316] R13: 0000000000000282 R14: 0000000000000001 R15: ffff8800ce3fcb98
Aug 13 17:36:37 titanium kernel: [104256.117771] FS:  00007f2713a36720(0000) GS:ffff8800df880000(0000) knlGS:0000000000000000
Aug 13 17:36:37 titanium kernel: [104256.118218] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
Aug 13 17:36:37 titanium kernel: [104256.118668] CR2: 0000000001581098 CR3: 00000000ce218000 CR4: 00000000000006e0
Aug 13 17:36:37 titanium kernel: [104256.119118] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Aug 13 17:36:37 titanium kernel: [104256.119563] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Aug 13 17:36:37 titanium kernel: [104256.120007] Process bash (pid: 3730, threadinfo ffff8800ce20e000, task ffff88018f7744a0)
Aug 13 17:36:37 titanium kernel: [104256.120462] Stack:
Aug 13 17:36:37 titanium kernel: [104256.120909]  ffff88018f484600 000000d000000001 ffff8800ce20fd30 ffff8800ce3fcb80
Aug 13 17:36:37 titanium kernel: [104256.121353]  ffff8800b2cdd730 ffff88018f484600 0000000000000001 ffff8800ce3fcb98
Aug 13 17:36:37 titanium kernel: [104256.121800]  ffff8800ce20fdd0 ffffffff8106322c ffff8801866d16e0 ffff880191f7f998
Aug 13 17:36:37 titanium kernel: [104256.122251] Call Trace:
Aug 13 17:36:37 titanium kernel: [104256.122695]  [<ffffffff8106322c>] dup_mmap+0x12c/0x3a0
Aug 13 17:36:37 titanium kernel: [104256.123140]  [<ffffffff81063db0>] dup_mm+0xc0/0x1c0
Aug 13 17:36:37 titanium kernel: [104256.123584]  [<ffffffff8106479f>] copy_process+0x8bf/0xe80
Aug 13 17:36:37 titanium kernel: [104256.124031]  [<ffffffff812ad1cc>] ? apparmor_file_alloc_security+0x2c/0x60
Aug 13 17:36:37 titanium kernel: [104256.124477]  [<ffffffff81064e09>] do_fork+0x59/0x330
Aug 13 17:36:37 titanium kernel: [104256.124921]  [<ffffffff81181127>] ? alloc_fd+0xf7/0x150
Aug 13 17:36:37 titanium kernel: [104256.125365]  [<ffffffff815d7c0e>] ? _raw_spin_lock+0xe/0x20
Aug 13 17:36:37 titanium kernel: [104256.125810]  [<ffffffff8116ed71>] ? do_pipe_flags+0xd1/0x130
Aug 13 17:36:37 titanium kernel: [104256.126254]  [<ffffffff81015138>] sys_clone+0x28/0x30
Aug 13 17:36:37 titanium kernel: [104256.126698]  [<ffffffff8100c2e3>] stub_clone+0x13/0x20
Aug 13 17:36:37 titanium kernel: [104256.127141]  [<ffffffff8100bfc2>] ? system_call_fastpath+0x16/0x1b
Aug 13 17:36:37 titanium kernel: [104256.127584] Code: 0f 1f 44 00 00 49 89 c5 fa 66 0f 1f 44 00 00 4c 8b 07 65 4c 03 04 25 a8 dc 00 00 4d 8b 20 4d 85 e4 0f 84 a0 00 00 00 48 63 47 18 <49> 8b 04 04 49 89 00 4c 89 ef 57 9d 0f 1f 44 00 00 4d 85 e4 75
Aug 13 17:36:37 titanium kernel: [104256.128631] RIP  [<ffffffff811551e8>] kmem_cache_alloc+0x58/0x110
Aug 13 17:36:37 titanium kernel: [104256.129075]  RSP <ffff8800ce20fd10>
Aug 13 17:36:37 titanium kernel: [104256.131047] ---[ end trace c246b6438e1a5d2a ]---
Aug 13 17:36:50 titanium kernel: [104268.448232] general protection fault: 0000 [#4] SMP
Aug 13 17:36:50 titanium kernel: [104268.448689] last sysfs file: /sys/devices/system/cpu/cpu3/cpufreq/scaling_governor
Aug 13 17:36:50 titanium kernel: [104268.449130] CPU 2
Aug 13 17:36:50 titanium kernel: [104268.449137] Modules linked in: nfsd lockd nfs_acl auth_rpcgss sunrpc exportfs snd_hda_codec_realtek ppdev nouveau snd_hda_intel serio_raw snd_hda_codec ttm snd_hwdep parport_pc snd_pcm drm_kms_helper drm snd_timer snd i2c_algo_bit video soundcore lp snd_page_alloc parport raid10 raid456 async_pq async_xor xor async_memcpy async_raid6_recov e1000 ahci r8169 e1000e xhci_hcd pata_jmicron raid6_pq libahci async_tx raid1 raid0 multipath linear
Aug 13 17:36:50 titanium kernel: [104268.451555]
Aug 13 17:36:50 titanium kernel: [104268.451995] Pid: 1203, comm: winbindd Tainted: G      D     2.6.38-10-server #46-Ubuntu Gigabyte Technology Co., Ltd. P55-USB3/P55-USB3
Aug 13 17:36:50 titanium kernel: [104268.452899] RIP: 0010:[<ffffffff811551e8>]  [<ffffffff811551e8>] kmem_cache_alloc+0x58/0x110
Aug 13 17:36:50 titanium kernel: [104268.453360] RSP: 0018:ffff8801865e7d88  EFLAGS: 00010082
Aug 13 17:36:50 titanium kernel: [104268.453805] RAX: 0000000000000000 RBX: ffff88019f805780 RCX: ffffffff81135fa7
Aug 13 17:36:50 titanium kernel: [104268.454245] RDX: 0000000000000001 RSI: 00000000000080d0 RDI: ffff88019f805780
Aug 13 17:36:50 titanium kernel: [104268.454688] RBP: ffff8801865e7dc8 R08: ffff8800df896fe0 R09: 0000000000000000
Aug 13 17:36:50 titanium kernel: [104268.455131] R10: ffff880192b6aa10 R11: ffff880192b6aa48 R12: fffd8800ce3fcc38
Aug 13 17:36:50 titanium kernel: [104268.455574] R13: 0000000000000286 R14: 0000000000001000 R15: 0000000000000000
Aug 13 17:36:50 titanium kernel: [104268.456019] FS:  00007f25ff734740(0000) GS:ffff8800df880000(0000) knlGS:0000000000000000
Aug 13 17:36:50 titanium kernel: [104268.456464] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Aug 13 17:36:50 titanium kernel: [104268.456908] CR2: 0000000001581098 CR3: 000000018fcf9000 CR4: 00000000000006e0
Aug 13 17:36:50 titanium kernel: [104268.457352] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Aug 13 17:36:50 titanium kernel: [104268.457798] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Aug 13 17:36:50 titanium kernel: [104268.458244] Process winbindd (pid: 1203, threadinfo ffff8801865e6000, task ffff8801865ddb80)
Aug 13 17:36:50 titanium kernel: [104268.458684] Stack:
Aug 13 17:36:50 titanium kernel: [104268.459117]  0000000000088000 000080d000000024 0000000000000000 00007f25ff742000
Aug 13 17:36:50 titanium kernel: [104268.459571]  ffff880190d18a80 0000000000000001 0000000000001000 0000000000000000
Aug 13 17:36:50 titanium kernel: [104268.460026]  ffff8801865e7e98 ffffffff81135fa7 ffff8801900ec180 0000000000000000
Aug 13 17:36:50 titanium kernel: [104268.460478] Call Trace:
Aug 13 17:36:50 titanium kernel: [104268.460915]  [<ffffffff81135fa7>] mmap_region+0x2d7/0x500
Aug 13 17:36:50 titanium kernel: [104268.461352]  [<ffffffff81010f8d>] ? arch_get_unmapped_area_topdown+0x2bd/0x2f0
Aug 13 17:36:50 titanium kernel: [104268.461791]  [<ffffffff81136505>] do_mmap_pgoff+0x335/0x370
Aug 13 17:36:50 titanium kernel: [104268.462225]  [<ffffffff8113673e>] sys_mmap_pgoff+0x1fe/0x230
Aug 13 17:36:50 titanium kernel: [104268.462659]  [<ffffffff81010ad9>] sys_mmap+0x29/0x30
Aug 13 17:36:50 titanium kernel: [104268.463093]  [<ffffffff8100bfc2>] system_call_fastpath+0x16/0x1b
Aug 13 17:36:50 titanium kernel: [104268.463528] Code: 0f 1f 44 00 00 49 89 c5 fa 66 0f 1f 44 00 00 4c 8b 07 65 4c 03 04 25 a8 dc 00 00 4d 8b 20 4d 85 e4 0f 84 a0 00 00 00 48 63 47 18 <49> 8b 04 04 49 89 00 4c 89 ef 57 9d 0f 1f 44 00 00 4d 85 e4 75
Aug 13 17:36:50 titanium kernel: [104268.464644] RIP  [<ffffffff811551e8>] kmem_cache_alloc+0x58/0x110
Aug 13 17:36:50 titanium kernel: [104268.465122]  RSP <ffff8801865e7d88>
Aug 13 17:36:50 titanium kernel: [104268.465597] ---[ end trace c246b6438e1a5d2b ]---
```A few more details:  I have write cache disabled on my data drives to try to prevent corruption.  My server is running an Intel i3-530 @ 2.93 GHz.  It has 3x2GB RAM, which tests fine with memtest86.  If you'd like any other information, or for me to run any tests, just let me know.

(Note:  I've heard people say that running green drives in RAID is bad because they sometimes drop out of the array even when they're fine.  This is NOT the issue I've been having - all my drives have been "up" (according to mdadm) the whole time.)

---

### Post by YesWeCan on 2011-08-13
Hi. I have no experience of this but I have some "groping in the dark" questions that may spark some ideas.
After the crash happens and you reboot, what error reports do you get? Does ext4 realise it is corrupted? Does mdadm pass an integrity check?
Presumably, and I am no expert, the journalling system will detect stuff that was written incorrectly eg: if a disk head went wild and smeared junk everywhere. But not if the fault occurred at a higher level. If madam went nuts, presumably the ext4 will be ok but RAID  will not pass an integrity check.
The stack traces show "general protection fault" instances. That doesn't sound like a disk write error; more like a memory fault, but not necessarily. How many passes of memtest did you run?

---

### Post by searing on 2011-08-13
I don't see any other errors, which is odd.  I see this other tidbit in syslog, but I don't think it's related:

```
Aug 13 17:38:11 titanium kernel: [    6.624449] EXT4-fs (dm-0): INFO: recovery required on readonly filesystem
Aug 13 17:38:11 titanium kernel: [    6.624452] EXT4-fs (dm-0): write access will be enabled during recovery
Aug 13 17:38:11 titanium kernel: [    8.880816] EXT4-fs (dm-0): recovery complete
Aug 13 17:38:11 titanium kernel: [    8.881250] EXT4-fs (dm-0): mounted filesystem with ordered data mode. Opts: (null)
```You're right though.  I'm a bit uneasy about the fact that the data managed to get corrupted without more stuff going off in the logs.

Does mdadm usually print something to syslog if it detects it needs to verify a raid array?  I don't see anything in there, and I don't remember it verifying, but I left it alone for a couple hours after the first crash (I have many other projects to work on), so maybe it kicked off and finished.

I let memtest run all night long, the last time this happened.  I forget how many passes it made, but as I left it for about 8-9 hours, it made several.

I suppose I could post my whole syslog over the past couple days, but I don't want to spam the forum with unrelated information.

It may not be a disk IO error, but it only happens when the server is put under heavy writes (typically about 100 MiB/s, over a gigabit connection).  It may also be some sort of race condition, because I usually have *something* reading from the server (my collection of desktop backgrounds, music, etc.), but I was under the impression that IO operations to a single device were serialized.

Edit:  I should add, I don't have any spare 1.5 TB drives to test out.  I don't mind getting them RMA'd, but I need something wrong with them - the fact that they don't even have bad sectors means I can't really get them replaced.

---

### Post by searing on 2011-08-13
I was just peeking around at the SMART data for all the drives, and I found this on one of the drives (sde):

```
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   099   051    Pre-fail  Always       -       6
  3 Spin_Up_Time            0x0007   071   071   011    Pre-fail  Always       -       9390
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       377
  5 Reallocated_Sector_Ct   0x0033   100   100   010    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   100   100   051    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0025   100   100   015    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0032   097   097   000    Old_age   Always       -       13148
 10 Spin_Retry_Count        0x0033   100   100   051    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x0012   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       211
 13 Read_Soft_Error_Rate    0x000e   100   099   000    Old_age   Always       -       6
183 Runtime_Bad_Block       0x0032   100   100   000    Old_age   Always       -       0
184 End-to-End_Error        0x0033   100   100   000    Pre-fail  Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       32
188 Command_Timeout         0x0032   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   075   064   000    Old_age   Always       -       25 (Lifetime Min/Max 18/25)
194 Temperature_Celsius     0x0022   075   062   000    Old_age   Always       -       25 (Lifetime Min/Max 18/27)
195 Hardware_ECC_Recovered  0x001a   100   100   000    Old_age   Always       -       1440853
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       1
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   100   100   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x000a   100   100   000    Old_age   Always       -       0
201 Soft_Read_Error_Rate    0x000a   253   253   000    Old_age   Always       -       0
```

And this, on sdf:
```
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   100   051    Pre-fail  Always       -       5
  3 Spin_Up_Time            0x0007   073   073   011    Pre-fail  Always       -       8980
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       96
  5 Reallocated_Sector_Ct   0x0033   100   100   010    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   100   100   051    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0025   100   100   015    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0032   099   099   000    Old_age   Always       -       6744
 10 Spin_Retry_Count        0x0033   100   100   051    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x0012   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       96
 13 Read_Soft_Error_Rate    0x000e   100   100   000    Old_age   Always       -       5
183 Runtime_Bad_Block       0x0032   100   100   000    Old_age   Always       -       0
184 End-to-End_Error        0x0033   100   100   000    Pre-fail  Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       22
188 Command_Timeout         0x0032   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   074   065   000    Old_age   Always       -       26 (Lifetime Min/Max 18/26)
194 Temperature_Celsius     0x0022   074   069   000    Old_age   Always       -       26 (Lifetime Min/Max 18/28)
195 Hardware_ECC_Recovered  0x001a   100   100   000    Old_age   Always       -       2003492
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   100   100   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x000a   100   100   000    Old_age   Always       -       0
201 Soft_Read_Error_Rate    0x000a   253   253   000    Old_age   Always       -       0
```

The part that worries me is the Raw_Read_Error_Rate.  There are no bad sectors (it seems), but none of the other six data drives have a nonzero value in that field (or in Read_Sort_Error_Rate).  The Raw_Read_Error_Rate is listed as Pre-fail, but the other field is Old_age - should I be looking for a replacement for these drives, or is this just a typical situation for drives under constant moderate/heavy use?

---

### Post by YesWeCan on 2011-08-13
So after the crash and you pull the plug, it reboots and looks pretty ok, except that you came across files that were corrupted?

mdadm probably doesn't do an integrity check unless it knows something is wrong. You can tell it to (use your raid device name):
[COLOR="Navy"]sudo -s
echo check > /sys/block/md0/md/sync_action
tail -f /var/log/syslog[/COLOR] (to monitor progress and results)

I was trying to find some details about "check" but finding documentation about some aspects of mdadm is like trying to find water on Mars. There is a scrap here: [http://fts.ifac.cnr.it/cgi-bin/dwww/usr/share/doc/mdadm/md.txt.gz](http://fts.ifac.cnr.it/cgi-bin/dwww/usr/share/doc/mdadm/md.txt.gz)

8-9 hours of memtest sounds pretty thorough.

---

### Post by coffee412 on 2011-08-13
Those samsung drives seem to have a high failure rate. Atleast from what I have been reading across the net. 

I would think that any problem with a drive dropping out of the array would show up when checking the array. They drop out and stay dropped out until they are either replaced or re-added into the array. 

I have an array that is 1 tb in size made up of Seagate 320 giggers. They are enterprise level and have been going strong for 6 years. But I never mix my drives in an array. This can sometimes cause problems. 

If your getting bad writes then you should see them in the logs. "cat /var/log/messages |grep sd " and see if bad writes are actually happening.

At the expense of trashing the array you could test the drives individually to make sure they all work correctly. Otherwise maybe try taking the western digital out of the mix and reconfigure it to a raid5 and try a test write. 

Whatever the problem is its going to take a few to figure it out. It might come down to a controller cache error too.

Thats my thoughts,

coffee

---

### Post by YesWeCan on 2011-08-13
> **searing said:**
> The part that worries me is the Raw_Read_Error_Rate.  There are no bad sectors (it seems), but none of the other six data drives have a nonzero value in that field (or in Read_Sort_Error_Rate).  The Raw_Read_Error_Rate is listed as Pre-fail, but the other field is Old_age - should I be looking for a replacement for these drives, or is this just a typical situation for drives under constant moderate/heavy use?
I sort of doubt these low "raw read errors", which are errors before any level of correction is applied, are important. Note the THRESH value is 10x higher. This number would be huge if disk errors were causing all your file corruptions and the SMART thing would have blown a gasket. I'm not persuaded, yet, that this is a disk read/write fault. Make a note of these logs and check them again after the next crash.

---

### Post by YesWeCan on 2011-08-13
[http://en.wikipedia.org/wiki/General_protection_fault](http://en.wikipedia.org/wiki/General_protection_fault)

If a CPU has 3 general protection faults it shuts down. This is what you are seeing - nothing works and you have to power-cycle. The stack trace shots you posted show 2 general protection faults.

AFAIK a general protection fault is a big deal. It is a fundamental failure of the system. I can't imagine a disk failure would cause this.

I am no expert, tho.

---

### Post by searing on 2011-08-13
So I just rebooted the server again, and I got a DeviceDisappeared event in syslog, followed by a NewArray event, as if one of the drives flickered out and back in to the array.  Furthermore, this seems to have triggered an ext4 recovery, which fixed the data I've checked so far (I will be checking more soon).  I guess that means it's "solved", but I'm still curious as to what happened, and devices going out of the array doesn't make me feel comfortable.

Edit:  I just forced an mdadm check per YesWeCan's instructions.

---

### Post by YesWeCan on 2011-08-13
It's good news that the ext4 recovery is working.
BTW is your Ubuntu OS also installed on the RAID?

---

### Post by searing on 2011-08-13
No.  The OS is running on a much smaller IDE drive in the same machine (80GB, but only 40GB is partitioned - I figure this could allow for an easy switch to a new OS if desired).  My config files get backed up, but that's it - the rest of it can easily be reinstalled.

---

### Post by YesWeCan on 2011-08-13
Have you any way of checking the error rate on the 80GB IDE drive. I'm still not happy about this general protection fault. That's like the OS was trashed.
It would be really key to know which drive dropped out in your log.
Since the failures occur during heavy writing that also means heavy psu drain, vibration perhaps. A bad cable could cause an intermittent drop out.

---

### Post by searing on 2011-08-13
Oh my.  This is the OS drive.

```
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   117   100   006    Pre-fail  Always       -       161655292
  3 Spin_Up_Time            0x0003   098   097   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       128
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   075   060   030    Pre-fail  Always       -       31834319
  9 Power_On_Hours          0x0032   093   093   000    Old_age   Always       -       6837
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       132
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   066   057   045    Old_age   Always       -       34 (Lifetime Min/Max 26/35)
194 Temperature_Celsius     0x0022   034   043   000    Old_age   Always       -       34 (0 18 0 0)
195 Hardware_ECC_Recovered  0x001a   108   073   000    Old_age   Always       -       222405415
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0000   100   253   000    Old_age   Offline      -       0
202 Data_Address_Mark_Errs  0x0032   100   253   000    Old_age   Always       -       0
```That looks scary.

Edit:  My PSU should be more than fine - it's a Fatal1ty 550W one (I don't have the model number on me).  It's quite a nice PSU, if it's the PSU that's at fault then I'll RMA it.

---

### Post by YesWeCan on 2011-08-13
Bingo. :)

---

