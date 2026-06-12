---
title: "High IO causes IO to lock up"
date: 2012-05-07
forum: Server Platforms
---

### Post by infecticide on 2012-05-07
Getting messages like these in the dmesg output.



[ 1081.848137] INFO: task kjournald:388 blocked for more than 120 seconds.
[ 1081.850181] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[ 1081.852432] kjournald       D 0000000000000000     0   388      2 0x00000000
[ 1081.852454]  ffff8803fed2dc10 0000000000000046 ffff8803fed2dbb0 ffffffff8103dbb9
[ 1081.852483]  ffff8803fed2dfd8 ffff8803fed2dfd8 ffff8803fed2dfd8 0000000000013780
[ 1081.852511]  ffff8803ff682de0 ffff8803fee6c4d0 ffff8803fed2dbf0 ffff88041dc14040
[ 1081.852539] Call Trace:
[ 1081.852560]  [<ffffffff8103dbb9>] ? default_spin_lock_flags+0x9/0x10
[ 1081.852579]  [<ffffffff811a86d0>] ? __wait_on_buffer+0x30/0x30
[ 1081.852594]  [<ffffffff8165a55f>] schedule+0x3f/0x60
[ 1081.852607]  [<ffffffff8165a60f>] io_schedule+0x8f/0xd0
[ 1081.852621]  [<ffffffff811a86de>] sleep_on_buffer+0xe/0x20
[ 1081.852635]  [<ffffffff8165ae2f>] __wait_on_bit+0x5f/0x90
[ 1081.852650]  [<ffffffff811a86d0>] ? __wait_on_buffer+0x30/0x30
[ 1081.852664]  [<ffffffff8165aedc>] out_of_line_wait_on_bit+0x7c/0x90
[ 1081.852679]  [<ffffffff8108af00>] ? autoremove_wake_function+0x40/0x40
[ 1081.852694]  [<ffffffff811a86ce>] __wait_on_buffer+0x2e/0x30
[ 1081.852709]  [<ffffffff81257553>] journal_commit_transaction+0xa23/0xfc0
[ 1081.852724]  [<ffffffff8165c46e>] ? _raw_spin_lock+0xe/0x20
[ 1081.852740]  [<ffffffff81077bd2>] ? try_to_del_timer_sync+0x92/0x130
[ 1081.852756]  [<ffffffff8125b06b>] kjournald+0xeb/0x250
[ 1081.852769]  [<ffffffff8108aec0>] ? add_wait_queue+0x60/0x60
[ 1081.852782]  [<ffffffff8125af80>] ? commit_timeout+0x10/0x10
[ 1081.852795]  [<ffffffff8108a42c>] kthread+0x8c/0xa0
[ 1081.852811]  [<ffffffff81666bf4>] kernel_thread_helper+0x4/0x10
[ 1081.852825]  [<ffffffff8108a3a0>] ? flush_kthread_worker+0xa0/0xa0
[ 1081.852839]  [<ffffffff81666bf0>] ? gs_change+0x13/0x13


2 mins before these appear, all IO to the RAID array stops, DSTAT shows 0 write 0 read.

At the time this occured, the machine was rebuilding a RAID 5 and I was rsyncing some files from another machine on the LAN.

I can recreate this issue even after the RAID is finished rebuilding.

I am running Ubuntu Server 12.04.

Any thoughts are appreciated.

---

### Post by HermanAB on 2012-05-07
Try ionice.

---

### Post by Doug S on 2012-05-07
On my older more pathetic computer, I have a problem with 12.04 server under very high disk I/O situations. The I/O will lock up, however in my case it will eventually (I think 30 seconds) unfreeze and continue.
 
I have isolated the issue down to the udev package: version "udev 175-0ubuntu6" does not have the problem; version "udev 175-0ubuntu9" has the problem. I was continuing, and was going to start compiling udev myself, removing the various differences. However, something has come up and I will not get to this for another week or two.
 
I do not know if your issue is from the same root cause or not, nor have I observed any other postings that might be the same root cause (and I have been looking).
 
References:
[Launchpad bug report ]("https://bugs.launchpad.net/ubuntu/+source/udev/+bug/986654")
[Forums thread ]("http://ubuntuforums.org/showthread.php?t=1958838")( a little out of date now).

---

