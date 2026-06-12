---
title: "xfs problem"
date: 2010-06-13
forum: Server Platforms
---

### Post by davidmaxwaterman on 2010-06-13
Hi,

Related to my other issue, having repaired the raid5 array, I am having trouble getting the XFS filesystem working. Below is the /var/log/messages - you can see the messages where the raid finished rebuilding, after which I tried a 'mount'. That resulted in the message 'Killed'. I then ran 'sudo xfs_repair /dev/md2' but this seems to just sit there and 'top' (etc) show no activity at all.

Any ideas?

Max,

```
Jun 13 10:40:19 jeeves kernel: [ 4122.625897] md: md2: resync done.
Jun 13 10:40:19 jeeves kernel: [ 4122.911576] RAID5 conf printout:
Jun 13 10:40:19 jeeves kernel: [ 4122.911587]  --- rd:6 wd:6
Jun 13 10:40:19 jeeves kernel: [ 4122.911593]  disk 0, o:1, dev:sde
Jun 13 10:40:19 jeeves kernel: [ 4122.911598]  disk 1, o:1, dev:sdd
Jun 13 10:40:19 jeeves kernel: [ 4122.911602]  disk 2, o:1, dev:sdg
Jun 13 10:40:19 jeeves kernel: [ 4122.911606]  disk 3, o:1, dev:sdi
Jun 13 10:40:19 jeeves kernel: [ 4122.911610]  disk 4, o:1, dev:sdh
Jun 13 10:40:19 jeeves kernel: [ 4122.911615]  disk 5, o:1, dev:sdj
Jun 13 10:42:35 jeeves kernel: [ 4258.133833] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
Jun 13 10:42:35 jeeves kernel: [ 4258.138381] SGI XFS Quota Management subsystem
Jun 13 10:42:35 jeeves kernel: [ 4258.139146] Filesystem "md2": Disabling barriers, trial barrier write failed
Jun 13 10:42:35 jeeves kernel: [ 4258.139352] XFS mounting filesystem md2
Jun 13 10:42:35 jeeves kernel: [ 4258.315816] Starting XFS recovery on filesystem: md2 (logdev: internal)
Jun 13 10:42:45 jeeves kernel: [ 4268.263275] Pid: 10735, comm: mount Tainted: P           2.6.32-22-generic-pae #33-Ubuntu
Jun 13 10:42:45 jeeves kernel: [ 4268.263281] Call Trace:
Jun 13 10:42:45 jeeves kernel: [ 4268.263331]  [<fc2d4573>] xfs_error_report+0x53/0x60 [xfs]
Jun 13 10:42:45 jeeves kernel: [ 4268.263358]  [<fc2adbba>] ? xfs_free_extent+0xba/0xe0 [xfs]
Jun 13 10:42:45 jeeves kernel: [ 4268.263383]  [<fc2ac0b2>] xfs_free_ag_extent+0x4e2/0x6c0 [xfs]
Jun 13 10:42:45 jeeves kernel: [ 4268.263407]  [<fc2adbba>] ? xfs_free_extent+0xba/0xe0 [xfs]
Jun 13 10:42:45 jeeves kernel: [ 4268.263432]  [<fc2adbba>] xfs_free_extent+0xba/0xe0 [xfs]
Jun 13 10:42:45 jeeves kernel: [ 4268.263466]  [<fc2e6d24>] xlog_recover_process_efi+0x2b4/0x2f0 [xfs]
Jun 13 10:42:45 jeeves kernel: [ 4268.263500]  [<fc2e6dc7>] xlog_recover_process_efis+0x67/0xb0 [xfs]
Jun 13 10:42:45 jeeves kernel: [ 4268.263534]  [<fc2eac7e>] xlog_recover_finish+0x1e/0x100 [xfs]
Jun 13 10:42:45 jeeves kernel: [ 4268.263566]  [<fc2e3f43>] xfs_log_mount_finish+0x23/0x30 [xfs]
Jun 13 10:42:45 jeeves kernel: [ 4268.263600]  [<fc2eeb8a>] xfs_mountfs+0x45a/0x6e0 [xfs]
Jun 13 10:42:45 jeeves kernel: [ 4268.263634]  [<fc2f9c49>] ? kmem_zalloc+0x19/0x50 [xfs]
Jun 13 10:42:45 jeeves kernel: [ 4268.263668]  [<fc2ef534>] ? xfs_mru_cache_create+0x104/0x140 [xfs]
Jun 13 10:42:45 jeeves kernel: [ 4268.263703]  [<fc305350>] xfs_fs_fill_super+0x1c0/0x330 [xfs]
Jun 13 10:42:45 jeeves kernel: [ 4268.263717]  [<c02134b0>] ? set_bdev_super+0x0/0x30
Jun 13 10:42:45 jeeves kernel: [ 4268.263725]  [<c02148f2>] get_sb_bdev+0x162/0x1a0
Jun 13 10:42:45 jeeves kernel: [ 4268.263760]  [<fc305190>] ? xfs_fs_fill_super+0x0/0x330 [xfs]
Jun 13 10:42:45 jeeves kernel: [ 4268.263794]  [<fc303336>] xfs_fs_get_sb+0x26/0x30 [xfs]
Jun 13 10:42:45 jeeves kernel: [ 4268.263828]  [<fc305190>] ? xfs_fs_fill_super+0x0/0x330 [xfs]
Jun 13 10:42:45 jeeves kernel: [ 4268.263835]  [<c0214467>] vfs_kern_mount+0x67/0x170
Jun 13 10:42:45 jeeves kernel: [ 4268.263846]  [<c0228d77>] ? get_fs_type+0x97/0xb0
Jun 13 10:42:45 jeeves kernel: [ 4268.263853]  [<c02145ce>] do_kern_mount+0x3e/0xe0
Jun 13 10:42:45 jeeves kernel: [ 4268.263861]  [<c022be83>] do_mount+0x1c3/0x200
Jun 13 10:42:45 jeeves kernel: [ 4268.263868]  [<c022bf2b>] sys_mount+0x6b/0xa0
Jun 13 10:42:45 jeeves kernel: [ 4268.263876]  [<c0109763>] sysenter_do_call+0x12/0x28
Jun 13 10:42:45 jeeves kernel: [ 4268.263899] Pid: 10735, comm: mount Tainted: P           2.6.32-22-generic-pae #33-Ubuntu
Jun 13 10:42:45 jeeves kernel: [ 4268.263903] Call Trace:
Jun 13 10:42:45 jeeves kernel: [ 4268.263934]  [<fc2d4573>] xfs_error_report+0x53/0x60 [xfs]
Jun 13 10:42:45 jeeves kernel: [ 4268.263967]  [<fc2e6d37>] ? xlog_recover_process_efi+0x2c7/0x2f0 [xfs]
Jun 13 10:42:45 jeeves kernel: [ 4268.264001]  [<fc2f154e>] xfs_trans_cancel+0xce/0xf0 [xfs]
Jun 13 10:42:45 jeeves kernel: [ 4268.264033]  [<fc2e6d37>] ? xlog_recover_process_efi+0x2c7/0x2f0 [xfs]
Jun 13 10:42:45 jeeves kernel: [ 4268.264066]  [<fc2e6d37>] xlog_recover_process_efi+0x2c7/0x2f0 [xfs]
Jun 13 10:42:45 jeeves kernel: [ 4268.264099]  [<fc2e6dc7>] xlog_recover_process_efis+0x67/0xb0 [xfs]
Jun 13 10:42:45 jeeves kernel: [ 4268.264133]  [<fc2eac7e>] xlog_recover_finish+0x1e/0x100 [xfs]
Jun 13 10:42:45 jeeves kernel: [ 4268.264216]  [<fc2e3f43>] xfs_log_mount_finish+0x23/0x30 [xfs]
Jun 13 10:42:45 jeeves kernel: [ 4268.264250]  [<fc2eeb8a>] xfs_mountfs+0x45a/0x6e0 [xfs]
Jun 13 10:42:45 jeeves kernel: [ 4268.264283]  [<fc2f9c49>] ? kmem_zalloc+0x19/0x50 [xfs]
Jun 13 10:42:45 jeeves kernel: [ 4268.264316]  [<fc2ef534>] ? xfs_mru_cache_create+0x104/0x140 [xfs]
Jun 13 10:42:45 jeeves kernel: [ 4268.264350]  [<fc305350>] xfs_fs_fill_super+0x1c0/0x330 [xfs]
Jun 13 10:42:45 jeeves kernel: [ 4268.264360]  [<c02134b0>] ? set_bdev_super+0x0/0x30
Jun 13 10:42:45 jeeves kernel: [ 4268.264367]  [<c02148f2>] get_sb_bdev+0x162/0x1a0
Jun 13 10:42:45 jeeves kernel: [ 4268.264401]  [<fc305190>] ? xfs_fs_fill_super+0x0/0x330 [xfs]
Jun 13 10:42:45 jeeves kernel: [ 4268.264435]  [<fc303336>] xfs_fs_get_sb+0x26/0x30 [xfs]
Jun 13 10:42:45 jeeves kernel: [ 4268.264469]  [<fc305190>] ? xfs_fs_fill_super+0x0/0x330 [xfs]
Jun 13 10:42:45 jeeves kernel: [ 4268.264477]  [<c0214467>] vfs_kern_mount+0x67/0x170
Jun 13 10:42:45 jeeves kernel: [ 4268.264485]  [<c0228d77>] ? get_fs_type+0x97/0xb0
Jun 13 10:42:45 jeeves kernel: [ 4268.264492]  [<c02145ce>] do_kern_mount+0x3e/0xe0
Jun 13 10:42:45 jeeves kernel: [ 4268.264499]  [<c022be83>] do_mount+0x1c3/0x200
Jun 13 10:42:45 jeeves kernel: [ 4268.264506]  [<c022bf2b>] sys_mount+0x6b/0xa0
Jun 13 10:42:45 jeeves kernel: [ 4268.264513]  [<c0109763>] sysenter_do_call+0x12/0x28
Jun 13 10:42:45 jeeves kernel: [ 4268.264522] xfs_force_shutdown(md2,0x8) called from line 1162 of file /build/buildd/linux-2.6.32/fs/xfs/xfs_trans.c.  Return address = 0xfc2f1566
Jun 13 10:42:45 jeeves kernel: [ 4268.264566] XFS: log mount finish failed
Jun 13 10:42:45 jeeves kernel: [ 4268.264734] xfs_force_shutdown(<NULL>,0x8) called from line 566 of file /build/buildd/linux-2.6.32/fs/xfs/xfs_trans_ail.c.  Return address = 0xfc2f2a50
Jun 13 10:42:45 jeeves kernel: [ 4268.264816] *pdpt = 000000001071a001 *pde = 0000000000000000 
Jun 13 10:42:45 jeeves kernel: [ 4268.264839] Modules linked in: xfs exportfs appletalk rfcomm sco bridge stp bnep l2cap bluetooth binfmt_misc kvm_amd kvm raid456 async_raid6_recov async_pq snd_hda_codec_realtek raid6_pq async_xor xor async_memcpy async_tx snd_hda_intel snd_hda_codec snd_hwdep snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq uvcvideo videodev v4l1_compat hid_apple nvidia(P) snd_timer snd_seq_device ppdev fbcon tileblit font bitblit softcursor psmouse joydev sbp2 agpgart vga16fb serio_raw vgastate parport_pc ohci1394 snd k8temp soundcore snd_page_alloc lp i2c_nforce2 parport usbhid hid ieee1394 pata_hpt37x pata_amd sata_nv sata_sil24 forcedeth
Jun 13 10:42:45 jeeves kernel: [ 4268.264957] 
Jun 13 10:42:45 jeeves kernel: [ 4268.264964] Pid: 10735, comm: mount Tainted: P           (2.6.32-22-generic-pae #33-Ubuntu) MS-7250
Jun 13 10:42:45 jeeves kernel: [ 4268.264971] EIP: 0060:[<fc2e4ebe>] EFLAGS: 00210202 CPU: 1
Jun 13 10:42:45 jeeves kernel: [ 4268.265003] EIP is at xfs_log_force_umount+0x1e/0x190 [xfs]
Jun 13 10:42:45 jeeves kernel: [ 4268.265008] EAX: f18ae080 EBX: f18ae080 ECX: ffffef32 EDX: 00000000
Jun 13 10:42:45 jeeves kernel: [ 4268.265013] ESI: 746e656d EDI: 00000000 EBP: f3fbdd1c ESP: f3fbdcfc
Jun 13 10:42:45 jeeves kernel: [ 4268.265019]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
Jun 13 10:42:45 jeeves kernel: [ 4268.265032]  f3fbdd1c fc306bec fc30c71f fc30c735 fc30f120 00000008 f18ae080 00000000
Jun 13 10:42:45 jeeves kernel: [ 4268.265045] <0> f3fbdd50 fc2f9441 00000005 fc30a528 00000000 00000008 00000236 fc30a320
Jun 13 10:42:45 jeeves kernel: [ 4268.265058] <0> fc2f2a50 00000000 f18ae080 f18ae5c0 f18ae5c0 f3fbdd7c fc2f2a50 00000236
Jun 13 10:42:45 jeeves kernel: [ 4268.265107]  [<fc306bec>] ? cmn_err+0x8c/0xb0 [xfs]
Jun 13 10:42:45 jeeves kernel: [ 4268.265141]  [<fc2f9441>] ? xfs_do_force_shutdown+0x51/0x1c0 [xfs]
Jun 13 10:42:45 jeeves kernel: [ 4268.265175]  [<fc2f2a50>] ? xfs_trans_ail_delete+0x80/0x100 [xfs]
Jun 13 10:42:45 jeeves kernel: [ 4268.265208]  [<fc2f2a50>] ? xfs_trans_ail_delete+0x80/0x100 [xfs]
Jun 13 10:42:45 jeeves kernel: [ 4268.265237]  [<fc2c684d>] ? xfs_buf_iodone+0x2d/0x40 [xfs]
Jun 13 10:42:45 jeeves kernel: [ 4268.265266]  [<fc2c67e9>] ? xfs_buf_do_callbacks+0x29/0x40 [xfs]
Jun 13 10:42:45 jeeves kernel: [ 4268.265295]  [<fc2c7087>] ? xfs_buf_iodone_callbacks+0x127/0x1a0 [xfs]
Jun 13 10:42:45 jeeves kernel: [ 4268.265305]  [<c0130c68>] ? default_spin_lock_flags+0x8/0x10
Jun 13 10:42:45 jeeves kernel: [ 4268.265314]  [<c05b18bf>] ? _spin_lock_irqsave+0x2f/0x50
Jun 13 10:42:45 jeeves kernel: [ 4268.265324]  [<c017498d>] ? down_trylock+0x2d/0x40
Jun 13 10:42:45 jeeves kernel: [ 4268.265357]  [<fc2fcbbd>] ? xfs_buf_cond_lock+0xd/0x20 [xfs]
Jun 13 10:42:45 jeeves kernel: [ 4268.265391]  [<fc2fd9b1>] ? xfs_buf_iodone_work+0x21/0x80 [xfs]
Jun 13 10:42:45 jeeves kernel: [ 4268.265425]  [<fc2fda70>] ? xfs_buf_ioend+0x60/0x90 [xfs]
Jun 13 10:42:45 jeeves kernel: [ 4268.265457]  [<fc2f93db>] ? xfs_bioerror+0x3b/0x50 [xfs]
Jun 13 10:42:45 jeeves kernel: [ 4268.265491]  [<fc301e93>] ? xfs_bdstrat_cb+0x23/0x60 [xfs]
Jun 13 10:42:45 jeeves kernel: [ 4268.265525]  [<fc2fdc6d>] ? xfs_flush_buftarg+0x6d/0x130 [xfs]
Jun 13 10:42:45 jeeves kernel: [ 4268.265559]  [<fc2fdd52>] ? xfs_free_buftarg+0x22/0x70 [xfs]
Jun 13 10:42:45 jeeves kernel: [ 4268.265593]  [<fc304b65>] ? xfs_close_devices+0x55/0x60 [xfs]
Jun 13 10:42:45 jeeves kernel: [ 4268.265627]  [<fc30533d>] ? xfs_fs_fill_super+0x1ad/0x330 [xfs]
Jun 13 10:42:45 jeeves kernel: [ 4268.265636]  [<c02134b0>] ? set_bdev_super+0x0/0x30
Jun 13 10:42:45 jeeves kernel: [ 4268.265644]  [<c02148f2>] ? get_sb_bdev+0x162/0x1a0
Jun 13 10:42:45 jeeves kernel: [ 4268.265678]  [<fc305190>] ? xfs_fs_fill_super+0x0/0x330 [xfs]
Jun 13 10:42:45 jeeves kernel: [ 4268.265712]  [<fc303336>] ? xfs_fs_get_sb+0x26/0x30 [xfs]
Jun 13 10:42:45 jeeves kernel: [ 4268.265746]  [<fc305190>] ? xfs_fs_fill_super+0x0/0x330 [xfs]
Jun 13 10:42:45 jeeves kernel: [ 4268.265754]  [<c0214467>] ? vfs_kern_mount+0x67/0x170
Jun 13 10:42:45 jeeves kernel: [ 4268.265762]  [<c0228d77>] ? get_fs_type+0x97/0xb0
Jun 13 10:42:45 jeeves kernel: [ 4268.265769]  [<c02145ce>] ? do_kern_mount+0x3e/0xe0
Jun 13 10:42:45 jeeves kernel: [ 4268.265776]  [<c022be83>] ? do_mount+0x1c3/0x200
Jun 13 10:42:45 jeeves kernel: [ 4268.265783]  [<c022bf2b>] ? sys_mount+0x6b/0xa0
Jun 13 10:42:45 jeeves kernel: [ 4268.265790]  [<c0109763>] ? sysenter_do_call+0x12/0x28
Jun 13 10:42:45 jeeves kernel: [ 4268.265939] ---[ end trace 47f922ca193e6b5d ]---
```

---

