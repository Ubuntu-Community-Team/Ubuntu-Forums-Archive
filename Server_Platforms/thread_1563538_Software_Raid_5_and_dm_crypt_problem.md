---
title: "Software Raid 5 and dm_crypt problem"
date: 2010-08-29
forum: Server Platforms
---

### Post by boba23 on 2010-08-29
Hey Folks,

I have a freshly created software raid5 using mdadm on Ubuntu Lucid 64bit Server. It consists of 6 Samsung 750GB drives. I am using dm_crypt to encrypt the array. File system is ext4.
Right now I am trying to copy back my data, and now for the second time my copy thread in midnight commander hangs after a few hours with the following trace in dmesg:

[221558.011009] general protection fault: 0000 [#1] SMP
[221558.013171] last sysfs file: /sys/devices/pci0000:00/0000:00:0a.0/0000:02:00.0/irq
[221558.015351] CPU 1
[221558.017521] Modules linked in: snd_hda_codec_atihdmi snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_timer it87 hwmon_vid snd soundcore snd_page_alloc edac_core lp k8temp edac_mce_amd i2c_piix4 parport shpchp sha256_generic cryptd aes_x86_64 aes_generic dm_crypt raid10 raid1 raid0 multipath linear raid456 async_pq async_xor xor async_memcpy async_raid6_recov raid6_pq async_tx fbcon tileblit font bitblit softcursor vga16fb vgastate radeon ttm drm_kms_helper ahci sata_promise pata_atiixp drm i2c_algo_bit r8169 mii
[221558.020638] Pid: 400, comm: md0_raid5 Not tainted 2.6.32-24-server #41-Ubuntu Unknow
[221558.020638] RIP: 0010:[<ffffffff814353b8>]  [<ffffffff814353b8>] clone_endio+0x38/0xe0
[221558.020638] RSP: 0018:ffff880069531c40  EFLAGS: 00010246
[221558.020638] RAX: ffffffffa023f760 RBX: 0000000000000000 RCX: 0100000000000081
[221558.020638] RDX: 0000000000000017 RSI: 0000000000000000 RDI: ffffc9001247e040
[221558.035928] RBP: ffff880069531c70 R08: 0000000000000000 R09: 010000000000282c
[221558.035928] R10: 0000000000000000 R11: 0000000000000001 R12: ffff88000ca0ed80
[221558.035928] R13: ffff88000df85ed0 R14: ffff8800695ca600 R15: ffbf8800116cb348
[221558.035928] FS:  00007fb75e7f4700(0000) GS:ffff880001c40000(0000) knlGS:0000000000000000
[221558.035928] CS:  0010 DS: 0018 ES: 0018 CR0: 000000008005003b
[221558.035928] CR2: 00007f2d10190000 CR3: 0000000053ae8000 CR4: 00000000000006e0
[221558.035928] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[221558.035928] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[221558.035928] Process md0_raid5 (pid: 400, threadinfo ffff880069530000, task ffff88006a08dbc0)
[221558.035928] Stack:
[221558.035928]  ffff88001be85ed8 0000000000000000 0000000000000000 ffff88000ca0ed80
[221558.035928] <0> ffff8800695ca600 ffff88001be85ed8 ffff880069531c80 ffffffff8117159d
[221558.035928] <0> ffff880069531cb0 ffffffffa023d8c9 ffff880069531ca0 ffff88004d8312b0
[221558.035928] Call Trace:
[221558.035928]  [<ffffffff8117159d>] bio_endio+0x1d/0x40
[221558.035928]  [<ffffffffa023d8c9>] crypt_dec_pending+0x69/0x90 [dm_crypt]
[221558.035928]  [<ffffffffa023daa8>] crypt_endio+0x68/0x150 [dm_crypt]
[221558.035928]  [<ffffffff8117159d>] bio_endio+0x1d/0x40
[221558.035928]  [<ffffffffa0200add>] handle_stripe5+0x46d/0x9a0 [raid456]
[221558.035928]  [<ffffffffa0201028>] handle_stripe+0x18/0x30 [raid456]
[221558.035928]  [<ffffffffa0201432>] raid5d+0x202/0x320 [raid456]
[221558.035928]  [<ffffffff814298dc>] md_thread+0x5c/0x130
[221558.035928]  [<ffffffff81085090>] ? autoremove_wake_function+0x0/0x40
[221558.035928]  [<ffffffff81429880>] ? md_thread+0x0/0x130
[221558.035928]  [<ffffffff81084d16>] kthread+0x96/0xa0
[221558.035928]  [<ffffffff810141ea>] child_rip+0xa/0x20
[221558.035928]  [<ffffffff81084c80>] ? kthread+0x0/0xa0
[221558.035928]  [<ffffffff810141e0>] ? child_rip+0x0/0x20
[221558.035928] Code: 89 65 e0 4c 89 6d e8 4c 89 75 f0 4c 89 7d f8 0f 1f 44 00 00 4c 8b 6f 58 49 89 fc 85 f6 89 f3 49 8b 7d 08 4d 8b 7d 00 48 8b 47 08 <4d> 8b 37 48 8b 40 48 75 0e 41 f6 44 24 18 01 ba fb ff ff ff 0f
[221558.035928] RIP  [<ffffffff814353b8>] clone_endio+0x38/0xe0
[221558.035928]  RSP <ffff880069531c40>
[221558.133125] ---[ end trace 29f7fd9a7bbb5a00 ]---

The raid5 array stays ok, no drives get kicked out or anything. I have to reboot though to get the hanging mc process killed. After that my raid5 is still fine. No rebuild or similiar.
Can anybody help me here? Am I having a raid or dmcrypt problem? Or could it be anything else? I am running a AMD 4850e dual core cpu, without a fan, just a massive scythe cooler. Temperatures through lmsensors seem very much ok though.
Any thoughts and ideas would be very much appreciated.

Thanks

boba

---

### Post by diabloa on 2010-12-20
Hi,

I'd be interested to know if you found a solution to your problem as I am experiencing similar errors with a crypted raid5 setup. I'm using Ubuntu Server 10.10 64bit. I cant even get my raid5 to do a full resync after having to restart my system :/ It worked without a problem for at least a month or so. The error also most likely occurs when copying a lot of data to the system.
Setup: 5x 2TB Samsung SATA drives, Intel I3, Zotac H55-ITX WiFi.

```
Dec 20 19:26:04 storage kernel: [ 3762.958925] general protection fault: 0000 [#1] SMP
Dec 20 19:26:04 storage kernel: [ 3762.958959] last sysfs file: /sys/devices/virtual/block/md0/md/array_state
Dec 20 19:26:04 storage kernel: [ 3762.958989] CPU 0
Dec 20 19:26:04 storage kernel: [ 3762.958999] Modules linked in: xts gf128mul cryptd aes_x86_64 aes_generic parport_pc ppdev dm_crypt snd_hda_codec_intelhdmi snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd soundcore snd_page_alloc lp parport raid10 raid1 raid0 multipath linear raid456 async_pq async_xor xor async_memcpy async_raid6_recov raid6_pq async_tx i915 drm_kms_helper drm ahci i2c_algo_bit libahci video e1000e output intel_agp
Dec 20 19:26:04 storage kernel: [ 3762.959305]
Dec 20 19:26:04 storage kernel: [ 3762.959316] Pid: 347, comm: md0_raid5 Not tainted 2.6.35-23-generic #41-Ubuntu To be filled by O.E.M./To Be Filled By O.E.M.
Dec 20 19:26:04 storage kernel: [ 3762.959362] RIP: 0010:[<ffffffffa016182e>]  [<ffffffffa016182e>] xor_sse_5+0x6e/0x3f0 [xor]
Dec 20 19:26:04 storage kernel: [ 3762.959402] RSP: 0018:ffff880068f6bae0  EFLAGS: 00010202
Dec 20 19:26:04 storage kernel: [ 3762.959425] RAX: ffff880037385000 RBX: 000000008005003b RCX: 0000000000000010
Dec 20 19:26:04 storage kernel: [ 3762.959454] RDX: ffff880037386000 RSI: 49241a495bca8000 RDI: 0000000000001000
Dec 20 19:26:04 storage kernel: [ 3762.959483] RBP: ffff880068f6bb30 R08: ffff880037383000 R09: ffff880037382000
Dec 20 19:26:04 storage kernel: [ 3762.959513] R10: 0000000000000100 R11: ffff880068f6bae0 R12: 0000000000000000
Dec 20 19:26:04 storage kernel: [ 3762.959542] R13: 0000000000000004 R14: 0000000000000004 R15: 0000000000000004
Dec 20 19:26:04 storage kernel: [ 3762.959572] FS:  0000000000000000(0000) GS:ffff880001e00000(0000) knlGS:0000000000000000
Dec 20 19:26:04 storage kernel: [ 3762.959604] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Dec 20 19:26:04 storage kernel: [ 3762.959629] CR2: 00007facc5844000 CR3: 000000005940c000 CR4: 00000000000006f0
Dec 20 19:26:04 storage kernel: [ 3762.959659] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Dec 20 19:26:04 storage kernel: [ 3762.959688] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Dec 20 19:26:04 storage kernel: [ 3762.959718] Process md0_raid5 (pid: 347, threadinfo ffff880068f6a000, task ffff880037bf44a0)
Dec 20 19:26:04 storage kernel: [ 3762.959752] Stack:
Dec 20 19:26:04 storage kernel: [ 3762.959762]  0000000000000000 0000000000000000 40e86a0000000000 0000000000000000
Dec 20 19:26:04 storage kernel: [ 3762.959799] <0> 0000000000000000 ffff000000010000 7571636100000001 0000000000657269
Dec 20 19:26:04 storage kernel: [ 3762.959841] <0> ffffffffffffffb6 ffff88006ce12438 ffff880068f6bb40 ffffffffa0161beb
Dec 20 19:26:04 storage kernel: [ 3762.959885] Call Trace:
Dec 20 19:26:04 storage kernel: [ 3762.959900]  [<ffffffffa0161beb>] xor_blocks+0x3b/0x84 [xor]
Dec 20 19:26:04 storage kernel: [ 3762.959926]  [<ffffffffa016810f>] do_sync_xor+0x10f/0x160 [async_xor]
Dec 20 19:26:04 storage kernel: [ 3762.959955]  [<ffffffffa0168516>] async_xor+0x106/0x140 [async_xor]
Dec 20 19:26:04 storage kernel: [ 3762.959982]  [<ffffffffa01685af>] async_xor_val+0x5f/0xf8 [async_xor]
Dec 20 19:26:04 storage kernel: [ 3762.960011]  [<ffffffffa0177e35>] __raid_run_ops+0x6e5/0x7d0 [raid456]
Dec 20 19:26:04 storage kernel: [ 3762.960041]  [<ffffffff810594fb>] ? dequeue_task_fair+0x8b/0x90
Dec 20 19:26:04 storage kernel: [ 3762.960068]  [<ffffffffa0179e38>] handle_stripe5+0x5e8/0x9f0 [raid456]
Dec 20 19:26:04 storage kernel: [ 3762.960097]  [<ffffffffa017a258>] handle_stripe+0x18/0x30 [raid456]
Dec 20 19:26:04 storage kernel: [ 3762.960125]  [<ffffffffa017a66f>] raid5d+0x20f/0x330 [raid456]
Dec 20 19:26:04 storage kernel: [ 3762.960153]  [<ffffffff81036dc9>] ? default_spin_lock_flags+0x9/0x10
Dec 20 19:26:04 storage kernel: [ 3762.960183]  [<ffffffff8144ab3c>] md_thread+0x5c/0x130
Dec 20 19:26:04 storage kernel: [ 3762.960207]  [<ffffffff8107f620>] ? autoremove_wake_function+0x0/0x40
Dec 20 19:26:04 storage kernel: [ 3762.960235]  [<ffffffff8144aae0>] ? md_thread+0x0/0x130
Dec 20 19:26:04 storage kernel: [ 3762.960258]  [<ffffffff8107f0c6>] kthread+0x96/0xa0
Dec 20 19:26:04 storage kernel: [ 3762.960281]  [<ffffffff8100aee4>] kernel_thread_helper+0x4/0x10
Dec 20 19:26:04 storage kernel: [ 3762.960307]  [<ffffffff8107f030>] ? kthread+0x0/0xa0
Dec 20 19:26:04 storage kernel: [ 3762.960329]  [<ffffffff8100aee0>] ? kernel_thread_helper+0x0/0x10
Dec 20 19:26:04 storage kernel: [ 3762.960355] Code: 86 20 01 00 00 eb 16 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 0f 18 82 00 01 00 00 0f $
Dec 20 19:26:04 storage kernel: [ 3762.960625] RIP  [<ffffffffa016182e>] xor_sse_5+0x6e/0x3f0 [xor]
Dec 20 19:26:04 storage kernel: [ 3762.960654]  RSP <ffff880068f6bae0>
Dec 20 19:26:04 storage kernel: [ 3762.968049] ---[ end trace 663f00e0225c49ce ]---

```

---

### Post by boba23 on 2010-12-21
Hey,

well yea, for me it's been a hardware failure. I had one defective stick of ram ;-) maybe you should check your HW too, go run few rounds of memtest86 first to make sure your ram is good.

boba

---

