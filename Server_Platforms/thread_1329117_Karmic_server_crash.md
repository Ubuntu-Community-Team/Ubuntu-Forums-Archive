---
title: "Karmic server crash"
date: 2009-11-17
forum: Server Platforms
---

### Post by wyldfury on 2009-11-17
Hi,

Had a server crash yesterday. Found two bits of information in syslog just prior to the crash and I've included them below.
Does anyone have an idea what has caused the problem? Narrowing down to the offending programs would at least let me make bug reports.

Thanks
Guy

> Nov 16 18:12:15 stoat kernel: [381514.433739] BUG: soft lockup - CPU#3 stuck for 61s! [imap:31104]
Nov 16 18:12:15 stoat kernel: [381514.433751] Modules linked in: ocfs2 quota_tree ocfs2_dlmfs ocfs2_stack_o2cb ocfs2_dlm ocfs2_nodemanager ocfs2_stackglue configfs crc32c ib_iser rdma_cm ib_cm iw_cm ib_sa ib_mad ib_core ib_addr iscsi_tcp libiscsi_tcp libiscsi scsi_transport_iscsi nfsd exportfs nfs lockd nfs_acl auth_rpcgss sunrpc iptable_filter ip_tables x_tables lp parport psmouse serio_raw 3w_9xxx sky2
Nov 16 18:12:15 stoat kernel: [381514.433751] CPU 3:
Nov 16 18:12:15 stoat kernel: [381514.433751] Modules linked in: ocfs2 quota_tree ocfs2_dlmfs ocfs2_stack_o2cb ocfs2_dlm ocfs2_nodemanager ocfs2_stackglue configfs crc32c ib_iser rdma_cm ib_cm iw_cm ib_sa ib_mad ib_core ib_addr iscsi_tcp libiscsi_tcp libiscsi scsi_transport_iscsi nfsd exportfs nfs lockd nfs_acl auth_rpcgss sunrpc iptable_filter ip_tables x_tables lp parport psmouse serio_raw 3w_9xxx sky2
Nov 16 18:12:15 stoat kernel: [381514.433751] Pid: 31104, comm: imap Tainted: G      D    2.6.31-14-server #48-Ubuntu System Product Name
Nov 16 18:12:15 stoat kernel: [381514.433751] RIP: 0010:[<ffffffff815258b0>]  [<ffffffff815258b0>] __mutex_lock_slowpath+0x30/0x160
Nov 16 18:12:15 stoat kernel: [381514.433751] RSP: 0018:ffff880046a45ba8  EFLAGS: 00000286
Nov 16 18:12:15 stoat kernel: [381514.433751] RAX: 00000000fffffffe RBX: ffff880046a45c08 RCX: 0000000000000012
Nov 16 18:12:15 stoat kernel: [381514.433751] RDX: 0000000000000000 RSI: ffff880076e8c000 RDI: ffff880043c18e28
Nov 16 18:12:15 stoat kernel: [381514.433751] RBP: ffffffff81012b6e R08: ffff88007c0ee900 R09: 0000000000000001
Nov 16 18:12:15 stoat kernel: [381514.433751] R10: 0000000000000000 R11: 0000000000000246 R12: ffff880046a45b98
Nov 16 18:12:15 stoat kernel: [381514.433751] R13: ffffffff81012b6e R14: ffffffff8152966f R15: ffff880046a45b48
Nov 16 18:12:15 stoat kernel: [381514.433751] FS:  00007ff2cfefa6f0(0000) GS:ffff880001a4c000(0000) knlGS:0000000000000000
Nov 16 18:12:15 stoat kernel: [381514.433751] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Nov 16 18:12:15 stoat kernel: [381514.433751] CR2: 000000000045f600 CR3: 0000000053d69000 CR4: 00000000000006e0
Nov 16 18:12:15 stoat kernel: [381514.433751] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Nov 16 18:12:15 stoat kernel: [381514.433751] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Nov 16 18:12:15 stoat kernel: [381514.433751] Call Trace:
Nov 16 18:12:15 stoat kernel: [381514.433751]  [<ffffffff815258c5>] ? __mutex_lock_slowpath+0x45/0x160
Nov 16 18:12:15 stoat kernel: [381514.433751]  [<ffffffffa00e4fc1>] ? nfs_access_get_cached+0x71/0x190 [nfs]
Nov 16 18:12:15 stoat kernel: [381514.433751]  [<ffffffff815253ce>] ? mutex_lock+0x1e/0x40
Nov 16 18:12:15 stoat kernel: [381514.433751]  [<ffffffff811277a9>] ? real_lookup+0x39/0x150
Nov 16 18:12:15 stoat kernel: [381514.433751]  [<ffffffff81129440>] ? do_lookup+0xb0/0xe0
Nov 16 18:12:15 stoat kernel: [381514.433751]  [<ffffffff81129fed>] ? __link_path_walk+0x6ad/0xdc0
Nov 16 18:12:15 stoat kernel: [381514.433751]  [<ffffffff810dbdd6>] ? generic_file_aio_read+0xb6/0x1d0
Nov 16 18:12:15 stoat kernel: [381514.433751]  [<ffffffff8112a8e7>] ? path_walk+0x57/0xb0
Nov 16 18:12:15 stoat kernel: [381514.433751]  [<ffffffff8112a993>] ? do_path_lookup+0x53/0xa0
Nov 16 18:12:15 stoat kernel: [381514.433751]  [<ffffffff8112b632>] ? user_path_at+0x52/0xa0
Nov 16 18:12:15 stoat kernel: [381514.433751]  [<ffffffff81122827>] ? vfs_fstatat+0x37/0x70
Nov 16 18:12:15 stoat kernel: [381514.433751]  [<ffffffff812767ca>] ? __up_read+0x9a/0xc0
Nov 16 18:12:15 stoat kernel: [381514.433751]  [<ffffffff81122986>] ? vfs_stat+0x16/0x20
Nov 16 18:12:15 stoat kernel: [381514.433751]  [<ffffffff811229af>] ? sys_newstat+0x1f/0x50
Nov 16 18:12:15 stoat kernel: [381514.433751]  [<ffffffff8152966f>] ? do_page_fault+0x18f/0x360
Nov 16 18:12:15 stoat kernel: [381514.433751]  [<ffffffff815272e9>] ? do_device_not_available+0x9/0x10
Nov 16 18:12:15 stoat kernel: [381514.433751]  [<ffffffff81012e5b>] ? device_not_available+0x1b/0x20
Nov 16 18:12:15 stoat kernel: [381514.433751]  [<ffffffff81011fc2>] ? system_call_fastpath+0x16/0x1b

> Nov 16 18:20:02 stoat kernel: [381981.250995] BUG: unable to handle kernel paging request at 0000001d00008038
Nov 16 18:20:02 stoat kernel: [381981.251039] IP: [<ffffffffa0080c22>] rpcauth_checkverf+0x32/0x70 [sunrpc]
Nov 16 18:20:02 stoat kernel: [381981.251097] PGD 42d17067 PUD 0
Nov 16 18:20:02 stoat kernel: [381981.251127] Oops: 0000 [#2] SMP
Nov 16 18:20:02 stoat kernel: [381981.251157] last sysfs file: /sys/fs/o2cb/interface_revision
Nov 16 18:20:02 stoat kernel: [381981.251190] CPU 0
Nov 16 18:20:02 stoat kernel: [381981.251216] Modules linked in: ocfs2 quota_tree ocfs2_dlmfs ocfs2_stack_o2cb ocfs2_dlm ocfs2_nodemanager ocfs2_stackglue configfs crc32c ib_iser rdma_cm ib_cm iw_cm ib_sa ib_mad ib_core ib_addr iscsi_tcp libiscsi_tcp libiscsi scsi_transport_iscsi nfsd exportfs nfs lockd nfs_acl auth_rpcgss sunrpc iptable_filter ip_tables x_tables lp parport psmouse serio_raw 3w_9xxx sky2
Nov 16 18:20:02 stoat kernel: [381981.251446] Pid: 5551, comm: maildrop Tainted: G      D    2.6.31-14-server #48-Ubuntu System Product Name
Nov 16 18:20:02 stoat kernel: [381981.251502] RIP: 0010:[<ffffffffa0080c22>]  [<ffffffffa0080c22>] rpcauth_checkverf+0x32/0x70 [sunrpc]
Nov 16 18:20:02 stoat kernel: [381981.251571] RSP: 0018:ffff880018003848  EFLAGS: 00010246
Nov 16 18:20:02 stoat kernel: [381981.251602] RAX: 0000001d00008000 RBX: ffff88005f3148c0 RCX: 0000000000000405
Nov 16 18:20:02 stoat kernel: [381981.251653] RDX: 0000000000000000 RSI: ffff880055e339d0 RDI: ffff88005f3148c0
Nov 16 18:20:02 stoat kernel: [381981.251704] RBP: ffff880018003868 R08: ffff880018002000 R09: 0000000000000000
Nov 16 18:20:02 stoat kernel: [381981.251755] R10: 0000000000000000 R11: 00000000ffffffff R12: ffff88005c464b40
Nov 16 18:20:02 stoat kernel: [381981.251806] R13: ffff880055e339d0 R14: ffff88007c9bbc00 R15: ffff8800379782f0
Nov 16 18:20:02 stoat kernel: [381981.252806] FS:  00007f22779f6710(0000) GS:ffff8800019f2000(0000) knlGS:0000000000000000
Nov 16 18:20:02 stoat kernel: [381981.252859] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Nov 16 18:20:02 stoat kernel: [381981.252891] CR2: 0000001d00008038 CR3: 0000000046c5a000 CR4: 00000000000006f0
Nov 16 18:20:02 stoat kernel: [381981.252942] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Nov 16 18:20:02 stoat kernel: [381981.252993] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Nov 16 18:20:02 stoat kernel: [381981.253044] Process maildrop (pid: 5551, threadinfo ffff880018002000, task ffff88005ef396b0)
Nov 16 18:20:02 stoat kernel: [381981.253097] Stack:
Nov 16 18:20:02 stoat kernel: [381981.253120]  ffff88005f314950 ffff88005f3148c0 ffff88007acb9260 ffff88007acb9260
Nov 16 18:20:02 stoat kernel: [381981.253161] <0> ffff8800180038a8 ffffffffa0078415 ffff88005f314950 0000000000000001
Nov 16 18:20:02 stoat kernel: [381981.253220] <0> 0000000000000000 ffff88005f3148c0 ffff88007acb9260 ffffffffa010b420
Nov 16 18:20:02 stoat kernel: [381981.253298] Call Trace:
Nov 16 18:20:02 stoat kernel: [381981.253335]  [<ffffffffa0078415>] rpc_verify_header+0x1b5/0x5a0 [sunrpc]
Nov 16 18:20:02 stoat kernel: [381981.253385]  [<ffffffffa010b420>] ? nfs4_xdr_dec_readdir+0x0/0x70 [nfs]
Nov 16 18:20:02 stoat kernel: [381981.253429]  [<ffffffffa0078930>] call_decode+0x130/0x220 [sunrpc]
Nov 16 18:20:02 stoat kernel: [381981.253474]  [<ffffffffa007fe4a>] __rpc_execute+0xba/0x220 [sunrpc]
Nov 16 18:20:02 stoat kernel: [381981.253518]  [<ffffffffa007ffd1>] rpc_execute+0x21/0x30 [sunrpc]
Nov 16 18:20:02 stoat kernel: [381981.253561]  [<ffffffffa0078af5>] rpc_run_task+0x35/0x80 [sunrpc]
Nov 16 18:20:02 stoat kernel: [381981.253605]  [<ffffffffa007f1e8>] ? rpc_put_task+0xa8/0xb0 [sunrpc]
Nov 16 18:20:02 stoat kernel: [381981.253649]  [<ffffffffa0078c3d>] rpc_call_sync+0x3d/0x70 [sunrpc]
Nov 16 18:20:02 stoat kernel: [381981.253694]  [<ffffffffa010116d>] _nfs4_call_sync+0x1d/0x20 [nfs]
Nov 16 18:20:02 stoat kernel: [381981.253738]  [<ffffffffa0101f42>] _nfs4_proc_readdir+0x112/0x1c0 [nfs]
Nov 16 18:20:02 stoat kernel: [381981.253784]  [<ffffffffa0102048>] nfs4_proc_readdir+0x58/0x90 [nfs]
Nov 16 18:20:02 stoat kernel: [381981.253826]  [<ffffffffa00e49b6>] nfs_readdir_filler+0xe6/0x1c0 [nfs]
Nov 16 18:20:02 stoat kernel: [381981.253868]  [<ffffffffa00e48d0>] ? nfs_readdir_filler+0x0/0x1c0 [nfs]
Nov 16 18:20:02 stoat kernel: [381981.253905]  [<ffffffff810da479>] __read_cache_page+0x79/0xe0
Nov 16 18:20:02 stoat kernel: [381981.253939]  [<ffffffff8112dea8>] ? filldir+0x78/0xe0
Nov 16 18:20:02 stoat kernel: [381981.253978]  [<ffffffffa00e48d0>] ? nfs_readdir_filler+0x0/0x1c0 [nfs]
Nov 16 18:20:02 stoat kernel: [381981.254013]  [<ffffffff810db451>] read_cache_page_async+0x31/0xd0
Nov 16 18:20:02 stoat kernel: [381981.254054]  [<ffffffffa00e5ac2>] ? nfs_do_filldir+0x182/0x1f0 [nfs]
Nov 16 18:20:02 stoat kernel: [381981.254089]  [<ffffffff810db4fd>] read_cache_page+0xd/0x60
Nov 16 18:20:02 stoat kernel: [381981.254129]  [<ffffffffa00e5d76>] nfs_readdir+0x246/0xa60 [nfs]
Nov 16 18:20:02 stoat kernel: [381981.254173]  [<ffffffffa0081f40>] ? generic_lookup_cred+0x10/0x20 [sunrpc]
Nov 16 18:20:02 stoat kernel: [381981.254208]  [<ffffffff8112de30>] ? filldir+0x0/0xe0
Nov 16 18:20:02 stoat kernel: [381981.254248]  [<ffffffffa00eab0b>] ? put_nfs_open_context+0xb/0x10 [nfs]
Nov 16 18:20:02 stoat kernel: [381981.254292]  [<ffffffffa00eb8c7>] ? nfs_open+0x147/0x1d0 [nfs]
Nov 16 18:20:02 stoat kernel: [381981.254333]  [<ffffffffa00e4850>] ? nfs_opendir+0x0/0x80 [nfs]
Nov 16 18:20:02 stoat kernel: [381981.254374]  [<ffffffffa00e48a5>] ? nfs_opendir+0x55/0x80 [nfs]
Nov 16 18:20:02 stoat kernel: [381981.254418]  [<ffffffffa0105490>] ? nfs4_decode_dirent+0x0/0x140 [nfs]
Nov 16 18:20:02 stoat kernel: [381981.254461]  [<ffffffffa00eac31>] ? nfs_getattr+0x81/0x130 [nfs]
Nov 16 18:20:02 stoat kernel: [381981.254494]  [<ffffffff8112de30>] ? filldir+0x0/0xe0
Nov 16 18:20:02 stoat kernel: [381981.254525]  [<ffffffff8112e070>] vfs_readdir+0xb0/0xd0
Nov 16 18:20:02 stoat kernel: [381981.254557]  [<ffffffff8112e1f0>] sys_getdents+0x80/0xe0
Nov 16 18:20:02 stoat kernel: [381981.254590]  [<ffffffff81011fc2>] system_call_fastpath+0x16/0x1b
Nov 16 18:20:02 stoat kernel: [381981.254622] Code: 20 f6 05 f1 d5 02 00 10 48 89 5d e8 4c 89 6d f8 48 89 fb 4c 89 65 f0 49 89 f5 4c 8b 67 50 75 1c 49 8b 44 24 38 4c 89 ee 48 89 df <ff> 50 38 48 8b 5d e8 4c 8b 65 f0 4c 8b 6d f8 c9 c3 49 8b 44 24
Nov 16 18:20:02 stoat kernel: [381981.254842] RIP  [<ffffffffa0080c22>] rpcauth_checkverf+0x32/0x70 [sunrpc]
Nov 16 18:20:02 stoat kernel: [381981.254889]  RSP <ffff880018003848>
Nov 16 18:20:02 stoat kernel: [381981.254916] CR2: 0000001d00008038
Nov 16 18:20:02 stoat kernel: [381981.255163] ---[ end trace dad10a76f4f93b63 ]---

---

