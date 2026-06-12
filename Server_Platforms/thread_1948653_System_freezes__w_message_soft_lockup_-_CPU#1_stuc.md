---
title: "System freezes  w/ message soft lockup - CPU#1 stuck for 61s!)"
date: 2012-03-28
forum: Server Platforms
---

### Post by zeedee on 2012-03-28
Hi all,

every 2 or 3 months my system freezes and I don't have any clue why but right before the system denies access it prints lines like "BUG: soft lockup - CPU#1 stuck for 61s!"

Below there's some information about the system and output right before I have to reset.

Can somebody tell me what's going on here, please?

Thanks for any kind of help.

Cheers,

Chris


```
$ lsb_release -r
Release:	10.04
```

```
$ uname -a
Linux xxx.yyy.zzz 2.6.32-40-server #87-Ubuntu SMP Tue Mar 6 02:10:02 UTC 2012 x86_64 GNU/Linux
```

```
[389134.783752]  [<ffffffff81013172>] ? system_call_fastpath+0x16/0x1b
[389135.851251] BUG: soft lockup - CPU#1 stuck for 61s! [sw-collectd:2746]
[389135.851251] Modules linked in: iptable_nat nf_nat ip6table_mangle iptable_mangle ipt_REJECT xt_tcpudp nf_conntrack_ipv4 nf_defrag_ipv4 xt_state nf_conntrack ip6table_filter ip6_tables iptable_filter ip_tables x_tables ib_iser rdma_cm ib_cm iw_cm ib_sa ib_mad ib_core ib_addr iscsi_tcp libiscsi_tcp libiscsi scsi_transport_iscsi dm_crypt edac_core edac_mce_amd i2c_piix4 e1000e serio_raw pata_atiixp shpchp lp parport raid10 raid456 async_pq async_xor xor async_memcpy async_raid6_recov raid6_pq async_tx raid0 multipath linear raid1 fbcon tileblit font bitblit softcursor vga16fb vgastate radeon ttm drm_kms_helper drm i2c_algo_bit ahci
[389135.851251] CPU 1:
[389135.851251] Modules linked in: iptable_nat nf_nat ip6table_mangle iptable_mangle ipt_REJECT xt_tcpudp nf_conntrack_ipv4 nf_defrag_ipv4 xt_state nf_conntrack ip6table_filter ip6_tables iptable_filter ip_tables x_tables ib_iser rdma_cm ib_cm iw_cm ib_sa ib_mad ib_core ib_addr iscsi_tcp libiscsi_tcp libiscsi scsi_transport_iscsi dm_crypt edac_core edac_mce_amd i2c_piix4 e1000e serio_raw pata_atiixp shpchp lp parport raid10 raid456 async_pq async_xor xor async_memcpy async_raid6_recov raid6_pq async_tx raid0 multipath linear raid1 fbcon tileblit font bitblit softcursor vga16fb vgastate radeon ttm drm_kms_helper drm i2c_algo_bit ahci
[389135.851251] Pid: 2746, comm: sw-collectd Tainted: G      D    2.6.32-39-server #86-Ubuntu MS-96B3
[389135.851251] RIP: 0010:[<ffffffff810397f9>]  [<ffffffff810397f9>] __ticket_spin_lock+0x19/0x20
[389135.851251] RSP: 0018:ffff8801fab05b38  EFLAGS: 00000293
[389135.851251] RAX: 0000000000004259 RBX: ffff8801fab05b38 RCX: 0000000000000034
[389135.851251] RDX: 0000000000004257 RSI: ffff88021266d310 RDI: ffff880214b7414c
[389135.851251] RBP: ffffffff81013c6e R08: 2010000000000000 R09: fdcf99b189acc402
[389135.851251] R10: ffff88021320fe00 R11: 0000000000000003 R12: ffff88000910fe70
[389135.851251] R13: ffff88000918fb80 R14: 00000000000003ff R15: 0000000000015e00
[389135.851251] FS:  00007f8791dc8700(0000) GS:ffff880009080000(0000) knlGS:00000000f750b6d0
[389135.851251] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
[389135.851251] CR2: 00007f8798200000 CR3: 00000001faad0000 CR4: 00000000000006e0
[389135.851251] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[389135.851251] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[389135.851251] Call Trace:
[389135.851251]  [<ffffffff8156072e>] ? _spin_lock+0xe/0x20
[389135.851251]  [<ffffffff81216f54>] ? do_get_write_access+0x4b4/0x5d0
[389135.851251]  [<ffffffff811707c7>] ? __getblk+0x27/0x50
[389135.851251]  [<ffffffff81217201>] ? journal_get_write_access+0x31/0x50
[389135.851251]  [<ffffffff811ca0cd>] ? __ext3_journal_get_write_access+0x2d/0x60
[389135.851251]  [<ffffffff811bbcfb>] ? ext3_reserve_inode_write+0x7b/0xa0
[389135.851251]  [<ffffffff811bbd4b>] ? ext3_mark_inode_dirty+0x2b/0x50
[389135.851251]  [<ffffffff811bbef1>] ? ext3_dirty_inode+0x61/0xa0
[389135.851251]  [<ffffffff81169f22>] ? __mark_inode_dirty+0x42/0x1e0
[389135.851251]  [<ffffffff8115dd65>] ? touch_atime+0x135/0x180
[389135.851251]  [<ffffffff810f615d>] ? generic_file_mmap+0x5d/0x60
[389135.851251]  [<ffffffff8111d1c4>] ? mmap_region+0x404/0x590
[389135.851251]  [<ffffffff8111d685>] ? do_mmap_pgoff+0x335/0x380
[389135.851251]  [<ffffffff8110f0b4>] ? sys_mmap_pgoff+0x1d4/0x2a0
[389135.851251]  [<ffffffff810f9c87>] ? sys_fadvise64_64+0x77/0x210
[389135.851251]  [<ffffffff81017ac9>] ? sys_mmap+0x29/0x30
[389135.851251]  [<ffffffff81013172>] ? system_call_fastpath+0x16/0x1b
[389150.882502] BUG: soft lockup - CPU#2 stuck for 61s! [postgres:1129]
[389150.882502] Modules linked in: iptable_nat nf_nat ip6table_mangle iptable_mangle ipt_REJECT xt_tcpudp nf_conntrack_ipv4 nf_defrag_ipv4 xt_state nf_conntrack ip6table_filter ip6_tables iptable_filter ip_tables x_tables ib_iser rdma_cm ib_cm iw_cm ib_sa ib_mad ib_core ib_addr iscsi_tcp libiscsi_tcp libiscsi scsi_transport_iscsi dm_crypt edac_core edac_mce_amd i2c_piix4 e1000e serio_raw pata_atiixp shpchp lp parport raid10 raid456 async_pq async_xor xor async_memcpy async_raid6_recov raid6_pq async_tx raid0 multipath linear raid1 fbcon tileblit font bitblit softcursor vga16fb vgastate radeon ttm drm_kms_helper drm i2c_algo_bit ahci
[389150.882502] CPU 2:
[389150.882502] Modules linked in: iptable_nat nf_nat ip6table_mangle iptable_mangle ipt_REJECT xt_tcpudp nf_conntrack_ipv4 nf_defrag_ipv4 xt_state nf_conntrack ip6table_filter ip6_tables iptable_filter ip_tables x_tables ib_iser rdma_cm ib_cm iw_cm ib_sa ib_mad ib_core ib_addr iscsi_tcp libiscsi_tcp libiscsi scsi_transport_iscsi dm_crypt edac_core edac_mce_amd i2c_piix4 e1000e serio_raw pata_atiixp shpchp lp parport raid10 raid456 async_pq async_xor xor async_memcpy async_raid6_recov raid6_pq async_tx raid0 multipath linear raid1 fbcon tileblit font bitblit softcursor vga16fb vgastate radeon ttm drm_kms_helper drm i2c_algo_bit ahci
[389150.882502] Pid: 1129, comm: postgres Tainted: G      D    2.6.32-39-server #86-Ubuntu MS-96B3
[389150.882502] RIP: 0010:[<ffffffff810397f7>]  [<ffffffff810397f7>] __ticket_spin_lock+0x17/0x20
[389150.882502] RSP: 0018:ffff8801fa999a18  EFLAGS: 00000297
[389150.882502] RAX: 000000000000425b RBX: ffff8801fa999a18 RCX: 0000000000000034
[389150.882502] RDX: 0000000000004257 RSI: ffff88020c78f850 RDI: ffff880214b7414c
[389150.882502] RBP: ffffffff81013c6e R08: a010000000000000 R09: fdd5878ace361402
[389150.882502] R10: ffff88021320fe00 R11: 0000000000000246 R12: ffff8802170b1330
[389150.882502] R13: 0000000000000002 R14: 000280da65747300 R15: 0000000000000001
[389150.882502] FS:  00007f9c6a4d8720(0000) GS:ffff880009100000(0000) knlGS:00000000f750b6d0
[389150.882502] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
[389150.882502] CR2: 00007f9c6a4f3000 CR3: 00000001fa8e8000 CR4: 00000000000006e0
[389150.882502] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[389150.882502] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[389150.882502] Call Trace:
[389150.882502]  [<ffffffff8156072e>] ? _spin_lock+0xe/0x20
[389150.882502]  [<ffffffff81216f54>] ? do_get_write_access+0x4b4/0x5d0
[389150.882502]  [<ffffffff81217201>] ? journal_get_write_access+0x31/0x50
[389150.882502]  [<ffffffff811ca0cd>] ? __ext3_journal_get_write_access+0x2d/0x60
[389150.882502]  [<ffffffff811bbcfb>] ? ext3_reserve_inode_write+0x7b/0xa0
[389150.882502]  [<ffffffff811bbd4b>] ? ext3_mark_inode_dirty+0x2b/0x50
[389150.882502]  [<ffffffff811bbef1>] ? ext3_dirty_inode+0x61/0xa0
[389150.882502]  [<ffffffff81169f22>] ? __mark_inode_dirty+0x42/0x1e0
[389150.882502]  [<ffffffff8115dd65>] ? touch_atime+0x135/0x180
[389150.882502]  [<ffffffff810f7938>] ? T.811+0x2b8/0x410
[389150.882502]  [<ffffffff810f7b46>] ? generic_file_aio_read+0xb6/0x1d0
[389150.882502]  [<ffffffff81146d1a>] ? do_sync_read+0xfa/0x140
[389150.882502]  [<ffffffff81086200>] ? autoremove_wake_function+0x0/0x40
[389150.882502]  [<ffffffff8111d685>] ? do_mmap_pgoff+0x335/0x380
[389150.882502]  [<ffffffff81256226>] ? security_file_permission+0x16/0x20
[389150.882502]  [<ffffffff811475d5>] ? vfs_read+0xb5/0x1a0
[389150.882502]  [<ffffffff81147791>] ? sys_read+0x51/0x80
[389150.882502]  [<ffffffff81013172>] ? system_call_fastpath+0x16/0x1b
[389198.130002] BUG: soft lockup - CPU#0 stuck for 61s! [rsyslogd:21258]
[389198.130002] Modules linked in: iptable_nat nf_nat ip6table_mangle iptable_mangle ipt_REJECT xt_tcpudp nf_conntrack_ipv4 nf_defrag_ipv4 xt_state nf_conntrack ip6table_filter ip6_tables iptable_filter ip_tables x_tables ib_iser rdma_cm ib_cm iw_cm ib_sa ib_mad ib_core ib_addr iscsi_tcp libiscsi_tcp libiscsi scsi_transport_iscsi dm_crypt edac_core edac_mce_amd i2c_piix4 e1000e serio_raw pata_atiixp shpchp lp parport raid10 raid456 async_pq async_xor xor async_memcpy async_raid6_recov raid6_pq async_tx raid0 multipath linear raid1 fbcon tileblit font bitblit softcursor vga16fb vgastate radeon ttm drm_kms_helper drm i2c_algo_bit ahci
[389198.130002] CPU 0:
[389198.130002] Modules linked in: iptable_nat nf_nat ip6table_mangle iptable_mangle ipt_REJECT xt_tcpudp nf_conntrack_ipv4 nf_defrag_ipv4 xt_state nf_conntrack ip6table_filter ip6_tables iptable_filter ip_tables x_tables ib_iser rdma_cm ib_cm iw_cm ib_sa ib_mad ib_core ib_addr iscsi_tcp libiscsi_tcp libiscsi scsi_transport_iscsi dm_crypt edac_core edac_mce_amd i2c_piix4 e1000e serio_raw pata_atiixp shpchp lp parport raid10 raid456 async_pq async_xor xor async_memcpy async_raid6_recov raid6_pq async_tx raid0 multipath linear raid1 fbcon tileblit font bitblit softcursor vga16fb vgastate radeon ttm drm_kms_helper drm i2c_algo_bit ahci
[389198.130002] Pid: 21258, comm: rsyslogd Tainted: G      D    2.6.32-39-server #86-Ubuntu MS-96B3
[389198.130002] RIP: 0010:[<ffffffff810397f7>]  [<ffffffff810397f7>] __ticket_spin_lock+0x17/0x20
[389198.130002] RSP: 0018:ffff8801fabeda18  EFLAGS: 00000297
[389198.130002] RAX: 0000000000004258 RBX: ffff8801fabeda18 RCX: 0000000000000000
[389198.130002] RDX: 0000000000004257 RSI: 0000000000000000 RDI: ffff880214b7414c
[389198.130002] RBP: ffffffff81013c6e R08: ffff8800090129c0 R09: 0000000000000070
[389198.130002] R10: 0000000000000000 R11: ffff8800904fb008 R12: ffff880214b7414c
[389198.130002] R13: ffff880214b74190 R14: ffffffff81214f83 R15: ffff8801fabed9a8
[389198.130002] FS:  00007f7dbfeb7700(0000) GS:ffff880009000000(0000) knlGS:00000000f750b6d0
[389198.130002] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
[389198.130002] CR2: 00007f775f557000 CR3: 000000020cb47000 CR4: 00000000000006f0
[389198.130002] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[389198.130002] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[389198.130002] Call Trace:
[389198.130002]  [<ffffffff8156072e>] ? _spin_lock+0xe/0x20
[389198.130002]  [<ffffffff81216751>] ? journal_dirty_data+0x71/0x270
[389198.130002]  [<ffffffff811708f8>] ? __set_page_dirty+0x88/0xf0
[389198.130002]  [<ffffffff811babd0>] ? ext3_journal_dirty_data+0x20/0x50
[389198.130002]  [<ffffffff811bac25>] ? journal_dirty_data_fn+0x25/0x30
[389198.130002]  [<ffffffff811b9cf7>] ? walk_page_buffers+0x87/0xc0
[389198.130002]  [<ffffffff811bac00>] ? journal_dirty_data_fn+0x0/0x30
[389198.130002]  [<ffffffff811be2a3>] ? ext3_ordered_write_end+0x83/0x170
[389198.130002]  [<ffffffff810f5f32>] ? generic_perform_write+0x122/0x1d0
[389198.130002]  [<ffffffff811c5254>] ? __ext3_journal_stop+0x34/0x60
[389198.130002]  [<ffffffff810f7063>] ? generic_file_buffered_write+0x73/0xd0
[389198.130002]  [<ffffffff810f8660>] ? __generic_file_aio_write+0x240/0x470
[389198.130002]  [<ffffffff810896c1>] ? lock_hrtimer_base+0x31/0x60
[389198.130002]  [<ffffffff810f88ff>] ? generic_file_aio_write+0x6f/0xe0
[389198.130002]  [<ffffffff81146bda>] ? do_sync_write+0xfa/0x140
[389198.130002]  [<ffffffff812bc6b6>] ? rb_erase+0xd6/0x160
[389198.130002]  [<ffffffff81086200>] ? autoremove_wake_function+0x0/0x40
[389198.130002]  [<ffffffff81256226>] ? security_file_permission+0x16/0x20
[389198.130002]  [<ffffffff81146ed8>] ? vfs_write+0xb8/0x1a0
[389198.130002]  [<ffffffff81147711>] ? sys_write+0x51/0x80
[389198.130002]  [<ffffffff81013172>] ? system_call_fastpath+0x16/0x1b
[389201.353752] BUG: soft lockup - CPU#3 stuck for 61s! [mysqld:1137]
[389201.353752] Modules linked in: iptable_nat nf_nat ip6table_mangle iptable_mangle ipt_REJECT xt_tcpudp nf_conntrack_ipv4 nf_defrag_ipv4 xt_state nf_conntrack ip6table_filter ip6_tables iptable_filter ip_tables x_tables ib_iser rdma_cm ib_cm iw_cm ib_sa ib_mad ib_core ib_addr iscsi_tcp libiscsi_tcp libiscsi scsi_transport_iscsi dm_crypt edac_core edac_mce_amd i2c_piix4 e1000e serio_raw pata_atiixp shpchp lp parport raid10 raid456 async_pq async_xor xor async_memcpy async_raid6_recov raid6_pq async_tx raid0 multipath linear raid1 fbcon tileblit font bitblit softcursor vga16fb vgastate radeon ttm drm_kms_helper drm i2c_algo_bit ahci
[389201.353752] CPU 3:
[389201.353752] Modules linked in: iptable_nat nf_nat ip6table_mangle iptable_mangle ipt_REJECT xt_tcpudp nf_conntrack_ipv4 nf_defrag_ipv4 xt_state nf_conntrack ip6table_filter ip6_tables iptable_filter ip_tables x_tables ib_iser rdma_cm ib_cm iw_cm ib_sa ib_mad ib_core ib_addr iscsi_tcp libiscsi_tcp libiscsi scsi_transport_iscsi dm_crypt edac_core edac_mce_amd i2c_piix4 e1000e serio_raw pata_atiixp shpchp lp parport raid10 raid456 async_pq async_xor xor async_memcpy async_raid6_recov raid6_pq async_tx raid0 multipath linear raid1 fbcon tileblit font bitblit softcursor vga16fb vgastate radeon ttm drm_kms_helper drm i2c_algo_bit ahci
[389201.353752] Pid: 1137, comm: mysqld Tainted: G      D    2.6.32-39-server #86-Ubuntu MS-96B3
[389201.353752] RIP: 0010:[<ffffffff810397f7>]  [<ffffffff810397f7>] __ticket_spin_lock+0x17/0x20
[389201.353752] RSP: 0018:ffff8801fa97ba18  EFLAGS: 00000293
[389201.353752] RAX: 000000000000425a RBX: ffff8801fa97ba18 RCX: 0000000000000034
[389201.353752] RDX: 0000000000004257 RSI: ffff8802125570e0 RDI: ffff880214b7414c
[389201.353752] RBP: ffffffff81013c6e R08: c010000000000000 R09: fdcfab13b5543802
[389201.353752] R10: ffff88021320fe00 R11: 0000000000000293 R12: 0000000000000003
[389201.353752] R13: 0000000000000001 R14: 0000000000000001 R15: ffff880009115e68
[389201.353752] FS:  00007f13617e4700(0000) GS:ffff880009180000(0000) knlGS:00000000f750b6d0
[389201.353752] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
[389201.353752] CR2: 00007fa0750d6000 CR3: 00000001fa92d000 CR4: 00000000000006e0
[389201.353752] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[389201.353752] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[389201.353752] Call Trace:
[389201.353752]  [<ffffffff8156072e>] ? _spin_lock+0xe/0x20
[389201.353752]  [<ffffffff81216f54>] ? do_get_write_access+0x4b4/0x5d0
[389201.353752]  [<ffffffff81217201>] ? journal_get_write_access+0x31/0x50
[389201.353752]  [<ffffffff811ca0cd>] ? __ext3_journal_get_write_access+0x2d/0x60
[389201.353752]  [<ffffffff811bbcfb>] ? ext3_reserve_inode_write+0x7b/0xa0
[389201.353752]  [<ffffffff811bbd4b>] ? ext3_mark_inode_dirty+0x2b/0x50
[389201.353752]  [<ffffffff811bbef1>] ? ext3_dirty_inode+0x61/0xa0
[389201.353752]  [<ffffffff81169f22>] ? __mark_inode_dirty+0x42/0x1e0
[389201.353752]  [<ffffffff8115dd65>] ? touch_atime+0x135/0x180
[389201.353752]  [<ffffffff810f7938>] ? T.811+0x2b8/0x410
[389201.353752]  [<ffffffff810f7b46>] ? generic_file_aio_read+0xb6/0x1d0
[389201.353752]  [<ffffffff81146d1a>] ? do_sync_read+0xfa/0x140
[389201.353752]  [<ffffffff8115414b>] ? path_walk+0x7b/0xe0
[389201.353752]  [<ffffffff81086200>] ? autoremove_wake_function+0x0/0x40
[389201.353752]  [<ffffffff81256226>] ? security_file_permission+0x16/0x20
[389201.353752]  [<ffffffff811475d5>] ? vfs_read+0xb5/0x1a0
[389201.353752]  [<ffffffff81147791>] ? sys_read+0x51/0x80
[389201.353752]  [<ffffffff81013172>] ? system_call_fastpath+0x16/0x1b
[389202.421252] BUG: soft lockup - CPU#1 stuck for 61s! [sw-collectd:2746]
[389202.421252] Modules linked in: iptable_nat nf_nat ip6table_mangle iptable_mangle ipt_REJECT xt_tcpudp nf_conntrack_ipv4 nf_defrag_ipv4 xt_state nf_conntrack ip6table_filter ip6_tables iptable_filter ip_tables x_tables ib_iser rdma_cm ib_cm iw_cm ib_sa ib_mad ib_core ib_addr iscsi_tcp libiscsi_tcp libiscsi scsi_transport_iscsi dm_crypt edac_core edac_mce_amd i2c_piix4 e1000e serio_raw pata_atiixp shpchp lp parport raid10 raid456 async_pq async_xor xor async_memcpy async_raid6_recov raid6_pq async_tx raid0 multipath linear raid1 fbcon tileblit font bitblit softcursor vga16fb vgastate radeon ttm drm_kms_helper drm i2c_algo_bit ahci
[389202.421252] CPU 1:
[389202.421252] Modules linked in: iptable_nat nf_nat ip6table_mangle iptable_mangle ipt_REJECT xt_tcpudp nf_conntrack_ipv4 nf_defrag_ipv4 xt_state nf_conntrack ip6table_filter ip6_tables iptable_filter ip_tables x_tables ib_iser rdma_cm ib_cm iw_cm ib_sa ib_mad ib_core ib_addr iscsi_tcp libiscsi_tcp libiscsi scsi_transport_iscsi dm_crypt edac_core edac_mce_amd i2c_piix4 e1000e serio_raw pata_atiixp shpchp lp parport raid10 raid456 async_pq async_xor xor async_memcpy async_raid6_recov raid6_pq async_tx raid0 multipath linear raid1 fbcon tileblit font bitblit softcursor vga16fb vgastate radeon ttm drm_kms_helper drm i2c_algo_bit ahci
[389202.421252] Pid: 2746, comm: sw-collectd Tainted: G      D    2.6.32-39-server #86-Ubuntu MS-96B3
[389202.421252] RIP: 0010:[<ffffffff810397f7>]  [<ffffffff810397f7>] __ticket_spin_lock+0x17/0x20
[389202.421252] RSP: 0018:ffff8801fab05b38  EFLAGS: 00000293
[389202.421252] RAX: 0000000000004259 RBX: ffff8801fab05b38 RCX: 0000000000000034
[389202.421252] RDX: 0000000000004257 RSI: ffff88021266d310 RDI: ffff880214b7414c
[389202.421252] RBP: ffffffff81013c6e R08: 2010000000000000 R09: fdcf99b189acc402
[389202.421252] R10: ffff88021320fe00 R11: 0000000000000003 R12: ffff88000910fe70
[389202.421252] R13: ffff88000918fb80 R14: 00000000000003ff R15: 0000000000015e00
[389202.421252] FS:  00007f8791dc8700(0000) GS:ffff880009080000(0000) knlGS:00000000f750b6d0
[389202.421252] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
[389202.421252] CR2: 00007f8798200000 CR3: 00000001faad0000 CR4: 00000000000006e0
[389202.421252] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[389202.421252] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[389202.421252] Call Trace:
[389202.421252]  [<ffffffff8156072e>] ? _spin_lock+0xe/0x20
[389202.421252]  [<ffffffff81216f54>] ? do_get_write_access+0x4b4/0x5d0
[389202.421252]  [<ffffffff811707c7>] ? __getblk+0x27/0x50
[389202.421252]  [<ffffffff81217201>] ? journal_get_write_access+0x31/0x50
[389202.421252]  [<ffffffff811ca0cd>] ? __ext3_journal_get_write_access+0x2d/0x60
[389202.421252]  [<ffffffff811bbcfb>] ? ext3_reserve_inode_write+0x7b/0xa0
[389202.421252]  [<ffffffff811bbd4b>] ? ext3_mark_inode_dirty+0x2b/0x50
[389202.421252]  [<ffffffff811bbef1>] ? ext3_dirty_inode+0x61/0xa0
[389202.421252]  [<ffffffff81169f22>] ? __mark_inode_dirty+0x42/0x1e0
[389202.421252]  [<ffffffff8115dd65>] ? touch_atime+0x135/0x180
[389202.421252]  [<ffffffff810f615d>] ? generic_file_mmap+0x5d/0x60
[389202.421252]  [<ffffffff8111d1c4>] ? mmap_region+0x404/0x590
[389202.421252]  [<ffffffff8111d685>] ? do_mmap_pgoff+0x335/0x380
[389202.421252]  [<ffffffff8110f0b4>] ? sys_mmap_pgoff+0x1d4/0x2a0
[389202.421252]  [<ffffffff810f9c87>] ? sys_fadvise64_64+0x77/0x210
[389202.421252]  [<ffffffff81017ac9>] ? sys_mmap+0x29/0x30
[389202.421252]  [<ffffffff81013172>] ? system_call_fastpath+0x16/0x1b

```

---

