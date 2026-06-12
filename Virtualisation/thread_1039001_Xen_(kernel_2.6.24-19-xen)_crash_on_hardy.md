---
title: "Xen (kernel 2.6.24-19-xen) crash on hardy"
date: 2009-01-14
forum: Virtualisation
---

### Post by kichenin on 2009-01-14
We have installed Ubuntu Hardy 8.0.4 server edition on HP DL-360 server and installed Xen 3.2 . On DomU Ubuntu Hardy 8.0.4 server is installed(kernel version 2.6.24-19-xen) on a 450GB LVM.

But the domU crashes randomly with the following error. we are able to access the domU console and domU network is ping-able.

[96466.420498] BUG: soft lockup - CPU#2 stuck for 11s! [kjournald:2119]
[96466.420504]
[96466.420507] Pid: 2119, comm: kjournald Tainted: G      D (2.6.24-19-xen #1)
[96466.420510] EIP: 0061:[<c03277a7>] EFLAGS: 00000286 CPU: 2
[96466.420515] EIP is at _spin_lock+0x7/0x10
[96466.420517] EAX: ed04ff98 EBX: 00000000 ECX: 00000000 EDX: f578e000
[96466.420521] ESI: 00000916 EDI: 00000000 EBP: 00000000 ESP: ec661c4c
[96466.420524]  DS: 007b ES: 007b FS: 00d8 GS: 0000 SS: 0069
[96466.420530] CR0: 8005003b CR2: b07fe000 CR3: 2c79d000 CR4: 00002660
[96466.420535] DR0: 00000000 DR1: 00000000 DR2: 00000000 DR3: 00000000
[96466.420539] DR6: ffff0ff0 DR7: 00000400
[96466.420542]  [<c01a717b>] __find_get_block_slow+0x5b/0x150
[96466.420550]  [<c01a7566>] __find_get_block+0xd6/0x200
[96466.420556]  [<c01fd1f3>] blk_recount_segments+0x33/0x70
[96466.420562]  [<c01a76b3>] __getblk+0x23/0x2b0
[96466.420568]  [<c01ff648>] get_request+0x148/0x350
[96466.420573]  [<c01045c4>] __switch_to+0x2f4/0x480
[96466.420579]  [<c01a9ba0>] __bread+0x10/0xa0
[96466.420584]  [<ee0ba4d6>] ext3_get_branch+0x96/0x110 [ext3]
[96466.420597]  [<ee0ba7ee>] ext3_get_blocks_handle+0x9e/0x9e0 [ext3]
[96466.420608]  [<c0200934>] blk_plug_device+0x54/0xd0
[96466.420614]  [<c0201db8>] __make_request+0xb8/0x6f0
[96466.420619]  [<c01fb50c>] elv_merged_request+0x4c/0x50
[96466.420625]  [<c020a422>] __next_cpu+0x12/0x20
[96466.420631]  [<c0108333>] sched_clock+0x23/0x70
[96466.420637]  [<c01045c4>] __switch_to+0x2f4/0x480
[96466.420643]  [<ee0bb382>] ext3_get_block+0x82/0x100 [ext3]
[96466.420655]  [<c01a6744>] generic_block_bmap+0x54/0x70
[96466.420661]  [<ee0bc370>] ext3_bmap+0x0/0x90 [ext3]
[96466.420672]  [<ee0bc3e5>] ext3_bmap+0x75/0x90 [ext3]
[96466.420684]  [<ee0bb300>] ext3_get_block+0x0/0x100 [ext3]
[96466.420694]  [<ee0bc370>] ext3_bmap+0x0/0x90 [ext3]
[96466.420706]  [<c0198ade>] bmap+0x2e/0x40
[96466.420711]  [<ee084e86>] journal_bmap+0x26/0xa0 [jbd]
[96466.420721]  [<ee0844c4>] __journal_remove_journal_head+0xe4/0x100 [jbd]
[96466.420730]  [<ee085915>] journal_remove_journal_head+0x15/0x40 [jbd]
[96466.420741]  [<ee085c4a>] journal_get_descriptor_buffer+0x1a/0xb0 [jbd]
[96466.420750]  [<ee082551>] journal_commit_transaction+0x961/0xda0 [jbd]
[96466.420760]  [<c0130a67>] lock_timer_base+0x27/0x60
[96466.420765]  [<c0130ae5>] try_to_del_timer_sync+0x45/0x50
[96466.420770]  [<ee085760>] kjournald+0xa0/0x200 [jbd]
[96466.420778]  [<c013bb90>] autoremove_wake_function+0x0/0x40
[96466.420783]  [<ee0856c0>] kjournald+0x0/0x200 [jbd]
[96466.420790]  [<c013b8d2>] kthread+0x42/0x70
[96466.420795]  [<c013b890>] kthread+0x0/0x70
[96466.420799]  [<c0105bb7>] kernel_thread_helper+0x7/0x10
[96466.420804]  =======================

The above message scrolls non stop. 
Any help will be really useful

Regards
Rada

---

