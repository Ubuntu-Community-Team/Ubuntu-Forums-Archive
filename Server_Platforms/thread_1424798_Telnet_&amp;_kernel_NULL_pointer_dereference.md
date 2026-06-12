---
title: "Telnet &amp; kernel NULL pointer dereference"
date: 2010-03-08
forum: Server Platforms
---

### Post by hovis on 2010-03-08
I am using 'telnet' & 'expect' in a cron shell script to send commands to 'vlc' and am getting the following kernel bug sometimes followed by a complete kernel lockup.

```
[  215.163820] BUG: unable to handle kernel NULL pointer dereference at (null)
[  215.163952] IP: [<ffffffff812f8872>] process_echoes+0xf2/0x340
[  215.164050] PGD 19bd88067 PUD 1a7818067 PMD 0 
[  215.164204] Oops: 0000 [#1] SMP 
[  215.164323] last sysfs file: /sys/devices/virtual/block/md3/md/metadata_version
[  215.164399] CPU 0 
[  215.164482] Modules linked in: radeon ttm drm i5000_edac i2c_algo_bit edac_core ppdev lp i5k_amb shpchp parport_pc serio_raw parport iptable_filter ip_tables x_tables raid10 raid456 raid6_pq async_xor async_memcpy async_tx e1000e xor raid1 raid0 multipath floppy linear
[  215.165606] Pid: 1524, comm: telnet Not tainted 2.6.31-20-server #57-Ubuntu X7DB8
[  215.165680] RIP: 0010:[<ffffffff812f8872>]  [<ffffffff812f8872>] process_echoes+0xf2/0x340
[  215.165791] RSP: 0018:ffff88019bde9778  EFLAGS: 00010246
[  215.165848] RAX: 0000000000000000 RBX: 0000000000000000 RCX: 0000000000001f00
[  215.165908] RDX: ffff8801a7482800 RSI: ffff8801a7483000 RDI: ffff8801a7483000
[  215.165968] RBP: ffff88019bde97d8 R08: 0000000000000000 R09: ffff8801a6050a0e
[  215.166028] R10: 0000000000000001 R11: 0000000000000000 R12: ffff8801a7483000
[  215.166088] R13: 0000000000000001 R14: 0000000000001f00 R15: 0000000000001000
[  215.166148] FS:  00007f4abfa1c710(0000) GS:ffff880028034000(0000) knlGS:0000000000000000
[  215.166224] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
[  215.166282] CR2: 0000000000000000 CR3: 00000001a6ce6000 CR4: 00000000000006f0
[  215.166342] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[  215.166402] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[  215.166462] Process telnet (pid: 1524, threadinfo ffff88019bde8000, task ffff8801a5d016b0)
[  215.166538] Stack:
[  215.166589]  ffff88019bde9788 ffff8801a74834d0 ffff8801a74834f0 ffff88019bde97a8
[  215.166747] <0> 0000000000000000 ffff8801a74834f0 ffff88019bde97d8 ffff8801a7483000
[  215.166986] <0> 000000000000000a 0000000000000003 000000000000000a 0000000000000001
[  215.167271] Call Trace:
[  215.167325]  [<ffffffff812fac04>] n_tty_receive_char+0x784/0x7c0
[  215.167385]  [<ffffffff812fae1c>] n_tty_receive_buf+0x1dc/0x490
[  215.167445]  [<ffffffff8104ef15>] ? finish_task_switch+0x65/0x120
[  215.167506]  [<ffffffff81528619>] ? thread_return+0x48/0x37f
[  215.167566]  [<ffffffff81036419>] ? default_spin_lock_flags+0x9/0x10
[  215.167626]  [<ffffffff812fd75b>] flush_to_ldisc+0x17b/0x1b0
[  215.167685]  [<ffffffff812fd820>] tty_flush_to_ldisc+0x10/0x20
[  215.167743]  [<ffffffff812f8b35>] n_tty_poll+0x75/0x190
[  215.167801]  [<ffffffff812f45e2>] tty_poll+0x82/0x90
[  215.167859]  [<ffffffff8112f5da>] do_select+0x38a/0x6b0
[  215.167917]  [<ffffffff8112f900>] ? __pollwait+0x0/0xf0
[  215.167975]  [<ffffffff8112f9f0>] ? pollwake+0x0/0x60
[  215.168031]  [<ffffffff8112f9f0>] ? pollwake+0x0/0x60
[  215.168088]  [<ffffffff8112f9f0>] ? pollwake+0x0/0x60
[  215.168146]  [<ffffffff8105b087>] ? check_preempt_wakeup+0x27/0x210
[  215.168206]  [<ffffffff81053668>] ? try_to_wake_up+0x118/0x340
[  215.168265]  [<ffffffff8105389d>] ? default_wake_function+0xd/0x10
[  215.168325]  [<ffffffff81045ae9>] ? __wake_up_common+0x59/0x90
[  215.168383]  [<ffffffff81130145>] core_sys_select+0x185/0x2b0
[  215.168443]  [<ffffffff8104a65e>] ? __wake_up+0x4e/0x70
[  215.168500]  [<ffffffff812fc9f9>] ? tty_ldisc_deref+0x9/0x10
[  215.168559]  [<ffffffff812f5ef8>] ? tty_write+0x228/0x290
[  215.168616]  [<ffffffff811304c2>] sys_select+0x42/0x110
[  215.168676]  [<ffffffff81012002>] system_call_fastpath+0x16/0x1b
[  215.168733] Code: 41 83 ee 01 4c 89 e7 e8 6d b7 ff ff 48 83 c3 01 41 83 ed 01 48 8d 83 00 f0 ff ff 4c 39 fb 48 0f 43 d8 45 85 ed 0f 8e b4 00 00 00 <0f> b6 3b 40 80 ff ff 75 a5 48 8d 43 01 4c 39 f8 48 0f 44 45 c0 
[  215.170978] RIP  [<ffffffff812f8872>] process_echoes+0xf2/0x340
[  215.171069]  RSP <ffff88019bde9778>
[  215.171122] CR2: 0000000000000000
[  215.171201] ---[ end trace 0f910c2dbcf2ad7b ]---
```

The shell script:-

```
#!/bin/bash
spawn telnet localhost 4212
expect "Password: "
send "admin\n"
expect "> "
send "load /tmp/commands.txt\n"
expect "> "
send "exit\n"
```

When the kernel bug occurs, the telnet program is left in a 'defunct' state and is impossible to kill.

Ubuntu 9.10 server, amd64, software RAID1, latest updates installed.

Of course, the bug is intermittent!, and it occurs on another piece of identical hardware (Supermicro 3U server).  I also cannot reproduce it on a slightly different Supermicro chassis (no software RAID) so I am rather stumped!

Anyone seen anything like this?  Apologies if this is the wrong place for this, please advise if I should post this elsewhere.

---

### Post by hovis on 2010-03-26
Replying to oneself in case someone else encounters this.

Solved it on Karmic by building a newer kernel (2.6.32.10).  This contains various 'tty' fixes since Karmic's kernel.  Lucid (beta1) kernel is also ok.

---

