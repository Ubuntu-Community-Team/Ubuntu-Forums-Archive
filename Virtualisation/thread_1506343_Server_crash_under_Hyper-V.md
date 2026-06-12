---
title: "Server crash under Hyper-V"
date: 2010-06-10
forum: Virtualisation
---

### Post by jplotzke on 2010-06-10
Hi All,

I've been running 3 instances of Ubuntu under Win08 Server via Hyper-V for the last three weeks now.  Two instances are Ubuntu 10.04 Server and another Ubuntu 8.04 Server.  All three have the Hyper-V Integration Components installed and running.

However, I can't get the 10.04 machines to stay running for more than a few days without crashing -- normally with a screen full of "task * has been blocked for more than 120 seconds" messages.  This stops essentially all services on the machine and I'm forced to reboot it.  This doesn't happen at all on the 8.04 machine.

Here's some lines from /var/log/messages below.  I'm wondering if the integration tools have something to do with the problem as the first line is with the STORVSC module.  Does anyone else have this problem or can offer any assistance on how to dig deeper?   If this doesn't clear up, I'll probably need to back everything down to 8.04 if that doesn't have this problem.

Thanks!

```

Jun  9 12:39:57 netguy-backup01 kernel: [ 8733.040391] STORVSC_DRV: sdev (ffff88000f6c3000) dev obj (ffff88000c0e1240) - host resetting...
Jun  9 12:39:57 netguy-backup01 kernel: [ 8733.040398] STORVSC: resetting host adapter...
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.273227] kjournald     D 00000000ffffffff     0   627      2 0x00000000
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.273234]  ffff880006891c30 0000000000000046 0000000000015bc0 0000000000015bc0
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.273240]  ffff88000d7c31a0 ffff880006891fd8 0000000000015bc0 ffff88000d7c2de0
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.273242]  0000000000015bc0 ffff880006891fd8 0000000000015bc0 ffff88000d7c31a0
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.273246] Call Trace:
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.273273]  [<ffffffff8116d1d0>] ? sync_buffer+0x0/0x50
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.273284]  [<ffffffff81555627>] io_schedule+0x47/0x70
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.273287]  [<ffffffff8116d215>] sync_buffer+0x45/0x50
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.273289]  [<ffffffff81555c4f>] __wait_on_bit+0x5f/0x90
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.273291]  [<ffffffff8116bfb1>] ? submit_bh+0x111/0x140
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.273293]  [<ffffffff8116d1d0>] ? sync_buffer+0x0/0x50
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.273296]  [<ffffffff81555cf8>] out_of_line_wait_on_bit+0x78/0x90
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.273306]  [<ffffffff81084fe0>] ? wake_bit_function+0x0/0x40
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.273308]  [<ffffffff8116d1c6>] __wait_on_buffer+0x26/0x30
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.273314]  [<ffffffff81212bfb>] journal_commit_transaction+0x31b/0xe40
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.273322]  [<ffffffff810397a9>] ? default_spin_lock_flags+0x9/0x10
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.273326]  [<ffffffff81076bdc>] ? lock_timer_base+0x3c/0x70
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.273329]  [<ffffffff81077665>] ? try_to_del_timer_sync+0x75/0xd0
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.273331]  [<ffffffff81216a9d>] kjournald+0xed/0x250
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.273334]  [<ffffffff81084fa0>] ? autoremove_wake_function+0x0/0x40
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.273336]  [<ffffffff812169b0>] ? kjournald+0x0/0x250
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.273338]  [<ffffffff81084c26>] kthread+0x96/0xa0
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.273343]  [<ffffffff810141ea>] child_rip+0xa/0x20
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.273345]  [<ffffffff81084b90>] ? kthread+0x0/0xa0
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.273347]  [<ffffffff810141e0>] ? child_rip+0x0/0x20
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.284748] flush-8:16    D 00000000ffffffff     0  1011      2 0x00000000
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.284752]  ffff88000312b8c0 0000000000000046 0000000000015bc0 0000000000015bc0
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.284754]  ffff88000c1031a0 ffff88000312bfd8 0000000000015bc0 ffff88000c102de0
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.284758]  0000000000015bc0 ffff88000312bfd8 0000000000015bc0 ffff88000c1031a0
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.284761] Call Trace:
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.284764]  [<ffffffff8116d1d0>] ? sync_buffer+0x0/0x50
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.284766]  [<ffffffff81555627>] io_schedule+0x47/0x70
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.284769]  [<ffffffff8116d215>] sync_buffer+0x45/0x50
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.284771]  [<ffffffff81555afa>] __wait_on_bit_lock+0x5a/0xc0
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.284778]  [<ffffffff812b503e>] ? __prop_inc_percpu_max+0x7e/0xd0
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.284780]  [<ffffffff8116d1d0>] ? sync_buffer+0x0/0x50
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.284782]  [<ffffffff8116d760>] ? end_buffer_async_write+0x0/0x180
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.284784]  [<ffffffff81555bd8>] out_of_line_wait_on_bit_lock+0x78/0x90
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.284787]  [<ffffffff81084fe0>] ? wake_bit_function+0x0/0x40
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.284789]  [<ffffffff8116d396>] __lock_buffer+0x36/0x40
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.284791]  [<ffffffff8116e073>] __block_write_full_page+0x383/0x3c0
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.284798]  [<ffffffff810f3577>] ? unlock_page+0x27/0x30
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.284800]  [<ffffffff8116d760>] ? end_buffer_async_write+0x0/0x180
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.284803]  [<ffffffff8116e9e0>] block_write_full_page_endio+0xe0/0x120
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.284805]  [<ffffffff8116d760>] ? end_buffer_async_write+0x0/0x180
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.284807]  [<ffffffff8116ea35>] block_write_full_page+0x15/0x20
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.284811]  [<ffffffff811b681d>] ext3_ordered_writepage+0x1dd/0x200
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.284814]  [<ffffffff810fb717>] __writepage+0x17/0x40
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.284816]  [<ffffffff810fc8cf>] write_cache_pages+0x21f/0x4d0
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.284820]  [<ffffffff810fb700>] ? __writepage+0x0/0x40
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.284822]  [<ffffffff810fcba4>] generic_writepages+0x24/0x30
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.284825]  [<ffffffff810fcbe5>] do_writepages+0x35/0x40
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.284828]  [<ffffffff811655b6>] writeback_single_inode+0xf6/0x3d0
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.284830]  [<ffffffff81166220>] writeback_inodes_wb+0x410/0x5e0
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.284833]  [<ffffffff811664fa>] wb_writeback+0x10a/0x1d0
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.284835]  [<ffffffff81077665>] ? try_to_del_timer_sync+0x75/0xd0
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.284837]  [<ffffffff815558db>] ? schedule_timeout+0x19b/0x300
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.284839]  [<ffffffff8116682c>] wb_do_writeback+0x18c/0x1a0
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.284841]  [<ffffffff81166893>] bdi_writeback_task+0x53/0xe0
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.284845]  [<ffffffff8110e526>] bdi_start_fn+0x86/0x100
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.284847]  [<ffffffff8110e4a0>] ? bdi_start_fn+0x0/0x100
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.284849]  [<ffffffff81084c26>] kthread+0x96/0xa0
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.284851]  [<ffffffff810141ea>] child_rip+0xa/0x20
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.284853]  [<ffffffff81084b90>] ? kthread+0x0/0xa0
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.284855]  [<ffffffff810141e0>] ? child_rip+0x0/0x20
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.295884] rsync         D 00000000ffffffff     0  1023   1021 0x00000000
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.295888]  ffff8800045919e8 0000000000000086 0000000000015bc0 0000000000015bc0
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.295890]  ffff88000c101ab0 ffff880004591fd8 0000000000015bc0 ffff88000c1016f0
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.295893]  0000000000015bc0 ffff880004591fd8 0000000000015bc0 ffff88000c101ab0
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.295895] Call Trace:
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.295898]  [<ffffffff8116d1d0>] ? sync_buffer+0x0/0x50
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.295901]  [<ffffffff81555627>] io_schedule+0x47/0x70
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.295903]  [<ffffffff8116d215>] sync_buffer+0x45/0x50
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.295905]  [<ffffffff81555c4f>] __wait_on_bit+0x5f/0x90
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.295907]  [<ffffffff8116d1d0>] ? sync_buffer+0x0/0x50
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.295909]  [<ffffffff81555cf8>] out_of_line_wait_on_bit+0x78/0x90
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.295912]  [<ffffffff81084fe0>] ? wake_bit_function+0x0/0x40
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.295914]  [<ffffffff8116d1c6>] __wait_on_buffer+0x26/0x30
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.295918]  [<ffffffff811bddec>] ext3_find_entry+0xfc/0x430
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.295920]  [<ffffffff8155749e>] ? _spin_lock+0xe/0x20
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.295924]  [<ffffffff81156330>] ? d_rehash+0x50/0x60
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.295927]  [<ffffffff811be16d>] ext3_lookup+0x4d/0x130
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.295929]  [<ffffffff8114d082>] real_lookup+0xe2/0x160
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.295931]  [<ffffffff8114f028>] do_lookup+0xb8/0xf0
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.295935]  [<ffffffff8108c771>] ? in_group_p+0x31/0x40
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.295937]  [<ffffffff8114f59d>] __link_path_walk+0x1ad/0xf80
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.295941]  [<ffffffff811570da>] ? dput+0xba/0x180
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.295943]  [<ffffffff811505ea>] path_walk+0x6a/0xe0
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.295945]  [<ffffffff811507bb>] do_path_lookup+0x5b/0xa0
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.295949]  [<ffffffff81144a81>] ? get_empty_filp+0xa1/0x170
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.295951]  [<ffffffff81151763>] do_filp_open+0x103/0xba0
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.295954]  [<ffffffff8155749e>] ? _spin_lock+0xe/0x20
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.295956]  [<ffffffff8115edb0>] ? mntput_no_expire+0x30/0x110
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.295958]  [<ffffffff8115d2da>] ? alloc_fd+0x10a/0x150
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.295961]  [<ffffffff81141109>] do_sys_open+0x69/0x170
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.295963]  [<ffffffff81141250>] sys_open+0x20/0x30
Jun  9 12:42:24 netguy-backup01 kernel: [ 8880.295967]  [<ffffffff810131b2>] system_call_fastpath+0x16/0x1b
Jun  9 12:44:24 netguy-backup01 kernel: [ 9000.300974] kjournald     D 00000000ffffffff     0   627      2 0x00000000
Jun  9 12:44:24 netguy-backup01 kernel: [ 9000.300983]  ffff880006891c30 0000000000000046 0000000000015bc0 0000000000015bc0
Jun  9 12:44:24 netguy-backup01 kernel: [ 9000.300986]  ffff88000d7c31a0 ffff880006891fd8 0000000000015bc0 ffff88000d7c2de0
Jun  9 12:44:24 netguy-backup01 kernel: [ 9000.300988]  0000000000015bc0 ffff880006891fd8 0000000000015bc0 ffff88000d7c31a0
Jun  9 12:44:24 netguy-backup01 kernel: [ 9000.300991] Call Trace:
Jun  9 12:44:24 netguy-backup01 kernel: [ 9000.300998]  [<ffffffff8116d1d0>] ? sync_buffer+0x0/0x50
Jun  9 12:44:24 netguy-backup01 kernel: [ 9000.301002]  [<ffffffff81555627>] io_schedule+0x47/0x70
Jun  9 12:44:24 netguy-backup01 kernel: [ 9000.301004]  [<ffffffff8116d215>] sync_buffer+0x45/0x50
Jun  9 12:44:24 netguy-backup01 kernel: [ 9000.301006]  [<ffffffff81555c4f>] __wait_on_bit+0x5f/0x90
Jun  9 12:44:24 netguy-backup01 kernel: [ 9000.301009]  [<ffffffff8116bfb1>] ? submit_bh+0x111/0x140
Jun  9 12:44:24 netguy-backup01 kernel: [ 9000.301011]  [<ffffffff8116d1d0>] ? sync_buffer+0x0/0x50
Jun  9 12:44:24 netguy-backup01 kernel: [ 9000.301013]  [<ffffffff81555cf8>] out_of_line_wait_on_bit+0x78/0x90
Jun  9 12:44:24 netguy-backup01 kernel: [ 9000.301016]  [<ffffffff81084fe0>] ? wake_bit_function+0x0/0x40
Jun  9 12:44:24 netguy-backup01 kernel: [ 9000.301018]  [<ffffffff8116d1c6>] __wait_on_buffer+0x26/0x30
Jun  9 12:44:24 netguy-backup01 kernel: [ 9000.301021]  [<ffffffff81212bfb>] journal_commit_transaction+0x31b/0xe40
Jun  9 12:44:24 netguy-backup01 kernel: [ 9000.301025]  [<ffffffff810397a9>] ? default_spin_lock_flags+0x9/0x10
Jun  9 12:44:24 netguy-backup01 kernel: [ 9000.301028]  [<ffffffff81076bdc>] ? lock_timer_base+0x3c/0x70
Jun  9 12:44:24 netguy-backup01 kernel: [ 9000.301030]  [<ffffffff81077665>] ? try_to_del_timer_sync+0x75/0xd0
Jun  9 12:44:24 netguy-backup01 kernel: [ 9000.301033]  [<ffffffff81216a9d>] kjournald+0xed/0x250
Jun  9 12:44:24 netguy-backup01 kernel: [ 9000.301035]  [<ffffffff81084fa0>] ? autoremove_wake_function+0x0/0x40
Jun  9 12:44:24 netguy-backup01 kernel: [ 9000.301037]  [<ffffffff812169b0>] ? kjournald+0x0/0x250
Jun  9 12:44:24 netguy-backup01 kernel: [ 9000.301039]  [<ffffffff81084c26>] kthread+0x96/0xa0
Jun  9 12:44:24 netguy-backup01 kernel: [ 9000.301042]  [<ffffffff810141ea>] child_rip+0xa/0x20
Jun  9 12:44:24 netguy-backup01 kernel: [ 9000.301044]  [<ffffffff81084b90>] ? kthread+0x0/0xa0
Jun  9 12:44:24 netguy-backup01 kernel: [ 9000.301045]  [<ffffffff810141e0>] ? child_rip+0x0/0x20

```

---

### Post by jplotzke on 2010-06-10
Just had another crash -- This one seems much worse  :)

Here's a screenshot of the dump.  Is there anyway to get more information about what happened?

[IMG]http://i50.tinypic.com/2gwylw4.png[/IMG]

---

### Post by ZakMcRofl on 2010-08-23
I am experiencing the same issue.
Did you find out more about the problem? Is there a solution?

---

### Post by mglat on 2010-11-17
I am experiencing the same problems with Ubuntu 10.04-server and kernel 2.6.32-25-server via MS Hyper-V. Any suggestions?

---

### Post by cybertoto on 2010-12-19
Hello..
I've got exactly the same problem. Ubuntu 10.10-server on Hyper V. It crashes mostly during file transfer (SSH, FTP, SAMBA, ...) with the network.

Did somebody have an idea ?

---

### Post by tgalati4 on 2010-12-19
I'm sure Microsoft will have a quick fix for this problem.

Why do I have the feeling that this would not be a problem under Xen, VMware, or any other virtual machine with a Linux host?

---

### Post by Sef on 2010-12-20
Moved to Virtualization subforum.

---

### Post by kraucer on 2011-03-22
> **Sef said:**
> Moved to Virtualization subforum.

I'm having the same problem: Ubuntu Server 64 bit 10:10 + kernel 2.6.35-22-server Hyper-V +. Any idea how to solve? There is a bug report here: https: / / bugs.launchpad.net / ubuntu / + source / linux / + bug/652812

---

