---
title: "Server hung, with ssh &amp; webserver unresponsive for some minutes, syslogs show: task X"
date: 2011-10-15
forum: Server Platforms
---

### Post by davidparks21 on 2011-10-15
The server (natty) hung for anywhere from a few minutes to as much as maybe an hour (I'm not sure). The syslog shows some errors I can't make heads or tails of, they're attached in the hopes they make more sense to someone else.

INFO: task jbd2/xvda1-8:136 blocked for more than 120 seconds.
INFO: task java:11610 blocked for more than 120 seconds.
etc.

```
Oct 13 22:03:43 localhost kernel: [185521.096127] INFO: task jbd2/xvda1-8:136 blocked for more than 120 seconds.
Oct 13 22:03:43 localhost kernel: [185521.096146] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Oct 13 22:03:43 localhost kernel: [185521.096157] jbd2/xvda1-8    D eb35fe18     0   136      2 0x00000000
Oct 13 22:03:43 localhost kernel: [185521.096162]  eb35fe60 00000246 eb1b09b8 eb35fe18 c0135b80 44bcee4c eb3141ac c097f680
Oct 13 22:03:43 localhost kernel: [185521.096168]  3b71d7cd 0000a892 eb3141a8 c097f680 c097f680 ec696680 eb313f20 e9a40000
Oct 13 22:03:43 localhost kernel: [185521.096174]  c08c6f80 0187099e eb35fe20 c01077d9 eb35fe28 eb1b09b8 eb35fe58 c0181af8
Oct 13 22:03:43 localhost kernel: [185521.096180] Call Trace:
Oct 13 22:03:43 localhost kernel: [185521.096190]  [<c0135b80>] ? pvclock_clocksource_read+0xa0/0x110
Oct 13 22:03:43 localhost kernel: [185521.096195]  [<c01077d9>] ? xen_clocksource_read+0x19/0x20
Oct 13 22:03:43 localhost kernel: [185521.096200]  [<c0181af8>] ? ktime_get_ts+0xf8/0x120
Oct 13 22:03:43 localhost kernel: [185521.096206]  [<c06355af>] io_schedule+0x5f/0xa0
Oct 13 22:03:43 localhost kernel: [185521.096211]  [<c0259c58>] sync_buffer+0x38/0x40
Oct 13 22:03:43 localhost kernel: [185521.096215]  [<c0635dad>] __wait_on_bit+0x4d/0x70
Oct 13 22:03:43 localhost kernel: [185521.096218]  [<c0259c20>] ? sync_buffer+0x0/0x40
Oct 13 22:03:43 localhost kernel: [185521.096221]  [<c0259c20>] ? sync_buffer+0x0/0x40
Oct 13 22:03:43 localhost kernel: [185521.096224]  [<c0635e31>] out_of_line_wait_on_bit+0x61/0x70
Oct 13 22:03:43 localhost kernel: [185521.096229]  [<c0176e20>] ? wake_bit_function+0x0/0x60
Oct 13 22:03:43 localhost kernel: [185521.096232]  [<c0259c1e>] __wait_on_buffer+0x2e/0x30
Oct 13 22:03:43 localhost kernel: [185521.096237]  [<c02f6d6b>] jbd2_journal_commit_transaction+0x4cb/0xf30
Oct 13 22:03:43 localhost kernel: [185521.096241]  [<c06373d9>] ? _raw_spin_unlock_irqrestore+0x19/0x20
Oct 13 22:03:43 localhost kernel: [185521.096245]  [<c0167637>] ? try_to_del_timer_sync+0x67/0xb0
Oct 13 22:03:43 localhost kernel: [185521.096249]  [<c02fb2fe>] kjournald2+0x8e/0x1c0
Oct 13 22:03:43 localhost kernel: [185521.096252]  [<c0176dd0>] ? autoremove_wake_function+0x0/0x50
Oct 13 22:03:43 localhost kernel: [185521.096255]  [<c02fb270>] ? kjournald2+0x0/0x1c0
Oct 13 22:03:43 localhost kernel: [185521.096258]  [<c0176864>] kthread+0x74/0x80
Oct 13 22:03:43 localhost kernel: [185521.096261]  [<c01767f0>] ? kthread+0x0/0x80
Oct 13 22:03:43 localhost kernel: [185521.096265]  [<c010b0fe>] kernel_thread_helper+0x6/0x10
Oct 13 22:03:43 localhost kernel: [185521.096272] INFO: task java:11610 blocked for more than 120 seconds.
Oct 13 22:03:43 localhost kernel: [185521.096282] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Oct 13 22:03:43 localhost kernel: [185521.096291] java            D c1157cd8     0 11610      1 0x00000000
Oct 13 22:03:43 localhost kernel: [185521.096295]  c1157ce0 00000286 c01542dd c1157cd8 c010775b c1157cc4 c101742c c097f680
Oct 13 22:03:43 localhost kernel: [185521.096301]  b3eb4995 0000a893 c1017428 c097f680 c097f680 ec696680 c10171a0 c086cf60
Oct 13 22:03:43 localhost kernel: [185521.096307]  c1157ccc c0135b80 ba41686c 017f78fc 52d5d139 03e5075e 00000200 c10171a0
Oct 13 22:03:43 localhost kernel: [185521.096313] Call Trace:
Oct 13 22:03:43 localhost kernel: [185521.096317]  [<c01542dd>] ? account_idle_ticks+0xd/0x10
Oct 13 22:03:43 localhost kernel: [185521.096320]  [<c010775b>] ? do_stolen_accounting+0x21b/0x250
Oct 13 22:03:43 localhost kernel: [185521.096324]  [<c0135b80>] ? pvclock_clocksource_read+0xa0/0x110
Oct 13 22:03:43 localhost kernel: [185521.096327]  [<c010721e>] ? __raw_callee_save_xen_restore_fl+0x6/0x8
Oct 13 22:03:43 localhost kernel: [185521.096330]  [<c06373d9>] ? _raw_spin_unlock_irqrestore+0x19/0x20
Oct 13 22:03:43 localhost kernel: [185521.096334]  [<c0177038>] ? prepare_to_wait+0x48/0x70
Oct 13 22:03:43 localhost kernel: [185521.096337]  [<c02f5ca5>] do_get_write_access+0x235/0x3f0
Oct 13 22:03:43 localhost kernel: [185521.096340]  [<c025aa64>] ? __find_get_block+0xb4/0xe0
Oct 13 22:03:43 localhost kernel: [185521.096344]  [<c0176e20>] ? wake_bit_function+0x0/0x60
Oct 13 22:03:43 localhost kernel: [185521.096348]  [<c02f478d>] ? start_this_handle.clone.5+0x39d/0x420
Oct 13 22:03:43 localhost kernel: [185521.096352]  [<c01424a4>] ? update_cfs_load+0x204/0x290
Oct 13 22:03:43 localhost kernel: [185521.096355]  [<c02f5f68>] jbd2_journal_get_write_access+0x28/0x40
Oct 13 22:03:43 localhost kernel: [185521.096359]  [<c02de97f>] __ext4_journal_get_write_access+0x2f/0x80
Oct 13 22:03:43 localhost kernel: [185521.096365]  [<c02bbef7>] ext4_reserve_inode_write+0x67/0x80
Oct 13 22:03:43 localhost kernel: [185521.096368]  [<c02bbf4c>] ext4_mark_inode_dirty+0x3c/0x1c0
Oct 13 22:03:43 localhost kernel: [185521.096374]  [<c02d3423>] ? ext4_journal_start_sb+0x93/0x110
Oct 13 22:03:43 localhost kernel: [185521.096378]  [<c02c0b51>] ? ext4_dirty_inode+0x31/0x50
Oct 13 22:03:43 localhost kernel: [185521.096381]  [<c02c0b51>] ext4_dirty_inode+0x31/0x50
Oct 13 22:03:43 localhost kernel: [185521.096385]  [<c0253ed9>] __mark_inode_dirty+0x29/0x1d0
Oct 13 22:03:43 localhost kernel: [185521.096388]  [<c025b4ec>] ? __set_page_dirty+0x6c/0xc0
Oct 13 22:03:43 localhost kernel: [185521.096392]  [<c0249741>] file_update_time+0xc1/0x140
Oct 13 22:03:43 localhost kernel: [185521.096396]  [<c0208d1f>] do_wp_page+0x12f/0x820
Oct 13 22:03:43 localhost kernel: [185521.096399]  [<c017ad89>] ? hrtimer_cancel+0x19/0x30
Oct 13 22:03:43 localhost kernel: [185521.096402]  [<c020b276>] handle_pte_fault+0x296/0x2f0
Oct 13 22:03:43 localhost kernel: [185521.096406]  [<c0105a64>] ? pte_mfn_to_pfn+0xa4/0xc0
Oct 13 22:03:43 localhost kernel: [185521.096409]  [<c020bf39>] handle_mm_fault+0x109/0x1b0
Oct 13 22:03:43 localhost kernel: [185521.096413]  [<c063aad0>] ? do_page_fault+0x0/0x490
Oct 13 22:03:43 localhost kernel: [185521.096416]  [<c063ac2e>] do_page_fault+0x15e/0x490
Oct 13 22:03:43 localhost kernel: [185521.096421]  [<c018b76e>] ? sys_futex+0x6e/0x120
Oct 13 22:03:43 localhost kernel: [185521.096424]  [<c063aad0>] ? do_page_fault+0x0/0x490
Oct 13 22:03:43 localhost kernel: [185521.096427]  [<c0637e3f>] error_code+0x67/0x6c
Oct 13 22:03:43 localhost kernel: [185521.096430] INFO: task java:11614 blocked for more than 120 seconds.
Oct 13 22:03:43 localhost kernel: [185521.096437] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Oct 13 22:03:43 localhost kernel: [185521.096446] java            D eb1b3c44     0 11614      1 0x00000000
Oct 13 22:03:43 localhost kernel: [185521.096450]  eb1b3c68 00000286 c010775b eb1b3c44 5f8f1640 0000a10a e9a4742c c097f680
Oct 13 22:03:43 localhost kernel: [185521.096456]  e74d77b9 0000a890 e9a47428 c097f680 c097f680 ec696680 e9a471a0 c086cf60
Oct 13 22:03:43 localhost kernel: [185521.096462]  c063732d eb1b3c3c c039391c ffffffe0 c02f478d eb089400 00000200 e9a471a0
Oct 13 22:03:43 localhost kernel: [185521.096468] Call Trace:
Oct 13 22:03:43 localhost kernel: [185521.096471]  [<c010775b>] ? do_stolen_accounting+0x21b/0x250
Oct 13 22:03:43 localhost kernel: [185521.096474]  [<c063732d>] ? _raw_spin_lock+0xd/0x10
Oct 13 22:03:43 localhost kernel: [185521.096478]  [<c039391c>] ? __percpu_counter_add+0x8c/0xb0
Oct 13 22:03:43 localhost kernel: [185521.096481]  [<c02f478d>] ? start_this_handle.clone.5+0x39d/0x420
Oct 13 22:03:43 localhost kernel: [185521.096485]  [<c010721e>] ? __raw_callee_save_xen_restore_fl+0x6/0x8
Oct 13 22:03:43 localhost kernel: [185521.096488]  [<c06373d9>] ? _raw_spin_unlock_irqrestore+0x19/0x20
Oct 13 22:03:43 localhost kernel: [185521.096491]  [<c0177038>] ? prepare_to_wait+0x48/0x70
Oct 13 22:03:43 localhost kernel: [185521.096494]  [<c02f5ca5>] do_get_write_access+0x235/0x3f0
Oct 13 22:03:43 localhost kernel: [185521.096498]  [<c025aa64>] ? __find_get_block+0xb4/0xe0
Oct 13 22:03:43 localhost kernel: [185521.096501]  [<c0176e20>] ? wake_bit_function+0x0/0x60
Oct 13 22:03:43 localhost kernel: [185521.096504]  [<c02f478d>] ? start_this_handle.clone.5+0x39d/0x420
Oct 13 22:03:43 localhost kernel: [185521.096508]  [<c01077d9>] ? xen_clocksource_read+0x19/0x20
Oct 13 22:03:43 localhost kernel: [185521.096511]  [<c02f5f68>] jbd2_journal_get_write_access+0x28/0x40
Oct 13 22:03:43 localhost kernel: [185521.096515]  [<c02de97f>] __ext4_journal_get_write_access+0x2f/0x80
Oct 13 22:03:43 localhost kernel: [185521.096518]  [<c02bbef7>] ext4_reserve_inode_write+0x67/0x80
Oct 13 22:03:43 localhost kernel: [185521.096522]  [<c02bbf4c>] ext4_mark_inode_dirty+0x3c/0x1c0
Oct 13 22:03:43 localhost kernel: [185521.096525]  [<c02d3423>] ? ext4_journal_start_sb+0x93/0x110
Oct 13 22:03:43 localhost kernel: [185521.096529]  [<c02c0b51>] ? ext4_dirty_inode+0x31/0x50
Oct 13 22:03:43 localhost kernel: [185521.096532]  [<c02c0b51>] ext4_dirty_inode+0x31/0x50
Oct 13 22:03:43 localhost kernel: [185521.096535]  [<c0253ed9>] __mark_inode_dirty+0x29/0x1d0
Oct 13 22:03:43 localhost kernel: [185521.096539]  [<c03275d4>] ? security_inode_need_killpriv+0x14/0x20
Oct 13 22:03:43 localhost kernel: [185521.096543]  [<c01eb644>] ? file_remove_suid+0x24/0x80
Oct 13 22:03:43 localhost kernel: [185521.096546]  [<c0249741>] file_update_time+0xc1/0x140
Oct 13 22:03:43 localhost kernel: [185521.096550]  [<c01ed478>] __generic_file_aio_write+0x1e8/0x4e0
Oct 13 22:03:43 localhost kernel: [185521.096553]  [<c01ed7ce>] generic_file_aio_write+0x5e/0xd0
Oct 13 22:03:43 localhost kernel: [185521.096556]  [<c06373d9>] ? _raw_spin_unlock_irqrestore+0x19/0x20
Oct 13 22:03:43 localhost kernel: [185521.096560]  [<c02b54b4>] ext4_file_write+0x54/0x2a0
Oct 13 22:03:43 localhost kernel: [185521.096563]  [<c0189e42>] ? futex_wait+0x1c2/0x280
Oct 13 22:03:43 localhost kernel: [185521.096567]  [<c02322f4>] do_sync_write+0xa4/0xe0
Oct 13 22:03:43 localhost kernel: [185521.096570]  [<c023272c>] ? rw_verify_area+0x6c/0x130
Oct 13 22:03:43 localhost kernel: [185521.096574]  [<c0232ab2>] vfs_write+0xa2/0x170
Oct 13 22:03:43 localhost kernel: [185521.096576]  [<c0232250>] ? do_sync_write+0x0/0xe0
Oct 13 22:03:43 localhost kernel: [185521.096579]  [<c0232d92>] sys_write+0x42/0x70
Oct 13 22:03:43 localhost kernel: [185521.096582]  [<c0637754>] syscall_call+0x7/0xb
Oct 13 22:03:43 localhost kernel: [185521.096586] INFO: task java:11632 blocked for more than 120 seconds.
Oct 13 22:03:43 localhost kernel: [185521.096593] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Oct 13 22:03:43 localhost kernel: [185521.096601] java            D e9921480     0 11632      1 0x00000000
Oct 13 22:03:43 localhost kernel: [185521.096605]  eb12bc68 00000286 c06373d9 e9921480 eb12bbfc c01770a1 e98b4e4c c097f680
Oct 13 22:03:43 localhost kernel: [185521.096611]  b4f8677b 0000a89b e98b4e48 c097f680 c097f680 ec696680 e98b4bc0 e9a43f20
Oct 13 22:03:43 localhost kernel: [185521.096617]  c0243d55 00000000 68de56ac 00000001 c0242c70 0000001c 00000200 e98b4bc0
Oct 13 22:03:43 localhost kernel: [185521.096623] Call Trace:
Oct 13 22:03:43 localhost kernel: [185521.096626]  [<c06373d9>] ? _raw_spin_unlock_irqrestore+0x19/0x20
Oct 13 22:03:43 localhost kernel: [185521.096629]  [<c01770a1>] ? remove_wait_queue+0x41/0x50
Oct 13 22:03:43 localhost kernel: [185521.096633]  [<c0243d55>] ? do_sys_poll+0x145/0x1e0
Oct 13 22:03:43 localhost kernel: [185521.096637]  [<c0242c70>] ? __pollwait+0x0/0xd0
Oct 13 22:03:43 localhost kernel: [185521.096640]  [<c010721e>] ? __raw_callee_save_xen_restore_fl+0x6/0x8
Oct 13 22:03:43 localhost kernel: [185521.096643]  [<c06373d9>] ? _raw_spin_unlock_irqrestore+0x19/0x20
Oct 13 22:03:43 localhost kernel: [185521.096646]  [<c0177038>] ? prepare_to_wait+0x48/0x70
Oct 13 22:03:43 localhost kernel: [185521.096650]  [<c02f5ca5>] do_get_write_access+0x235/0x3f0
Oct 13 22:03:43 localhost kernel: [185521.096653]  [<c025aa64>] ? __find_get_block+0xb4/0xe0
Oct 13 22:03:43 localhost kernel: [185521.096656]  [<c0176e20>] ? wake_bit_function+0x0/0x60
Oct 13 22:03:43 localhost kernel: [185521.096659]  [<c02f478d>] ? start_this_handle.clone.5+0x39d/0x420
Oct 13 22:03:43 localhost kernel: [185521.096663]  [<c02f5f68>] jbd2_journal_get_write_access+0x28/0x40
Oct 13 22:03:43 localhost kernel: [185521.096666]  [<c02de97f>] __ext4_journal_get_write_access+0x2f/0x80
Oct 13 22:03:43 localhost kernel: [185521.096670]  [<c02bbef7>] ext4_reserve_inode_write+0x67/0x80
Oct 13 22:03:43 localhost kernel: [185521.096673]  [<c02bbf4c>] ext4_mark_inode_dirty+0x3c/0x1c0
Oct 13 22:03:43 localhost kernel: [185521.096677]  [<c02d3423>] ? ext4_journal_start_sb+0x93/0x110
Oct 13 22:03:43 localhost kernel: [185521.096680]  [<c02c0b51>] ? ext4_dirty_inode+0x31/0x50
Oct 13 22:03:43 localhost kernel: [185521.096684]  [<c02c0b51>] ext4_dirty_inode+0x31/0x50
Oct 13 22:03:43 localhost kernel: [185521.096687]  [<c0253ed9>] __mark_inode_dirty+0x29/0x1d0
Oct 13 22:03:43 localhost kernel: [185521.096690]  [<c03275d4>] ? security_inode_need_killpriv+0x14/0x20
Oct 13 22:03:43 localhost kernel: [185521.096693]  [<c01eb644>] ? file_remove_suid+0x24/0x80
Oct 13 22:03:43 localhost kernel: [185521.096696]  [<c0249741>] file_update_time+0xc1/0x140
Oct 13 22:03:43 localhost kernel: [185521.096699]  [<c01ed478>] __generic_file_aio_write+0x1e8/0x4e0
Oct 13 22:03:43 localhost kernel: [185521.096702]  [<c0104bb0>] ? xen_mc_flush+0x90/0x1b0
Oct 13 22:03:43 localhost kernel: [185521.096706]  [<c01ed7ce>] generic_file_aio_write+0x5e/0xd0
Oct 13 22:03:43 localhost kernel: [185521.096709]  [<c02b54b4>] ext4_file_write+0x54/0x2a0
Oct 13 22:03:43 localhost kernel: [185521.096712]  [<c010721e>] ? __raw_callee_save_xen_restore_fl+0x6/0x8
Oct 13 22:03:43 localhost kernel: [185521.096716]  [<c0225ce8>] ? kmem_cache_free+0x68/0xd0
Oct 13 22:03:43 localhost kernel: [185521.096719]  [<c0225ce8>] ? kmem_cache_free+0x68/0xd0
Oct 13 22:03:43 localhost kernel: [185521.096722]  [<c024443f>] ? __d_free+0x2f/0x50
Oct 13 22:03:43 localhost kernel: [185521.096725]  [<c02322f4>] do_sync_write+0xa4/0xe0
Oct 13 22:03:43 localhost kernel: [185521.096728]  [<c023272c>] ? rw_verify_area+0x6c/0x130
Oct 13 22:03:43 localhost kernel: [185521.096731]  [<c0232ab2>] vfs_write+0xa2/0x170
Oct 13 22:03:43 localhost kernel: [185521.096736]  [<c0232250>] ? do_sync_write+0x0/0xe0
Oct 13 22:03:43 localhost kernel: [185521.096739]  [<c0232d92>] sys_write+0x42/0x70
Oct 13 22:03:43 localhost kernel: [185521.096742]  [<c0637754>] syscall_call+0x7/0xb
Oct 13 22:03:43 localhost kernel: [185521.096745] INFO: task java:11633 blocked for more than 120 seconds.
Oct 13 22:03:43 localhost kernel: [185521.096752] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Oct 13 22:03:43 localhost kernel: [185521.096761] java            D 00200200     0 11633      1 0x00000000
Oct 13 22:03:43 localhost kernel: [185521.096765]  c10bfce0 00000286 00100100 00200200 e9921140 c117ad90 eb85a86c c097f680
Oct 13 22:03:43 localhost kernel: [185521.096771]  3fa48480 0000a89e eb85a868 c097f680 c097f680 ec696680 eb85a5e0 c086cf60
Oct 13 22:03:43 localhost kernel: [185521.096777]  80000001 5501a067 eb078200 b77b2000 00000000 00000000 00000200 eb85a5e0
Oct 13 22:03:43 localhost kernel: [185521.096783] Call Trace:
Oct 13 22:03:43 localhost kernel: [185521.096786]  [<c010721e>] ? __raw_callee_save_xen_restore_fl+0x6/0x8
Oct 13 22:03:43 localhost kernel: [185521.096790]  [<c06373d9>] ? _raw_spin_unlock_irqrestore+0x19/0x20
Oct 13 22:03:43 localhost kernel: [185521.096793]  [<c0177038>] ? prepare_to_wait+0x48/0x70
Oct 13 22:03:43 localhost kernel: [185521.096796]  [<c02f5ca5>] do_get_write_access+0x235/0x3f0
Oct 13 22:03:43 localhost kernel: [185521.096800]  [<c025aa64>] ? __find_get_block+0xb4/0xe0
Oct 13 22:03:43 localhost kernel: [185521.096803]  [<c0176e20>] ? wake_bit_function+0x0/0x60
Oct 13 22:03:43 localhost kernel: [185521.096806]  [<c02f478d>] ? start_this_handle.clone.5+0x39d/0x420
Oct 13 22:03:43 localhost kernel: [185521.096811]  [<c054e1e4>] ? sk_reset_timer+0x14/0x20
Oct 13 22:03:43 localhost kernel: [185521.096814]  [<c02f5f68>] jbd2_journal_get_write_access+0x28/0x40
Oct 13 22:03:43 localhost kernel: [185521.096818]  [<c02de97f>] __ext4_journal_get_write_access+0x2f/0x80
Oct 13 22:03:43 localhost kernel: [185521.096822]  [<c02bbef7>] ext4_reserve_inode_write+0x67/0x80
Oct 13 22:03:43 localhost kernel: [185521.096825]  [<c02bbf4c>] ext4_mark_inode_dirty+0x3c/0x1c0
Oct 13 22:03:43 localhost kernel: [185521.096829]  [<c02d3423>] ? ext4_journal_start_sb+0x93/0x110
Oct 13 22:03:43 localhost kernel: [185521.096832]  [<c02c0b51>] ? ext4_dirty_inode+0x31/0x50
Oct 13 22:03:43 localhost kernel: [185521.096836]  [<c02c0b51>] ext4_dirty_inode+0x31/0x50
Oct 13 22:03:43 localhost kernel: [185521.096839]  [<c0253ed9>] __mark_inode_dirty+0x29/0x1d0
Oct 13 22:03:43 localhost kernel: [185521.096842]  [<c025b4ec>] ? __set_page_dirty+0x6c/0xc0
Oct 13 22:03:43 localhost kernel: [185521.096845]  [<c0249741>] file_update_time+0xc1/0x140
Oct 13 22:03:43 localhost kernel: [185521.096848]  [<c0208d1f>] do_wp_page+0x12f/0x820
Oct 13 22:03:43 localhost kernel: [185521.096851]  [<c020b276>] handle_pte_fault+0x296/0x2f0
Oct 13 22:03:43 localhost kernel: [185521.096855]  [<c0105a64>] ? pte_mfn_to_pfn+0xa4/0xc0
Oct 13 22:03:43 localhost kernel: [185521.096858]  [<c020bf39>] handle_mm_fault+0x109/0x1b0
Oct 13 22:03:43 localhost kernel: [185521.096861]  [<c063aad0>] ? do_page_fault+0x0/0x490
Oct 13 22:03:43 localhost kernel: [185521.096864]  [<c063ac2e>] do_page_fault+0x15e/0x490
Oct 13 22:03:43 localhost kernel: [185521.096868]  [<c01078b8>] ? xen_clocksource_get_cycles+0x8/0x10
Oct 13 22:03:43 localhost kernel: [185521.096871]  [<c01818b0>] ? getnstimeofday+0x50/0x130
Oct 13 22:03:43 localhost kernel: [185521.096875]  [<c0387d32>] ? copy_to_user+0x42/0x60
Oct 13 22:03:43 localhost kernel: [185521.096879]  [<c015e372>] ? sys_gettimeofday+0x32/0x70
Oct 13 22:03:43 localhost kernel: [185521.096882]  [<c063aad0>] ? do_page_fault+0x0/0x490
Oct 13 22:03:43 localhost kernel: [185521.096885]  [<c0637e3f>] error_code+0x67/0x6c
Oct 13 22:05:43 localhost kernel: [185641.096048] INFO: task jbd2/xvda1-8:136 blocked for more than 120 seconds.
Oct 13 22:05:43 localhost kernel: [185641.096067] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Oct 13 22:05:43 localhost kernel: [185641.096077] jbd2/xvda1-8    D eb35fe18     0   136      2 0x00000000
Oct 13 22:05:43 localhost kernel: [185641.096083]  eb35fe60 00000246 eb1b09b8 eb35fe18 c0135b80 44bcee4c eb3141ac c097f680
Oct 13 22:05:43 localhost kernel: [185641.096089]  3b71d7cd 0000a892 eb3141a8 c097f680 c097f680 ec696680 eb313f20 e9a40000
Oct 13 22:05:43 localhost kernel: [185641.096095]  c08c6f80 0187099e eb35fe20 c01077d9 eb35fe28 eb1b09b8 eb35fe58 c0181af8
Oct 13 22:05:43 localhost kernel: [185641.096102] Call Trace:
Oct 13 22:05:43 localhost kernel: [185641.096112]  [<c0135b80>] ? pvclock_clocksource_read+0xa0/0x110
Oct 13 22:05:43 localhost kernel: [185641.096117]  [<c01077d9>] ? xen_clocksource_read+0x19/0x20
Oct 13 22:05:43 localhost kernel: [185641.096122]  [<c0181af8>] ? ktime_get_ts+0xf8/0x120
Oct 13 22:05:43 localhost kernel: [185641.096128]  [<c06355af>] io_schedule+0x5f/0xa0
Oct 13 22:05:43 localhost kernel: [185641.096133]  [<c0259c58>] sync_buffer+0x38/0x40
Oct 13 22:05:43 localhost kernel: [185641.096136]  [<c0635dad>] __wait_on_bit+0x4d/0x70
Oct 13 22:05:43 localhost kernel: [185641.096140]  [<c0259c20>] ? sync_buffer+0x0/0x40
Oct 13 22:05:43 localhost kernel: [185641.096143]  [<c0259c20>] ? sync_buffer+0x0/0x40
Oct 13 22:05:43 localhost kernel: [185641.096146]  [<c0635e31>] out_of_line_wait_on_bit+0x61/0x70
Oct 13 22:05:43 localhost kernel: [185641.096151]  [<c0176e20>] ? wake_bit_function+0x0/0x60
Oct 13 22:05:43 localhost kernel: [185641.096154]  [<c0259c1e>] __wait_on_buffer+0x2e/0x30
Oct 13 22:05:43 localhost kernel: [185641.096159]  [<c02f6d6b>] jbd2_journal_commit_transaction+0x4cb/0xf30
Oct 13 22:05:43 localhost kernel: [185641.096163]  [<c06373d9>] ? _raw_spin_unlock_irqrestore+0x19/0x20
Oct 13 22:05:43 localhost kernel: [185641.096167]  [<c0167637>] ? try_to_del_timer_sync+0x67/0xb0
Oct 13 22:05:43 localhost kernel: [185641.096171]  [<c02fb2fe>] kjournald2+0x8e/0x1c0
Oct 13 22:05:43 localhost kernel: [185641.096174]  [<c0176dd0>] ? autoremove_wake_function+0x0/0x50
Oct 13 22:05:43 localhost kernel: [185641.096177]  [<c02fb270>] ? kjournald2+0x0/0x1c0
Oct 13 22:05:43 localhost kernel: [185641.096180]  [<c0176864>] kthread+0x74/0x80
Oct 13 22:05:43 localhost kernel: [185641.096183]  [<c01767f0>] ? kthread+0x0/0x80
Oct 13 22:05:43 localhost kernel: [185641.096187]  [<c010b0fe>] kernel_thread_helper+0x6/0x10
Oct 13 22:05:43 localhost kernel: [185641.096194] INFO: task java:11610 blocked for more than 120 seconds.
<a few more logs cut due to size limits>
```

---

### Post by CharlesA on 2011-10-15
It looks like java is causing the machine to hang. Are you running a web server?

---

### Post by davidparks21 on 2011-10-15
It is running a java web application which consists of Jetty and a Spring based web app.

Is there anything more than just "java caused it" that we can understand from these logs? 

I was very surprised that SSH was unresponsive as well, and for such a substantial amount of time. It doesn't seem like a "java" issue should have such wide reaching effects.

I'm running the basic JVM obtained with an "apt-get install openjdk-6-jdk". Version 1.6.0_22

---

### Post by CharlesA on 2011-10-15
It just sounds like java is eating up too much of the cpu or of memory and then being killed.

---

### Post by davidparks21 on 2011-10-16
Interesting. The webapp didn't seem to have any issue, I didn't note anything special in the logs and it was fully operational at the same time that SSH came back to life. 

I can't think of anything else running under Java on the system.

I did see at least one other inconclusive forum discussion somewhere with the same sort of problem.

Well, I'll have monitoring on both the webapp and ssh up shortly and see if it repeats its self. 

Scary not to know why it happened. Thanks for the thoughts on it so far!

---

