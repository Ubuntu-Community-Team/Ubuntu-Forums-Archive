---
title: "Can someone help me interpret this?  jbd2 task blocking"
date: 2014-06-08
forum: Server Platforms
---

### Post by MakOwner on 2014-06-08
I'm copying data from an NFS mount onto the local ext4 filesystem when this happens.
After a message like this and the 120 seconds or so of block, the data transfer completes and subsequent filesystem and file comparisons pass.



```

[ 4560.576044] INFO: task jbd2/md7-8:6846 blocked for more than 120 seconds.
[ 4560.608634] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[ 4560.625709] jbd2/md7-8      D ffff8801ff9104e0     0  6846      2 0x00000000
[ 4560.625719]  ffff88018421bca8 0000000000000046 ffff88020fc13ec0 ffff88020fd13ec0
[ 4560.625724]  ffff88018421bfd8 ffff88018421bfd8 ffff88018421bfd8 0000000000013ec0
[ 4560.625729]  ffff880204130000 ffff8802001c0000 ffff88018421bcb8 ffff88018421bdc0
[ 4560.625738] Call Trace:
[ 4560.625754]  [<ffffffff816f6729>] schedule+0x29/0x70
[ 4560.625760]  [<ffffffff81291184>] jbd2_journal_commit_transaction+0x1b4/0x13c0
[ 4560.625766]  [<ffffffff8108e54a>] ? finish_task_switch+0x4a/0xf0
[ 4560.625771]  [<ffffffff81045cd9>] ? default_spin_lock_flags+0x9/0x10
[ 4560.625776]  [<ffffffff816f78ee>] ? _raw_spin_lock_irqsave+0x2e/0x40
[ 4560.625781]  [<ffffffff8107fec0>] ? add_wait_queue+0x60/0x60
[ 4560.625785]  [<ffffffff812964b8>] kjournald2+0xb8/0x240
[ 4560.625789]  [<ffffffff8107fec0>] ? add_wait_queue+0x60/0x60
[ 4560.625793]  [<ffffffff81296400>] ? commit_timeout+0x10/0x10
[ 4560.625797]  [<ffffffff8107f300>] kthread+0xc0/0xd0
[ 4560.625801]  [<ffffffff8107f240>] ? flush_kthread_worker+0xb0/0xb0
[ 4560.625805]  [<ffffffff8170042c>] ret_from_fork+0x7c/0xb0
[ 4560.625809]  [<ffffffff8107f240>] ? flush_kthread_worker+0xb0/0xb0
[ 4560.625813] INFO: task mc:6879 blocked for more than 120 seconds.
[ 4560.642769] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[ 4560.660113] mc              D ffff8801ff9104e0     0  6879   6831 0x00000000
[ 4560.660118]  ffff88019969f8d0 0000000000000086 ffff88020fffcb08 ffff88020fd13ec0
[ 4560.660127]  ffff88019969ffd8 ffff88019969ffd8 ffff88019969ffd8 0000000000013ec0
[ 4560.660131]  ffff880204119740 ffff880200688000 0000000000000001 ffff880200688000
[ 4560.660140] Call Trace:
[ 4560.660146]  [<ffffffff816f6729>] schedule+0x29/0x70
[ 4560.660158]  [<ffffffff816f753d>] rwsem_down_failed_common+0xcd/0x170
[ 4560.660162]  [<ffffffff816f7615>] rwsem_down_read_failed+0x15/0x17
[ 4560.660172]  [<ffffffff813626f4>] call_rwsem_down_read_failed+0x14/0x30
[ 4560.660175]  [<ffffffff816f5a04>] ? down_read+0x24/0x2b
[ 4560.660184]  [<ffffffff8123b771>] ext4_da_map_blocks+0x71/0x1a0
[ 4560.660188]  [<ffffffff8123b8de>] ext4_da_get_block_prep+0x3e/0xa0
[ 4560.660197]  [<ffffffff811d182e>] __block_write_begin+0x1ae/0x4e0
[ 4560.660201]  [<ffffffff8123b8a0>] ? ext4_da_map_blocks+0x1a0/0x1a0
[ 4560.660210]  [<ffffffff811363cf>] ? grab_cache_page_write_begin+0x8f/0xf0
[ 4560.660215]  [<ffffffff8123f409>] ext4_da_write_begin+0xd9/0x270
[ 4560.660221]  [<ffffffff81241961>] ? ext4_da_write_end+0xc1/0x300
[ 4560.660225]  [<ffffffff8113573a>] generic_perform_write+0xca/0x210
[ 4560.660234]  [<ffffffff811c7650>] ? __mark_inode_dirty+0x40/0x2a0
[ 4560.660238]  [<ffffffff811358dd>] generic_file_buffered_write+0x5d/0x90
[ 4560.660245]  [<ffffffff811374c6>] __generic_file_aio_write+0x1b6/0x3b0
[ 4560.660250]  [<ffffffff8113773f>] generic_file_aio_write+0x7f/0x100
[ 4560.660257]  [<ffffffff81237de3>] ext4_file_write+0x93/0xe0
[ 4560.660262]  [<ffffffff8119c4c3>] do_sync_write+0xa3/0xe0
[ 4560.660271]  [<ffffffff810921a0>] ? try_to_wake_up+0x200/0x200
[ 4560.660275]  [<ffffffff8119cb63>] vfs_write+0xb3/0x180
[ 4560.660283]  [<ffffffff8119cea2>] sys_write+0x52/0xa0
[ 4560.660287]  [<ffffffff817004dd>] system_call_fastpath+0x1a/0x1f

```

---

