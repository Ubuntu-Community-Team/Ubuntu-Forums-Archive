---
title: "NFS service random crash"
date: 2015-01-22
forum: Server Platforms
---

### Post by dcastelltort on 2015-01-22
Hi,


We have recently replaced a nfs4 server that was running under ubuntu 12.10 by a new server running ubuntu 14.04. All clients connected to the nfs server are linux server running ubuntu 12.04/12.10. Since the replacing of the nfs server we experience random crash from the service (once every week/2 weeks). Clients can't browse the export from the NFS server until we restart the service. Looking at the logs on the server there is the following trace.


Someone has a clue of what's going on ? or experienced something similar ?

```

Jan 21 06:05:20 nfsfiler2 kernel: [398213.798328] INFO: task nfsd:1440 blocked for more than 120 seconds.
Jan 21 06:05:20 nfsfiler2 kernel: [398213.798371] Not tainted 3.13.0-24-generic #47-Ubuntu
Jan 21 06:05:20 nfsfiler2 kernel: [398213.798435] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Jan 21 06:05:20 nfsfiler2 kernel: [398213.798627] nfsd D ffff88013fd14440 0 1440 2 0x00000000
Jan 21 06:05:20 nfsfiler2 kernel: [398213.798630] ffff8800b595fce0 0000000000000002 ffff8800b921afe0 ffff8800b595ffd8
Jan 21 06:05:20 nfsfiler2 kernel: [398213.798633] 0000000000014440 0000000000014440 ffff8800b921afe0 ffffffffa01a90a0
Jan 21 06:05:20 nfsfiler2 kernel: [398213.798635] ffffffffa01a90a4 ffff8800b921afe0 00000000ffffffff ffffffffa01a90a8
Jan 21 06:05:20 nfsfiler2 kernel: [398213.798638] Call Trace:
Jan 21 06:05:20 nfsfiler2 kernel: [398213.798642] [<ffffffff8171a409>] schedule_preempt_disabled+0x29/0x70
Jan 21 06:05:20 nfsfiler2 kernel: [398213.798645] [<ffffffff8171c275>] __mutex_lock_slowpath+0x135/0x1b0
Jan 21 06:05:20 nfsfiler2 kernel: [398213.798654] [<ffffffffa00d09b0>] ? svcauth_unix_domain_release+0x30/0x30 [sunrpc]
Jan 21 06:05:20 nfsfiler2 kernel: [398213.798658] [<ffffffff8171c30f>] mutex_lock+0x1f/0x2f
Jan 21 06:05:20 nfsfiler2 kernel: [398213.798665] [<ffffffffa019714f>] nfsd4_renew+0x5f/0xf0 [nfsd]
Jan 21 06:05:20 nfsfiler2 kernel: [398213.798672] [<ffffffffa01865da>] nfsd4_proc_compound+0x56a/0x7b0 [nfsd]
Jan 21 06:05:20 nfsfiler2 kernel: [398213.798677] [<ffffffffa0172d2b>] nfsd_dispatch+0xbb/0x200 [nfsd]
Jan 21 06:05:20 nfsfiler2 kernel: [398213.798686] [<ffffffffa00cd63d>] svc_process_common+0x46d/0x6d0 [sunrpc]
Jan 21 06:05:20 nfsfiler2 kernel: [398213.798696] [<ffffffffa00cd9a7>] svc_process+0x107/0x170 [sunrpc]
Jan 21 06:05:20 nfsfiler2 kernel: [398213.798701] [<ffffffffa017271f>] nfsd+0xbf/0x130 [nfsd]
Jan 21 06:05:20 nfsfiler2 kernel: [398213.798706] [<ffffffffa0172660>] ? nfsd_destroy+0x80/0x80 [nfsd]
Jan 21 06:05:20 nfsfiler2 kernel: [398213.798708] [<ffffffff8108b312>] kthread+0xd2/0xf0
Jan 21 06:05:20 nfsfiler2 kernel: [398213.798711] [<ffffffff8108b240>] ? kthread_create_on_node+0x1d0/0x1d0
Jan 21 06:05:20 nfsfiler2 kernel: [398213.798714] [<ffffffff817263fc>] ret_from_fork+0x7c/0xb0
Jan 21 06:05:20 nfsfiler2 kernel: [398213.798717] [<ffffffff8108b240>] ? kthread_create_on_node+0x1d0/0x1d0
Jan 21 06:05:20 nfsfiler2 kernel: [398213.798721] INFO: task kworker/u4:2:9594 blocked for more than 120 seconds.
Jan 21 06:05:20 nfsfiler2 kernel: [398213.798882] Not tainted 3.13.0-24-generic #47-Ubuntu
Jan 21 06:05:20 nfsfiler2 kernel: [398213.799052] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Jan 21 06:05:20 nfsfiler2 kernel: [398213.799197] kworker/u4:2 D ffff88013fd14440 0 9594 2 0x00000000
Jan 21 06:05:20 nfsfiler2 kernel: [398213.799207] Workqueue: nfsd4 laundromat_main [nfsd]
Jan 21 06:05:20 nfsfiler2 kernel: [398213.799209] ffff8800365cbd40 0000000000000002 ffff8800b582c7d0 ffff8800365cbfd8
Jan 21 06:05:20 nfsfiler2 kernel: [398213.799212] 0000000000014440 0000000000014440 ffff8800b582c7d0 ffffffffa01a90a0
Jan 21 06:05:20 nfsfiler2 kernel: [398213.799214] ffffffffa01a90a4 ffff8800b582c7d0 00000000ffffffff ffffffffa01a90a8
Jan 21 06:05:20 nfsfiler2 kernel: [398213.799217] Call Trace:
Jan 21 06:05:20 nfsfiler2 kernel: [398213.799221] [<ffffffff8171a409>] schedule_preempt_disabled+0x29/0x70
Jan 21 06:05:20 nfsfiler2 kernel: [398213.799224] [<ffffffff8171c275>] __mutex_lock_slowpath+0x135/0x1b0
Jan 21 06:05:20 nfsfiler2 kernel: [398213.799227] [<ffffffff8171c30f>] mutex_lock+0x1f/0x2f
Jan 21 06:05:20 nfsfiler2 kernel: [398213.799234] [<ffffffffa0195a46>] laundromat_main+0x46/0x420 [nfsd]
Jan 21 06:05:20 nfsfiler2 kernel: [398213.799238] [<ffffffff810838a2>] process_one_work+0x182/0x450
Jan 21 06:05:20 nfsfiler2 kernel: [398213.799252] [<ffffffff81084641>] worker_thread+0x121/0x410
Jan 21 06:05:20 nfsfiler2 kernel: [398213.799256] [<ffffffff81084520>] ? rescuer_thread+0x3e0/0x3e0
Jan 21 06:05:20 nfsfiler2 kernel: [398213.799258] [<ffffffff8108b312>] kthread+0xd2/0xf0
Jan 21 06:05:20 nfsfiler2 kernel: [398213.799261] [<ffffffff8108b240>] ? kthread_create_on_node+0x1d0/0x1d0
Jan 21 06:05:20 nfsfiler2 kernel: [398213.799264] [<ffffffff817263fc>] ret_from_fork+0x7c/0xb0
Jan 21 06:05:20 nfsfiler2 kernel: [398213.799267] [<ffffffff8108b240>] ? kthread_create_on_node+0x1d0/0x1d0
```

---

### Post by ct302 on 2015-05-26
I'm having a similar issue. Currently using 14.04.2. Did you ever find a fix?

---

