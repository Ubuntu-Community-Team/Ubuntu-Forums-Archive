---
title: "Call Trace and Crash"
date: 2012-02-11
forum: Server Platforms
---

### Post by xlr8ed on 2012-02-11
Hello All,

I am running Ubuntu Server 11.04 x64 headless as my file server. Every few days, the server become mostly unresponsive and when I check the output of dmesg, always have something like what I have below.

I am running mdadm, and while I have access and can view navigate the / or home directories, nothing is accessible on the mdadm shares.  I was thinking of rebuilding the system, but was really hoping to get some insight into the problem, so I don't waste me time.  I'm decent at linux, but some of the bigger troubleshooting issue I have trouble with.

Thanks in advance.


[252421.329924] sas: command 0xffff8803dcefdb00, task 0xffff8804043eee00, timed out: BLK_EH_NOT_HANDLED
[252595.756710] INFO: task jbd2/md0-8:782 blocked for more than 120 seconds.
[252595.756752] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[252595.756787] jbd2/md0-8      D ffffffff81805120     0   782      2 0x00000000
[252595.756789]  ffff880402d51ad0 0000000000000046 ffff880402d51a80 ffff880402d51a80
[252595.756791]  ffff880402d51fd8 ffff880402d51fd8 ffff880402d51fd8 0000000000012a40
[252595.756793]  ffff88040695c560 ffff880406b49720 ffff88041f7ae6c8 ffff88041f5932c0
[252595.756795] Call Trace:
[252595.756800]  [<ffffffff81108fe0>] ? __lock_page+0x70/0x70
[252595.756802]  [<ffffffff815fc9ef>] io_schedule+0x8f/0xd0
[252595.756804]  [<ffffffff81108fee>] sleep_on_page+0xe/0x20
[252595.756805]  [<ffffffff815fd29f>] __wait_on_bit+0x5f/0x90
[252595.756807]  [<ffffffff81109158>] wait_on_page_bit+0x78/0x80
[252595.756810]  [<ffffffff81081740>] ? autoremove_wake_function+0x40/0x40
[252595.756811]  [<ffffffff8110926c>] filemap_fdatawait_range+0x10c/0x1a0
[252595.756813]  [<ffffffff8110932b>] filemap_fdatawait+0x2b/0x30
[252595.756815]  [<ffffffff81245c73>] journal_finish_inode_data_buffers+0x73/0x170
[252595.756817]  [<ffffffff81246575>] jbd2_journal_commit_transaction+0x675/0x1250
[252595.756819]  [<ffffffff8104ca0e>] ? perf_event_task_sched_out+0x2e/0xa0
[252595.756821]  [<ffffffff81081700>] ? add_wait_queue+0x60/0x60
[252595.756823]  [<ffffffff8124af7b>] kjournald2+0xbb/0x220
[252595.756824]  [<ffffffff81081700>] ? add_wait_queue+0x60/0x60
[252595.756826]  [<ffffffff8124aec0>] ? commit_timeout+0x10/0x10
[252595.756827]  [<ffffffff81080c5c>] kthread+0x8c/0xa0
[252595.756830]  [<ffffffff81607d24>] kernel_thread_helper+0x4/0x10
[252595.756831]  [<ffffffff81080bd0>] ? flush_kthread_worker+0xa0/0xa0
[252595.756833]  [<ffffffff81607d20>] ? gs_change+0x13/0x13
[252595.756843] INFO: task sabnzbdplus:2008 blocked for more than 120 seconds.
[252595.756859] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[252595.756878] sabnzbdplus     D ffffffff81805120     0  2008      1 0x00000000
[252595.756880]  ffff8803edb89a98 0000000000000086 ffff8803edb89a38 ffffffff810329a9
[252595.756882]  ffff8803edb89fd8 ffff8803edb89fd8 ffff8803edb89fd8 0000000000012a40
[252595.756883]  ffff880406940000 ffff8803edb24560 ffff8803edb89a88 ffff8803edb89af8
[252595.756885] Call Trace:
[252595.756887]  [<ffffffff810329a9>] ? default_spin_lock_flags+0x9/0x10
[252595.756888]  [<ffffffff8124508d>] do_get_write_access+0x27d/0x500
[252595.756891]  [<ffffffff81195fa9>] ? bh_lru_install+0x129/0x160
[252595.756893]  [<ffffffff81081740>] ? autoremove_wake_function+0x40/0x40
[252595.756894]  [<ffffffff81196067>] ? __find_get_block+0x87/0xe0
[252595.756896]  [<ffffffff81245450>] jbd2_journal_get_write_access+0x30/0x50
[252595.756899]  [<ffffffff8122b55e>] __ext4_journal_get_write_access+0x3e/0x80
[252595.756902]  [<ffffffff81200e4e>] ext4_new_inode+0x27e/0xbc0
[252595.756903]  [<ffffffff81220849>] ? ext4_journal_start_sb+0x69/0x170
[252595.756905]  [<ffffffff8120f537>] ext4_create+0xb7/0x140
[252595.756908]  [<ffffffff811724d3>] ? generic_permission+0x23/0xd0
[252595.756909]  [<ffffffff811738d4>] vfs_create+0xb4/0x120
[252595.756911]  [<ffffffff81174b81>] do_last+0x621/0x700
[252595.756912]  [<ffffffff8117688a>] path_openat+0xca/0x3f0
[252595.756914]  [<ffffffff81172255>] ? putname+0x35/0x50
[252595.756915]  [<ffffffff81176bf2>] do_filp_open+0x42/0xa0
[252595.756917]  [<ffffffff812f3231>] ? strncpy_from_user+0x31/0x40
[252595.756919]  [<ffffffff815fe82e>] ? _raw_spin_lock+0xe/0x20
[252595.756921]  [<ffffffff81183dc7>] ? alloc_fd+0xf7/0x150
[252595.756923]  [<ffffffff81166aad>] do_sys_open+0xed/0x220
[252595.756925]  [<ffffffff81166c00>] sys_open+0x20/0x30
[252595.756926]  [<ffffffff81606c02>] system_call_fastpath+0x16/0x1b
[252595.756932] INFO: task flush-9:0:1130 blocked for more than 120 seconds.
[252595.756947] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[252595.756966] flush-9:0       D ffffffff81805120     0  1130      2 0x00000000
[252595.756968]  ffff8803fc57d6a0 0000000000000046 ffff8803fc57d640 ffffffff810329a9
[252595.756969]  ffff8803fc57dfd8 ffff8803fc57dfd8 ffff8803fc57dfd8 0000000000012a40
[252595.756971]  ffff880406945c80 ffff8803dcda0000 ffff8803fc57d690 ffff8803fc57d700
[252595.756972] Call Trace:
[252595.756974]  [<ffffffff810329a9>] ? default_spin_lock_flags+0x9/0x10
[252595.756975]  [<ffffffff8124508d>] do_get_write_access+0x27d/0x500
[252595.756977]  [<ffffffff81081740>] ? autoremove_wake_function+0x40/0x40
[252595.756978]  [<ffffffff81196067>] ? __find_get_block+0x87/0xe0
[252595.756979]  [<ffffffff81245450>] jbd2_journal_get_write_access+0x30/0x50
[252595.756981]  [<ffffffff8122b55e>] __ext4_journal_get_write_access+0x3e/0x80
[252595.756983]  [<ffffffff812326cf>] ext4_mb_mark_diskspace_used+0x7f/0x4e0
[252595.756984]  [<ffffffff81233cbf>] ext4_mb_new_blocks+0x29f/0x460
[252595.756986]  [<ffffffff8122a4b1>] ext4_ext_map_blocks+0x5a1/0xb30
[252595.756989]  [<ffffffff81114d65>] ? pagevec_lookup_tag+0x25/0x40
[252595.756990]  [<ffffffff81207225>] ext4_map_blocks+0x1b5/0x240
[252595.756992]  [<ffffffff81209dab>] mpage_da_map_and_submit+0xbb/0x360
[252595.756993]  [<ffffffff8120a89c>] ext4_da_writepages+0x32c/0x5e0
[252595.756995]  [<ffffffff812e68a6>] ? cpumask_next_and+0x36/0x50
[252595.756997]  [<ffffffff81114271>] do_writepages+0x21/0x40
[252595.756999]  [<ffffffff8118ea03>] writeback_single_inode+0x103/0x270
[252595.757000]  [<ffffffff8118ee01>] writeback_sb_inodes+0xe1/0x1b0
[252595.757001]  [<ffffffff8118f166>] writeback_inodes_wb+0xa6/0xf0
[252595.757002]  [<ffffffff8118f4df>] wb_writeback+0x32f/0x430
[252595.757004]  [<ffffffff8118f678>] wb_check_old_data_flush+0x98/0xa0
[252595.757005]  [<ffffffff8118f7d1>] wb_do_writeback+0x151/0x1f0
[252595.757008]  [<ffffffff8106dd70>] ? usleep_range+0x50/0x50
[252595.757009]  [<ffffffff8118f8f3>] bdi_writeback_thread+0x83/0x2a0
[252595.757010]  [<ffffffff8118f870>] ? wb_do_writeback+0x1f0/0x1f0
[252595.757012]  [<ffffffff81080c5c>] kthread+0x8c/0xa0
[252595.757014]  [<ffffffff81607d24>] kernel_thread_helper+0x4/0x10
[252595.757015]  [<ffffffff81080bd0>] ? flush_kthread_worker+0xa0/0xa0
[252595.757017]  [<ffffffff81607d20>] ? gs_change+0x13/0x13
[252715.640351] INFO: task jbd2/md0-8:782 blocked for more than 120 seconds.
[252715.640393] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[252715.640436] jbd2/md0-8      D ffffffff81805120     0   782      2 0x00000000
[252715.640438]  ffff880402d51ad0 0000000000000046 ffff880402d51a80 ffff880402d51a80
[252715.640440]  ffff880402d51fd8 ffff880402d51fd8 ffff880402d51fd8 0000000000012a40
[252715.640442]  ffff88040695c560 ffff880406b49720 ffff88041f7ae6c8 ffff88041f5932c0
[252715.640444] Call Trace:
[252715.640449]  [<ffffffff81108fe0>] ? __lock_page+0x70/0x70
[252715.640452]  [<ffffffff815fc9ef>] io_schedule+0x8f/0xd0
[252715.640453]  [<ffffffff81108fee>] sleep_on_page+0xe/0x20
[252715.640455]  [<ffffffff815fd29f>] __wait_on_bit+0x5f/0x90
[252715.640456]  [<ffffffff81109158>] wait_on_page_bit+0x78/0x80
[252715.640459]  [<ffffffff81081740>] ? autoremove_wake_function+0x40/0x40
[252715.640460]  [<ffffffff8110926c>] filemap_fdatawait_range+0x10c/0x1a0
[252715.640462]  [<ffffffff8110932b>] filemap_fdatawait+0x2b/0x30
[252715.640464]  [<ffffffff81245c73>] journal_finish_inode_data_buffers+0x73/0x170
[252715.640466]  [<ffffffff81246575>] jbd2_journal_commit_transaction+0x675/0x1250
[252715.640468]  [<ffffffff8104ca0e>] ? perf_event_task_sched_out+0x2e/0xa0
[252715.640470]  [<ffffffff81081700>] ? add_wait_queue+0x60/0x60
[252715.640472]  [<ffffffff8124af7b>] kjournald2+0xbb/0x220
[252715.640473]  [<ffffffff81081700>] ? add_wait_queue+0x60/0x60
[252715.640475]  [<ffffffff8124aec0>] ? commit_timeout+0x10/0x10
[252715.640476]  [<ffffffff81080c5c>] kthread+0x8c/0xa0
[252715.640478]  [<ffffffff81607d24>] kernel_thread_helper+0x4/0x10
[252715.640480]  [<ffffffff81080bd0>] ? flush_kthread_worker+0xa0/0xa0
[252715.640482]  [<ffffffff81607d20>] ? gs_change+0x13/0x13
[252715.640492] INFO: task sabnzbdplus:2008 blocked for more than 120 seconds.
[252715.640509] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[252715.640527] sabnzbdplus     D ffffffff81805120     0  2008      1 0x00000000
[252715.640529]  ffff8803edb89a98 0000000000000086 ffff8803edb89a38 ffffffff810329a9
[252715.640531]  ffff8803edb89fd8 ffff8803edb89fd8 ffff8803edb89fd8 0000000000012a40
[252715.640532]  ffff880406940000 ffff8803edb24560 ffff8803edb89a88 ffff8803edb89af8
[252715.640534] Call Trace:
[252715.640536]  [<ffffffff810329a9>] ? default_spin_lock_flags+0x9/0x10
[252715.640537]  [<ffffffff8124508d>] do_get_write_access+0x27d/0x500
[252715.640540]  [<ffffffff81195fa9>] ? bh_lru_install+0x129/0x160
[252715.640542]  [<ffffffff81081740>] ? autoremove_wake_function+0x40/0x40
[252715.640543]  [<ffffffff81196067>] ? __find_get_block+0x87/0xe0
[252715.640545]  [<ffffffff81245450>] jbd2_journal_get_write_access+0x30/0x50
[252715.640548]  [<ffffffff8122b55e>] __ext4_journal_get_write_access+0x3e/0x80
[252715.640551]  [<ffffffff81200e4e>] ext4_new_inode+0x27e/0xbc0
[252715.640553]  [<ffffffff81220849>] ? ext4_journal_start_sb+0x69/0x170
[252715.640554]  [<ffffffff8120f537>] ext4_create+0xb7/0x140
[252715.640557]  [<ffffffff811724d3>] ? generic_permission+0x23/0xd0
[252715.640559]  [<ffffffff811738d4>] vfs_create+0xb4/0x120
[252715.640560]  [<ffffffff81174b81>] do_last+0x621/0x700
[252715.640562]  [<ffffffff8117688a>] path_openat+0xca/0x3f0
[252715.640563]  [<ffffffff81172255>] ? putname+0x35/0x50
[252715.640564]  [<ffffffff81176bf2>] do_filp_open+0x42/0xa0
[252715.640567]  [<ffffffff812f3231>] ? strncpy_from_user+0x31/0x40
[252715.640568]  [<ffffffff815fe82e>] ? _raw_spin_lock+0xe/0x20
[252715.640570]  [<ffffffff81183dc7>] ? alloc_fd+0xf7/0x150
[252715.640572]  [<ffffffff81166aad>] do_sys_open+0xed/0x220
[252715.640574]  [<ffffffff81166c00>] sys_open+0x20/0x30
[252715.640575]  [<ffffffff81606c02>] system_call_fastpath+0x16/0x1b
[252715.640580] INFO: task flush-9:0:1130 blocked for more than 120 seconds.
[252715.640596] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[252715.640615] flush-9:0       D ffffffff81805120     0  1130      2 0x00000000
[252715.640617]  ffff8803fc57d6a0 0000000000000046 ffff8803fc57d640 ffffffff810329a9
[252715.640618]  ffff8803fc57dfd8 ffff8803fc57dfd8 ffff8803fc57dfd8 0000000000012a40
[252715.640620]  ffff880406945c80 ffff8803dcda0000 ffff8803fc57d690 ffff8803fc57d700
[252715.640621] Call Trace:
[252715.640623]  [<ffffffff810329a9>] ? default_spin_lock_flags+0x9/0x10
[252715.640624]  [<ffffffff8124508d>] do_get_write_access+0x27d/0x500
[252715.640626]  [<ffffffff81081740>] ? autoremove_wake_function+0x40/0x40
[252715.640627]  [<ffffffff81196067>] ? __find_get_block+0x87/0xe0
[252715.640628]  [<ffffffff81245450>] jbd2_journal_get_write_access+0x30/0x50
[252715.640630]  [<ffffffff8122b55e>] __ext4_journal_get_write_access+0x3e/0x80
[252715.640632]  [<ffffffff812326cf>] ext4_mb_mark_diskspace_used+0x7f/0x4e0
[252715.640633]  [<ffffffff81233cbf>] ext4_mb_new_blocks+0x29f/0x460
[252715.640635]  [<ffffffff8122a4b1>] ext4_ext_map_blocks+0x5a1/0xb30
[252715.640637]  [<ffffffff81114d65>] ? pagevec_lookup_tag+0x25/0x40
[252715.640639]  [<ffffffff81207225>] ext4_map_blocks+0x1b5/0x240
[252715.640641]  [<ffffffff81209dab>] mpage_da_map_and_submit+0xbb/0x360
[252715.640642]  [<ffffffff8120a89c>] ext4_da_writepages+0x32c/0x5e0
[252715.640644]  [<ffffffff812e68a6>] ? cpumask_next_and+0x36/0x50
[252715.640646]  [<ffffffff81114271>] do_writepages+0x21/0x40
[252715.640647]  [<ffffffff8118ea03>] writeback_single_inode+0x103/0x270
[252715.640649]  [<ffffffff8118ee01>] writeback_sb_inodes+0xe1/0x1b0
[252715.640650]  [<ffffffff8118f166>] writeback_inodes_wb+0xa6/0xf0
[252715.640651]  [<ffffffff8118f4df>] wb_writeback+0x32f/0x430
[252715.640653]  [<ffffffff8118f678>] wb_check_old_data_flush+0x98/0xa0
[252715.640654]  [<ffffffff8118f7d1>] wb_do_writeback+0x151/0x1f0
[252715.640657]  [<ffffffff8106dd70>] ? usleep_range+0x50/0x50
[252715.640658]  [<ffffffff8118f8f3>] bdi_writeback_thread+0x83/0x2a0
[252715.640659]  [<ffffffff8118f870>] ? wb_do_writeback+0x1f0/0x1f0
[252715.640661]  [<ffffffff81080c5c>] kthread+0x8c/0xa0
[252715.640662]  [<ffffffff81607d24>] kernel_thread_helper+0x4/0x10
[252715.640664]  [<ffffffff81080bd0>] ? flush_kthread_worker+0xa0/0xa0
[252715.640666]  [<ffffffff81607d20>] ? gs_change+0x13/0x13
[252835.523984] INFO: task jbd2/md0-8:782 blocked for more than 120 seconds.
[252835.524026] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[252835.524071] jbd2/md0-8      D ffffffff81805120     0   782      2 0x00000000
[252835.524073]  ffff880402d51ad0 0000000000000046 ffff880402d51a80 ffff880402d51a80
[252835.524075]  ffff880402d51fd8 ffff880402d51fd8 ffff880402d51fd8 0000000000012a40
[252835.524076]  ffff88040695c560 ffff880406b49720 ffff88041f7ae6c8 ffff88041f5932c0
[252835.524078] Call Trace:
[252835.524083]  [<ffffffff81108fe0>] ? __lock_page+0x70/0x70
[252835.524086]  [<ffffffff815fc9ef>] io_schedule+0x8f/0xd0
[252835.524088]  [<ffffffff81108fee>] sleep_on_page+0xe/0x20
[252835.524089]  [<ffffffff815fd29f>] __wait_on_bit+0x5f/0x90
[252835.524091]  [<ffffffff81109158>] wait_on_page_bit+0x78/0x80
[252835.524093]  [<ffffffff81081740>] ? autoremove_wake_function+0x40/0x40
[252835.524095]  [<ffffffff8110926c>] filemap_fdatawait_range+0x10c/0x1a0
[252835.524097]  [<ffffffff8110932b>] filemap_fdatawait+0x2b/0x30
[252835.524099]  [<ffffffff81245c73>] journal_finish_inode_data_buffers+0x73/0x170
[252835.524100]  [<ffffffff81246575>] jbd2_journal_commit_transaction+0x675/0x1250
[252835.524103]  [<ffffffff8104ca0e>] ? perf_event_task_sched_out+0x2e/0xa0
[252835.524105]  [<ffffffff81081700>] ? add_wait_queue+0x60/0x60
[252835.524106]  [<ffffffff8124af7b>] kjournald2+0xbb/0x220
[252835.524108]  [<ffffffff81081700>] ? add_wait_queue+0x60/0x60
[252835.524109]  [<ffffffff8124aec0>] ? commit_timeout+0x10/0x10
[252835.524111]  [<ffffffff81080c5c>] kthread+0x8c/0xa0
[252835.524113]  [<ffffffff81607d24>] kernel_thread_helper+0x4/0x10
[252835.524115]  [<ffffffff81080bd0>] ? flush_kthread_worker+0xa0/0xa0
[252835.524116]  [<ffffffff81607d20>] ? gs_change+0x13/0x13
[252835.524127] INFO: task sabnzbdplus:2008 blocked for more than 120 seconds.
[252835.524143] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[252835.524162] sabnzbdplus     D ffffffff81805120     0  2008      1 0x00000000
[252835.524164]  ffff8803edb89a98 0000000000000086 ffff8803edb89a38 ffffffff810329a9
[252835.524165]  ffff8803edb89fd8 ffff8803edb89fd8 ffff8803edb89fd8 0000000000012a40
[252835.524167]  ffff880406940000 ffff8803edb24560 ffff8803edb89a88 ffff8803edb89af8
[252835.524168] Call Trace:
[252835.524171]  [<ffffffff810329a9>] ? default_spin_lock_flags+0x9/0x10
[252835.524172]  [<ffffffff8124508d>] do_get_write_access+0x27d/0x500
[252835.524175]  [<ffffffff81195fa9>] ? bh_lru_install+0x129/0x160
[252835.524176]  [<ffffffff81081740>] ? autoremove_wake_function+0x40/0x40
[252835.524178]  [<ffffffff81196067>] ? __find_get_block+0x87/0xe0
[252835.524179]  [<ffffffff81245450>] jbd2_journal_get_write_access+0x30/0x50
[252835.524183]  [<ffffffff8122b55e>] __ext4_journal_get_write_access+0x3e/0x80
[252835.524186]  [<ffffffff81200e4e>] ext4_new_inode+0x27e/0xbc0
[252835.524187]  [<ffffffff81220849>] ? ext4_journal_start_sb+0x69/0x170
[252835.524189]  [<ffffffff8120f537>] ext4_create+0xb7/0x140
[252835.524192]  [<ffffffff811724d3>] ? generic_permission+0x23/0xd0
[252835.524194]  [<ffffffff811738d4>] vfs_create+0xb4/0x120
[252835.524195]  [<ffffffff81174b81>] do_last+0x621/0x700
[252835.524197]  [<ffffffff8117688a>] path_openat+0xca/0x3f0
[252835.524198]  [<ffffffff81172255>] ? putname+0x35/0x50
[252835.524199]  [<ffffffff81176bf2>] do_filp_open+0x42/0xa0
[252835.524202]  [<ffffffff812f3231>] ? strncpy_from_user+0x31/0x40
[252835.524203]  [<ffffffff815fe82e>] ? _raw_spin_lock+0xe/0x20
[252835.524205]  [<ffffffff81183dc7>] ? alloc_fd+0xf7/0x150
[252835.524207]  [<ffffffff81166aad>] do_sys_open+0xed/0x220
[252835.524209]  [<ffffffff81166c00>] sys_open+0x20/0x30
[252835.524210]  [<ffffffff81606c02>] system_call_fastpath+0x16/0x1b
[252835.524216] INFO: task flush-9:0:1130 blocked for more than 120 seconds.
[252835.524232] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[252835.524250] flush-9:0       D ffffffff81805120     0  1130      2 0x00000000
[252835.524252]  ffff8803fc57d6a0 0000000000000046 ffff8803fc57d640 ffffffff810329a9
[252835.524254]  ffff8803fc57dfd8 ffff8803fc57dfd8 ffff8803fc57dfd8 0000000000012a40
[252835.524255]  ffff880406945c80 ffff8803dcda0000 ffff8803fc57d690 ffff8803fc57d700
[252835.524257] Call Trace:
[252835.524258]  [<ffffffff810329a9>] ? default_spin_lock_flags+0x9/0x10
[252835.524259]  [<ffffffff8124508d>] do_get_write_access+0x27d/0x500
[252835.524261]  [<ffffffff81081740>] ? autoremove_wake_function+0x40/0x40
[252835.524262]  [<ffffffff81196067>] ? __find_get_block+0x87/0xe0
[252835.524264]  [<ffffffff81245450>] jbd2_journal_get_write_access+0x30/0x50
[252835.524266]  [<ffffffff8122b55e>] __ext4_journal_get_write_access+0x3e/0x80
[252835.524267]  [<ffffffff812326cf>] ext4_mb_mark_diskspace_used+0x7f/0x4e0
[252835.524269]  [<ffffffff81233cbf>] ext4_mb_new_blocks+0x29f/0x460
[252835.524270]  [<ffffffff8122a4b1>] ext4_ext_map_blocks+0x5a1/0xb30
[252835.524273]  [<ffffffff81114d65>] ? pagevec_lookup_tag+0x25/0x40
[252835.524275]  [<ffffffff81207225>] ext4_map_blocks+0x1b5/0x240
[252835.524276]  [<ffffffff81209dab>] mpage_da_map_and_submit+0xbb/0x360
[252835.524277]  [<ffffffff8120a89c>] ext4_da_writepages+0x32c/0x5e0
[252835.524280]  [<ffffffff812e68a6>] ? cpumask_next_and+0x36/0x50
[252835.524281]  [<ffffffff81114271>] do_writepages+0x21/0x40
[252835.524283]  [<ffffffff8118ea03>] writeback_single_inode+0x103/0x270
[252835.524284]  [<ffffffff8118ee01>] writeback_sb_inodes+0xe1/0x1b0
[252835.524285]  [<ffffffff8118f166>] writeback_inodes_wb+0xa6/0xf0
[252835.524287]  [<ffffffff8118f4df>] wb_writeback+0x32f/0x430
[252835.524288]  [<ffffffff8118f678>] wb_check_old_data_flush+0x98/0xa0
[252835.524289]  [<ffffffff8118f7d1>] wb_do_writeback+0x151/0x1f0
[252835.524292]  [<ffffffff8106dd70>] ? usleep_range+0x50/0x50
[252835.524294]  [<ffffffff8118f8f3>] bdi_writeback_thread+0x83/0x2a0
[252835.524295]  [<ffffffff8118f870>] ? wb_do_writeback+0x1f0/0x1f0
[252835.524296]  [<ffffffff81080c5c>] kthread+0x8c/0xa0
[252835.524298]  [<ffffffff81607d24>] kernel_thread_helper+0x4/0x10
[252835.524299]  [<ffffffff81080bd0>] ? flush_kthread_worker+0xa0/0xa0
[252835.524301]  [<ffffffff81607d20>] ? gs_change+0x13/0x13
[252955.407642] INFO: task jbd2/md0-8:782 blocked for more than 120 seconds.
[252955.407683] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[252955.407731] jbd2/md0-8      D ffffffff81805120     0   782      2 0x00000000
[252955.407733]  ffff880402d51ad0 0000000000000046 ffff880402d51a80 ffff880402d51a80
[252955.407735]  ffff880402d51fd8 ffff880402d51fd8 ffff880402d51fd8 0000000000012a40
[252955.407737]  ffff88040695c560 ffff880406b49720 ffff88041f7ae6c8 ffff88041f5932c0
[252955.407739] Call Trace:
[252955.407743]  [<ffffffff81108fe0>] ? __lock_page+0x70/0x70
[252955.407746]  [<ffffffff815fc9ef>] io_schedule+0x8f/0xd0
[252955.407748]  [<ffffffff81108fee>] sleep_on_page+0xe/0x20
[252955.407749]  [<ffffffff815fd29f>] __wait_on_bit+0x5f/0x90
[252955.407751]  [<ffffffff81109158>] wait_on_page_bit+0x78/0x80
[252955.407753]  [<ffffffff81081740>] ? autoremove_wake_function+0x40/0x40
[252955.407755]  [<ffffffff8110926c>] filemap_fdatawait_range+0x10c/0x1a0
[252955.407757]  [<ffffffff8110932b>] filemap_fdatawait+0x2b/0x30
[252955.407759]  [<ffffffff81245c73>] journal_finish_inode_data_buffers+0x73/0x170
[252955.407760]  [<ffffffff81246575>] jbd2_journal_commit_transaction+0x675/0x1250
[252955.407763]  [<ffffffff8104ca0e>] ? perf_event_task_sched_out+0x2e/0xa0
[252955.407765]  [<ffffffff81081700>] ? add_wait_queue+0x60/0x60
[252955.407766]  [<ffffffff8124af7b>] kjournald2+0xbb/0x220
[252955.407768]  [<ffffffff81081700>] ? add_wait_queue+0x60/0x60
[252955.407769]  [<ffffffff8124aec0>] ? commit_timeout+0x10/0x10
[252955.407771]  [<ffffffff81080c5c>] kthread+0x8c/0xa0
[252955.407773]  [<ffffffff81607d24>] kernel_thread_helper+0x4/0x10
[252955.407775]  [<ffffffff81080bd0>] ? flush_kthread_worker+0xa0/0xa0
[252955.407776]  [<ffffffff81607d20>] ? gs_change+0x13/0x13

---

