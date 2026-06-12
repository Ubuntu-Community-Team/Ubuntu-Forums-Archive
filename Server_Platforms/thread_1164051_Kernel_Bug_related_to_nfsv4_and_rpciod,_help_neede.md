---
title: "Kernel Bug related to nfsv4 and rpciod, help needed"
date: 2009-05-19
forum: Server Platforms
---

### Post by xdcdx on 2009-05-19
Hello,

I have a cluster setup with Ubuntu 8.04 LTS server x86_64 version installed. We have 12 nodes, all of them share and mount one scratch directory with and from the rest of the nodes by NFSv4. And all of them mount the /home folder from node1.

In all of them we have all the latest security and kernel updates. Our kernel version is:
--$ uname -a
Linux 2.6.24-24-server #1 SMP Wed Apr 15 15:41:09 UTC 2009 x86_64 GNU/Linux

This bug also happened with older versions of the kernel (it happened on Linux 2.6.24-23-server for sure, and in 2.6.15-53-amd64-server probably too).

Randomly, in some nodes, we are experiencing a rare kernel bug that seem to hang the hard disk and/or the NFS server (althought I'm not sure of this),  and make the nodes to work buggily until restart. Work buggily means that I cannot ssh the nodes as a regular user (because the /home directory is nfs mounted), but I can ssh them as root. Sometimes a soft reboot (reboot command) works and sometimes it doesn't and I have to do a hard reboot (reset button).

When the bug appears, some nodes present the bug (we believe the nodes with running process), and some other keep working happily (the nodes with no running process). The nodes in which the bug appears, they all fail  the same time. The hardware of the nodes that have the bug is not different from the one from the nodes that keep working.

When the bug appears, the working nodes can't access the NFS mounts of the buggy nodes. As kern.log shows (attached below), the kernel bug is related to rpciod (used by NFSv4, I believe), and the cluster processes (most access data by NFS).

The kernel bug seems to appear randomly: sometimes the cluster works for week without a problem, and sometimes we get the bug two days in a row. When it appears, we restart the buggy nodes, and they keep working fine until the next time.

Can anybody guide me? I am completely lost about what might be causing this, or how can I solve this. If this is a real kernel bug, should I submit it to bugzilla.kernel.org ? Is there a specific list for Ubuntu's kernel bugs?

Here's how we export the home (for the node 1) and scratch directory (for the rest of the nodes):

heura1 /etc/exports
--------------------
/ 192.168.6.0/255.255.255.0(rw,sync,no_subtree_check,fsid=0)
/home                               192.168.6.0/255.255.255.0(rw,sync,nohide,no_root_squash,no_subtree_check)
/etc/exports

heura6 /etc/exports
--------------------
/                               192.168.6.0/255.255.255.0(rw,sync,fsid=0)
/scratch-local                  192.168.6.0/255.255.255.0(rw,sync,nohide)


Here's how we mount the home and scratch directorys for all of the nodes in /etc/fstab:

heura:/home /home nfs4 hard,intr,rsize=32768,wsize=32768 0 0
heura2:/scratch-local /scratch/2 nfs4 hard,intr,rsize=32768,wsize=32768 0 0


Here's the kern.log of the last time the bug occured, in two different nodes.

heura6 kern.log
---------------
May 19 01:40:45 heura6 kernel: [462902.541017] ------------[ cut here ]------------
May 19 01:40:45 heura6 kernel: [462902.541062] kernel BUG at /build/buildd/linux-2.6.24/net/sunrpc/rpcb_clnt.c:322!
May 19 01:40:45 heura6 kernel: [462902.541106] invalid opcode: 0000 [1] SMP 
May 19 01:40:45 heura6 kernel: [462902.541134] CPU 1 
May 19 01:40:45 heura6 kernel: [462902.541156] Modules linked in: autofs4 ipv6 nfs iptable_filter ip_tables x_tables nfsd lockd nfs_acl auth_rpcgss sunrpc exportfs parport_pc lp parport af_packet psmouse serio_raw shpchp iTCO_wdt i5000_edac button iTCO_vendor_support evdev edac_core pci_hotplug pcspkr ext3 jbd mbcache sg sd_mod ata_piix pata_acpi ata_generic libata scsi_mod ehci_hcd uhci_hcd usbcore e1000 raid10 raid456 async_xor async_memcpy async_tx xor raid1 raid0 multipath linear md_mod dm_mirror dm_snapshot dm_mod thermal processor fan fbcon tileblit font bitblit softcursor fuse
May 19 01:40:45 heura6 kernel: [462902.541459] Pid: 4397, comm: rpciod/1 Not tainted 2.6.24-24-server #1
May 19 01:40:45 heura6 kernel: [462902.541487] RIP: 0010:[sunrpc:rpcb_getport_async+0x272/0x3c0]  [sunrpc:rpcb_getport_async+0x272/0x3c0] :sunrpc:rpcb_getport_async+0x272/0x3c0
May 19 01:40:45 heura6 kernel: [462902.541555] RSP: 0018:ffff810255463e20  EFLAGS: 00010206
May 19 01:40:45 heura6 kernel: [462902.541582] RAX: ffffffff882e45c0 RBX: ffff8102549a4400 RCX: ffff81006c9ba110
May 19 01:40:45 heura6 kernel: [462902.541626] RDX: 00000000ffffff95 RSI: 0000000000000286 RDI: ffff81006c9ba008
May 19 01:40:45 heura6 kernel: [462902.541669] RBP: ffff8102538c5000 R08: 00000000000001f3 R09: 0000000000000001
May 19 01:40:45 heura6 kernel: [462902.541713] R10: 0000000000000003 R11: ffffffff882c6640 R12: ffff8102549a4a00
May 19 01:40:45 heura6 kernel: [462902.541756] R13: ffff81006c9ba008 R14: 0000000000000000 R15: 0000000000000000
May 19 01:40:45 heura6 kernel: [462902.541800] FS:  0000000000000000(0000) GS:ffff810257401800(0000) knlGS:0000000000000000
May 19 01:40:45 heura6 kernel: [462902.541846] CS:  0010 DS: 0018 ES: 0018 CR0: 000000008005003b
May 19 01:40:45 heura6 kernel: [462902.541873] CR2: 00000000f7bd4000 CR3: 00000002554ed000 CR4: 00000000000006e0
May 19 01:40:45 heura6 kernel: [462902.541916] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
May 19 01:40:45 heura6 kernel: [462902.541960] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
May 19 01:40:45 heura6 kernel: [462902.542004] Process rpciod/1 (pid: 4397, threadinfo ffff810255462000, task ffff8102559a4000)
May 19 01:40:45 heura6 kernel: [462902.542050] Stack:  0000000000000000 ffffffff882bdf60 0000000000000286 ffff81006c9ba098
May 19 01:40:45 heura6 kernel: [462902.542103]  0000000000000000 ffff81006c9ba008 ffff810255c2cb80 ffff81006c9ba0f8
May 19 01:40:45 heura6 kernel: [462902.542154]  0000000000000000 ffffffff882bdb3b ffffffffffffffff ffff810255c2cb80
May 19 01:40:45 heura6 kernel: [462902.542188] Call Trace:
May 19 01:40:45 heura6 kernel: [462902.542237]  [nfs:rpc_sleep_on+0x150/0x2b0] :sunrpc:rpc_sleep_on+0x150/0x2b0
May 19 01:40:45 heura6 kernel: [462902.542278]  [sunrpc:__rpc_execute+0x6b/0x290] :sunrpc:__rpc_execute+0x6b/0x290
May 19 01:40:45 heura6 kernel: [462902.542317]  [sunrpc:rpc_async_schedule+0x0/0x10] :sunrpc:rpc_async_schedule+0x0/0x10
May 19 01:40:45 heura6 kernel: [462902.542351]  [run_workqueue+0xcc/0x170] run_workqueue+0xcc/0x170
May 19 01:40:45 heura6 kernel: [462902.542379]  [worker_thread+0x0/0x110] worker_thread+0x0/0x110
May 19 01:40:45 heura6 kernel: [462902.542407]  [worker_thread+0x0/0x110] worker_thread+0x0/0x110
May 19 01:40:45 heura6 kernel: [462902.542435]  [worker_thread+0xa3/0x110] worker_thread+0xa3/0x110
May 19 01:40:45 heura6 kernel: [462902.542464]  [<ffffffff80254520>] autoremove_wake_function+0x0/0x30
May 19 01:40:45 heura6 kernel: [462902.542494]  [worker_thread+0x0/0x110] worker_thread+0x0/0x110
May 19 01:40:45 heura6 kernel: [462902.542522]  [worker_thread+0x0/0x110] worker_thread+0x0/0x110
May 19 01:40:45 heura6 kernel: [462902.542549]  [kthread+0x4b/0x80] kthread+0x4b/0x80
May 19 01:40:45 heura6 kernel: [462902.542577]  [child_rip+0xa/0x12] child_rip+0xa/0x12
May 19 01:40:45 heura6 kernel: [462902.542606]  [kthread+0x0/0x80] kthread+0x0/0x80
May 19 01:40:45 heura6 kernel: [462902.542633]  [child_rip+0x0/0x12] child_rip+0x0/0x12
May 19 01:40:45 heura6 kernel: [462902.542659] 
May 19 01:40:45 heura6 kernel: [462902.542678] 
May 19 01:40:45 heura6 kernel: [462902.542678] Code: 0f 0b eb fe 8b 85 b8 00 00 00 0f b7 b7 48 01 00 00 48 c7 c2 
May 19 01:40:45 heura6 kernel: [462902.544357] RIP  [sunrpc:rpcb_getport_async+0x272/0x3c0] :sunrpc:rpcb_getport_async+0x272/0x3c0
May 19 01:40:45 heura6 kernel: [462902.544398]  RSP <ffff810255463e20>
May 19 01:40:45 heura6 kernel: [462902.544660] ---[ end trace d3438eb0ca119884 ]---
May 19 01:40:45 heura6 kernel: [462902.544698] ------------[ cut here ]------------
May 19 01:40:45 heura6 kernel: [462902.544702] kernel BUG at /build/buildd/linux-2.6.24/net/sunrpc/rpcb_clnt.c:322!
May 19 01:40:45 heura6 kernel: [462902.544706] invalid opcode: 0000 [2] SMP 
May 19 01:40:45 heura6 kernel: [462902.544709] CPU 0 
May 19 01:40:45 heura6 kernel: [462902.544711] Modules linked in: autofs4 ipv6 nfs iptable_filter ip_tables x_tables nfsd lockd nfs_acl auth_rpcgss sunrpc exportfs parport_pc lp parport af_packet psmouse serio_raw shpchp iTCO_wdt i5000_edac button iTCO_vendor_support evdev edac_core pci_hotplug pcspkr ext3 jbd mbcache sg sd_mod ata_piix pata_acpi ata_generic libata scsi_mod ehci_hcd uhci_hcd usbcore e1000 raid10 raid456 async_xor async_memcpy async_tx xor raid1 raid0 multipath linear md_mod dm_mirror dm_snapshot dm_mod thermal processor fan fbcon tileblit font bitblit softcursor fuse
May 19 01:40:45 heura6 kernel: [462902.544765] Pid: 1987, comm: mhtrain Tainted: G      D 2.6.24-24-server #1
May 19 01:40:45 heura6 kernel: [462902.544767] RIP: 0010:[sunrpc:rpcb_getport_async+0x272/0x3c0]  [sunrpc:rpcb_getport_async+0x272/0x3c0] :sunrpc:rpcb_getport_async+0x272/0x3c0
May 19 01:40:45 heura6 kernel: [462902.544789] RSP: 0018:ffff8101b4885988  EFLAGS: 00010206
May 19 01:40:45 heura6 kernel: [462902.544791] RAX: ffffffff882e45c0 RBX: ffff8102549a4400 RCX: 00000000c0000100
May 19 01:40:45 heura6 kernel: [462902.544793] RDX: 0000000000000000 RSI: 00000000ffffff95 RDI: ffff8101b49dfc00
May 19 01:40:45 heura6 kernel: [462902.544794] RBP: ffff8102538c5000 R08: ffff8101b4884000 R09: 0000000000000002
May 19 01:40:45 heura6 kernel: [462902.544796] R10: ffff810001039c60 R11: ffffffff882c6640 R12: ffff8102549a4a00
May 19 01:40:45 heura6 kernel: [462902.544798] R13: ffff8101b49dfc00 R14: ffff8101b4885af8 R15: ffff8101b4885bc8
May 19 01:40:45 heura6 kernel: [462902.544801] FS:  00007f609c1926e0(0000) GS:ffffffff805c5000(0000) knlGS:0000000000000000
May 19 01:40:45 heura6 kernel: [462902.544803] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
May 19 01:40:45 heura6 kernel: [462902.544805] CR2: 00007f609b999000 CR3: 00000001b4911000 CR4: 00000000000006e0
May 19 01:40:45 heura6 kernel: [462902.544806] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
May 19 01:40:45 heura6 kernel: [462902.544808] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
May 19 01:40:45 heura6 kernel: [462902.544810] Process mhtrain (pid: 1987, threadinfo ffff8101b4884000, task ffff8102512637d0)
May 19 01:40:45 heura6 kernel: [462902.544812] Stack:  ffff8102538c5338 ffff8102538c5000 ffff8101b49dfc00 ffff8102549a4400
May 19 01:40:45 heura6 kernel: [462902.544820]  0000000000000000 ffff8101b49dfc00 ffffffff882cc390 ffff8101b49dfcf0
May 19 01:40:45 heura6 kernel: [462902.544824]  ffff8101b4885af8 ffffffff882bdb3b ffffffff882cc390 ffff8101b49dfc00
May 19 01:40:45 heura6 kernel: [462902.544829] Call Trace:
May 19 01:40:45 heura6 kernel: [462902.544846]  [sunrpc:__rpc_execute+0x6b/0x290] :sunrpc:__rpc_execute+0x6b/0x290
May 19 01:40:45 heura6 kernel: [462902.544859]  [sunrpc:rpc_do_run_task+0x76/0xd0] :sunrpc:rpc_do_run_task+0x76/0xd0
May 19 01:40:45 heura6 kernel: [462902.544873]  [sunrpc:rpc_call_sync+0x15/0x40] :sunrpc:rpc_call_sync+0x15/0x40
May 19 01:40:45 heura6 kernel: [462902.544891]  [nfs:_nfs4_proc_getattr+0x65/0x70] :nfs:_nfs4_proc_getattr+0x65/0x70
May 19 01:40:45 heura6 kernel: [462902.544899]  [sunrpc:recalc_sigpending+0xe/0x40] recalc_sigpending+0xe/0x40
May 19 01:40:45 heura6 kernel: [462902.544912]  [nfs:nfs4_proc_getattr+0x32/0x60] :nfs:nfs4_proc_getattr+0x32/0x60
May 19 01:40:45 heura6 kernel: [462902.544915]  [sunrpc:recalc_sigpending+0xe/0x40] recalc_sigpending+0xe/0x40
May 19 01:40:45 heura6 kernel: [462902.544927]  [nfs:__nfs_revalidate_inode+0x1cd/0x300] :nfs:__nfs_revalidate_inode+0x1cd/0x300
May 19 01:40:45 heura6 kernel: [462902.544933]  [__link_path_walk+0xaf9/0xe90] __link_path_walk+0xaf9/0xe90
May 19 01:40:45 heura6 kernel: [462902.544948]  [sunrpc:rpcauth_lookup_credcache+0xa8/0x230] :sunrpc:rpcauth_lookup_credcache+0xa8/0x230
May 19 01:40:45 heura6 kernel: [462902.544960]  [nfs:nfs_do_access+0x32/0x350] :nfs:nfs_do_access+0x32/0x350
May 19 01:40:45 heura6 kernel: [462902.544965]  [nfs:dput+0x1f/0x170] dput+0x1f/0x130
May 19 01:40:45 heura6 kernel: [462902.544975]  [nfs:nfs_open_revalidate+0x81/0x1d0] :nfs:nfs_open_revalidate+0x81/0x1d0
May 19 01:40:45 heura6 kernel: [462902.544989]  [nfs:nfs_revalidate_mapping_nolock+0x47/0xa0] :nfs:nfs_revalidate_mapping_nolock+0x47/0xa0
May 19 01:40:45 heura6 kernel: [462902.545002]  [nfs:nfs_follow_link+0x1c/0x90] :nfs:nfs_follow_link+0x1c/0x90
May 19 01:40:45 heura6 kernel: [462902.545007]  [__link_path_walk+0xcb2/0xe90] __link_path_walk+0xcb2/0xe90
May 19 01:40:45 heura6 kernel: [462902.545013]  [link_path_walk+0x5b/0x100] link_path_walk+0x5b/0x100
May 19 01:40:45 heura6 kernel: [462902.545022]  [get_unused_fd_flags+0x77/0x120] get_unused_fd_flags+0x77/0x120
May 19 01:40:45 heura6 kernel: [462902.545027]  [do_path_lookup+0x8a/0x250] do_path_lookup+0x8a/0x250
May 19 01:40:45 heura6 kernel: [462902.545031]  [__path_lookup_intent_open+0x6a/0xd0] __path_lookup_intent_open+0x6a/0xd0
May 19 01:40:45 heura6 kernel: [462902.545036]  [open_namei+0x89/0x710] open_namei+0x89/0x710
May 19 01:40:45 heura6 kernel: [462902.545040]  [__dequeue_entity+0x3d/0x50] __dequeue_entity+0x3d/0x50
May 19 01:40:45 heura6 kernel: [462902.545044]  [__switch_to+0x1ba/0x310] __switch_to+0x1ba/0x310
May 19 01:40:45 heura6 kernel: [462902.545049]  [do_filp_open+0x1c/0x50] do_filp_open+0x1c/0x50
May 19 01:40:45 heura6 kernel: [462902.545055]  [get_unused_fd_flags+0x77/0x120] get_unused_fd_flags+0x77/0x120
May 19 01:40:45 heura6 kernel: [462902.545060]  [do_sys_open+0x5a/0xf0] do_sys_open+0x5a/0xf0
May 19 01:40:45 heura6 kernel: [462902.545064]  [system_call+0x7e/0x83] system_call+0x7e/0x83
May 19 01:40:45 heura6 kernel: [462902.545069] 
May 19 01:40:45 heura6 kernel: [462902.545070] 
May 19 01:40:45 heura6 kernel: [462902.545071] Code: 0f 0b eb fe 8b 85 b8 00 00 00 0f b7 b7 48 01 00 00 48 c7 c2 
May 19 01:40:45 heura6 kernel: [462902.545081] RIP  [sunrpc:rpcb_getport_async+0x272/0x3c0] :sunrpc:rpcb_getport_async+0x272/0x3c0
May 19 01:40:45 heura6 kernel: [462902.545095]  RSP <ffff8101b4885988>
May 19 01:40:45 heura6 kernel: [462902.545097] ---[ end trace d3438eb0ca119884 ]---
May 19 01:40:45 heura6 kernel: [462902.553615] ------------[ cut here ]------------
May 19 01:40:45 heura6 kernel: [462902.553676] kernel BUG at /build/buildd/linux-2.6.24/net/sunrpc/rpcb_clnt.c:322!
May 19 01:40:45 heura6 kernel: [462902.553751] invalid opcode: 0000 [3] SMP 
May 19 01:40:45 heura6 kernel: [462902.553870] CPU 0 
May 19 01:40:45 heura6 kernel: [462902.553952] Modules linked in: autofs4 ipv6 nfs iptable_filter ip_tables x_tables nfsd lockd nfs_acl auth_rpcgss sunrpc exportfs parport_pc lp parport af_packet psmouse serio_raw shpchp iTCO_wdt i5000_edac button iTCO_vendor_support evdev edac_core pci_hotplug pcspkr ext3 jbd mbcache sg sd_mod ata_piix pata_acpi ata_generic libata scsi_mod ehci_hcd uhci_hcd usbcore e1000 raid10 raid456 async_xor async_memcpy async_tx xor raid1 raid0 multipath linear md_mod dm_mirror dm_snapshot dm_mod thermal processor fan fbcon tileblit font bitblit softcursor fuse
May 19 01:40:45 heura6 kernel: [462902.556271] Pid: 3662, comm: bernoulli_local Tainted: G      D 2.6.24-24-server #1
May 19 01:40:45 heura6 kernel: [462902.556345] RIP: 0010:[sunrpc:rpcb_getport_async+0x272/0x3c0]  [sunrpc:rpcb_getport_async+0x272/0x3c0] :sunrpc:rpcb_getport_async+0x272/0x3c0
May 19 01:40:45 heura6 kernel: [462902.556474] RSP: 0018:ffff8101a1fe57c8  EFLAGS: 00010206
May 19 01:40:45 heura6 kernel: [462902.556530] RAX: ffffffff882e45c0 RBX: ffff8102549a4400 RCX: ffff8102599cb180
May 19 01:40:45 heura6 kernel: [462902.556604] RDX: ffff8102599cb180 RSI: ffff8102599cb1a8 RDI: ffff8101b49df900
May 19 01:40:45 heura6 kernel: [462902.556677] RBP: ffff8102538c5000 R08: ffff810001036900 R09: 000000000000006b
May 19 01:40:45 heura6 kernel: [462902.556751] R10: 0000000000000001 R11: ffffffff882c6640 R12: ffff8102549a4a00
May 19 01:40:45 heura6 kernel: [462902.556824] R13: ffff8101b49df900 R14: ffff8101a1fe5898 R15: ffff8101a1fe59c8
May 19 01:40:45 heura6 kernel: [462902.556898] FS:  00007f2444d626e0(0000) GS:ffffffff805c5000(0000) knlGS:0000000000000000
May 19 01:40:45 heura6 kernel: [462902.556973] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
May 19 01:40:45 heura6 kernel: [462902.557030] CR2: 00000000006e3b88 CR3: 00000001018a2000 CR4: 00000000000006e0
May 19 01:40:45 heura6 kernel: [462902.557104] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
May 19 01:40:45 heura6 kernel: [462902.557177] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
May 19 01:40:45 heura6 kernel: [462902.557251] Process bernoulli_local (pid: 3662, threadinfo ffff8101a1fe4000, task ffff8102530657d0)
May 19 01:40:45 heura6 kernel: [462902.557327] Stack:  ffff8101b49df900 ffffffff883bc178 ffff810250c54a80 ffffffff882b78c0
May 19 01:40:45 heura6 kernel: [462902.557564]  0000000000000000 ffff8101b49df900 ffffffff882cc390 ffff8101b49df9f0
May 19 01:40:45 heura6 kernel: [462902.557767]  ffff8101a1fe5898 ffffffff882bdb3b ffffffff882cc390 ffff8101b49df900
May 19 01:40:45 heura6 kernel: [462902.557924] Call Trace:
May 19 01:40:45 heura6 kernel: [462902.558033]  [sunrpc:call_allocate+0xc0/0x1b0] :sunrpc:call_allocate+0xc0/0x1b0
May 19 01:40:45 heura6 kernel: [462902.558103]  [sunrpc:__rpc_execute+0x6b/0x290] :sunrpc:__rpc_execute+0x6b/0x290
May 19 01:40:45 heura6 kernel: [462902.558173]  [sunrpc:rpc_do_run_task+0x76/0xd0] :sunrpc:rpc_do_run_task+0x76/0xd0
May 19 01:40:45 heura6 kernel: [462902.558247]  [nfs:decode_getfattr+0x89e/0x1140] :nfs:decode_getfattr+0x89e/0x1140
May 19 01:40:45 heura6 kernel: [462902.558317]  [sunrpc:rpc_call_sync+0x15/0x40] :sunrpc:rpc_call_sync+0x15/0x40
May 19 01:40:45 heura6 kernel: [462902.558386]  [nfs:nfs4_proc_access+0x8f/0x1e0] :nfs:nfs4_proc_access+0x8f/0x1e0
May 19 01:40:45 heura6 kernel: [462902.558457]  [nfs:nfs4_xdr_dec_getattr+0x0/0x60] :nfs:nfs4_xdr_dec_getattr+0x0/0x60
May 19 01:40:45 heura6 kernel: [462902.558526]  [nfs:nfs4_xdr_dec_getattr+0x4f/0x60] :nfs:nfs4_xdr_dec_getattr+0x4f/0x60
May 19 01:40:45 heura6 kernel: [462902.558591]  [__wait_on_bit+0x6b/0x80] __wait_on_bit+0x6b/0x80
May 19 01:40:45 heura6 kernel: [462902.558651]  [__wake_up_common+0x5a/0x90] __wake_up_common+0x5a/0x90
May 19 01:40:45 heura6 kernel: [462902.558713]  [__slab_free+0x1fe/0x350] __slab_free+0x1fe/0x350
May 19 01:40:45 heura6 kernel: [462902.558780]  [nfs:nfs_do_access+0xda/0x350] :nfs:nfs_do_access+0xda/0x350
May 19 01:40:45 heura6 kernel: [462902.558850]  [nfs:nfs_permission+0xd8/0x1a0] :nfs:nfs_permission+0xd8/0x1a0
May 19 01:40:45 heura6 kernel: [462902.558912]  [nfsd:permission+0xb0/0x1b0] permission+0xb0/0x160
May 19 01:40:45 heura6 kernel: [462902.558970]  [__link_path_walk+0x87/0xe90] __link_path_walk+0x87/0xe90
May 19 01:40:45 heura6 kernel: [462902.559032]  [link_path_walk+0x5b/0x100] link_path_walk+0x5b/0x100
May 19 01:40:45 heura6 kernel: [462902.559090]  [getname+0x33/0x220] getname+0x33/0x220
May 19 01:40:45 heura6 kernel: [462902.559150]  [get_unused_fd_flags+0x77/0x120] get_unused_fd_flags+0x77/0x120
May 19 01:40:45 heura6 kernel: [462902.559211]  [__link_path_walk+0x66a/0xe90] __link_path_walk+0x66a/0xe90
May 19 01:40:45 heura6 kernel: [462902.559273]  [link_path_walk+0x5b/0x100] link_path_walk+0x5b/0x100
May 19 01:40:45 heura6 kernel: [462902.559331]  [getname+0x33/0x220] getname+0x33/0x220
May 19 01:40:45 heura6 kernel: [462902.559390]  [get_unused_fd_flags+0x77/0x120] get_unused_fd_flags+0x77/0x120
May 19 01:40:45 heura6 kernel: [462902.559451]  [do_path_lookup+0x8a/0x250] do_path_lookup+0x8a/0x250
May 19 01:40:45 heura6 kernel: [462902.559511]  [__path_lookup_intent_open+0x6a/0xd0] __path_lookup_intent_open+0x6a/0xd0
May 19 01:40:45 heura6 kernel: [462902.559571]  [open_namei+0xfa/0x710] open_namei+0xfa/0x710
May 19 01:40:45 heura6 kernel: [462902.559630]  [do_page_fault+0x1d0/0x840] do_page_fault+0x1d0/0x840
May 19 01:40:45 heura6 kernel: [462902.559690]  [do_filp_open+0x1c/0x50] do_filp_open+0x1c/0x50
May 19 01:40:45 heura6 kernel: [462902.559747]  [getname+0x33/0x220] getname+0x33/0x220
May 19 01:40:45 heura6 kernel: [462902.559807]  [get_unused_fd_flags+0x77/0x120] get_unused_fd_flags+0x77/0x120
May 19 01:40:45 heura6 kernel: [462902.559867]  [do_sys_open+0x5a/0xf0] do_sys_open+0x5a/0xf0
May 19 01:40:45 heura6 kernel: [462902.559926]  [system_call+0x7e/0x83] system_call+0x7e/0x83
May 19 01:40:45 heura6 kernel: [462902.559985] 
May 19 01:40:45 heura6 kernel: [462902.560034] 
May 19 01:40:45 heura6 kernel: [462902.560034] Code: 0f 0b eb fe 8b 85 b8 00 00 00 0f b7 b7 48 01 00 00 48 c7 c2 
May 19 01:40:45 heura6 kernel: [462902.560831] RIP  [sunrpc:rpcb_getport_async+0x272/0x3c0] :sunrpc:rpcb_getport_async+0x272/0x3c0
May 19 01:40:45 heura6 kernel: [462902.560933]  RSP <ffff8101a1fe57c8>
May 19 01:40:45 heura6 kernel: [462902.560996] ---[ end trace d3438eb0ca119884 ]---


-------------------------------------------------------------
-------------------------------------------------------------


heura 8 kern.log
----------------
May 19 01:39:39 heura8 kernel: [462824.028797] ------------[ cut here ]------------
May 19 01:39:39 heura8 kernel: [462824.028842] kernel BUG at /build/buildd/linux-2.6.24/net/sunrpc/rpcb_clnt.c:322!
May 19 01:39:39 heura8 kernel: [462824.028886] invalid opcode: 0000 [1] SMP 
May 19 01:39:39 heura8 kernel: [462824.028914] CPU 3 
May 19 01:39:39 heura8 kernel: [462824.028936] Modules linked in: autofs4 ipv6 nfs iptable_filter ip_tables x_tables nfsd lockd nfs_acl auth_rpcgss sunrpc exportfs parport_pc lp parport af_packet psmouse serio_raw evdev iTCO_wdt iTCO_vendor_support button i5000_edac edac_core shpchp pci_hotplug pcspkr ext3 jbd mbcache sg sd_mod ata_piix pata_acpi ehci_hcd ata_generic uhci_hcd usbcore libata scsi_mod e1000 raid10 raid456 async_xor async_memcpy async_tx xor raid1 raid0 multipath linear md_mod dm_mirror dm_snapshot dm_mod thermal processor fan fbcon tileblit font bitblit softcursor fuse
May 19 01:39:39 heura8 kernel: [462824.029239] Pid: 6549, comm: mhrecognise Not tainted 2.6.24-24-server #1
May 19 01:39:39 heura8 kernel: [462824.029268] RIP: 0010:[sunrpc:rpcb_getport_async+0x272/0x3c0]  [sunrpc:rpcb_getport_async+0x272/0x3c0] :sunrpc:rpcb_getport_async+0x272/0x3c0
May 19 01:39:39 heura8 kernel: [462824.029336] RSP: 0018:ffff81022fd7b7c8  EFLAGS: 00010287
May 19 01:39:39 heura8 kernel: [462824.029363] RAX: ffffffff882e65c0 RBX: ffff810250cb2e00 RCX: 00000000c0000100
May 19 01:39:39 heura8 kernel: [462824.029406] RDX: 0000000000000000 RSI: 0000000000000286 RDI: ffff81025201cd80
May 19 01:39:39 heura8 kernel: [462824.029450] RBP: ffff8102539d2800 R08: ffff81022fd7a000 R09: 0000000000000000
May 19 01:39:39 heura8 kernel: [462824.029493] R10: ffff81000105ac60 R11: ffffffff882c8640 R12: ffff810250cb2400
May 19 01:39:39 heura8 kernel: [462824.029537] R13: ffff81025201cd80 R14: ffff81022fd7b898 R15: ffff81022fd7b9c8
May 19 01:39:39 heura8 kernel: [462824.029581] FS:  00007f6ca0c026e0(0000) GS:ffff810257401f00(0000) knlGS:0000000000000000
May 19 01:39:39 heura8 kernel: [462824.029626] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
May 19 01:39:39 heura8 kernel: [462824.029653] CR2: 000000000a0c8004 CR3: 00000001667de000 CR4: 00000000000006e0
May 19 01:39:39 heura8 kernel: [462824.029697] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
May 19 01:39:39 heura8 kernel: [462824.029740] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
May 19 01:39:39 heura8 kernel: [462824.029784] Process mhrecognise (pid: 6549, threadinfo ffff81022fd7a000, task ffff8102549b4fe0)
May 19 01:39:39 heura8 kernel: [462824.029830] Stack:  ffffffff80254550 ffff81022fd7b7d0 0000000000000286 ffff81025201ce10
May 19 01:39:39 heura8 kernel: [462824.029883]  0000000000000000 ffff81025201cd80 ffffffff882ce390 ffff81025201ce70
May 19 01:39:39 heura8 kernel: [462824.029934]  ffff81022fd7b898 ffffffff882bfb3b ffffffff882ce390 ffff81025201cd80
May 19 01:39:39 heura8 kernel: [462824.029968] Call Trace:
May 19 01:39:39 heura8 kernel: [462824.030010]  [<ffffffff80254550>] wake_bit_function+0x0/0x30
May 19 01:39:39 heura8 kernel: [462824.030051]  [sunrpc:__rpc_execute+0x6b/0x290] :sunrpc:__rpc_execute+0x6b/0x290
May 19 01:39:39 heura8 kernel: [462824.030090]  [sunrpc:rpc_do_run_task+0x76/0xd0] :sunrpc:rpc_do_run_task+0x76/0xd0
May 19 01:39:39 heura8 kernel: [462824.030135]  [nfs:decode_getfattr+0x89e/0x1140] :nfs:decode_getfattr+0x89e/0x1140
May 19 01:39:39 heura8 kernel: [462824.030175]  [sunrpc:rpc_call_sync+0x15/0x40] :sunrpc:rpc_call_sync+0x15/0x40
May 19 01:39:39 heura8 kernel: [462824.030214]  [nfs:nfs4_proc_access+0x8f/0x1e0] :nfs:nfs4_proc_access+0x8f/0x1e0
May 19 01:39:39 heura8 kernel: [462824.030255]  [nfs:nfs4_xdr_dec_getattr+0x0/0x60] :nfs:nfs4_xdr_dec_getattr+0x0/0x60
May 19 01:39:39 heura8 kernel: [462824.030294]  [nfs:nfs4_xdr_dec_getattr+0x4f/0x60] :nfs:nfs4_xdr_dec_getattr+0x4f/0x60
May 19 01:39:39 heura8 kernel: [462824.030328]  [__wait_on_bit+0x6b/0x80] __wait_on_bit+0x6b/0x80
May 19 01:39:39 heura8 kernel: [462824.030357]  [__wake_up_common+0x5a/0x90] __wake_up_common+0x5a/0x90
May 19 01:39:39 heura8 kernel: [462824.030399]  [nfs:nfs_do_access+0xda/0x350] :nfs:nfs_do_access+0xda/0x350
May 19 01:39:39 heura8 kernel: [462824.030439]  [nfs:nfs_permission+0xd8/0x1a0] :nfs:nfs_permission+0xd8/0x1a0
May 19 01:39:39 heura8 kernel: [462824.030471]  [nfsd:permission+0xb0/0x1b0] permission+0xb0/0x160
May 19 01:39:39 heura8 kernel: [462824.030500]  [__link_path_walk+0x87/0xe90] __link_path_walk+0x87/0xe90
May 19 01:39:39 heura8 kernel: [462824.030531]  [link_path_walk+0x5b/0x100] link_path_walk+0x5b/0x100
May 19 01:39:39 heura8 kernel: [462824.030560]  [getname+0x33/0x220] getname+0x33/0x220
May 19 01:39:39 heura8 kernel: [462824.030590]  [get_unused_fd_flags+0x77/0x120] get_unused_fd_flags+0x77/0x120
May 19 01:39:39 heura8 kernel: [462824.030622]  [__link_path_walk+0x66a/0xe90] __link_path_walk+0x66a/0xe90
May 19 01:39:39 heura8 kernel: [462824.030654]  [link_path_walk+0x5b/0x100] link_path_walk+0x5b/0x100
May 19 01:39:39 heura8 kernel: [462824.032260]  [getname+0x33/0x220] getname+0x33/0x220
May 19 01:39:39 heura8 kernel: [462824.032289]  [get_unused_fd_flags+0x77/0x120] get_unused_fd_flags+0x77/0x120
May 19 01:39:39 heura8 kernel: [462824.032318]  [__slab_alloc+0x158/0x410] __slab_alloc+0x158/0x410
May 19 01:39:39 heura8 kernel: [462824.032345]  [get_empty_filp+0x31/0x150] get_empty_filp+0x31/0x150
May 19 01:39:39 heura8 kernel: [462824.032375]  [do_path_lookup+0x8a/0x250] do_path_lookup+0x8a/0x250
May 19 01:39:39 heura8 kernel: [462824.032404]  [__path_lookup_intent_open+0x6a/0xd0] __path_lookup_intent_open+0x6a/0xd0
May 19 01:39:39 heura8 kernel: [462824.032435]  [open_namei+0x89/0x710] open_namei+0x89/0x710
May 19 01:39:39 heura8 kernel: [462824.032462]  [<ffffffff80254520>] autoremove_wake_function+0x0/0x30
May 19 01:39:39 heura8 kernel: [462824.032494]  [do_filp_open+0x1c/0x50] do_filp_open+0x1c/0x50
May 19 01:39:39 heura8 kernel: [462824.032522]  [getname+0x33/0x220] getname+0x33/0x220
May 19 01:39:39 heura8 kernel: [462824.032551]  [get_unused_fd_flags+0x77/0x120] get_unused_fd_flags+0x77/0x120
May 19 01:39:39 heura8 kernel: [462824.032581]  [do_sys_open+0x5a/0xf0] do_sys_open+0x5a/0xf0
May 19 01:39:39 heura8 kernel: [462824.032610]  [system_call+0x7e/0x83] system_call+0x7e/0x83
May 19 01:39:39 heura8 kernel: [462824.032640] 
May 19 01:39:39 heura8 kernel: [462824.032659] 
May 19 01:39:39 heura8 kernel: [462824.032659] Code: 0f 0b eb fe 8b 85 b8 00 00 00 0f b7 b7 48 01 00 00 48 c7 c2 
May 19 01:39:39 heura8 kernel: [462824.032758] RIP  [sunrpc:rpcb_getport_async+0x272/0x3c0] :sunrpc:rpcb_getport_async+0x272/0x3c0
May 19 01:39:39 heura8 kernel: [462824.032800]  RSP <ffff81022fd7b7c8>
May 19 01:39:39 heura8 kernel: [462824.033062] ---[ end trace 5d73921843ccffdf ]---
May 19 01:40:43 heura8 kernel: [462886.993115] ------------[ cut here ]------------
May 19 01:40:43 heura8 kernel: [462886.993176] kernel BUG at /build/buildd/linux-2.6.24/net/sunrpc/rpcb_clnt.c:322!
May 19 01:40:43 heura8 kernel: [462886.993251] invalid opcode: 0000 [2] SMP 
May 19 01:40:43 heura8 kernel: [462886.993370] CPU 3 
May 19 01:40:43 heura8 kernel: [462886.993452] Modules linked in: autofs4 ipv6 nfs iptable_filter ip_tables x_tables nfsd lockd nfs_acl auth_rpcgss sunrpc exportfs parport_pc lp parport af_packet psmouse serio_raw evdev iTCO_wdt iTCO_vendor_support button i5000_edac edac_core shpchp pci_hotplug pcspkr ext3 jbd mbcache sg sd_mod ata_piix pata_acpi ehci_hcd ata_generic uhci_hcd usbcore libata scsi_mod e1000 raid10 raid456 async_xor async_memcpy async_tx xor raid1 raid0 multipath linear md_mod dm_mirror dm_snapshot dm_mod thermal processor fan fbcon tileblit font bitblit softcursor fuse
May 19 01:40:43 heura8 kernel: [462886.995781] Pid: 4429, comm: rpciod/3 Tainted: G      D 2.6.24-24-server #1
May 19 01:40:43 heura8 kernel: [462886.995841] RIP: 0010:[sunrpc:rpcb_getport_async+0x272/0x3c0]  [sunrpc:rpcb_getport_async+0x272/0x3c0] :sunrpc:rpcb_getport_async+0x272/0x3c0
May 19 01:40:43 heura8 kernel: [462886.995971] RSP: 0018:ffff810256873e20  EFLAGS: 00010287
May 19 01:40:43 heura8 kernel: [462886.996028] RAX: ffffffff882e65c0 RBX: ffff810250cb2e00 RCX: ffff81024a451a08
May 19 01:40:43 heura8 kernel: [462886.996101] RDX: 00000000ffffff95 RSI: 0000000000000286 RDI: ffff81024a451900
May 19 01:40:43 heura8 kernel: [462886.996175] RBP: ffff8102539d2800 R08: ffff810252de1c88 R09: 00000000ffffffff
May 19 01:40:43 heura8 kernel: [462886.996248] R10: ffff8100809da000 R11: ffffffff882c8640 R12: ffff810250cb2400
May 19 01:40:43 heura8 kernel: [462886.996322] R13: ffff81024a451900 R14: 0000000000000000 R15: 0000000000000000
May 19 01:40:43 heura8 kernel: [462886.996396] FS:  0000000000000000(0000) GS:ffff810257401f00(0000) knlGS:0000000000000000
May 19 01:40:43 heura8 kernel: [462886.996472] CS:  0010 DS: 0018 ES: 0018 CR0: 000000008005003b
May 19 01:40:43 heura8 kernel: [462886.996529] CR2: 00007fe811d58460 CR3: 0000000255413000 CR4: 00000000000006e0
May 19 01:40:43 heura8 kernel: [462886.996602] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
May 19 01:40:43 heura8 kernel: [462886.996676] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
May 19 01:40:43 heura8 kernel: [462886.996751] Process rpciod/3 (pid: 4429, threadinfo ffff810256872000, task ffff81025214e000)
May 19 01:40:43 heura8 kernel: [462886.996827] Stack:  0000000000000000 ffff8102539d2800 0000000000000286 ffff81024a451990
May 19 01:40:43 heura8 kernel: [462886.997065]  0000000000000000 ffff81024a451900 ffff810252de1c80 ffff81024a4519f0
May 19 01:40:43 heura8 kernel: [462886.997268]  0000000000000000 ffffffff882bfb3b ffffffffffffffff ffff810252de1c80
May 19 01:40:43 heura8 kernel: [462886.997426] Call Trace:
May 19 01:40:43 heura8 kernel: [462886.997537]  [sunrpc:__rpc_execute+0x6b/0x290] :sunrpc:__rpc_execute+0x6b/0x290
May 19 01:40:43 heura8 kernel: [462886.997607]  [sunrpc:rpc_async_schedule+0x0/0x10] :sunrpc:rpc_async_schedule+0x0/0x10
May 19 01:40:43 heura8 kernel: [462886.997672]  [run_workqueue+0xcc/0x170] run_workqueue+0xcc/0x170
May 19 01:40:43 heura8 kernel: [462886.997729]  [worker_thread+0x0/0x110] worker_thread+0x0/0x110
May 19 01:40:43 heura8 kernel: [462886.997787]  [worker_thread+0x0/0x110] worker_thread+0x0/0x110
May 19 01:40:43 heura8 kernel: [462886.997845]  [worker_thread+0xa3/0x110] worker_thread+0xa3/0x110
May 19 01:40:43 heura8 kernel: [462886.997904]  [<ffffffff80254520>] autoremove_wake_function+0x0/0x30
May 19 01:40:43 heura8 kernel: [462886.997964]  [worker_thread+0x0/0x110] worker_thread+0x0/0x110
May 19 01:40:43 heura8 kernel: [462886.998022]  [worker_thread+0x0/0x110] worker_thread+0x0/0x110
May 19 01:40:43 heura8 kernel: [462886.998079]  [kthread+0x4b/0x80] kthread+0x4b/0x80
May 19 01:40:43 heura8 kernel: [462886.998137]  [child_rip+0xa/0x12] child_rip+0xa/0x12
May 19 01:40:43 heura8 kernel: [462886.998197]  [kthread+0x0/0x80] kthread+0x0/0x80
May 19 01:40:43 heura8 kernel: [462886.998253]  [child_rip+0x0/0x12] child_rip+0x0/0x12
May 19 01:40:43 heura8 kernel: [462886.998310] 
May 19 01:40:43 heura8 kernel: [462886.998359] 
May 19 01:40:43 heura8 kernel: [462886.998359] Code: 0f 0b eb fe 8b 85 b8 00 00 00 0f b7 b7 48 01 00 00 48 c7 c2 
May 19 01:40:43 heura8 kernel: [462886.999160] RIP  [sunrpc:rpcb_getport_async+0x272/0x3c0] :sunrpc:rpcb_getport_async+0x272/0x3c0
May 19 01:40:43 heura8 kernel: [462886.999263]  RSP <ffff810256873e20>
May 19 01:40:43 heura8 kernel: [462886.999323] ------------[ cut here ]------------
May 19 01:40:43 heura8 kernel: [462886.999326] ---[ end trace 5d73921843ccffdf ]---
May 19 01:40:43 heura8 kernel: [462886.999436] kernel BUG at /build/buildd/linux-2.6.24/net/sunrpc/rpcb_clnt.c:322!
May 19 01:40:43 heura8 kernel: [462886.999512] invalid opcode: 0000 [3] SMP 
May 19 01:40:43 heura8 kernel: [462886.999634] CPU 1 
May 19 01:40:43 heura8 kernel: [462886.999719] Modules linked in: autofs4 ipv6 nfs iptable_filter ip_tables x_tables nfsd lockd nfs_acl auth_rpcgss sunrpc exportfs parport_pc lp parport af_packet psmouse serio_raw evdev iTCO_wdt iTCO_vendor_support button i5000_edac edac_core shpchp pci_hotplug pcspkr ext3 jbd mbcache sg sd_mod ata_piix pata_acpi ehci_hcd ata_generic uhci_hcd usbcore libata scsi_mod e1000 raid10 raid456 async_xor async_memcpy async_tx xor raid1 raid0 multipath linear md_mod dm_mirror dm_snapshot dm_mod thermal processor fan fbcon tileblit font bitblit softcursor fuse
May 19 01:40:43 heura8 kernel: [462887.002113] Pid: 19602, comm: bernoulli_local Tainted: G      D 2.6.24-24-server #1
May 19 01:40:43 heura8 kernel: [462887.002190] RIP: 0010:[sunrpc:rpcb_getport_async+0x272/0x3c0]  [sunrpc:rpcb_getport_async+0x272/0x3c0] :sunrpc:rpcb_getport_async+0x272/0x3c0
May 19 01:40:43 heura8 kernel: [462887.002315] RSP: 0018:ffff81023c8217c8  EFLAGS: 00010287
May 19 01:40:43 heura8 kernel: [462887.002372] RAX: ffffffff882e65c0 RBX: ffff810250cb2e00 RCX: 00000000c0000100
May 19 01:40:43 heura8 kernel: [462887.002448] RDX: 0000000000000000 RSI: 00000000ffffff95 RDI: ffff8100671dd900
May 19 01:40:43 heura8 kernel: [462887.002523] RBP: ffff8102539d2800 R08: ffff81023c820000 R09: 0000000000000000
May 19 01:40:43 heura8 kernel: [462887.002599] R10: ffff810001044c60 R11: ffffffff882c8640 R12: ffff810250cb2400
May 19 01:40:43 heura8 kernel: [462887.002674] R13: ffff8100671dd900 R14: ffff81023c821898 R15: ffff81023c8219c8
May 19 01:40:43 heura8 kernel: [462887.002750] FS:  00007f94dfd3f6e0(0000) GS:ffff810257401800(0000) knlGS:0000000000000000
May 19 01:40:43 heura8 kernel: [462887.002827] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
May 19 01:40:43 heura8 kernel: [462887.002886] CR2: 00007fa05a096000 CR3: 000000017da90000 CR4: 00000000000006e0
May 19 01:40:43 heura8 kernel: [462887.002961] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
May 19 01:40:43 heura8 kernel: [462887.003036] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
May 19 01:40:43 heura8 kernel: [462887.003111] Process bernoulli_local (pid: 19602, threadinfo ffff81023c820000, task ffff8102525da000)
May 19 01:40:43 heura8 kernel: [462887.003189] Stack:  ffff8102539d2b38 ffff8102539d2800 ffff8100671dd900 ffff810250cb2e00
May 19 01:40:43 heura8 kernel: [462887.003435]  0000000000000000 ffff8100671dd900 ffffffff882ce390 ffff8100671dd9f0
May 19 01:40:43 heura8 kernel: [462887.003646]  ffff81023c821898 ffffffff882bfb3b ffffffff882ce390 ffff8100671dd900
May 19 01:40:43 heura8 kernel: [462887.003809] Call Trace:
May 19 01:40:43 heura8 kernel: [462887.003922]  [sunrpc:__rpc_execute+0x6b/0x290] :sunrpc:__rpc_execute+0x6b/0x290
May 19 01:40:43 heura8 kernel: [462887.003994]  [sunrpc:rpc_do_run_task+0x76/0xd0] :sunrpc:rpc_do_run_task+0x76/0xd0
May 19 01:40:43 heura8 kernel: [462887.004065]  [sunrpc:rpcauth_unwrap_resp+0x9e/0xf0] :sunrpc:rpcauth_unwrap_resp+0x9e/0xf0
May 19 01:40:43 heura8 kernel: [462887.004138]  [sunrpc:rpc_call_sync+0x15/0x40] :sunrpc:rpc_call_sync+0x15/0x40
May 19 01:40:43 heura8 kernel: [462887.004214]  [nfs:nfs4_proc_access+0x8f/0x1e0] :nfs:nfs4_proc_access+0x8f/0x1e0
May 19 01:40:43 heura8 kernel: [462887.004276]  [flush_cpu_workqueue+0x40/0x90] flush_cpu_workqueue+0x40/0x90
May 19 01:40:43 heura8 kernel: [462887.004339]  [nfs:__wake_up+0x43/0x1d50] __wake_up+0x43/0x70
May 19 01:40:43 heura8 kernel: [462887.004409]  [sunrpc:rpc_put_task+0x99/0xc0] :sunrpc:rpc_put_task+0x99/0xc0
May 19 01:40:43 heura8 kernel: [462887.004478]  [nfs:nfs_find_actor+0x4a/0x60] :nfs:nfs_find_actor+0x4a/0x60
May 19 01:40:43 heura8 kernel: [462887.004540]  [find_inode+0x43/0x70] find_inode+0x43/0x70
May 19 01:40:43 heura8 kernel: [462887.004604]  [inotify_d_instantiate+0x12/0x40] inotify_d_instantiate+0x12/0x40
May 19 01:40:43 heura8 kernel: [462887.004674]  [nfs:nfs_do_access+0xda/0x350] :nfs:nfs_do_access+0xda/0x350
May 19 01:40:43 heura8 kernel: [462887.004746]  [nfs:nfs_permission+0xd8/0x1a0] :nfs:nfs_permission+0xd8/0x1a0
May 19 01:40:43 heura8 kernel: [462887.004809]  [nfsd:permission+0xb0/0x1b0] permission+0xb0/0x160
May 19 01:40:43 heura8 kernel: [462887.004869]  [__link_path_walk+0x87/0xe90] __link_path_walk+0x87/0xe90
May 19 01:40:43 heura8 kernel: [462887.004933]  [link_path_walk+0x5b/0x100] link_path_walk+0x5b/0x100
May 19 01:40:43 heura8 kernel: [462887.004997]  [get_unused_fd_flags+0x77/0x120] get_unused_fd_flags+0x77/0x120
May 19 01:40:43 heura8 kernel: [462887.005060]  [__link_path_walk+0x66a/0xe90] __link_path_walk+0x66a/0xe90
May 19 01:40:43 heura8 kernel: [462887.005123]  [link_path_walk+0x5b/0x100] link_path_walk+0x5b/0x100
May 19 01:40:43 heura8 kernel: [462887.005186]  [get_unused_fd_flags+0x77/0x120] get_unused_fd_flags+0x77/0x120
May 19 01:40:43 heura8 kernel: [462887.005249]  [do_path_lookup+0x8a/0x250] do_path_lookup+0x8a/0x250
May 19 01:40:43 heura8 kernel: [462887.005309]  [__path_lookup_intent_open+0x6a/0xd0] __path_lookup_intent_open+0x6a/0xd0
May 19 01:40:43 heura8 kernel: [462887.005373]  [open_namei+0xfa/0x710] open_namei+0xfa/0x710
May 19 01:40:43 heura8 kernel: [462887.005434]  [do_page_fault+0x1d0/0x840] do_page_fault+0x1d0/0x840
May 19 01:40:43 heura8 kernel: [462887.005495]  [error_exit+0x0/0x51] error_exit+0x0/0x51
May 19 01:40:43 heura8 kernel: [462887.005556]  [do_filp_open+0x1c/0x50] do_filp_open+0x1c/0x50
May 19 01:40:43 heura8 kernel: [462887.005617]  [get_unused_fd_flags+0x77/0x120] get_unused_fd_flags+0x77/0x120
May 19 01:40:43 heura8 kernel: [462887.005679]  [do_sys_open+0x5a/0xf0] do_sys_open+0x5a/0xf0
May 19 01:40:43 heura8 kernel: [462887.005739]  [system_call+0x7e/0x83] system_call+0x7e/0x83
May 19 01:40:43 heura8 kernel: [462887.005801] 
May 19 01:40:43 heura8 kernel: [462887.005852] 
May 19 01:40:43 heura8 kernel: [462887.005853] Code: 0f 0b eb fe 8b 85 b8 00 00 00 0f b7 b7 48 01 00 00 48 c7 c2 
May 19 01:40:43 heura8 kernel: [462887.006663] RIP  [sunrpc:rpcb_getport_async+0x272/0x3c0] :sunrpc:rpcb_getport_async+0x272/0x3c0
May 19 01:40:43 heura8 kernel: [462887.006767]  RSP <ffff81023c8217c8>
May 19 01:40:43 heura8 kernel: [462887.006830] ---[ end trace 5d73921843ccffdf ]---
May 19 01:40:43 heura8 kernel: [462887.007018] ------------[ cut here ]------------
May 19 01:40:43 heura8 kernel: [462887.007075] kernel BUG at /build/buildd/linux-2.6.24/net/sunrpc/rpcb_clnt.c:322!
May 19 01:40:43 heura8 kernel: [462887.007150] invalid opcode: 0000 [4] SMP 
May 19 01:40:43 heura8 kernel: [462887.007269] CPU 3 
May 19 01:40:43 heura8 kernel: [462887.007351] Modules linked in: autofs4 ipv6 nfs iptable_filter ip_tables x_tables nfsd lockd nfs_acl auth_rpcgss sunrpc exportfs parport_pc lp parport af_packet psmouse serio_raw evdev iTCO_wdt iTCO_vendor_support button i5000_edac edac_core shpchp pci_hotplug pcspkr ext3 jbd mbcache sg sd_mod ata_piix pata_acpi ehci_hcd ata_generic uhci_hcd usbcore libata scsi_mod e1000 raid10 raid456 async_xor async_memcpy async_tx xor raid1 raid0 multipath linear md_mod dm_mirror dm_snapshot dm_mod thermal processor fan fbcon tileblit font bitblit softcursor fuse
May 19 01:40:43 heura8 kernel: [462887.009685] Pid: 19281, comm: HVite Tainted: G      D 2.6.24-24-server #1
May 19 01:40:43 heura8 kernel: [462887.009745] RIP: 0010:[sunrpc:rpcb_getport_async+0x272/0x3c0]  [sunrpc:rpcb_getport_async+0x272/0x3c0] :sunrpc:rpcb_getport_async+0x272/0x3c0
May 19 01:40:43 heura8 kernel: [462887.011448] RSP: 0018:ffff810176fc9918  EFLAGS: 00010287
May 19 01:40:43 heura8 kernel: [462887.011504] RAX: ffffffff882e65c0 RBX: ffff810250cb2e00 RCX: 0000000000000000
May 19 01:40:43 heura8 kernel: [462887.011578] RDX: 0000000000000000 RSI: 00000000ffffff95 RDI: ffff81025201c180
May 19 01:40:43 heura8 kernel: [462887.011652] RBP: ffff8102539d2800 R08: 0000000000000000 R09: 0000000000000000
May 19 01:40:43 heura8 kernel: [462887.011726] R10: ffff81000105ac60 R11: ffffffff882c8640 R12: ffff810250cb2400
May 19 01:40:43 heura8 kernel: [462887.011799] R13: ffff81025201c180 R14: ffff810176fc99e8 R15: ffff810176fc9b18
May 19 01:40:43 heura8 kernel: [462887.011874] FS:  0000000000000000(0000) GS:ffff810257401f00(0063) knlGS:00000000f7dbcb60
May 19 01:40:43 heura8 kernel: [462887.011949] CS:  0010 DS: 002b ES: 002b CR0: 0000000080050033
May 19 01:40:43 heura8 kernel: [462887.012007] CR2: 00007fe811d58460 CR3: 000000017db49000 CR4: 00000000000006e0
May 19 01:40:43 heura8 kernel: [462887.012080] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
May 19 01:40:43 heura8 kernel: [462887.012154] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
May 19 01:40:43 heura8 kernel: [462887.012228] Process HVite (pid: 19281, threadinfo ffff810176fc8000, task ffff81025128d7d0)
May 19 01:40:43 heura8 kernel: [462887.012304] Stack:  ffff8102539d2b38 ffff8102539d2800 ffff81025201c180 ffff810250cb2e00
May 19 01:40:43 heura8 kernel: [462887.012542]  0000000000000000 ffff81025201c180 ffffffff882ce390 ffff81025201c270
May 19 01:40:43 heura8 kernel: [462887.012746]  ffff810176fc99e8 ffffffff882bfb3b ffffffff882ce390 ffff81025201c180
May 19 01:40:43 heura8 kernel: [462887.012904] Call Trace:
May 19 01:40:43 heura8 kernel: [462887.013015]  [sunrpc:__rpc_execute+0x6b/0x290] :sunrpc:__rpc_execute+0x6b/0x290
May 19 01:40:43 heura8 kernel: [462887.013085]  [sunrpc:rpc_do_run_task+0x76/0xd0] :sunrpc:rpc_do_run_task+0x76/0xd0
May 19 01:40:43 heura8 kernel: [462887.013155]  [sunrpc:rpc_call_sync+0x15/0x40] :sunrpc:rpc_call_sync+0x15/0x40
May 19 01:40:43 heura8 kernel: [462887.013225]  [nfs:nfs4_proc_access+0x8f/0x1e0] :nfs:nfs4_proc_access+0x8f/0x1e0
May 19 01:40:43 heura8 kernel: [462887.013295]  [ext3:__ext3_journal_dirty_metadata+0x2c/0x70] :ext3:__ext3_journal_dirty_metadata+0x2c/0x70
May 19 01:40:43 heura8 kernel: [462887.013375]  [ext3:ext3_mark_iloc_dirty+0x186/0x350] :ext3:ext3_mark_iloc_dirty+0x186/0x350
May 19 01:40:43 heura8 kernel: [462887.013451]  [nfs:nfs_do_access+0xda/0x350] :nfs:nfs_do_access+0xda/0x350
May 19 01:40:43 heura8 kernel: [462887.013522]  [nfs:nfs_permission+0xd8/0x1a0] :nfs:nfs_permission+0xd8/0x1a0
May 19 01:40:43 heura8 kernel: [462887.013582]  [nfsd:permission+0xb0/0x1b0] permission+0xb0/0x160
May 19 01:40:43 heura8 kernel: [462887.013641]  [__link_path_walk+0x87/0xe90] __link_path_walk+0x87/0xe90
May 19 01:40:43 heura8 kernel: [462887.013703]  [link_path_walk+0x5b/0x100] link_path_walk+0x5b/0x100
May 19 01:40:43 heura8 kernel: [462887.013765]  [get_unused_fd_flags+0x77/0x120] get_unused_fd_flags+0x77/0x120
May 19 01:40:43 heura8 kernel: [462887.013825]  [nfs:generic_file_aio_write+0x6f/0x220] generic_file_aio_write+0x6f/0xd0
May 19 01:40:43 heura8 kernel: [462887.013886]  [do_path_lookup+0x8a/0x250] do_path_lookup+0x8a/0x250
May 19 01:40:43 heura8 kernel: [462887.013946]  [__path_lookup_intent_open+0x6a/0xd0] __path_lookup_intent_open+0x6a/0xd0
May 19 01:40:43 heura8 kernel: [462887.014006]  [open_namei+0xfa/0x710] open_namei+0xfa/0x710
May 19 01:40:43 heura8 kernel: [462887.014065]  [<ffffffff80254520>] autoremove_wake_function+0x0/0x30
May 19 01:40:43 heura8 kernel: [462887.014127]  [do_filp_open+0x1c/0x50] do_filp_open+0x1c/0x50
May 19 01:40:43 heura8 kernel: [462887.014188]  [get_unused_fd_flags+0x77/0x120] get_unused_fd_flags+0x77/0x120
May 19 01:40:43 heura8 kernel: [462887.014248]  [do_sys_open+0x5a/0xf0] do_sys_open+0x5a/0xf0
May 19 01:40:43 heura8 kernel: [462887.014308]  [sysenter_do_call+0x1b/0x67] sysenter_do_call+0x1b/0x67
May 19 01:40:43 heura8 kernel: [462887.014368]  [dummy_vm_enough_memory+0x0/0x50] dummy_vm_enough_memory+0x0/0x50
May 19 01:40:43 heura8 kernel: [462887.014429] 
May 19 01:40:43 heura8 kernel: [462887.014478] 
May 19 01:40:43 heura8 kernel: [462887.014478] Code: 0f 0b eb fe 8b 85 b8 00 00 00 0f b7 b7 48 01 00 00 48 c7 c2 
May 19 01:40:43 heura8 kernel: [462887.015282] RIP  [sunrpc:rpcb_getport_async+0x272/0x3c0] :sunrpc:rpcb_getport_async+0x272/0x3c0
May 19 01:40:43 heura8 kernel: [462887.015385]  RSP <ffff810176fc9918>
May 19 01:40:43 heura8 kernel: [462887.015466] ---[ end trace 5d73921843ccffdf ]---
May 19 01:40:43 heura8 kernel: [462887.015943] ------------[ cut here ]------------
May 19 01:40:43 heura8 kernel: [462887.016000] kernel BUG at /build/buildd/linux-2.6.24/net/sunrpc/rpcb_clnt.c:322!
May 19 01:40:43 heura8 kernel: [462887.016076] invalid opcode: 0000 [5] SMP 
May 19 01:40:43 heura8 kernel: [462887.016197] CPU 1 
May 19 01:40:43 heura8 kernel: [462887.016281] Modules linked in: autofs4 ipv6 nfs iptable_filter ip_tables x_tables nfsd lockd nfs_acl auth_rpcgss sunrpc exportfs parport_pc lp parport af_packet psmouse serio_raw evdev iTCO_wdt iTCO_vendor_support button i5000_edac edac_core shpchp pci_hotplug pcspkr ext3 jbd mbcache sg sd_mod ata_piix pata_acpi ehci_hcd ata_generic uhci_hcd usbcore libata scsi_mod e1000 raid10 raid456 async_xor async_memcpy async_tx xor raid1 raid0 multipath linear md_mod dm_mirror dm_snapshot dm_mod thermal processor fan fbcon tileblit font bitblit softcursor fuse
May 19 01:40:43 heura8 kernel: [462887.018679] Pid: 18887, comm: HVite Tainted: G      D 2.6.24-24-server #1
May 19 01:40:43 heura8 kernel: [462887.018739] RIP: 0010:[sunrpc:rpcb_getport_async+0x272/0x3c0]  [sunrpc:rpcb_getport_async+0x272/0x3c0] :sunrpc:rpcb_getport_async+0x272/0x3c0
May 19 01:40:43 heura8 kernel: [462887.018863] RSP: 0018:ffff810100533918  EFLAGS: 00010287
May 19 01:40:43 heura8 kernel: [462887.018920] RAX: ffffffff882e65c0 RBX: ffff810250cb2e00 RCX: ffffffff802392ec
May 19 01:40:43 heura8 kernel: [462887.018995] RDX: 0000000000000000 RSI: 00000000ffffff95 RDI: ffff8100671dd180
May 19 01:40:43 heura8 kernel: [462887.019070] RBP: ffff8102539d2800 R08: 0000000000000000 R09: 0000000000000000
May 19 01:40:43 heura8 kernel: [462887.019145] R10: 0000000000000000 R11: ffffffff882c8640 R12: ffff810250cb2400
May 19 01:40:43 heura8 kernel: [462887.019220] R13: ffff8100671dd180 R14: ffff8101005339e8 R15: ffff810100533b18
May 19 01:40:43 heura8 kernel: [462887.019295] FS:  0000000000000000(0000) GS:ffff810257401800(0063) knlGS:00000000f7deeb60
May 19 01:40:43 heura8 kernel: [462887.019372] CS:  0010 DS: 002b ES: 002b CR0: 0000000080050033
May 19 01:40:43 heura8 kernel: [462887.019430] CR2: 00007fa05a096000 CR3: 000000023f066000 CR4: 00000000000006e0
May 19 01:40:43 heura8 kernel: [462887.019505] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
May 19 01:40:43 heura8 kernel: [462887.019580] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
May 19 01:40:43 heura8 kernel: [462887.019657] Process HVite (pid: 18887, threadinfo ffff810100532000, task ffff810252c6efe0)
May 19 01:40:43 heura8 kernel: [462887.019734] Stack:  ffff8102539d2b38 ffff8102539d2800 ffff8100671dd180 ffff810250cb2e00
May 19 01:40:43 heura8 kernel: [462887.019980]  0000000000000000 ffff8100671dd180 ffffffff882ce390 ffff8100671dd270
May 19 01:40:43 heura8 kernel: [462887.020189]  ffff8101005339e8 ffffffff882bfb3b ffffffff882ce390 ffff8100671dd180
May 19 01:40:43 heura8 kernel: [462887.020350] Call Trace:
May 19 01:40:43 heura8 kernel: [462887.020462]  [sunrpc:__rpc_execute+0x6b/0x290] :sunrpc:__rpc_execute+0x6b/0x290
May 19 01:40:43 heura8 kernel: [462887.020534]  [sunrpc:rpc_do_run_task+0x76/0xd0] :sunrpc:rpc_do_run_task+0x76/0xd0
May 19 01:40:43 heura8 kernel: [462887.020605]  [sunrpc:rpc_call_sync+0x15/0x40] :sunrpc:rpc_call_sync+0x15/0x40
May 19 01:40:43 heura8 kernel: [462887.020676]  [nfs:nfs4_proc_access+0x8f/0x1e0] :nfs:nfs4_proc_access+0x8f/0x1e0
May 19 01:40:43 heura8 kernel: [462887.020745]  [ext3:__ext3_journal_dirty_metadata+0x2c/0x70] :ext3:__ext3_journal_dirty_metadata+0x2c/0x70
May 19 01:40:43 heura8 kernel: [462887.020827]  [ext3:ext3_mark_iloc_dirty+0x186/0x350] :ext3:ext3_mark_iloc_dirty+0x186/0x350
May 19 01:40:43 heura8 kernel: [462887.020905]  [nfs:nfs_do_access+0xda/0x350] :nfs:nfs_do_access+0xda/0x350
May 19 01:40:43 heura8 kernel: [462887.020976]  [nfs:nfs_permission+0xd8/0x1a0] :nfs:nfs_permission+0xd8/0x1a0
May 19 01:40:43 heura8 kernel: [462887.021039]  [nfsd:permission+0xb0/0x1b0] permission+0xb0/0x160
May 19 01:40:43 heura8 kernel: [462887.021099]  [__link_path_walk+0x87/0xe90] __link_path_walk+0x87/0xe90
May 19 01:40:43 heura8 kernel: [462887.021162]  [link_path_walk+0x5b/0x100] link_path_walk+0x5b/0x100
May 19 01:40:43 heura8 kernel: [462887.021226]  [get_unused_fd_flags+0x77/0x120] get_unused_fd_flags+0x77/0x120
May 19 01:40:43 heura8 kernel: [462887.021286]  [nfs:generic_file_aio_write+0x6f/0x220] generic_file_aio_write+0x6f/0xd0
May 19 01:40:43 heura8 kernel: [462887.021348]  [do_path_lookup+0x8a/0x250] do_path_lookup+0x8a/0x250
May 19 01:40:43 heura8 kernel: [462887.021409]  [__path_lookup_intent_open+0x6a/0xd0] __path_lookup_intent_open+0x6a/0xd0
May 19 01:40:43 heura8 kernel: [462887.021472]  [open_namei+0xfa/0x710] open_namei+0xfa/0x710
May 19 01:40:43 heura8 kernel: [462887.021531]  [<ffffffff80254520>] autoremove_wake_function+0x0/0x30
May 19 01:40:43 heura8 kernel: [462887.021594]  [do_filp_open+0x1c/0x50] do_filp_open+0x1c/0x50
May 19 01:40:43 heura8 kernel: [462887.021656]  [get_unused_fd_flags+0x77/0x120] get_unused_fd_flags+0x77/0x120
May 19 01:40:43 heura8 kernel: [462887.021718]  [do_sys_open+0x5a/0xf0] do_sys_open+0x5a/0xf0
May 19 01:40:43 heura8 kernel: [462887.021779]  [sysenter_do_call+0x1b/0x67] sysenter_do_call+0x1b/0x67
May 19 01:40:43 heura8 kernel: [462887.021838]  [dummy_vm_enough_memory+0x0/0x50] dummy_vm_enough_memory+0x0/0x50
May 19 01:40:43 heura8 kernel: [462887.021900] 
May 19 01:40:43 heura8 kernel: [462887.021951] 
May 19 01:40:43 heura8 kernel: [462887.021952] Code: 0f 0b eb fe 8b 85 b8 00 00 00 0f b7 b7 48 01 00 00 48 c7 c2 
May 19 01:40:43 heura8 kernel: [462887.022764] RIP  [sunrpc:rpcb_getport_async+0x272/0x3c0] :sunrpc:rpcb_getport_async+0x272/0x3c0
May 19 01:40:43 heura8 kernel: [462887.022867]  RSP <ffff810100533918>
May 19 01:40:43 heura8 kernel: [462887.022924] ---[ end trace 5d73921843ccffdf ]---
May 19 01:40:43 heura8 kernel: [462887.026715] ------------[ cut here ]------------
May 19 01:40:43 heura8 kernel: [462887.026776] kernel BUG at /build/buildd/linux-2.6.24/net/sunrpc/rpcb_clnt.c:322!
May 19 01:40:43 heura8 kernel: [462887.026851] invalid opcode: 0000 [6] SMP 
May 19 01:40:43 heura8 kernel: [462887.026970] CPU 1 
May 19 01:40:43 heura8 kernel: [462887.027053] Modules linked in: autofs4 ipv6 nfs iptable_filter ip_tables x_tables nfsd lockd nfs_acl auth_rpcgss sunrpc exportfs parport_pc lp parport af_packet psmouse serio_raw evdev iTCO_wdt iTCO_vendor_support button i5000_edac edac_core shpchp pci_hotplug pcspkr ext3 jbd mbcache sg sd_mod ata_piix pata_acpi ehci_hcd ata_generic uhci_hcd usbcore libata scsi_mod e1000 raid10 raid456 async_xor async_memcpy async_tx xor raid1 raid0 multipath linear md_mod dm_mirror dm_snapshot dm_mod thermal processor fan fbcon tileblit font bitblit softcursor fuse
May 19 01:40:43 heura8 kernel: [462887.029391] Pid: 18887, comm: HVite Tainted: G      D 2.6.24-24-server #1
May 19 01:40:43 heura8 kernel: [462887.029450] RIP: 0010:[sunrpc:rpcb_getport_async+0x272/0x3c0]  [sunrpc:rpcb_getport_async+0x272/0x3c0] :sunrpc:rpcb_getport_async+0x272/0x3c0
May 19 01:40:43 heura8 kernel: [462887.029577] RSP: 0018:ffff810100533568  EFLAGS: 00010287
May 19 01:40:43 heura8 kernel: [462887.029634] RAX: ffffffff882e65c0 RBX: ffff810250cb2e00 RCX: ffffffff80288483
May 19 01:40:43 heura8 kernel: [462887.029708] RDX: ffffffff882e65c0 RSI: 0000000000011200 RDI: ffff8100671dda80
May 19 01:40:43 heura8 kernel: [462887.029782] RBP: ffff8102539d2800 R08: 0000000000000000 R09: 000000000000006d
May 19 01:40:43 heura8 kernel: [462887.029856] R10: 0000000000000001 R11: ffffffff882c8640 R12: ffff810250cb2400
May 19 01:40:43 heura8 kernel: [462887.029930] R13: ffff8100671dda80 R14: ffff81011d41f100 R15: 0000000000000001
May 19 01:40:43 heura8 kernel: [462887.030004] FS:  0000000000000000(0000) GS:ffff810257401800(0000) knlGS:0000000000000000
May 19 01:40:43 heura8 kernel: [462887.030080] CS:  0010 DS: 002b ES: 002b CR0: 0000000080050033
May 19 01:40:43 heura8 kernel: [462887.030137] CR2: 00007fa05a096000 CR3: 0000000000201000 CR4: 00000000000006e0
May 19 01:40:43 heura8 kernel: [462887.030211] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
May 19 01:40:43 heura8 kernel: [462887.030285] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
May 19 01:40:43 heura8 kernel: [462887.030359] Process HVite (pid: 18887, threadinfo ffff810100532000, task ffff810252c6efe0)
May 19 01:40:43 heura8 kernel: [462887.030435] Stack:  ffff8100671dda80 ffffffff883bdf80 ffff810250cd8bd0 ffffffff882b98c0
May 19 01:40:43 heura8 kernel: [462887.030673]  0000000000000000 ffff8100671dda80 ffffffff883a4ff0 ffff8100671ddb70
May 19 01:40:43 heura8 kernel: [462887.030877]  ffff81011d41f100 ffffffff882bfb3b ffffffff883a4ff0 ffff8100671dda80
May 19 01:40:43 heura8 kernel: [462887.031035] Call Trace:
May 19 01:40:43 heura8 kernel: [462887.031145]  [sunrpc:call_allocate+0xc0/0x1b0] :sunrpc:call_allocate+0xc0/0x1b0
May 19 01:40:43 heura8 kernel: [462887.031215]  [sunrpc:__rpc_execute+0x6b/0x290] :sunrpc:__rpc_execute+0x6b/0x290
May 19 01:40:43 heura8 kernel: [462887.031285]  [sunrpc:rpc_do_run_task+0x76/0xd0] :sunrpc:rpc_do_run_task+0x76/0xd0
May 19 01:40:43 heura8 kernel: [462887.032941]  [nfs:nfs4_do_close+0xe0/0x140] :nfs:nfs4_do_close+0xe0/0x140
May 19 01:40:43 heura8 kernel: [462887.033010]  [nfs:__put_nfs_open_context+0x77/0xf0] :nfs:__put_nfs_open_context+0x77/0xf0
May 19 01:40:43 heura8 kernel: [462887.033079]  [nfs:nfs_release+0x72/0x80] :nfs:nfs_release+0x72/0x80
May 19 01:40:43 heura8 kernel: [462887.033140]  [__fput+0xb1/0x1c0] __fput+0xb1/0x1c0
May 19 01:40:43 heura8 kernel: [462887.033199]  [filp_close+0x54/0x90] filp_close+0x54/0x90
May 19 01:40:43 heura8 kernel: [462887.033258]  [put_files_struct+0xb1/0xd0] put_files_struct+0xb1/0xd0
May 19 01:40:43 heura8 kernel: [462887.033317]  [do_exit+0x1dd/0x950] do_exit+0x1dd/0x950
May 19 01:40:43 heura8 kernel: [462887.033376]  [nfs:__wake_up+0x43/0x1d50] __wake_up+0x43/0x70
May 19 01:40:43 heura8 kernel: [462887.033436]  [die+0x52/0x70] die+0x52/0x70
May 19 01:40:43 heura8 kernel: [462887.033493]  [do_invalid_op+0x86/0xa0] do_invalid_op+0x86/0xa0
May 19 01:40:43 heura8 kernel: [462887.033561]  [sunrpc:rpcb_getport_async+0x272/0x3c0] :sunrpc:rpcb_getport_async+0x272/0x3c0
May 19 01:40:43 heura8 kernel: [462887.033627]  [error_exit+0x0/0x51] error_exit+0x0/0x51
May 19 01:40:43 heura8 kernel: [462887.033695]  [sunrpc:rpcb_getport_async+0x0/0x3c0] :sunrpc:rpcb_getport_async+0x0/0x3c0
May 19 01:40:43 heura8 kernel: [462887.033757]  [finish_task_switch+0xac/0xb0] finish_task_switch+0xac/0xb0
May 19 01:40:43 heura8 kernel: [462887.033826]  [sunrpc:rpcb_getport_async+0x272/0x3c0] :sunrpc:rpcb_getport_async+0x272/0x3c0
May 19 01:40:43 heura8 kernel: [462887.033898]  [sunrpc:rpc_wake_up_status+0x1f/0xa0] :sunrpc:rpc_wake_up_status+0x1f/0xa0
May 19 01:40:43 heura8 kernel: [462887.033969]  [sunrpc:__rpc_execute+0x6b/0x290] :sunrpc:__rpc_execute+0x6b/0x290
May 19 01:40:43 heura8 kernel: [462887.034039]  [sunrpc:rpc_do_run_task+0x76/0xd0] :sunrpc:rpc_do_run_task+0x76/0xd0
May 19 01:40:43 heura8 kernel: [462887.034110]  [sunrpc:rpc_call_sync+0x15/0x40] :sunrpc:rpc_call_sync+0x15/0x40
May 19 01:40:43 heura8 kernel: [462887.034179]  [nfs:nfs4_proc_access+0x8f/0x1e0] :nfs:nfs4_proc_access+0x8f/0x1e0
May 19 01:40:43 heura8 kernel: [462887.034247]  [ext3:__ext3_journal_dirty_metadata+0x2c/0x70] :ext3:__ext3_journal_dirty_metadata+0x2c/0x70
May 19 01:40:43 heura8 kernel: [462887.034328]  [ext3:ext3_mark_iloc_dirty+0x186/0x350] :ext3:ext3_mark_iloc_dirty+0x186/0x350
May 19 01:40:43 heura8 kernel: [462887.034404]  [nfs:nfs_do_access+0xda/0x350] :nfs:nfs_do_access+0xda/0x350
May 19 01:40:43 heura8 kernel: [462887.034475]  [nfs:nfs_permission+0xd8/0x1a0] :nfs:nfs_permission+0xd8/0x1a0
May 19 01:40:43 heura8 kernel: [462887.034536]  [nfsd:permission+0xb0/0x1b0] permission+0xb0/0x160
May 19 01:40:43 heura8 kernel: [462887.034595]  [__link_path_walk+0x87/0xe90] __link_path_walk+0x87/0xe90
May 19 01:40:43 heura8 kernel: [462887.034657]  [link_path_walk+0x5b/0x100] link_path_walk+0x5b/0x100
May 19 01:40:43 heura8 kernel: [462887.034719]  [get_unused_fd_flags+0x77/0x120] get_unused_fd_flags+0x77/0x120
May 19 01:40:43 heura8 kernel: [462887.034779]  [nfs:generic_file_aio_write+0x6f/0x220] generic_file_aio_write+0x6f/0xd0
May 19 01:40:43 heura8 kernel: [462887.034839]  [do_path_lookup+0x8a/0x250] do_path_lookup+0x8a/0x250
May 19 01:40:43 heura8 kernel: [462887.034899]  [__path_lookup_intent_open+0x6a/0xd0] __path_lookup_intent_open+0x6a/0xd0
May 19 01:40:43 heura8 kernel: [462887.034960]  [open_namei+0xfa/0x710] open_namei+0xfa/0x710
May 19 01:40:43 heura8 kernel: [462887.035019]  [<ffffffff80254520>] autoremove_wake_function+0x0/0x30
May 19 01:40:43 heura8 kernel: [462887.035081]  [do_filp_open+0x1c/0x50] do_filp_open+0x1c/0x50
May 19 01:40:43 heura8 kernel: [462887.035142]  [get_unused_fd_flags+0x77/0x120] get_unused_fd_flags+0x77/0x120
May 19 01:40:43 heura8 kernel: [462887.035202]  [do_sys_open+0x5a/0xf0] do_sys_open+0x5a/0xf0
May 19 01:40:43 heura8 kernel: [462887.035262]  [sysenter_do_call+0x1b/0x67] sysenter_do_call+0x1b/0x67
May 19 01:40:43 heura8 kernel: [462887.035320]  [dummy_vm_enough_memory+0x0/0x50] dummy_vm_enough_memory+0x0/0x50
May 19 01:40:43 heura8 kernel: [462887.035382] 
May 19 01:40:43 heura8 kernel: [462887.035431] 
May 19 01:40:43 heura8 kernel: [462887.035431] Code: 0f 0b eb fe 8b 85 b8 00 00 00 0f b7 b7 48 01 00 00 48 c7 c2 
May 19 01:40:43 heura8 kernel: [462887.036235] RIP  [sunrpc:rpcb_getport_async+0x272/0x3c0] :sunrpc:rpcb_getport_async+0x272/0x3c0
May 19 01:40:43 heura8 kernel: [462887.036338]  RSP <ffff810100533568>
May 19 01:40:43 heura8 kernel: [462887.036405] ---[ end trace 5d73921843ccffdf ]---
May 19 01:40:43 heura8 kernel: [462887.036462] Fixing recursive fault but reboot is needed!

---

