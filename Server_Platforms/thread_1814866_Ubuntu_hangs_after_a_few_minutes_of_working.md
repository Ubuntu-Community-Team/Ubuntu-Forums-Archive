---
title: "Ubuntu hangs after a few minutes of working"
date: 2011-07-30
forum: Server Platforms
---

### Post by procfs on 2011-07-30
Hi all ...

**Ubuntu Version** : 10.04 LTS & 11.04 (both tested)
**Hardware** : HP DL380 G7 (#cpu: 24 , ram:32G)

**Problem** : after installing the server edition of ubuntu (both 10.04 LTS & 11.04 ), the server hangs/stalls after a few minutes/hours of working  (e.g: while receiving data via scp)

here's a part of /var/log/syslog which might be useful :
```

Jul 30 15:25:20 venus kernel: [  992.076122] hpsa 0000:05:00.0: resetting device 2:0:0:1
Jul 30 15:26:52 venus kernel: [ 1084.169904] INFO: task jbd2/sda2-8:730 blocked for more than 120 seconds.
Jul 30 15:26:52 venus kernel: [ 1084.170015] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Jul 30 15:26:52 venus kernel: [ 1084.170128] jbd2/sda2-8     D 0000000000000001     0   730      2 0x00000000
Jul 30 15:26:52 venus kernel: [ 1084.170134]  ffff8803ff175d20 0000000000000046 ffff8803ff175fd8 ffff8803ff174000
Jul 30 15:26:52 venus kernel: [ 1084.170139]  0000000000013d00 ffff8803faf683b8 ffff8803ff175fd8 0000000000013d00
Jul 30 15:26:52 venus kernel: [ 1084.170143]  ffff8803ff8c8000 ffff8803faf68000 0000000000000002 ffff8803fca2f4a0
Jul 30 15:26:52 venus kernel: [ 1084.170147] Call Trace:
Jul 30 15:26:52 venus kernel: [ 1084.170158]  [<ffffffff81242540>] jbd2_journal_commit_transaction+0x1b0/0x1180
Jul 30 15:26:52 venus kernel: [ 1084.170166]  [<ffffffff8100a6e0>] ? __switch_to+0xc0/0x2f0
Jul 30 15:26:52 venus kernel: [ 1084.170172]  [<ffffffff815d779e>] ? _raw_spin_lock+0xe/0x20
Jul 30 15:26:52 venus kernel: [ 1084.170179]  [<ffffffff81074ceb>] ? lock_timer_base.clone.20+0x3b/0x70
Jul 30 15:26:52 venus kernel: [ 1084.170185]  [<ffffffff81087940>] ? autoremove_wake_function+0x0/0x40
Jul 30 15:26:52 venus kernel: [ 1084.170191]  [<ffffffff8124766b>] kjournald2+0xbb/0x220
Jul 30 15:26:52 venus kernel: [ 1084.170194]  [<ffffffff81087940>] ? autoremove_wake_function+0x0/0x40
Jul 30 15:26:52 venus kernel: [ 1084.170198]  [<ffffffff812475b0>] ? kjournald2+0x0/0x220
Jul 30 15:26:52 venus kernel: [ 1084.170201]  [<ffffffff810871f6>] kthread+0x96/0xa0
Jul 30 15:26:52 venus kernel: [ 1084.170207]  [<ffffffff8100cde4>] kernel_thread_helper+0x4/0x10
Jul 30 15:26:52 venus kernel: [ 1084.170210]  [<ffffffff81087160>] ? kthread+0x0/0xa0
Jul 30 15:26:52 venus kernel: [ 1084.170214]  [<ffffffff8100cde0>] ? kernel_thread_helper+0x0/0x10
Jul 30 15:26:52 venus kernel: [ 1084.170219] INFO: task flush-8:0:793 blocked for more than 120 seconds.
Jul 30 15:26:52 venus kernel: [ 1084.170315] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Jul 30 15:26:52 venus kernel: [ 1084.170427] flush-8:0       D 0000000000000001     0   793      2 0x00000000
Jul 30 15:26:52 venus kernel: [ 1084.170432]  ffff8803fca6f590 0000000000000046 ffff8803fca6ffd8 ffff8803fca6e000
Jul 30 15:26:52 venus kernel: [ 1084.170436]  0000000000013d00 ffff8803fe68df38 ffff8803fca6ffd8 0000000000013d00
Jul 30 15:26:52 venus kernel: [ 1084.170440]  ffff8803ff8c8000 ffff8803fe68db80 ffff8807fe3398c0 ffff88081fc13d00
Jul 30 15:26:52 venus kernel: [ 1084.170444] Call Trace:
Jul 30 15:26:52 venus kernel: [ 1084.170448]  [<ffffffff815d5720>] io_schedule+0x70/0xc0
Jul 30 15:26:52 venus kernel: [ 1084.170455]  [<ffffffff812c2819>] get_request_wait+0xc9/0x1a0
Jul 30 15:26:52 venus kernel: [ 1084.170459]  [<ffffffff81087940>] ? autoremove_wake_function+0x0/0x40
Jul 30 15:26:52 venus kernel: [ 1084.170464]  [<ffffffff812c2fd6>] __make_request+0x76/0x4c0
Jul 30 15:26:52 venus kernel: [ 1084.170468]  [<ffffffff812c04d2>] generic_make_request+0x2d2/0x5c0
Jul 30 15:26:52 venus kernel: [ 1084.170476]  [<ffffffff8110dac5>] ? mempool_alloc_slab+0x15/0x20
Jul 30 15:26:52 venus kernel: [ 1084.170480]  [<ffffffff8110de03>] ? mempool_alloc+0x53/0x130
Jul 30 15:26:52 venus kernel: [ 1084.170484]  [<ffffffff812c0847>] submit_bio+0x87/0x110
Jul 30 15:26:52 venus kernel: [ 1084.170490]  [<ffffffff8119777b>] ? bio_alloc_bioset+0x5b/0xf0
Jul 30 15:26:52 venus kernel: [ 1084.170494]  [<ffffffff81191a3b>] submit_bh+0xeb/0x120
Jul 30 15:26:52 venus kernel: [ 1084.170498]  [<ffffffff81193760>] __block_write_full_page+0x210/0x390
Jul 30 15:26:52 venus kernel: [ 1084.170501]  [<ffffffff81192b50>] ? end_buffer_async_write+0x0/0x170
Jul 30 15:26:52 venus kernel: [ 1084.170507]  [<ffffffff812063b0>] ? noalloc_get_block_write+0x0/0x30
Jul 30 15:26:52 venus kernel: [ 1084.170511]  [<ffffffff812063b0>] ? noalloc_get_block_write+0x0/0x30
Jul 30 15:26:52 venus kernel: [ 1084.170515]  [<ffffffff811945d3>] block_write_full_page_endio+0xe3/0x120
Jul 30 15:26:52 venus kernel: [ 1084.170518]  [<ffffffff81194625>] block_write_full_page+0x15/0x20
Jul 30 15:26:52 venus kernel: [ 1084.170523]  [<ffffffff812047ba>] mpage_da_submit_io+0x43a/0x4c0
Jul 30 15:26:52 venus kernel: [ 1084.170528]  [<ffffffff8120859e>] mpage_da_map_and_submit+0x1ae/0x440
Jul 30 15:26:52 venus kernel: [ 1084.170532]  [<ffffffff812090b6>] ext4_da_writepages+0x336/0x630
Jul 30 15:26:52 venus kernel: [ 1084.170537]  [<ffffffff811167a1>] do_writepages+0x21/0x40
Jul 30 15:26:52 venus kernel: [ 1084.170541]  [<ffffffff8118b7af>] writeback_single_inode+0x9f/0x240
Jul 30 15:26:52 venus kernel: [ 1084.170545]  [<ffffffff8118bb8b>] writeback_sb_inodes+0xcb/0x160
Jul 30 15:26:52 venus kernel: [ 1084.170549]  [<ffffffff8118bddb>] writeback_inodes_wb+0x10b/0x1c0
Jul 30 15:26:52 venus kernel: [ 1084.170553]  [<ffffffff8118c20e>] wb_writeback+0x37e/0x490
Jul 30 15:26:52 venus kernel: [ 1084.170557]  [<ffffffff815d794f>] ? _raw_spin_lock_irqsave+0x2f/0x40
Jul 30 15:26:52 venus kernel: [ 1084.170561]  [<ffffffff81074ceb>] ? lock_timer_base.clone.20+0x3b/0x70
Jul 30 15:26:52 venus kernel: [ 1084.170565]  [<ffffffff8118c541>] wb_do_writeback+0x221/0x230
Jul 30 15:26:52 venus kernel: [ 1084.170570]  [<ffffffff8118c5d2>] bdi_writeback_thread+0x82/0x260
Jul 30 15:26:52 venus kernel: [ 1084.170573]  [<ffffffff8118c550>] ? bdi_writeback_thread+0x0/0x260
Jul 30 15:26:52 venus kernel: [ 1084.170577]  [<ffffffff810871f6>] kthread+0x96/0xa0
Jul 30 15:26:52 venus kernel: [ 1084.170580]  [<ffffffff8100cde4>] kernel_thread_helper+0x4/0x10
Jul 30 15:26:52 venus kernel: [ 1084.170584]  [<ffffffff81087160>] ? kthread+0x0/0xa0
Jul 30 15:26:52 venus kernel: [ 1084.170588]  [<ffffffff8100cde0>] ? kernel_thread_helper+0x0/0x10
Jul 30 15:26:52 venus kernel: [ 1084.170594] INFO: task scp:1371 blocked for more than 120 seconds.
Jul 30 15:26:52 venus kernel: [ 1084.170683] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Jul 30 15:26:52 venus kernel: [ 1084.170794] scp             D 0000000000000002     0  1371      1 0x00000000
Jul 30 15:26:52 venus kernel: [ 1084.170799]  ffff8803fbd99908 0000000000000086 ffff8803fbd99fd8 ffff8803fbd98000
Jul 30 15:26:52 venus kernel: [ 1084.170803]  0000000000013d00 ffff8803faf6df38 ffff8803fbd99fd8 0000000000013d00
Jul 30 15:26:52 venus kernel: [ 1084.170807]  ffff8803ff8cdb80 ffff8803faf6db80 ffff8800df5f2ca8 ffff8800df233d00
Jul 30 15:26:52 venus kernel: [ 1084.170811] Call Trace:
Jul 30 15:26:52 venus kernel: [ 1084.170815]  [<ffffffff81191f00>] ? sync_buffer+0x0/0x50
Jul 30 15:26:52 venus kernel: [ 1084.170818]  [<ffffffff815d5720>] io_schedule+0x70/0xc0
Jul 30 15:26:52 venus kernel: [ 1084.170821]  [<ffffffff81191f40>] sync_buffer+0x40/0x50
Jul 30 15:26:52 venus kernel: [ 1084.170824]  [<ffffffff815d5e3f>] __wait_on_bit+0x5f/0x90
Jul 30 15:26:52 venus kernel: [ 1084.170828]  [<ffffffff8119777b>] ? bio_alloc_bioset+0x5b/0xf0
Jul 30 15:26:52 venus kernel: [ 1084.170831]  [<ffffffff81191f00>] ? sync_buffer+0x0/0x50
Jul 30 15:26:52 venus kernel: [ 1084.170834]  [<ffffffff815d5eec>] out_of_line_wait_on_bit+0x7c/0x90
Jul 30 15:26:52 venus kernel: [ 1084.170838]  [<ffffffff81087980>] ? wake_bit_function+0x0/0x50
Jul 30 15:26:52 venus kernel: [ 1084.170841]  [<ffffffff81191efe>] __wait_on_buffer+0x2e/0x30
Jul 30 15:26:52 venus kernel: [ 1084.170845]  [<ffffffff81194ea3>] __block_write_begin+0x393/0x570
Jul 30 15:26:52 venus kernel: [ 1084.170849]  [<ffffffff812067c0>] ? ext4_da_get_block_prep+0x0/0x140
Jul 30 15:26:52 venus kernel: [ 1084.170854]  [<ffffffff8110bf29>] ? grab_cache_page_write_begin+0x79/0xc0
Jul 30 15:26:52 venus kernel: [ 1084.170858]  [<ffffffff81207818>] ext4_da_write_begin+0x158/0x280
Jul 30 15:26:52 venus kernel: [ 1084.170862]  [<ffffffff81038c79>] ? default_spin_lock_flags+0x9/0x10
Jul 30 15:26:52 venus kernel: [ 1084.170866]  [<ffffffff8110acc2>] generic_perform_write+0xc2/0x1d0
Jul 30 15:26:52 venus kernel: [ 1084.170872]  [<ffffffff81237e1f>] ? ext4_xattr_security_get+0x2f/0x40
Jul 30 15:26:52 venus kernel: [ 1084.170876]  [<ffffffff8110ae2e>] generic_file_buffered_write+0x5e/0x90
Jul 30 15:26:52 venus kernel: [ 1084.170881]  [<ffffffff8110cd09>] __generic_file_aio_write+0x229/0x440
Jul 30 15:26:52 venus kernel: [ 1084.170885]  [<ffffffff8100c98e>] ? apic_timer_interrupt+0xe/0x20
Jul 30 15:26:52 venus kernel: [ 1084.170889]  [<ffffffff8110cf86>] generic_file_aio_write+0x66/0xd0
Jul 30 15:26:52 venus kernel: [ 1084.170893]  [<ffffffff811fdb19>] ext4_file_write+0x69/0x280
Jul 30 15:26:52 venus kernel: [ 1084.170899]  [<ffffffff81164b72>] do_sync_write+0xd2/0x110
Jul 30 15:26:52 venus kernel: [ 1084.170905]  [<ffffffff812adb78>] ? apparmor_file_permission+0x18/0x20
Jul 30 15:26:52 venus kernel: [ 1084.170912]  [<ffffffff8127901c>] ? security_file_permission+0x2c/0xb0
Jul 30 15:26:52 venus kernel: [ 1084.170916]  [<ffffffff81164fa1>] ? rw_verify_area+0x61/0xf0
Jul 30 15:26:52 venus kernel: [ 1084.170919]  [<ffffffff811652e6>] vfs_write+0xc6/0x180
Jul 30 15:26:52 venus kernel: [ 1084.170923]  [<ffffffff81165601>] sys_write+0x51/0x90
Jul 30 15:26:52 venus kernel: [ 1084.170929]  [<ffffffff81175a70>] ? sys_fcntl+0x70/0x90
Jul 30 15:26:52 venus kernel: [ 1084.170932]  [<ffffffff8100bfc2>] system_call_fastpath+0x16/0x1b
Jul 30 15:28:52 venus kernel: [ 1204.135738] INFO: task scsi_eh_2:297 blocked for more than 120 seconds.
Jul 30 15:28:52 venus kernel: [ 1204.135840] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Jul 30 15:28:52 venus kernel: [ 1204.135953] scsi_eh_2       D 0000000000000001     0   297      2 0x00000000
Jul 30 15:28:52 venus kernel: [ 1204.135958]  ffff8803fc791bb0 0000000000000046 ffff8803fc791fd8 ffff8803fc790000
Jul 30 15:28:52 venus kernel: [ 1204.135963]  0000000000013d00 ffff8803fbdc3178 ffff8803fc791fd8 0000000000013d00
Jul 30 15:28:52 venus kernel: [ 1204.135967]  ffff8803fc8e5b80 ffff8803fbdc2dc0 0000000000000034 7fffffffffffffff
Jul 30 15:28:52 venus kernel: [ 1204.135972] Call Trace:
Jul 30 15:28:52 venus kernel: [ 1204.135982]  [<ffffffff815d5bbd>] schedule_timeout+0x26d/0x2e0
Jul 30 15:28:52 venus kernel: [ 1204.135987]  [<ffffffff815d4c69>] wait_for_common+0xd9/0x180
Jul 30 15:28:52 venus kernel: [ 1204.135996]  [<ffffffff8105f6f0>] ? default_wake_function+0x0/0x20
Jul 30 15:28:52 venus kernel: [ 1204.136000]  [<ffffffff815d4ded>] wait_for_completion+0x1d/0x20
Jul 30 15:28:52 venus kernel: [ 1204.136006]  [<ffffffffa000361a>] hpsa_eh_device_reset_handler+0xfa/0x1c0 [hpsa]
Jul 30 15:28:52 venus kernel: [ 1204.136013]  [<ffffffff813e2bce>] scsi_try_bus_device_reset+0x2e/0x60
Jul 30 15:28:52 venus kernel: [ 1204.136017]  [<ffffffff813e434f>] scsi_eh_bus_device_reset+0xbf/0x1d0
Jul 30 15:28:52 venus kernel: [ 1204.136021]  [<ffffffff813e4dee>] scsi_eh_ready_devs+0x5e/0x140
Jul 30 15:28:52 venus kernel: [ 1204.136025]  [<ffffffff813e584d>] scsi_unjam_host+0xed/0x1f0
Jul 30 15:28:52 venus kernel: [ 1204.136029]  [<ffffffff813e5ad0>] scsi_error_handler+0x180/0x1d0
Jul 30 15:28:52 venus kernel: [ 1204.136032]  [<ffffffff813e5950>] ? scsi_error_handler+0x0/0x1d0
Jul 30 15:28:52 venus kernel: [ 1204.136038]  [<ffffffff810871f6>] kthread+0x96/0xa0
Jul 30 15:28:52 venus kernel: [ 1204.136044]  [<ffffffff8100cde4>] kernel_thread_helper+0x4/0x10
Jul 30 15:28:52 venus kernel: [ 1204.136047]  [<ffffffff81087160>] ? kthread+0x0/0xa0
Jul 30 15:28:52 venus kernel: [ 1204.136051]  [<ffffffff8100cde0>] ? kernel_thread_helper+0x0/0x10
Jul 30 15:28:52 venus kernel: [ 1204.136056] INFO: task jbd2/sda2-8:730 blocked for more than 120 seconds.
Jul 30 15:28:52 venus kernel: [ 1204.136154] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Jul 30 15:28:52 venus kernel: [ 1204.136266] jbd2/sda2-8     D 0000000000000001     0   730      2 0x00000000
Jul 30 15:28:52 venus kernel: [ 1204.136270]  ffff8803ff175d20 0000000000000046 ffff8803ff175fd8 ffff8803ff174000
Jul 30 15:28:52 venus kernel: [ 1204.136275]  0000000000013d00 ffff8803faf683b8 ffff8803ff175fd8 0000000000013d00
Jul 30 15:28:52 venus kernel: [ 1204.136279]  ffff8803ff8c8000 ffff8803faf68000 0000000000000002 ffff8803fca2f4a0
Jul 30 15:28:52 venus kernel: [ 1204.136283] Call Trace:
Jul 30 15:28:52 venus kernel: [ 1204.136289]  [<ffffffff81242540>] jbd2_journal_commit_transaction+0x1b0/0x1180
Jul 30 15:28:52 venus kernel: [ 1204.136296]  [<ffffffff8100a6e0>] ? __switch_to+0xc0/0x2f0
Jul 30 15:28:52 venus kernel: [ 1204.136301]  [<ffffffff815d779e>] ? _raw_spin_lock+0xe/0x20
Jul 30 15:28:52 venus kernel: [ 1204.136307]  [<ffffffff81074ceb>] ? lock_timer_base.clone.20+0x3b/0x70
Jul 30 15:28:52 venus kernel: [ 1204.136311]  [<ffffffff81087940>] ? autoremove_wake_function+0x0/0x40
Jul 30 15:28:52 venus kernel: [ 1204.136316]  [<ffffffff8124766b>] kjournald2+0xbb/0x220
Jul 30 15:28:52 venus kernel: [ 1204.136320]  [<ffffffff81087940>] ? autoremove_wake_function+0x0/0x40
Jul 30 15:28:52 venus kernel: [ 1204.136323]  [<ffffffff812475b0>] ? kjournald2+0x0/0x220
Jul 30 15:28:52 venus kernel: [ 1204.136327]  [<ffffffff810871f6>] kthread+0x96/0xa0
Jul 30 15:28:52 venus kernel: [ 1204.136330]  [<ffffffff8100cde4>] kernel_thread_helper+0x4/0x10
Jul 30 15:28:52 venus kernel: [ 1204.136334]  [<ffffffff81087160>] ? kthread+0x0/0xa0
Jul 30 15:28:52 venus kernel: [ 1204.136337]  [<ffffffff8100cde0>] ? kernel_thread_helper+0x0/0x10
Jul 30 15:28:52 venus kernel: [ 1204.136340] INFO: task jbd2/sda3-8:739 blocked for more than 120 seconds.
Jul 30 15:28:52 venus kernel: [ 1204.136438] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Jul 30 15:28:52 venus kernel: [ 1204.136550] jbd2/sda3-8     D 0000000000000001     0   739      2 0x00000000
Jul 30 15:28:52 venus kernel: [ 1204.136554]  ffff8803feadbc20 0000000000000046 ffff8803feadbfd8 ffff8803feada000
Jul 30 15:28:52 venus kernel: [ 1204.136559]  0000000000013d00 ffff8803fae79a98 ffff8803feadbfd8 0000000000013d00
Jul 30 15:28:52 venus kernel: [ 1204.136563]  ffff8803ff8c8000 ffff8803fae796e0 ffff88081ffee1b8 ffff88081fc13d00
Jul 30 15:28:52 venus kernel: [ 1204.136567] Call Trace:
Jul 30 15:28:52 venus kernel: [ 1204.136571]  [<ffffffff81191f00>] ? sync_buffer+0x0/0x50
Jul 30 15:28:52 venus kernel: [ 1204.136575]  [<ffffffff815d5720>] io_schedule+0x70/0xc0
Jul 30 15:28:52 venus kernel: [ 1204.136578]  [<ffffffff81191f40>] sync_buffer+0x40/0x50
Jul 30 15:28:52 venus kernel: [ 1204.136581]  [<ffffffff815d5e3f>] __wait_on_bit+0x5f/0x90
Jul 30 15:28:52 venus kernel: [ 1204.136584]  [<ffffffff81191f00>] ? sync_buffer+0x0/0x50
Jul 30 15:28:52 venus kernel: [ 1204.136587]  [<ffffffff815d5eec>] out_of_line_wait_on_bit+0x7c/0x90
Jul 30 15:28:52 venus kernel: [ 1204.136591]  [<ffffffff81087980>] ? wake_bit_function+0x0/0x50
Jul 30 15:28:52 venus kernel: [ 1204.136594]  [<ffffffff81191efe>] __wait_on_buffer+0x2e/0x30
Jul 30 15:28:52 venus kernel: [ 1204.136598]  [<ffffffff81243439>] jbd2_journal_commit_transaction+0x10a9/0x1180
Jul 30 15:28:52 venus kernel: [ 1204.136603]  [<ffffffff81075e95>] ? try_to_del_timer_sync+0x85/0xe0
Jul 30 15:28:52 venus kernel: [ 1204.136607]  [<ffffffff8124766b>] kjournald2+0xbb/0x220
Jul 30 15:28:52 venus kernel: [ 1204.136611]  [<ffffffff81087940>] ? autoremove_wake_function+0x0/0x40
Jul 30 15:28:52 venus kernel: [ 1204.136614]  [<ffffffff812475b0>] ? kjournald2+0x0/0x220
Jul 30 15:28:52 venus kernel: [ 1204.136617]  [<ffffffff810871f6>] kthread+0x96/0xa0
Jul 30 15:28:52 venus kernel: [ 1204.136621]  [<ffffffff8100cde4>] kernel_thread_helper+0x4/0x10
Jul 30 15:28:52 venus kernel: [ 1204.136625]  [<ffffffff81087160>] ? kthread+0x0/0xa0
Jul 30 15:28:52 venus kernel: [ 1204.136628]  [<ffffffff8100cde0>] ? kernel_thread_helper+0x0/0x10
Jul 30 15:28:52 venus kernel: [ 1204.136632] INFO: task flush-8:0:793 blocked for more than 120 seconds.
Jul 30 15:28:52 venus kernel: [ 1204.136728] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Jul 30 15:28:52 venus kernel: [ 1204.136840] flush-8:0       D 0000000000000001     0   793      2 0x00000000
Jul 30 15:28:52 venus kernel: [ 1204.136843]  ffff8803fca6f590 0000000000000046 ffff8803fca6ffd8 ffff8803fca6e000
Jul 30 15:28:52 venus kernel: [ 1204.136848]  0000000000013d00 ffff8803fe68df38 ffff8803fca6ffd8 0000000000013d00
Jul 30 15:28:52 venus kernel: [ 1204.136852]  ffff8803ff8c8000 ffff8803fe68db80 ffff8807fe3398c0 ffff88081fc13d00
Jul 30 15:28:52 venus kernel: [ 1204.136856] Call Trace:
Jul 30 15:28:52 venus kernel: [ 1204.136860]  [<ffffffff815d5720>] io_schedule+0x70/0xc0
Jul 30 15:28:52 venus kernel: [ 1204.136867]  [<ffffffff812c2819>] get_request_wait+0xc9/0x1a0
Jul 30 15:28:52 venus kernel: [ 1204.136871]  [<ffffffff81087940>] ? autoremove_wake_function+0x0/0x40
Jul 30 15:28:52 venus kernel: [ 1204.136875]  [<ffffffff812c2fd6>] __make_request+0x76/0x4c0
Jul 30 15:28:52 venus kernel: [ 1204.136879]  [<ffffffff812c04d2>] generic_make_request+0x2d2/0x5c0
Jul 30 15:28:52 venus kernel: [ 1204.136888]  [<ffffffff8110dac5>] ? mempool_alloc_slab+0x15/0x20
Jul 30 15:28:52 venus kernel: [ 1204.136891]  [<ffffffff8110de03>] ? mempool_alloc+0x53/0x130
Jul 30 15:28:52 venus kernel: [ 1204.136895]  [<ffffffff812c0847>] submit_bio+0x87/0x110
Jul 30 15:28:52 venus kernel: [ 1204.136900]  [<ffffffff8119777b>] ? bio_alloc_bioset+0x5b/0xf0
Jul 30 15:28:52 venus kernel: [ 1204.136904]  [<ffffffff81191a3b>] submit_bh+0xeb/0x120
Jul 30 15:28:52 venus kernel: [ 1204.136908]  [<ffffffff81193760>] __block_write_full_page+0x210/0x390
Jul 30 15:28:52 venus kernel: [ 1204.136911]  [<ffffffff81192b50>] ? end_buffer_async_write+0x0/0x170
Jul 30 15:28:52 venus kernel: [ 1204.136917]  [<ffffffff812063b0>] ? noalloc_get_block_write+0x0/0x30
Jul 30 15:28:52 venus kernel: [ 1204.136921]  [<ffffffff812063b0>] ? noalloc_get_block_write+0x0/0x30
Jul 30 15:28:52 venus kernel: [ 1204.136924]  [<ffffffff811945d3>] block_write_full_page_endio+0xe3/0x120
Jul 30 15:28:52 venus kernel: [ 1204.136928]  [<ffffffff81194625>] block_write_full_page+0x15/0x20
Jul 30 15:28:52 venus kernel: [ 1204.136933]  [<ffffffff812047ba>] mpage_da_submit_io+0x43a/0x4c0
Jul 30 15:28:52 venus kernel: [ 1204.136937]  [<ffffffff8120859e>] mpage_da_map_and_submit+0x1ae/0x440
Jul 30 15:28:52 venus kernel: [ 1204.136942]  [<ffffffff812090b6>] ext4_da_writepages+0x336/0x630
Jul 30 15:28:52 venus kernel: [ 1204.136946]  [<ffffffff811167a1>] do_writepages+0x21/0x40
Jul 30 15:28:52 venus kernel: [ 1204.136951]  [<ffffffff8118b7af>] writeback_single_inode+0x9f/0x240
Jul 30 15:28:52 venus kernel: [ 1204.136955]  [<ffffffff8118bb8b>] writeback_sb_inodes+0xcb/0x160
Jul 30 15:28:52 venus kernel: [ 1204.136959]  [<ffffffff8118bddb>] writeback_inodes_wb+0x10b/0x1c0
Jul 30 15:28:52 venus kernel: [ 1204.136963]  [<ffffffff8118c20e>] wb_writeback+0x37e/0x490
Jul 30 15:28:52 venus kernel: [ 1204.136967]  [<ffffffff815d794f>] ? _raw_spin_lock_irqsave+0x2f/0x40
Jul 30 15:28:52 venus kernel: [ 1204.136971]  [<ffffffff81074ceb>] ? lock_timer_base.clone.20+0x3b/0x70
Jul 30 15:28:52 venus kernel: [ 1204.136976]  [<ffffffff8118c541>] wb_do_writeback+0x221/0x230
Jul 30 15:28:52 venus kernel: [ 1204.136980]  [<ffffffff8118c5d2>] bdi_writeback_thread+0x82/0x260
Jul 30 15:28:52 venus kernel: [ 1204.136984]  [<ffffffff8118c550>] ? bdi_writeback_thread+0x0/0x260
Jul 30 15:28:52 venus kernel: [ 1204.136987]  [<ffffffff810871f6>] kthread+0x96/0xa0
Jul 30 15:28:52 venus kernel: [ 1204.136991]  [<ffffffff8100cde4>] kernel_thread_helper+0x4/0x10
Jul 30 15:28:52 venus kernel: [ 1204.136994]  [<ffffffff81087160>] ? kthread+0x0/0xa0
Jul 30 15:28:52 venus kernel: [ 1204.136998]  [<ffffffff8100cde0>] ? kernel_thread_helper+0x0/0x10
Jul 30 15:28:52 venus kernel: [ 1204.137003] INFO: task scp:1371 blocked for more than 120 seconds.
Jul 30 15:28:52 venus kernel: [ 1204.137092] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Jul 30 15:28:52 venus kernel: [ 1204.137204] scp             D 0000000000000002     0  1371      1 0x00000000
Jul 30 15:28:52 venus kernel: [ 1204.137208]  ffff8803fbd99908 0000000000000086 ffff8803fbd99fd8 ffff8803fbd98000
Jul 30 15:28:52 venus kernel: [ 1204.137212]  0000000000013d00 ffff8803faf6df38 ffff8803fbd99fd8 0000000000013d00
Jul 30 15:28:52 venus kernel: [ 1204.137217]  ffff8803ff8cdb80 ffff8803faf6db80 ffff8800df5f2ca8 ffff8800df233d00
Jul 30 15:28:52 venus kernel: [ 1204.137221] Call Trace:
Jul 30 15:28:52 venus kernel: [ 1204.137224]  [<ffffffff81191f00>] ? sync_buffer+0x0/0x50
Jul 30 15:28:52 venus kernel: [ 1204.137227]  [<ffffffff815d5720>] io_schedule+0x70/0xc0
Jul 30 15:28:52 venus kernel: [ 1204.137230]  [<ffffffff81191f40>] sync_buffer+0x40/0x50
Jul 30 15:28:52 venus kernel: [ 1204.137233]  [<ffffffff815d5e3f>] __wait_on_bit+0x5f/0x90
Jul 30 15:28:52 venus kernel: [ 1204.137237]  [<ffffffff8119777b>] ? bio_alloc_bioset+0x5b/0xf0
Jul 30 15:28:52 venus kernel: [ 1204.137240]  [<ffffffff81191f00>] ? sync_buffer+0x0/0x50
Jul 30 15:28:52 venus kernel: [ 1204.137243]  [<ffffffff815d5eec>] out_of_line_wait_on_bit+0x7c/0x90
Jul 30 15:28:52 venus kernel: [ 1204.137247]  [<ffffffff81087980>] ? wake_bit_function+0x0/0x50
Jul 30 15:28:52 venus kernel: [ 1204.137250]  [<ffffffff81191efe>] __wait_on_buffer+0x2e/0x30
Jul 30 15:28:52 venus kernel: [ 1204.137254]  [<ffffffff81194ea3>] __block_write_begin+0x393/0x570
Jul 30 15:28:52 venus kernel: [ 1204.137258]  [<ffffffff812067c0>] ? ext4_da_get_block_prep+0x0/0x140
Jul 30 15:28:52 venus kernel: [ 1204.137263]  [<ffffffff8110bf29>] ? grab_cache_page_write_begin+0x79/0xc0
Jul 30 15:28:52 venus kernel: [ 1204.137266]  [<ffffffff81207818>] ext4_da_write_begin+0x158/0x280
Jul 30 15:28:52 venus kernel: [ 1204.137271]  [<ffffffff81038c79>] ? default_spin_lock_flags+0x9/0x10
Jul 30 15:28:52 venus kernel: [ 1204.137275]  [<ffffffff8110acc2>] generic_perform_write+0xc2/0x1d0
Jul 30 15:28:52 venus kernel: [ 1204.137281]  [<ffffffff81237e1f>] ? ext4_xattr_security_get+0x2f/0x40
Jul 30 15:28:52 venus kernel: [ 1204.137285]  [<ffffffff8110ae2e>] generic_file_buffered_write+0x5e/0x90
Jul 30 15:28:52 venus kernel: [ 1204.137290]  [<ffffffff8110cd09>] __generic_file_aio_write+0x229/0x440
Jul 30 15:28:52 venus kernel: [ 1204.137294]  [<ffffffff8100c98e>] ? apic_timer_interrupt+0xe/0x20
Jul 30 15:28:52 venus kernel: [ 1204.137298]  [<ffffffff8110cf86>] generic_file_aio_write+0x66/0xd0
Jul 30 15:28:52 venus kernel: [ 1204.137302]  [<ffffffff811fdb19>] ext4_file_write+0x69/0x280
Jul 30 15:28:52 venus kernel: [ 1204.137308]  [<ffffffff81164b72>] do_sync_write+0xd2/0x110
Jul 30 15:28:52 venus kernel: [ 1204.137315]  [<ffffffff812adb78>] ? apparmor_file_permission+0x18/0x20
Jul 30 15:28:52 venus kernel: [ 1204.137321]  [<ffffffff8127901c>] ? security_file_permission+0x2c/0xb0
Jul 30 15:28:52 venus kernel: [ 1204.137325]  [<ffffffff81164fa1>] ? rw_verify_area+0x61/0xf0
Jul 30 15:28:52 venus kernel: [ 1204.137329]  [<ffffffff811652e6>] vfs_write+0xc6/0x180
Jul 30 15:28:52 venus kernel: [ 1204.137332]  [<ffffffff81165601>] sys_write+0x51/0x90
Jul 30 15:28:52 venus kernel: [ 1204.137338]  [<ffffffff81175a70>] ? sys_fcntl+0x70/0x90
Jul 30 15:28:52 venus kernel: [ 1204.137341]  [<ffffffff8100bfc2>] system_call_fastpath+0x16/0x1b
Jul 30 15:28:52 venus kernel: [ 1204.137346] INFO: task scp:1660 blocked for more than 120 seconds.
Jul 30 15:28:52 venus kernel: [ 1204.137435] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Jul 30 15:28:52 venus kernel: [ 1204.137547] scp             D 0000000000000002     0  1660      1 0x00000000
Jul 30 15:28:52 venus kernel: [ 1204.137551]  ffff8803ff0f9a58 0000000000000082 ffff8803ff0f9fd8 ffff8803ff0f8000
Jul 30 15:28:52 venus kernel: [ 1204.137555]  0000000000013d00 ffff8803fce61a98 ffff8803ff0f9fd8 0000000000013d00
Jul 30 15:28:52 venus kernel: [ 1204.137559]  ffff8803ff8cdb80 ffff8803fce616e0 ffff8803ff0f9a38 ffff8803fc95b800
Jul 30 15:28:52 venus kernel: [ 1204.137563] Call Trace:
Jul 30 15:28:52 venus kernel: [ 1204.137569]  [<ffffffff8123fde2>] start_this_handle.clone.7+0x362/0x4a0
Jul 30 15:28:52 venus kernel: [ 1204.137574]  [<ffffffff81087940>] ? autoremove_wake_function+0x0/0x40
Jul 30 15:28:52 venus kernel: [ 1204.137578]  [<ffffffff8123ffea>] jbd2__journal_start+0xca/0x110
Jul 30 15:28:52 venus kernel: [ 1204.137582]  [<ffffffff81240043>] jbd2_journal_start+0x13/0x20
Jul 30 15:28:52 venus kernel: [ 1204.137588]  [<ffffffff8121d453>] ext4_journal_start_sb+0xb3/0x140
Jul 30 15:28:52 venus kernel: [ 1204.137592]  [<ffffffff81209727>] ext4_dirty_inode+0x27/0x60
Jul 30 15:28:52 venus kernel: [ 1204.137596]  [<ffffffff8118b4ef>] __mark_inode_dirty+0x3f/0x260
Jul 30 15:28:52 venus kernel: [ 1204.137601]  [<ffffffff8117f315>] file_update_time+0xf5/0x170
Jul 30 15:28:52 venus kernel: [ 1204.137606]  [<ffffffff8110ccd8>] __generic_file_aio_write+0x1f8/0x440
Jul 30 15:28:52 venus kernel: [ 1204.137610]  [<ffffffff8115f36d>] ? mem_cgroup_charge_common+0x6d/0x90
Jul 30 15:28:52 venus kernel: [ 1204.137614]  [<ffffffff8110cf86>] generic_file_aio_write+0x66/0xd0
Jul 30 15:28:52 venus kernel: [ 1204.137618]  [<ffffffff811fdb19>] ext4_file_write+0x69/0x280
Jul 30 15:28:52 venus kernel: [ 1204.137622]  [<ffffffff81164b72>] do_sync_write+0xd2/0x110
Jul 30 15:28:52 venus kernel: [ 1204.137626]  [<ffffffff812adb78>] ? apparmor_file_permission+0x18/0x20
Jul 30 15:28:52 venus kernel: [ 1204.137630]  [<ffffffff8127901c>] ? security_file_permission+0x2c/0xb0
Jul 30 15:28:52 venus kernel: [ 1204.137634]  [<ffffffff81164fa1>] ? rw_verify_area+0x61/0xf0
Jul 30 15:28:52 venus kernel: [ 1204.137638]  [<ffffffff811652e6>] vfs_write+0xc6/0x180
Jul 30 15:28:52 venus kernel: [ 1204.137641]  [<ffffffff81165601>] sys_write+0x51/0x90
Jul 30 15:28:52 venus kernel: [ 1204.137645]  [<ffffffff811788e6>] ? sys_poll+0x76/0x110
Jul 30 15:28:52 venus kernel: [ 1204.137649]  [<ffffffff8100bfc2>] system_call_fastpath+0x16/0x1b
Jul 30 15:28:52 venus kernel: [ 1204.137652] INFO: task scp:1688 blocked for more than 120 seconds.
Jul 30 15:28:52 venus kernel: [ 1204.137740] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Jul 30 15:28:52 venus kernel: [ 1204.137852] scp             D 0000000000000002     0  1688      1 0x00000000
Jul 30 15:28:52 venus kernel: [ 1204.137856]  ffff8803ff153c88 0000000000000082 ffff8803ff153fd8 ffff8803ff152000
Jul 30 15:28:52 venus kernel: [ 1204.137860]  0000000000013d00 ffff8803faf783b8 ffff8803ff153fd8 0000000000013d00
Jul 30 15:28:52 venus kernel: [ 1204.137864]  ffff8803ff8cdb80 ffff8803faf78000 0000000000000000 ffff8803fd81ccf8
Jul 30 15:28:52 venus kernel: [ 1204.137869] Call Trace:
Jul 30 15:28:52 venus kernel: [ 1204.137872]  [<ffffffff815d6537>] __mutex_lock_slowpath+0xf7/0x180
Jul 30 15:28:52 venus kernel: [ 1204.137876]  [<ffffffff8115f36d>] ? mem_cgroup_charge_common+0x6d/0x90
Jul 30 15:28:52 venus kernel: [ 1204.137879]  [<ffffffff815d5f23>] mutex_lock+0x23/0x50
Jul 30 15:28:52 venus kernel: [ 1204.137884]  [<ffffffff8110cf73>] generic_file_aio_write+0x53/0xd0
Jul 30 15:28:52 venus kernel: [ 1204.137887]  [<ffffffff811fdb19>] ext4_file_write+0x69/0x280
Jul 30 15:28:52 venus kernel: [ 1204.137891]  [<ffffffff81164b72>] do_sync_write+0xd2/0x110
Jul 30 15:28:52 venus kernel: [ 1204.137896]  [<ffffffff812adb78>] ? apparmor_file_permission+0x18/0x20
Jul 30 15:28:52 venus kernel: [ 1204.137900]  [<ffffffff8127901c>] ? security_file_permission+0x2c/0xb0
Jul 30 15:28:52 venus kernel: [ 1204.137904]  [<ffffffff81164fa1>] ? rw_verify_area+0x61/0xf0
Jul 30 15:28:52 venus kernel: [ 1204.137907]  [<ffffffff811652e6>] vfs_write+0xc6/0x180
Jul 30 15:28:52 venus kernel: [ 1204.137911]  [<ffffffff81165601>] sys_write+0x51/0x90
Jul 30 15:28:52 venus kernel: [ 1204.137914]  [<ffffffff811788e6>] ? sys_poll+0x76/0x110
Jul 30 15:28:52 venus kernel: [ 1204.137918]  [<ffffffff8100bfc2>] system_call_fastpath+0x16/0x1b

```
thanks in advance :)

P.S : the log above has been generated in 11.04 64bit

---

### Post by procfs on 2011-07-31
any opinions ?!?

---

### Post by konsole on 2011-07-31
From memory HP provide a Smartstart bootable diagnostics cd that will detect faulty disks, ram etc.

Boot this and run the tests.

---

### Post by fleg on 2012-03-27
i have exactly the same problem with a BL465 g7 under ubuntu 11.10
did you find a workaround or a fix ?

---

### Post by hawkmage on 2012-03-27
My first guess is that there is an issue with the NIC driver.  Is there a linux driver from HP for your system?

---

### Post by fleg on 2012-03-29
I don't see any problems with the NIC. What do you mean ?

---

