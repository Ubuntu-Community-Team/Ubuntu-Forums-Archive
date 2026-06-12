---
title: "BUG: unable to handle kernel paging request at ffffc90216ee1388"
date: 2011-05-09
forum: Server Platforms
---

### Post by larsponken on 2011-05-09
Yesterday evening server became unresponsive and this is what shows in syslog:

```
May  8 22:32:02 dhcp44 kernel: [476280.263685] BUG: unable to handle kernel paging request at ffffc90216ee1388
May  8 22:32:02 dhcp44 kernel: [476280.263694] IP: [<ffffffff812a1c36>] generic_make_request+0xe6/0x4f0
May  8 22:32:02 dhcp44 kernel: [476280.263704] PGD 21fc1a067 PUD 0 
May  8 22:32:02 dhcp44 kernel: [476280.263709] Oops: 0000 [#1] SMP 
May  8 22:32:02 dhcp44 kernel: [476280.263714] last sysfs file: /sys/devices/pci0000:00/0000:00:19.0/irq
May  8 22:32:02 dhcp44 kernel: [476280.263718] CPU 6 
May  8 22:32:02 dhcp44 kernel: [476280.263721] Modules linked in: binfmt_misc vboxnetadp vboxnetflt vboxdrv ipt_REJECT ipt_LOG xt_limit xt_tcpudp ipt_addrtype fbcon tileblit font bitblit softcursor vga16fb vgastate xt_state snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi ip6table_filter ip6_tables snd_rawmidi radeon snd_seq_midi_event ttm snd_seq drm_kms_helper snd_timer snd_seq_device drm i2c_algo_bit lp ppdev snd dell_wmi soundcore parport_pc parport psmouse dcdbas serio_raw snd_page_alloc nf_nat_irc nf_conntrack_irc nf_nat_ftp nf_nat nf_conntrack_ipv4 nf_defrag_ipv4 nf_conntrack_ftp nf_conntrack iptable_filter ip_tables x_tables dm_raid45 ahci e1000e xor
May  8 22:32:02 dhcp44 kernel: [476280.263793] Pid: 1084, comm: flush-251:2 Not tainted 2.6.32-31-server #61-Ubuntu OptiPlex 980                 
May  8 22:32:02 dhcp44 kernel: [476280.263797] RIP: 0010:[<ffffffff812a1c36>]  [<ffffffff812a1c36>] generic_make_request+0xe6/0x4f0
May  8 22:32:02 dhcp44 kernel: [476280.263804] RSP: 0018:ffff88020a02f640  EFLAGS: 00010202
May  8 22:32:02 dhcp44 kernel: [476280.263808] RAX: ffff88020c65dc00 RBX: ffff8800d85ca000 RCX: 0000000000000000
May  8 22:32:02 dhcp44 kernel: [476280.263811] RDX: ffff88020c65e258 RSI: ffff8800d85ca000 RDI: ffffc90216ee1380
May  8 22:32:02 dhcp44 kernel: [476280.263815] RBP: ffff88020a02f700 R08: ffff8800091925a0 R09: 00000000000000c0
May  8 22:32:02 dhcp44 kernel: [476280.263819] R10: 0000000000000000 R11: 0000000000000000 R12: 0000000000000001
May  8 22:32:02 dhcp44 kernel: [476280.263822] R13: ffff8800d85ca000 R14: 0000000000000008 R15: 0000000000000001
May  8 22:32:02 dhcp44 kernel: [476280.263827] FS:  0000000000000000(0000) GS:ffff880009180000(0000) knlGS:0000000000000000
May  8 22:32:02 dhcp44 kernel: [476280.263831] CS:  0010 DS: 0018 ES: 0018 CR0: 000000008005003b
May  8 22:32:02 dhcp44 kernel: [476280.263834] CR2: ffffc90216ee1388 CR3: 0000000001001000 CR4: 00000000000026e0
May  8 22:32:02 dhcp44 kernel: [476280.263838] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
May  8 22:32:02 dhcp44 kernel: [476280.263842] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
May  8 22:32:02 dhcp44 kernel: [476280.263846] Process flush-251:2 (pid: 1084, threadinfo ffff88020a02e000, task ffff88020c65dc00)
May  8 22:32:02 dhcp44 kernel: [476280.263850] Stack:
May  8 22:32:02 dhcp44 kernel: [476280.263852]  ffff88020a02f6a8 ffff8802172e5510 ffff88020a02f660 ffffffff810f8475
May  8 22:32:02 dhcp44 kernel: [476280.263858] <0> ffff88020c65e258 ffff88020c65dc00 ffff88020c65dc00 0000000000000016
May  8 22:32:02 dhcp44 kernel: [476280.263864] <0> ffff88020c65dc00 0000001000000037 ffff8801f821caf0 000000000000001f
May  8 22:32:02 dhcp44 kernel: [476280.263871] Call Trace:
May  8 22:32:02 dhcp44 kernel: [476280.263879]  [<ffffffff810f8475>] ? mempool_alloc_slab+0x15/0x20
May  8 22:32:02 dhcp44 kernel: [476280.263885]  [<ffffffff812a20c0>] submit_bio+0x80/0x110
May  8 22:32:02 dhcp44 kernel: [476280.263892]  [<ffffffff8116f509>] submit_bh+0xf9/0x140
May  8 22:32:02 dhcp44 kernel: [476280.263898]  [<ffffffff81171430>] __block_write_full_page+0x1d0/0x3b0
May  8 22:32:02 dhcp44 kernel: [476280.263904]  [<ffffffff810f8475>] ? mempool_alloc_slab+0x15/0x20
May  8 22:32:02 dhcp44 kernel: [476280.263910]  [<ffffffff81170cd0>] ? end_buffer_async_write+0x0/0x180
May  8 22:32:02 dhcp44 kernel: [476280.263918]  [<ffffffff811e1b00>] ? noalloc_get_block_write+0x0/0x60
May  8 22:32:02 dhcp44 kernel: [476280.263924]  [<ffffffff811e1b00>] ? noalloc_get_block_write+0x0/0x60
May  8 22:32:02 dhcp44 kernel: [476280.263930]  [<ffffffff81171f40>] block_write_full_page_endio+0xe0/0x120
May  8 22:32:02 dhcp44 kernel: [476280.263937]  [<ffffffff811dceb0>] ? ext4_bh_delay_or_unwritten+0x0/0x30
May  8 22:32:02 dhcp44 kernel: [476280.263943]  [<ffffffff81171f95>] block_write_full_page+0x15/0x20
May  8 22:32:02 dhcp44 kernel: [476280.263948]  [<ffffffff811dfa38>] ext4_writepage+0xd8/0x2a0
May  8 22:32:02 dhcp44 kernel: [476280.263954]  [<ffffffff811ddf0c>] mpage_da_submit_io+0x14c/0x1c0
May  8 22:32:02 dhcp44 kernel: [476280.263960]  [<ffffffff811e2f78>] __mpage_da_writepage+0x188/0x1a0
May  8 22:32:02 dhcp44 kernel: [476280.263965]  [<ffffffff810ff797>] write_cache_pages+0x1d7/0x3e0
May  8 22:32:02 dhcp44 kernel: [476280.263970]  [<ffffffff811e2df0>] ? __mpage_da_writepage+0x0/0x1a0
May  8 22:32:02 dhcp44 kernel: [476280.263975]  [<ffffffff811e297a>] ext4_da_writepages+0x2ba/0x620
May  8 22:32:02 dhcp44 kernel: [476280.263981]  [<ffffffff810ff9f1>] do_writepages+0x21/0x40
May  8 22:32:02 dhcp44 kernel: [476280.263986]  [<ffffffff81168b16>] writeback_single_inode+0xf6/0x3d0
May  8 22:32:02 dhcp44 kernel: [476280.263992]  [<ffffffff81169245>] writeback_sb_inodes+0x195/0x280
May  8 22:32:02 dhcp44 kernel: [476280.263997]  [<ffffffff81169a60>] writeback_inodes_wb+0xa0/0x1b0
May  8 22:32:02 dhcp44 kernel: [476280.264002]  [<ffffffff81169dab>] wb_writeback+0x23b/0x2a0
May  8 22:32:02 dhcp44 kernel: [476280.264008]  [<ffffffff81077bbc>] ? lock_timer_base+0x3c/0x70
May  8 22:32:02 dhcp44 kernel: [476280.264014]  [<ffffffff81169f8c>] wb_do_writeback+0x17c/0x190
May  8 22:32:02 dhcp44 kernel: [476280.264019]  [<ffffffff81077cd0>] ? process_timeout+0x0/0x10
May  8 22:32:02 dhcp44 kernel: [476280.264024]  [<ffffffff81169ff3>] bdi_writeback_task+0x53/0xf0
May  8 22:32:02 dhcp44 kernel: [476280.264030]  [<ffffffff81111456>] bdi_start_fn+0x86/0x100
May  8 22:32:02 dhcp44 kernel: [476280.264035]  [<ffffffff811113d0>] ? bdi_start_fn+0x0/0x100
May  8 22:32:02 dhcp44 kernel: [476280.264041]  [<ffffffff81085c76>] kthread+0x96/0xa0
May  8 22:32:02 dhcp44 kernel: [476280.264047]  [<ffffffff810141ea>] child_rip+0xa/0x20
May  8 22:32:02 dhcp44 kernel: [476280.264053]  [<ffffffff81085be0>] ? kthread+0x0/0xa0
May  8 22:32:02 dhcp44 kernel: [476280.264057]  [<ffffffff810141e0>] ? child_rip+0x0/0x20
May  8 22:32:02 dhcp44 kernel: [476280.264060] Code: 06 00 00 48 83 7b 08 00 0f 84 c7 01 00 00 48 c7 43 08 00 00 00 00 44 8b 73 30 41 c1 ee 09 45 85 f6 0f 84 9e 01 00 00 48 8b 7b 10 <48> 8b 47 08 48 8b 40 68 48 c1 f8 09 48 85 c0 74 1b 44 89 f2 48 
May  8 22:32:02 dhcp44 kernel: [476280.264106] RIP  [<ffffffff812a1c36>] generic_make_request+0xe6/0x4f0
May  8 22:32:02 dhcp44 kernel: [476280.264112]  RSP <ffff88020a02f640>
May  8 22:32:02 dhcp44 kernel: [476280.264114] CR2: ffffc90216ee1388
May  8 22:32:02 dhcp44 kernel: [476280.264118] ---[ end trace e8eca076d193e9c1 ]---
```What happened?  Anyone?

---

### Post by CyberBob on 2011-10-24
I've been having the same issues recently.  Any resolution?

```

```Oct 24 09:00:16 solimeno kernel: [ 6848.483274] BUG: unable to handle kernel paging request at 002673c0
Oct 24 09:00:16 solimeno kernel: [ 6848.483707] IP: [<c0202494>] mem_cgroup_del_lru_list+0x34/0x80
Oct 24 09:00:16 solimeno kernel: [ 6848.483982] *pde = 00000000
Oct 24 09:00:16 solimeno kernel: [ 6848.484021] Oops: 0000 [#1] SMP
Oct 24 09:00:16 solimeno kernel: [ 6848.484021] last sysfs file: /sys/devices/virtual/sound/timer/uevent
Oct 24 09:00:16 solimeno kernel: [ 6848.484021] Modules linked in: quota_v2 quota_tree snd_via82xx gameport snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_page_alloc snd_mpu401_uart snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq fbcon tileblit snd_timer font snd_seq_device bitblit softcursor snd vga16fb via_agp ppdev soundcore agpgart vgastate parport_pc i2c_viapro psmouse shpchp lp parport raid10 raid456 async_raid6_recov async_pq raid6_pq async_xor xor async_memcpy async_tx 8139too raid1 8139cp mii sata_via pata_via raid0 multipath linear
Oct 24 09:00:16 solimeno kernel: [ 6848.484021]
Oct 24 09:00:16 solimeno kernel: [ 6848.484021] Pid: 4005, comm: apache2 Not tainted (2.6.32-27-generic #49-Ubuntu) MS-7211
Oct 24 09:00:16 solimeno kernel: [ 6848.484021] EIP: 0060:[<c0202494>] EFLAGS: 00010086 CPU: 0
Oct 24 09:00:16 solimeno kernel: [ 6848.484021] EIP is at mem_cgroup_del_lru_list+0x34/0x80
Oct 24 09:00:16 solimeno kernel: [ 6848.484021] EAX: c1a66d04 EBX: 00000001 ECX: e6828c00 EDX: 002673c0
Oct 24 09:00:16 solimeno kernel: [ 6848.484021] ESI: 00000001 EDI: c079ac60 EBP: def9fd3c ESP: def9fd34
Oct 24 09:00:16 solimeno kernel: [ 6848.484021]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
Oct 24 09:00:16 solimeno kernel: [ 6848.484021] Process apache2 (pid: 4005, ti=def9e000 task=dd9c72c0 task.ti=def9e000)
Oct 24 09:00:16 solimeno kernel: [ 6848.484021] Stack:
Oct 24 09:00:16 solimeno kernel: [ 6848.484021]  c108f3a0 00000001 def9fd58 c01d3678 00000286 c079b080 c108f3a0 22af5000
Oct 24 09:00:16 solimeno kernel: [ 6848.484021] <0> def9fdf8 def9fd64 c01f1fe2 defaebd4 def9fdb4 c01e42c8 c1805208 00000006
Oct 24 09:00:16 solimeno kernel: [ 6848.484021] <0> 00000000 00000000 00000282 c1803050 0471d067 00000000 00000000 ffffff00
Oct 24 09:00:16 solimeno kernel: [ 6848.484021] Call Trace:
Oct 24 09:00:16 solimeno kernel: [ 6848.484021]  [<c01d3678>] ? put_page+0xc8/0x120
Oct 24 09:00:16 solimeno kernel: [ 6848.484021]  [<c01f1fe2>] ? free_page_and_swap_cache+0x22/0x50
Oct 24 09:00:16 solimeno kernel: [ 6848.484021]  [<c01e42c8>] ? zap_pte_range+0x368/0x3f0
Oct 24 09:00:16 solimeno kernel: [ 6848.484021]  [<c01e5ca6>] ? unmap_vmas+0x186/0x350
Oct 24 09:00:16 solimeno kernel: [ 6848.484021]  [<c01ea7b0>] ? exit_mmap+0xa0/0x160
Oct 24 09:00:16 solimeno kernel: [ 6848.484021]  [<c014aba7>] ? mmput+0x37/0xd0
Oct 24 09:00:16 solimeno kernel: [ 6848.484021]  [<c0150672>] ? exit_mm+0xe2/0x120

---

