---
title: "Server (Hardy Heron) keeps crashing, need help decoding messages...."
date: 2009-06-23
forum: Server Platforms
---

### Post by dblagbro on 2009-06-23
Hello and thanks for reading.  I'm running Ubuntu Server AMD64 Hardy Heron and my server keeps crashing.  Not staying up for more than a few hours at a time.

I know to start with /var/log/messages but I don't know what these messages mean.  Can someone help me?

This is the latest messages - I've been replacing/swapping hardware and may have a a faulty Perc5i controller but that controller is removed and I'm still getting crashes... have also replaced memory and video cards...  have a spare mother board but haven't tried that and not really planning to unless something here inidcates it may be bad:


Jun 22 23:01:30 ubuntu -- MARK --
Jun 22 23:21:30 ubuntu -- MARK --
Jun 22 23:41:30 ubuntu -- MARK --
Jun 23 00:01:30 ubuntu -- MARK --
Jun 23 00:21:30 ubuntu -- MARK --
Jun 23 00:41:30 ubuntu -- MARK --
Jun 23 01:01:30 ubuntu -- MARK --
Jun 23 01:21:30 ubuntu -- MARK --
Jun 23 01:41:30 ubuntu -- MARK --
Jun 23 01:47:10 ubuntu kernel: [19606.218391] PGD 8063 PUD 11063 PMD 0
Jun 23 01:47:10 ubuntu kernel: [19606.218445] CPU 2
Jun 23 01:47:10 ubuntu kernel: [19606.218466] Modules linked in: vmnet vsock(F) vmci vmmon iptable_filter ip_tables x_tables reiserfs parport_pc lp parport loop ipv6 sky2 button shpchp pci_hotplug evdev pcspkr ext3 jbd mbcache sr_mod cdrom pata_marvell sg sd_mod ata_generic usb_storage libusual skge pata_acpi ehci_hcd megaraid_sas uhci_hcd libata scsi_mod usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
Jun 23 01:47:10 ubuntu kernel: [19606.218688] Pid: 5354, comm: vmware-vmx Tainted: GF       2.6.24-24-server #1
Jun 23 01:47:10 ubuntu kernel: [19606.218716] RIP: 0010:[copy_page_range+0x47b/0x730]  [copy_page_range+0x47b/0x730] copy_page_range+0x47b/0x730
Jun 23 01:47:10 ubuntu kernel: [19606.218763] RSP: 0018:ffff810226845d48  EFLAGS: 00010282
Jun 23 01:47:10 ubuntu kernel: [19606.218789] RAX: ffff8102314b2580 RBX: 800000028e9d0045 RCX: ffff810000012000
Jun 23 01:47:10 ubuntu kernel: [19606.218818] RDX: ffff8102314b2580 RSI: 0000000042324000 RDI: 000000000028e9d0
Jun 23 01:47:10 ubuntu kernel: [19606.218846] RBP: ffff81022442d920 R08: ffff810228001a4c R09: 000000000000009f
Jun 23 01:47:10 ubuntu kernel: [19606.218875] R10: 0000000000000000 R11: 0000000000000000 R12: 800000028e9d0045
Jun 23 01:47:10 ubuntu kernel: [19606.218904] R13: 0000000042324000 R14: ffff8101b9d5e920 R15: 0000000042367000
Jun 23 01:47:10 ubuntu kernel: [19606.218933] FS:  0000000042366950(0063) GS:ffff810228001b80(0000) knlGS:0000000000000000
Jun 23 01:47:10 ubuntu kernel: [19606.218979] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
Jun 23 01:47:10 ubuntu kernel: [19606.219005] CR2: ffff8102314b2580 CR3: 00000002268ce000 CR4: 00000000000006e0
Jun 23 01:47:10 ubuntu kernel: [19606.219034] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Jun 23 01:47:10 ubuntu kernel: [19606.219063] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Jun 23 01:47:10 ubuntu kernel: [19606.219092] Process vmware-vmx (pid: 5354, threadinfo ffff810226844000, task ffff81022554a000)
Jun 23 01:47:10 ubuntu kernel: [19606.219137] Stack:  ffffffff00000000 ffff810225520a40 ffff8102255210c0 ffff810226845e0c
Jun 23 01:47:10 ubuntu kernel: [19606.219190]  ffff8102244798f0 ffff8102255209c0 ffff810225521040 ffff8102268ce000
Jun 23 01:47:10 ubuntu kernel: [19606.219240]  ffff8101b4879000 0000000042367000 0000000042367000 0000000042367000
Jun 23 01:47:10 ubuntu kernel: [19606.219274] Call Trace:
Jun 23 01:47:10 ubuntu kernel: [19606.219315]  [copy_process+0xa58/0x1500] copy_process+0xa58/0x1500
Jun 23 01:47:10 ubuntu kernel: [19606.219344]  [system_call+0x7e/0x83] system_call+0x7e/0x83
Jun 23 01:47:10 ubuntu kernel: [19606.219369]  [do_fork+0x48/0x2a0] do_fork+0x48/0x2a0
Jun 23 01:47:10 ubuntu kernel: [19606.219395]  [ptregscall_common+0x67/0xb0] ptregscall_common+0x67/0xb0
Jun 23 01:47:10 ubuntu kernel: [19606.219424]
Jun 23 01:47:10 ubuntu kernel: [19606.219442]
Jun 23 01:47:10 ubuntu kernel: [19606.219442] Code: 48 8b 00 48 89 d1 25 00 40 02 00 48 3d 00 40 02 00 0f 84 88
Jun 23 01:47:10 ubuntu kernel: [19606.219570]  RSP <ffff810226845d48>
Jun 23 01:47:10 ubuntu kernel: [19606.219818] ---[ end trace e9f4871134e68998 ]---
Jun 23 01:49:20 ubuntu kernel: [19735.774501] CPU 0
Jun 23 01:49:20 ubuntu kernel: [19735.774582] Modules linked in: vmnet vsock(F) vmci vmmon iptable_filter ip_tables x_tables reiserfs parport_pc lp parport loop ipv6 sky2 button shpchp pci_hotplug evdev pcspkr ext3 jbd mbcache sr_mod cdrom pata_marvell sg sd_mod ata_generic usb_storage libusual skge pata_acpi ehci_hcd megaraid_sas uhci_hcd libata scsi_mod usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
Jun 23 01:49:20 ubuntu kernel: [19735.776177] Pid: 6177, comm: webAccess Tainted: GF     D 2.6.24-24-server #1
Jun 23 01:49:20 ubuntu kernel: [19735.776233] RIP: 0010:[page_remove_rmap+0x11a/0x130]  [page_remove_rmap+0x11a/0x130] page_remove_rmap+0x11a/0x130
Jun 23 01:49:20 ubuntu kernel: [19735.776342] RSP: 0018:ffff810207875bd8  EFLAGS: 00010246
Jun 23 01:49:20 ubuntu kernel: [19735.776395] RAX: 0000000000000000 RBX: ffff81022e1b1a60 RCX: 00000000ffffffff
Jun 23 01:49:20 ubuntu kernel: [19735.776451] RDX: 00000000ffffffff RSI: 0000000000000000 RDI: ffffffff8058ffa4
Jun 23 01:49:20 ubuntu kernel: [19735.776506] RBP: ffff8101b49c30b0 R08: 0000000000000000 R09: ffff8100000bc880
Jun 23 01:49:20 ubuntu kernel: [19735.776562] R10: 0000000000000000 R11: ffffffff80372bd0 R12: 00007fb1ec021000
Jun 23 01:49:20 ubuntu kernel: [19735.776618] R13: ffff81022e1b1a60 R14: 00007fb1eea41000 R15: 000000000007f557
Jun 23 01:49:20 ubuntu kernel: [19735.776673] FS:  0000000000000000(0000) GS:ffffffff805c5000(0000) knlGS:0000000000000000
Jun 23 01:49:20 ubuntu kernel: [19735.776745] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Jun 23 01:49:20 ubuntu kernel: [19735.776798] CR2: 00007fb209f3b790 CR3: 0000000000201000 CR4: 00000000000006e0
Jun 23 01:49:20 ubuntu kernel: [19735.776854] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Jun 23 01:49:20 ubuntu kernel: [19735.776909] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Jun 23 01:49:20 ubuntu kernel: [19735.776965] Process webAccess (pid: 6177, threadinfo ffff810207874000, task ffff810226d94000)
Jun 23 01:49:20 ubuntu kernel: [19735.777037] Stack:  ffff81022fab9c40 00007fb1ec200000 ffff8101d95b6108 ffffffff80295eaf
Jun 23 01:49:20 ubuntu kernel: [19735.777253]  0000000000000000 ffffffff806797a0 00007fb1eea40fff ffff8100010327b8
Jun 23 01:49:20 ubuntu kernel: [19735.777439]  0000000000000000 ffff810207875cf8 ffffffffffffffff 0000000000000000
Jun 23 01:49:20 ubuntu kernel: [19735.777581] Call Trace:
Jun 23 01:49:20 ubuntu kernel: [19735.777673]  [unmap_vmas+0x4ef/0x820] unmap_vmas+0x4ef/0x820
Jun 23 01:49:20 ubuntu kernel: [19735.777729]  [exit_mmap+0x77/0x100] exit_mmap+0x77/0x100
Jun 23 01:49:20 ubuntu kernel: [19735.777783]  [mmput+0x1e/0xb0] mmput+0x1e/0xb0
Jun 23 01:49:20 ubuntu kernel: [19735.777835]  [do_exit+0x1c0/0x950] do_exit+0x1c0/0x950
Jun 23 01:49:20 ubuntu kernel: [19735.777888]  [__dequeue_signal+0x2d/0x1e0] __dequeue_signal+0x2d/0x1e0
Jun 23 01:49:20 ubuntu kernel: [19735.777942]  [do_group_exit+0x2c/0x80] do_group_exit+0x2c/0x80
Jun 23 01:49:20 ubuntu kernel: [19735.777996]  [get_signal_to_deliver+0x2f7/0x4b0] get_signal_to_deliver+0x2f7/0x4b0
Jun 23 01:49:20 ubuntu kernel: [19735.778052]  [do_notify_resume+0xc4/0x810] do_notify_resume+0xc4/0x810
Jun 23 01:49:20 ubuntu kernel: [19735.778106]  [jbd:wake_up_bit+0x18/0x40] wake_up_bit+0x18/0x40
Jun 23 01:49:20 ubuntu kernel: [19735.778160]  [d_kill+0x48/0x70] d_kill+0x48/0x70
Jun 23 01:49:20 ubuntu kernel: [19735.778212]  [reiserfs:dput+0x1f/0xe10] dput+0x1f/0x130
Jun 23 01:49:20 ubuntu kernel: [19735.778265]  [sys_accept+0x1dd/0x200] sys_accept+0x1dd/0x200
Jun 23 01:49:20 ubuntu kernel: [19735.778319]  [sys_futex+0xab/0x140] sys_futex+0xab/0x140
Jun 23 01:49:20 ubuntu kernel: [19735.778373]  [sysret_signal+0x1c/0x27] sysret_signal+0x1c/0x27
Jun 23 01:49:20 ubuntu kernel: [19735.778426]  [ptregscall_common+0x67/0xb0] ptregscall_common+0x67/0xb0
Jun 23 01:49:20 ubuntu kernel: [19735.778481]
Jun 23 01:49:20 ubuntu kernel: [19735.778526]
Jun 23 01:49:20 ubuntu kernel: [19735.778526] Code: 0f 0b eb fe 48 8b 53 10 e9 65 ff ff ff 66 0f 1f 84 00 00 00
Jun 23 01:49:20 ubuntu kernel: [19735.779329]  RSP <ffff810207875bd8>
Jun 23 01:49:20 ubuntu kernel: [19735.779394] ---[ end trace e9f4871134e68998 ]---
Jun 23 02:01:30 ubuntu -- MARK --
Jun 23 09:21:12 ubuntu syslogd 1.5.0#1ubuntu1: restart.

---

### Post by dblagbro on 2009-06-24
.... and last night's crash:


Jun 23 10:01:12 ubuntu -- MARK --
Jun 23 10:21:12 ubuntu -- MARK --
Jun 23 10:41:12 ubuntu -- MARK --
Jun 23 11:01:12 ubuntu -- MARK --
Jun 23 11:21:12 ubuntu -- MARK --
Jun 23 11:41:12 ubuntu -- MARK --
Jun 23 12:01:12 ubuntu -- MARK --
Jun 23 12:21:12 ubuntu -- MARK --
Jun 23 12:41:12 ubuntu -- MARK --
Jun 23 13:01:12 ubuntu -- MARK --
Jun 23 13:21:12 ubuntu -- MARK --
Jun 23 13:41:12 ubuntu -- MARK --
Jun 23 14:01:12 ubuntu -- MARK --
Jun 23 14:21:12 ubuntu -- MARK --
Jun 23 14:41:12 ubuntu -- MARK --
Jun 23 15:01:12 ubuntu -- MARK --
Jun 23 15:21:12 ubuntu -- MARK --
Jun 23 15:41:12 ubuntu -- MARK --
Jun 23 16:01:12 ubuntu -- MARK --
Jun 23 16:21:12 ubuntu -- MARK --
Jun 23 16:41:12 ubuntu -- MARK --
Jun 23 17:01:12 ubuntu -- MARK --
Jun 23 17:21:12 ubuntu -- MARK --
Jun 23 17:41:12 ubuntu -- MARK --
Jun 23 18:01:12 ubuntu -- MARK --
Jun 23 18:21:12 ubuntu -- MARK --
Jun 23 18:41:12 ubuntu -- MARK --
Jun 23 19:01:12 ubuntu -- MARK --
Jun 23 19:21:12 ubuntu -- MARK --
Jun 23 19:41:12 ubuntu -- MARK --
Jun 23 20:01:12 ubuntu -- MARK --
Jun 23 20:21:12 ubuntu -- MARK --
Jun 23 20:41:12 ubuntu -- MARK --
Jun 23 21:01:12 ubuntu -- MARK --
Jun 23 21:21:12 ubuntu -- MARK --
Jun 23 21:41:12 ubuntu -- MARK --
Jun 23 22:01:12 ubuntu -- MARK --
Jun 23 22:21:12 ubuntu -- MARK --
Jun 23 22:41:12 ubuntu -- MARK --
Jun 23 23:01:12 ubuntu -- MARK --
Jun 23 23:21:12 ubuntu -- MARK --
Jun 23 23:41:12 ubuntu -- MARK --
Jun 24 00:01:12 ubuntu -- MARK --
Jun 24 00:21:12 ubuntu -- MARK --
Jun 24 00:41:12 ubuntu -- MARK --
Jun 24 01:01:12 ubuntu -- MARK --
Jun 24 01:21:12 ubuntu -- MARK --
Jun 24 01:41:12 ubuntu -- MARK --
Jun 24 02:01:12 ubuntu -- MARK --
Jun 24 02:21:12 ubuntu -- MARK --
Jun 24 02:41:12 ubuntu -- MARK --
Jun 24 03:01:12 ubuntu -- MARK --
Jun 24 03:09:01 ubuntu kernel: [64079.822585] cron[5272]: segfault at 7f1e257a7a30 rip 7f1e086e6b70 rsp 7fff108f8760 error 4
Jun 24 03:21:12 ubuntu -- MARK --
Jun 24 03:41:12 ubuntu -- MARK --
Jun 24 04:01:12 ubuntu -- MARK --
Jun 24 04:21:12 ubuntu -- MARK --
Jun 24 04:41:12 ubuntu -- MARK --
Jun 24 05:01:12 ubuntu -- MARK --
Jun 24 05:21:12 ubuntu -- MARK --
Jun 24 05:41:12 ubuntu -- MARK --
Jun 24 06:01:12 ubuntu -- MARK --
Jun 24 06:21:12 ubuntu -- MARK --
Jun 24 06:41:12 ubuntu -- MARK --
Jun 24 07:01:12 ubuntu -- MARK --
Jun 24 07:21:12 ubuntu -- MARK --
Jun 24 07:41:12 ubuntu -- MARK --
Jun 24 08:01:12 ubuntu -- MARK --
Jun 24 08:21:12 ubuntu -- MARK --
Jun 24 08:41:12 ubuntu -- MARK --
Jun 24 10:28:20 ubuntu syslogd 1.5.0#1ubuntu1: restart.
Jun 24 10:28:20 ubuntu kernel: Inspecting /boot/System.map-2.6.24-24-server
Jun 24 10:28:20 ubuntu kernel: Loaded 28776 symbols from /boot/System.map-2.6.24-24-server.
Jun 24 10:28:20 ubuntu kernel: Symbols match kernel version 2.6.24.



shows NOTHING!

This machine has run Window's 2003 server for a year and a half NO PROBLEMS...  I've been lead to believe that Ubuntu Server was stabil however I'm finding this is NOT the case.
I've also been told there's plenty of support for Ubuntu, just post a problem in a forum and someone will help you... this is also NOT the case as I've been posting various versions of this same thread and gotten absolutely NO responses.

I guess  linux really isn't ready for real business applications until a reliable support mechanism is made available.

-d

---

