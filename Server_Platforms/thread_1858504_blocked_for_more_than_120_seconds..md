---
title: "blocked for more than 120 seconds."
date: 2011-10-12
forum: Server Platforms
---

### Post by frankyue on 2011-10-12
I have 3 servers with ubuntu 10.10 platform and the kernel is 2.6.35-22.

Today all of my servers get freeze , I can not to login by ssh to the server. 

Checked the log find something wrong with the kernel :
Oct 12 09:53:22 ip-10-58-242-31 kernel: [15096446.245590] INFO: task ruby:3370 blocked for more than 120 seconds.
Oct 12 09:53:22 ip-10-58-242-31 kernel: [15096446.245612] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Oct 12 09:53:22 ip-10-58-242-31 kernel: [15096446.245620] ruby          D ffff880003dec980     0  3370   3364 0x00000004
Oct 12 09:53:22 ip-10-58-242-31 kernel: [15096446.245626]  ffff8801d4f29a08 0000000000000286 0000000000000000 0000000000015980
Oct 12 09:53:22 ip-10-58-242-31 kernel: [15096446.245632]  ffff8801d4f29fd8 0000000000015980 ffff8801d4f29fd8 ffff8801d7258000
Oct 12 09:53:22 ip-10-58-242-31 kernel: [15096446.245638]  0000000000015980 0000000000015980 ffff8801d4f29fd8 0000000000015980
Oct 12 09:53:22 ip-10-58-242-31 kernel: [15096446.245644] Call Trace:
Oct 12 09:53:22 ip-10-58-242-31 kernel: [15096446.245656]  [<ffffffff812410c5>] request_wait_answer+0x85/0x240
Oct 12 09:53:22 ip-10-58-242-31 kernel: [15096446.245663]  [<ffffffff8107f080>] ? autoremove_wake_function+0x0/0x40
Oct 12 09:53:22 ip-10-58-242-31 kernel: [15096446.245667]  [<ffffffff812412fc>] fuse_request_send+0x7c/0x90
Oct 12 09:53:22 ip-10-58-242-31 kernel: [15096446.245671]  [<ffffffff8124392a>] fuse_do_getattr+0x10a/0x2b0
Oct 12 09:53:22 ip-10-58-242-31 kernel: [15096446.245679]  [<ffffffff814aacd5>] ? memcpy_toiovec+0x55/0x80
Oct 12 09:53:22 ip-10-58-242-31 kernel: [15096446.245684]  [<ffffffff812457e5>] fuse_update_attributes+0x75/0x80
Oct 12 09:53:22 ip-10-58-242-31 kernel: [15096446.245688]  [<ffffffff81245910>] fuse_permission+0xc0/0x200
Oct 12 09:53:22 ip-10-58-242-31 kernel: [15096446.245694]  [<ffffffff8115ccd0>] exec_permission+0x30/0x90
Oct 12 09:53:22 ip-10-58-242-31 kernel: [15096446.245698]  [<ffffffff8115fa39>] link_path_walk+0x89/0xab0
Oct 12 09:53:22 ip-10-58-242-31 kernel: [15096446.245701]  [<ffffffff811602c0>] link_path_walk+0x910/0xab0
Oct 12 09:53:22 ip-10-58-242-31 kernel: [15096446.245705]  [<ffffffff8115ff13>] link_path_walk+0x563/0xab0
Oct 12 09:53:22 ip-10-58-242-31 kernel: [15096446.245709]  [<ffffffff81161783>] do_filp_open+0x143/0x660
Oct 12 09:53:22 ip-10-58-242-31 kernel: [15096446.245715]  [<ffffffff810072bf>] ? xen_restore_fl_direct_end+0x0/0x1
Oct 12 09:53:22 ip-10-58-242-31 kernel: [15096446.245719]  [<ffffffff810043c6>] ? xen_mc_flush+0x96/0x1c0
Oct 12 09:53:22 ip-10-58-242-31 kernel: [15096446.245723]  [<ffffffff81006b3d>] ? xen_force_evtchn_callback+0xd/0x10
Oct 12 09:53:22 ip-10-58-242-31 kernel: [15096446.245727]  [<ffffffff8115da4b>] ? getname+0x3b/0x240
Oct 12 09:53:22 ip-10-58-242-31 kernel: [15096446.245734]  [<ffffffff815a3fbe>] ? _raw_spin_lock+0xe/0x20
Oct 12 09:53:22 ip-10-58-242-31 kernel: [15096446.245738]  [<ffffffff8116ce4a>] ? alloc_fd+0x10a/0x150
Oct 12 09:53:22 ip-10-58-242-31 kernel: [15096446.245745]  [<ffffffff81151009>] do_sys_open+0x69/0x170
Oct 12 09:53:22 ip-10-58-242-31 kernel: [15096446.245749]  [<ffffffff81151150>] sys_open+0x20/0x30
Oct 12 09:53:22 ip-10-58-242-31 kernel: [15096446.245753]  [<ffffffff8100a0f2>] system_call_fastpath+0x16/0x1b 

Can anyone give me some information to fix it?

---

