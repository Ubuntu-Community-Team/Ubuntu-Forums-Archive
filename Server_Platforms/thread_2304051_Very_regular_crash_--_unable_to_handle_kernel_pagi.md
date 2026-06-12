---
title: "Very regular crash -- unable to handle kernel paging request"
date: 2015-11-23
forum: Server Platforms
---

### Post by dmtroyer2 on 2015-11-23
Hi,

I'm having an issue where a number of applications are crashing my Trusty Tahr server. Here is an example when it manages to log to /var/log/kern.log

Any help where to start looking would be much appreciated!

```
[ 1391.195502] VBOXGUEST_IOCTL_HGCM_CALL: 64 Failed. rc=-228.
[ 1391.199749] BUG: unable to handle kernel paging request at ffff880001003570
[ 1391.199829] IP: [<ffffffffa00f6fab>] VbglR0HGCMInternalCall+0x82b/0xe40 [vboxguest]
[ 1391.199901] PGD 1fe2067 PUD 1fe3067 PMD 80000000010001e1
[ 1391.199939] Oops: 0003 [#1] SMP
[ 1391.199972] Modules linked in: vboxsf(OX) joydev crct10dif_pclmul crc32_pclmul ghash_clmulni_intel aesni_intel aes_x86_64 lrw gf128mul glue_helper ablk_helper cryptd nfsd auth_rpcgss nfs_acl nfs lockd sunrpc fscache vboxvideo(OX) i2c_piix4 serio_raw vboxguest(OX) video drm lp parport mac_hid psmouse ahci libahci pata_acpi e1000
[ 1391.200175] CPU: 0 PID: 1595 Comm: gulp Tainted: G           OX 3.13.0-68-generic #111-Ubuntu
[ 1391.200240] Hardware name: innotek GmbH VirtualBox/VirtualBox, BIOS VirtualBox 12/01/2006
[ 1391.200303] task: ffff880039c8e000 ti: ffff88000013a000 task.ti: ffff88000013a000
[ 1391.200364] RIP: 0010:[<ffffffffa00f6fab>]  [<ffffffffa00f6fab>] VbglR0HGCMInternalCall+0x82b/0xe40 [vboxguest]
[ 1391.200442] RSP: 0018:ffff88000013b868  EFLAGS: 00010293
[ 1391.200478] RAX: 1680286780000000 RBX: ffff880001003570 RCX: 0000000000000000
[ 1391.200518] RDX: 0000000000000000 RSI: 0000000000000202 RDI: 0000000000000202
[ 1391.200559] RBP: ffff88000013ba18 R08: 00000000ffffff1c R09: ffff88003b350378
[ 1391.200599] R10: 0000000000000000 R11: 0000000000000030 R12: 00000000000ec7a2
[ 1391.200638] R13: 0000000000000000 R14: 000000000015a98e R15: ffff88003c217dc4
[ 1391.200679] FS:  00007f281e7fc700(0000) GS:ffff88003fc00000(0000) knlGS:0000000000000000
[ 1391.201414] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
[ 1391.201803] CR2: ffff880001003570 CR3: 000000003c759000 CR4: 00000000000406f0
[ 1391.202197] Stack:
[ 1391.202576]  ffff88003c31c110 0000000000000000 0000000200000002 ffff88003b3503c4
[ 1391.203341]  ffff88000013bb70 ffffffffa011c620 ffffffffa00f2500 ffff88000013bb50
[ 1391.204108]  ffff88003b3503e4 0000000000000001 ffff88003c31cb90 ffff88003b350378
[ 1391.204916] Call Trace:
[ 1391.205320]  [<ffffffffa00f2500>] ? vgdrvHgcmAsyncWaitCallbackWorker+0x250/0x250 [vboxguest]
[ 1391.206089]  [<ffffffff810ab100>] ? prepare_to_wait_exclusive+0x90/0x90
[ 1391.206483]  [<ffffffffa00f29a7>] ? vgdrvIoCtl_HGCMCall+0x277/0x300 [vboxguest]
[ 1391.207244]  [<ffffffffa00f47da>] ? VGDrvCommonIoCtl+0x24a/0x1bf0 [vboxguest]
[ 1391.207637]  [<ffffffffa00f29a7>] vgdrvIoCtl_HGCMCall+0x277/0x300 [vboxguest]
[ 1391.208040]  [<ffffffffa00f47da>] VGDrvCommonIoCtl+0x24a/0x1bf0 [vboxguest]
[ 1391.208422]  [<ffffffffa027f90d>] ? sf_stat+0x5d/0x100 [vboxsf]
[ 1391.208792]  [<ffffffffa027fa31>] ? sf_inode_revalidate+0x81/0xd0 [vboxsf]
[ 1391.209159]  [<ffffffff811c9372>] ? __inode_permission+0x52/0xc0
[ 1391.209518]  [<ffffffff811c93f8>] ? inode_permission+0x18/0x50
[ 1391.209872]  [<ffffffff811d73e0>] ? __d_lookup+0x120/0x160
[ 1391.210220]  [<ffffffffa027fa98>] ? sf_dentry_revalidate+0x18/0x30 [vboxsf]
[ 1391.210574]  [<ffffffff811c8fad>] ? lookup_fast+0x26d/0x2c0
[ 1391.210945]  [<ffffffff811ccdf5>] ? path_lookupat+0x155/0x790
[ 1391.211305]  [<ffffffff8101bc03>] ? native_sched_clock+0x13/0x80
[ 1391.211658]  [<ffffffff8101bc79>] ? sched_clock+0x9/0x10
[ 1391.212005]  [<ffffffff811a33b5>] ? kmem_cache_alloc+0x35/0x1e0
[ 1391.212345]  [<ffffffff811ce35f>] ? getname_flags+0x4f/0x190
[ 1391.212680]  [<ffffffff811cd45b>] ? filename_lookup+0x2b/0xc0
[ 1391.213009]  [<ffffffff811cf034>] ? user_path_at_empty+0x54/0x90
[ 1391.213334]  [<ffffffff810aaca8>] ? __wake_up_common+0x58/0x90
[ 1391.213652]  [<ffffffff81200261>] ? fsnotify+0x241/0x320
[ 1391.213961]  [<ffffffff811cf081>] ? user_path_at+0x11/0x20
[ 1391.214261]  [<ffffffff811c3140>] ? vfs_fstatat+0x50/0xa0
[ 1391.214552]  [<ffffffff811c35df>] ? SYSC_newstat+0x1f/0x40
[ 1391.214835]  [<ffffffff811be45c>] ? vfs_write+0x15c/0x1f0
[ 1391.215108]  [<ffffffff811bee1c>] ? SyS_write+0x7c/0xa0
[ 1391.215380]  [<ffffffff811c382e>] ? SyS_newstat+0xe/0x10
[ 1391.215644]  [<ffffffff81734cdd>] ? system_call_fastpath+0x1a/0x1f
[ 1391.215900] Code: c0 0f 88 6a 05 00 00 41 8b 47 04 44 8b 85 c0 fe ff ff 41 83 c5 01 8b 8d b8 fe ff ff 89 43 04 e9 4b ff ff ff 0f 1f 40 00 49 8b 07 <48> 89 03 49 8b 47 08 48 89 43 08 e9 34 ff ff ff 0f 1f 44 00 00
[ 1391.216713] RIP  [<ffffffffa00f6fab>] VbglR0HGCMInternalCall+0x82b/0xe40 [vboxguest]
[ 1391.217361]  RSP <ffff88000013b868>
[ 1391.217623] CR2: ffff880001003570

```

---

