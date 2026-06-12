---
title: "Server crash (10.04) - warning: unix_trigger_event: read timeout for service public/f"
date: 2012-02-12
forum: Server Platforms
---

### Post by welly on 2012-02-12
Hi chaps,

On Saturday morning my Ubuntu 10.04 server ground to a halt and needed rebooting. On examining the server graphs from that morning, I found the following:

[IMG]http://i.imgur.com/q8n4A.png[/IMG]

[IMG]http://i.imgur.com/5eTbV.png[/IMG]

and in the syslog file itself, it looked like the following:

```

Feb 11 06:46:06 production postfix/master[1048]: warning: unix_trigger_event: read timeout for service public/flush
Feb 11 06:47:44 production kernel: [330329.885491] INFO: task cron:18701 blocked for more than 120 seconds.
Feb 11 06:47:44 production kernel: [330329.916472] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Feb 11 06:47:44 production kernel: [330329.979842] cron          D 0000000000000000     0 18701    953 0x00000000
Feb 11 06:47:44 production kernel: [330329.979857]  ffff880049dcfd10 0000000000000086 0000000000015d00 0000000000015d00
Feb 11 06:47:44 production kernel: [330329.979864]  ffff8800708603b8 ffff880049dcffd8 0000000000015d00 ffff880070860000
Feb 11 06:47:44 production kernel: [330329.979868]  0000000000015d00 ffff880049dcffd8 0000000000015d00 ffff8800708603b8
Feb 11 06:47:44 production kernel: [330329.979871] Call Trace:
Feb 11 06:47:44 production kernel: [330329.979883]  [<ffffffff81154ed0>] ? filldir+0x0/0xe0
Feb 11 06:47:44 production kernel: [330329.979889]  [<ffffffff8153f9cd>] schedule_timeout+0x22d/0x300
Feb 11 06:47:44 production kernel: [330329.979895]  [<ffffffff8104b3c9>] ? sched_slice+0x59/0xa0
Feb 11 06:47:44 production kernel: [330329.979899]  [<ffffffff8115de93>] ? dup_fd+0x33/0x340
Feb 11 06:47:44 production kernel: [330329.979904]  [<ffffffff812b4323>] ? cpumask_next_and+0x23/0x40
Feb 11 06:47:44 production kernel: [330329.979907]  [<ffffffff812b977d>] ? rb_insert_color+0x9d/0x160
Feb 11 06:47:44 production kernel: [330329.979910]  [<ffffffff8153f5eb>] wait_for_common+0xdb/0x180
Feb 11 06:47:44 production kernel: [330329.979914]  [<ffffffff8105ddcb>] ? enqueue_task_fair+0x5b/0xa0
Feb 11 06:47:44 production kernel: [330329.979917]  [<ffffffff8105ccb0>] ? default_wake_function+0x0/0x20
Feb 11 06:47:44 production kernel: [330329.979920]  [<ffffffff8153f74d>] wait_for_completion+0x1d/0x20
Feb 11 06:47:44 production kernel: [330329.979923]  [<ffffffff81065870>] do_fork+0x150/0x440
Feb 11 06:47:44 production kernel: [330329.979926]  [<ffffffff8115ff30>] ? mntput_no_expire+0x30/0x110
Feb 11 06:47:44 production kernel: [330329.979931]  [<ffffffff8107e085>] ? set_one_prio+0x75/0xd0
Feb 11 06:47:44 production kernel: [330329.979936]  [<ffffffff8101a085>] sys_vfork+0x25/0x30
Feb 11 06:47:44 production kernel: [330329.979940]  [<ffffffff81012513>] stub_vfork+0x13/0x20
Feb 11 06:47:44 production kernel: [330329.979943]  [<ffffffff810121b2>] ? system_call_fastpath+0x16/0x1b
Feb 11 06:47:44 production kernel: [330329.979947] INFO: task cron:18704 blocked for more than 120 seconds.
Feb 11 06:47:44 production kernel: [330330.011777] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Feb 11 06:47:44 production kernel: [330330.076513] cron          D 0000000000000000     0 18704    953 0x00000000
Feb 11 06:47:44 production kernel: [330330.076517]  ffff88007b7c7d10 0000000000000086 0000000000015d00 0000000000015d00
Feb 11 06:47:44 production kernel: [330330.076521]  ffff880078cf03b8 ffff88007b7c7fd8 0000000000015d00 ffff880078cf0000
Feb 11 06:47:44 production kernel: [330330.076524]  0000000000015d00 ffff88007b7c7fd8 0000000000015d00 ffff880078cf03b8
Feb 11 06:47:44 production kernel: [330330.076528] Call Trace:
Feb 11 06:47:44 production kernel: [330330.076535]  [<ffffffff81154ed0>] ? filldir+0x0/0xe0
Feb 11 06:47:44 production kernel: [330330.076540]  [<ffffffff8153f9cd>] schedule_timeout+0x22d/0x300
Feb 11 06:47:44 production kernel: [330330.076545]  [<ffffffff8104b3c9>] ? sched_slice+0x59/0xa0
Feb 11 06:47:44 production kernel: [330330.076549]  [<ffffffff8115de93>] ? dup_fd+0x33/0x340
Feb 11 06:47:44 production kernel: [330330.076553]  [<ffffffff812b4323>] ? cpumask_next_and+0x23/0x40
Feb 11 06:47:44 production kernel: [330330.076557]  [<ffffffff8153f5eb>] wait_for_common+0xdb/0x180
Feb 11 06:47:44 production kernel: [330330.076560]  [<ffffffff8105ddcb>] ? enqueue_task_fair+0x5b/0xa0
Feb 11 06:47:44 production kernel: [330330.076563]  [<ffffffff8105ccb0>] ? default_wake_function+0x0/0x20
Feb 11 06:47:44 production kernel: [330330.076566]  [<ffffffff8153f74d>] wait_for_completion+0x1d/0x20
Feb 11 06:47:44 production kernel: [330330.076569]  [<ffffffff81065870>] do_fork+0x150/0x440
Feb 11 06:47:44 production kernel: [330330.076572]  [<ffffffff8115ff30>] ? mntput_no_expire+0x30/0x110
Feb 11 06:47:44 production kernel: [330330.076577]  [<ffffffff8107e085>] ? set_one_prio+0x75/0xd0
Feb 11 06:47:44 production kernel: [330330.076582]  [<ffffffff8101a085>] sys_vfork+0x25/0x30
Feb 11 06:47:44 production kernel: [330330.076586]  [<ffffffff81012513>] stub_vfork+0x13/0x20
Feb 11 06:47:44 production kernel: [330330.076589]  [<ffffffff810121b2>] ? system_call_fastpath+0x16/0x1b

```

I'm not really sure where to start with resolving this problem so looking for any advice on where to start tracking down the source of this.

Thanks in advance!

Alastair

---

### Post by jmordkoff on 2012-05-21
My public server just had the same issue Saturday night, also related to a cron job. 

I'd really appreciate any pointers anyone has that can help me get to the bottom of this. 

filldir does not seem to have or call any code that could possibly block, so I'm at a loss to explain how this occurred in the first place.

The cron task runs every 30 minutes and has run clean many times since the reboot. 

smartd was not enabled and it is now, but I don't think disk io is the cause.

---

### Post by jmordkoff on 2012-05-21
root@www:/var/log# cat /etc/debian_version 
squeeze/sid
root@www:/var/log# 
root@www:/var/log# 
root@www:/var/log# 
root@www:/var/log# uname -a
Linux www 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 05:14:15 UTC 2010 x86_64 GNU/Linux
root@www:/var/log#

---

