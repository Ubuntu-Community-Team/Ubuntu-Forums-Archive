---
title: "ubnutu 1604 with kernel 4.4.087 moving into kernel panic state."
date: 2017-08-04
forum: Ubuntu/Debian BASED
---

### Post by kailashms on 2017-08-04
Hi Team,

i have a case, where i am able to see that my vm which is Ubuntu 16.04 running with the kernel,4.4.0.87 is facing kernel panic issue.
Aug  3 22:06:13 prexec1.findo.hosts [36498.579578] CPU: 0 PID: 65286 Comm: kworker/u128:3 Tainted: G        W       4.4.0-87-generic #110~14.04.1-Ubuntu
Aug  3 22:06:13 prexec1.findo.hosts [36498.647964] Hardware name: Microsoft Corporation Virtual Machine/Virtual Machine, BIOS 090006  05/23/2012
Aug  3 22:06:13 prexec1.findo.hosts [36498.647964] Workqueue: netns cleanup_net
Aug  3 22:06:13 prexec1.findo.hosts
Aug  3 22:06:13 prexec1.findo.hosts [36498.647964] task: ffff8802940dc600 ti: ffff880182b64000 task.ti: ffff880182b64000
Aug  3 22:06:13 prexec1.findo.hosts [36498.686564] RIP: 0010:[<ffffffff817e8b65>]
Aug  3 22:06:13 prexec1.findo.hosts  [<ffffffff817e8b65>] in6_dev_finish_destroy+0x35/0xb0
Aug  3 22:06:13 prexec1.findo.hosts [36498.686564] RSP: 0000:ffff880182b67c10  EFLAGS: 00010246
Aug  3 22:06:13 prexec1.findo.hosts [36498.686564] RAX: ffff8802820d4000 RBX: ffff880016d82000 RCX: 0000000000000006
Aug  3 22:06:13 prexec1.findo.hosts [36498.686564] RDX: 0000000000000000 RSI: 0000000000000000 RDI: 0000000000000009
Aug  3 22:06:13 prexec1.findo.hosts [36498.686564] RBP: ffff880182b67c20 R08: 000000000000000a R09: 0000000000000000
Aug  3 22:06:13 prexec1.findo.hosts [36498.686564] R10: 0000000000000000 R11: 0000000000000728 R12: ffff880016d83400
Aug  3 22:06:13 prexec1.findo.hosts [36498.686564] R13: 0000000000000006 R14: ffff880182b67cc0 R15: 0000000000000000
Aug  3 22:06:13 prexec1.findo.hosts [36498.686564] FS:  0000000000000000(0000) GS:ffff880297600000(0000) knlGS:0000000000000000
Aug  3 22:06:13 prexec1.findo.hosts [36498.686564] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Aug  3 22:06:13 prexec1.findo.hosts [36498.686564] CR2: 000000c4201ca658 CR3: 0000000146a1b000 CR4: 00000000001406f0
Aug  3 22:06:13 prexec1.findo.hosts [36498.686564] Stack:
Aug  3 22:06:13 prexec1.findo.hosts [36498.686564]  ffff88027c038000
Aug  3 22:06:13 prexec1.findo.hosts  0000000000000000
Aug  3 22:06:13 prexec1.findo.hosts  ffff880182b67c38
Aug  3 22:06:13 prexec1.findo.hosts  ffffffff817be360
Aug  3 22:06:13 prexec1.findo.hosts
Aug  3 22:06:13 prexec1.findo.hosts [36498.686564]  00000000ffffffeb
Aug  3 22:06:13 prexec1.findo.hosts  ffff880182b67c70
Aug  3 22:06:13 prexec1.findo.hosts  ffffffff8109dde9
Aug  3 22:06:13 prexec1.findo.hosts  ffff880182b67cc0
Aug  3 22:06:13 prexec1.findo.hosts
Aug  3 22:06:13 prexec1.findo.hosts [36498.686564]  0000000000000006
Aug  3 22:06:13 prexec1.findo.hosts  ffff880146ab2000
Aug  3 22:06:13 prexec1.findo.hosts  00000001008a0d09
Aug  3 22:06:13 prexec1.findo.hosts  00000000000000fa
Aug  3 22:06:13 prexec1.findo.hosts
Aug  3 22:06:13 prexec1.findo.hosts [36498.899431] Call Trace:
Aug  3 22:06:13 prexec1.findo.hosts [36498.899431]  [<ffffffff817be360>] ip6_route_dev_notify+0x110/0x130
Aug  3 22:06:13 prexec1.findo.hosts [36498.899431]  [<ffffffff8109dde9>] notifier_call_chain+0x49/0x70
Aug  3 22:06:13 prexec1.findo.hosts [36498.899431]  [<ffffffff8109df06>] raw_notifier_call_chain+0x16/0x20
Aug  3 22:06:13 prexec1.findo.hosts [36498.899431]  [<ffffffff81701d35>] call_netdevice_notifiers_info+0x35/0x60
Aug  3 22:06:13 prexec1.findo.hosts [36498.899431]  [<ffffffff8170c007>] netdev_run_todo+0x157/0x300
Aug  3 22:06:13 prexec1.findo.hosts [36498.899431]  [<ffffffff81703a4e>] ? rollback_registered_many+0x22e/0x2e0
Aug  3 22:06:13 prexec1.findo.hosts [36498.899431]  [<ffffffff817172fe>] rtnl_unlock+0xe/0x10
Aug  3 22:06:13 prexec1.findo.hosts [36498.899431]  [<ffffffff81704d98>] default_device_exit_batch+0x138/0x150
Aug  3 22:06:13 prexec1.findo.hosts [36498.899431]  [<ffffffff810bf540>] ? __wake_up_sync+0x20/0x20
Aug  3 22:06:13 prexec1.findo.hosts [36498.899431]  [<ffffffff816fd252>] ops_exit_list.isra.4+0x52/0x60
Aug  3 22:06:13 prexec1.findo.hosts [36498.899431]  [<ffffffff816fe223>] cleanup_net+0x1b3/0x280
Aug  3 22:06:13 prexec1.findo.hosts [36498.899431]  [<ffffffff81096d90>] process_one_work+0x150/0x3f0
Aug  3 22:06:13 prexec1.findo.hosts [36498.899431]  [<ffffffff8109750a>] worker_thread+0x11a/0x470
Aug  3 22:06:13 prexec1.findo.hosts [36498.899431]  [<ffffffff810973f0>] ? rescuer_thread+0x310/0x310
Aug  3 22:06:13 prexec1.findo.hosts [36498.899431]  [<ffffffff8109cdc6>] kthread+0xd6/0xf0
Aug  3 22:06:13 prexec1.findo.hosts [36498.899431]  [<ffffffff8109ccf0>] ? kthread_park+0x60/0x60
Aug  3 22:06:13 prexec1.findo.hosts [36498.899431]  [<ffffffff8180d00f>] ret_from_fork+0x3f/0x70
Aug  3 22:06:13 prexec1.findo.hosts [36498.899431]  [<ffffffff8109ccf0>] ? kthread_park+0x60/0x60
Aug  3 22:06:13 prexec1.findo.hosts [36498.899431] Code:

is this bug in the kernel?
for 4.4.0.83 we could see that it is bug?
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1702910](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1702910)

please let me know if you need other details about the same.

Thanks,

Kailash B

---

### Post by kailashms on 2017-08-04
can anybody guide me on this

---

