---
title: "kvm-guest gets read-only every day"
date: 2010-04-09
forum: Virtualisation
---

### Post by derjoerg on 2010-04-09
Hi,

I've a 64-bit AMD server with 4 virtual-machines. On the host and all the guests I just upgraded from jaunty to karmic without a problem (everything 64bit-server version).

But ...

since the upgrade one of my virtual machines puts its filesystem to read-only once a day. A "shutdown" is not working anymore and I have to do a "virsh destroy xyz" and "virsh start xyz" on the host.

Below is the output from kern.log with a lot of ata-failures. Can someone point me to the right direction what I can do/check/modify?

All the other vms are running without a problem.

```

Apr  9 01:37:55 www kernel: [47906.384870] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Apr  9 01:37:55 www kernel: [47906.431983] ata1.00: cmd ca/00:90:58:05:f8/00:00:00:00:00/e1 tag 0 dma 73728 out
Apr  9 01:37:55 www kernel: [47906.431987]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Apr  9 01:37:55 www kernel: [47906.444197] ata1.00: status: { DRDY }
Apr  9 01:37:55 www kernel: [47911.490151] ata1: link is slow to respond, please be patient (ready=0)
Apr  9 01:37:55 www kernel: [47916.470149] ata1: device not ready (errno=-16), forcing hardreset
Apr  9 01:37:55 www kernel: [47916.470218] ata1: soft resetting link
Apr  9 01:37:55 www kernel: [47916.645226] ata1.00: configured for MWDMA2
Apr  9 01:37:55 www kernel: [47916.645240] ata1.00: device reported invalid CHS sector 0
Apr  9 01:37:55 www kernel: [47916.645277] ata1: EH complete
Apr  9 01:37:55 www kernel: [47947.040359] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Apr  9 01:37:55 www kernel: [47947.041187] ata1.00: cmd ca/00:90:58:05:f8/00:00:00:00:00/e1 tag 0 dma 73728 out
Apr  9 01:37:55 www kernel: [47947.041190]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Apr  9 01:37:55 www kernel: [47947.045291] ata1.00: status: { DRDY }
Apr  9 01:37:55 www kernel: [47952.080132] ata1: link is slow to respond, please be patient (ready=0)
Apr  9 01:37:55 www kernel: [47957.060147] ata1: device not ready (errno=-16), forcing hardreset
Apr  9 01:37:55 www kernel: [47957.060217] ata1: soft resetting link
Apr  9 01:37:55 www kernel: [47957.222667] ata1.00: configured for MWDMA2
Apr  9 01:37:55 www kernel: [47957.222678] ata1.00: device reported invalid CHS sector 0
Apr  9 01:37:55 www kernel: [47957.222701] ata1: EH complete
Apr  9 01:37:55 www kernel: [47988.040342] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Apr  9 01:37:55 www kernel: [47988.041990] ata1.00: cmd ca/00:90:58:05:f8/00:00:00:00:00/e1 tag 0 dma 73728 out
Apr  9 01:37:55 www kernel: [47988.041993]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Apr  9 01:37:55 www kernel: [47988.046860] ata1.00: status: { DRDY }
Apr  9 01:37:55 www kernel: [47993.080146] ata1: link is slow to respond, please be patient (ready=0)
Apr  9 01:37:55 www kernel: [47998.060131] ata1: device not ready (errno=-16), forcing hardreset
Apr  9 01:37:55 www kernel: [47998.060200] ata1: soft resetting link
Apr  9 01:37:55 www kernel: [47998.222686] ata1.00: configured for MWDMA2
Apr  9 01:37:55 www kernel: [47998.222697] ata1.00: device reported invalid CHS sector 0
Apr  9 01:37:55 www kernel: [47998.222719] ata1: EH complete
Apr  9 01:37:55 www kernel: [48029.040356] ata1.00: limiting speed to MWDMA1:PIO2
Apr  9 01:37:55 www kernel: [48029.040367] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Apr  9 01:37:55 www kernel: [48029.042022] ata1.00: cmd ca/00:90:58:05:f8/00:00:00:00:00/e1 tag 0 dma 73728 out
Apr  9 01:37:55 www kernel: [48029.042025]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Apr  9 01:37:55 www kernel: [48029.046880] ata1.00: status: { DRDY }
Apr  9 01:37:55 www kernel: [48034.080139] ata1: link is slow to respond, please be patient (ready=0)
Apr  9 01:37:55 www kernel: [48039.060153] ata1: device not ready (errno=-16), forcing hardreset
Apr  9 01:37:55 www kernel: [48039.060221] ata1: soft resetting link
Apr  9 01:37:55 www kernel: [48039.222680] ata1.00: configured for MWDMA1
Apr  9 01:37:55 www kernel: [48039.222691] ata1.00: device reported invalid CHS sector 0
Apr  9 01:37:55 www kernel: [48039.222713] ata1: EH complete
Apr  9 01:37:55 www kernel: [48070.040343] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Apr  9 01:37:55 www kernel: [48070.041974] ata1.00: cmd ca/00:90:58:05:f8/00:00:00:00:00/e1 tag 0 dma 73728 out
Apr  9 01:37:55 www kernel: [48070.041977]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Apr  9 01:37:55 www kernel: [48070.046791] ata1.00: status: { DRDY }
Apr  9 01:37:55 www kernel: [48075.080150] ata1: link is slow to respond, please be patient (ready=0)
Apr  9 01:37:55 www kernel: [48080.070204] ata1: device not ready (errno=-16), forcing hardreset
Apr  9 01:37:55 www kernel: [48080.070274] ata1: soft resetting link
Apr  9 01:37:55 www kernel: [48080.232674] ata1.00: configured for MWDMA1
Apr  9 01:37:55 www kernel: [48080.232686] ata1.00: device reported invalid CHS sector 0
Apr  9 01:37:55 www kernel: [48080.232708] ata1: EH complete
Apr  9 01:37:55 www kernel: [48111.040372] ata1.00: limiting speed to PIO2
Apr  9 01:37:55 www kernel: [48111.040382] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Apr  9 01:37:55 www kernel: [48111.042027] ata1.00: cmd ca/00:90:58:05:f8/00:00:00:00:00/e1 tag 0 dma 73728 out
Apr  9 01:37:55 www kernel: [48111.042030]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Apr  9 01:37:55 www kernel: [48111.046879] ata1.00: status: { DRDY }
Apr  9 01:37:55 www kernel: [48116.080128] ata1: link is slow to respond, please be patient (ready=0)
Apr  9 01:37:55 www kernel: [48120.440140] INFO: task ata_aux:24 blocked for more than 120 seconds.
Apr  9 01:37:55 www kernel: [48120.441817] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Apr  9 01:37:55 www kernel: [48120.444348] ata_aux       D 0000000000000000     0    24      2 0x00000000
Apr  9 01:37:55 www kernel: [48120.444372]  ffff88003eae7990 0000000000000046 ffff88003eae7990 0000000000015880
Apr  9 01:37:55 www kernel: [48120.444404]  ffff88003ea6de70 0000000000015880 0000000000015880 0000000000015880
Apr  9 01:37:55 www kernel: [48120.444411]  0000000000015880 ffff88003ea6de70 0000000000015880 0000000000015880
Apr  9 01:37:55 www kernel: [48120.444419] Call Trace:
Apr  9 01:37:55 www kernel: [48120.444540]  [<ffffffff81528755>] schedule_timeout+0x1d5/0x230
Apr  9 01:37:55 www kernel: [48120.444651]  [<ffffffff81276cb7>] ? kobject_put+0x27/0x60
Apr  9 01:37:55 www kernel: [48120.444659]  [<ffffffff8152a0a0>] ? _spin_lock_irq+0x10/0x20
Apr  9 01:37:55 www kernel: [48120.444714]  [<ffffffff8133d4f2>] ? scsi_request_fn+0xd2/0x500
Apr  9 01:37:55 www kernel: [48120.444761]  [<ffffffff8106ac69>] ? del_timer+0x59/0x70
Apr  9 01:37:55 www kernel: [48120.444769]  [<ffffffff81527b90>] wait_for_common+0xd0/0x170
Apr  9 01:37:55 www kernel: [48120.444786]  [<ffffffff8125a525>] ? elv_insert+0x85/0x1f0
Apr  9 01:37:55 www kernel: [48120.451751]  [<ffffffff81053890>] ? default_wake_function+0x0/0x10
Apr  9 01:37:55 www kernel: [48120.492000]  [<ffffffff81260eca>] ? __generic_unplug_device+0x1a/0x40
Apr  9 01:37:55 www kernel: [48120.492009]  [<ffffffff81527cc8>] wait_for_completion+0x18/0x20
Apr  9 01:37:55 www kernel: [48120.492018]  [<ffffffff812686c7>] blk_execute_rq+0x87/0xe0
Apr  9 01:37:55 www kernel: [48120.492025]  [<ffffffff812653ac>] ? blk_get_request+0x6c/0xa0
Apr  9 01:37:55 www kernel: [48120.492032]  [<ffffffff8133ed47>] scsi_execute+0xf7/0x160
Apr  9 01:37:55 www kernel: [48120.492039]  [<ffffffff8133ef87>] scsi_execute_req+0xa7/0x180
Apr  9 01:37:55 www kernel: [48120.492047]  [<ffffffff813485b0>] sd_spinup_disk+0x90/0x520
Apr  9 01:37:55 www kernel: [48120.492054]  [<ffffffff8134ae52>] sd_revalidate_disk+0xb2/0x2e0
Apr  9 01:37:55 www kernel: [48120.492063]  [<ffffffff81276e5a>] ? kobject_get+0x1a/0x30
Apr  9 01:37:55 www kernel: [48120.492100]  [<ffffffff8114b623>] revalidate_disk+0x33/0x90
Apr  9 01:37:55 www kernel: [48120.492109]  [<ffffffff81347522>] sd_rescan+0x22/0x40
Apr  9 01:37:55 www kernel: [48120.492116]  [<ffffffff813403ef>] scsi_rescan_device+0x4f/0x70
Apr  9 01:37:55 www kernel: [48120.492133]  [<ffffffff8135d8ea>] ata_scsi_dev_rescan+0xaa/0x100
Apr  9 01:37:55 www kernel: [48120.492140]  [<ffffffff8135d840>] ? ata_scsi_dev_rescan+0x0/0x100
Apr  9 01:37:55 www kernel: [48120.492160]  [<ffffffff810731f5>] run_workqueue+0x95/0x170
Apr  9 01:37:55 www kernel: [48120.492168]  [<ffffffff81073374>] worker_thread+0xa4/0x120
Apr  9 01:37:55 www kernel: [48120.492177]  [<ffffffff81078500>] ? autoremove_wake_function+0x0/0x40
Apr  9 01:37:55 www kernel: [48120.492185]  [<ffffffff810732d0>] ? worker_thread+0x0/0x120
Apr  9 01:37:55 www kernel: [48120.492192]  [<ffffffff81078116>] kthread+0xa6/0xb0
Apr  9 01:37:55 www kernel: [48120.492228]  [<ffffffff8101312a>] child_rip+0xa/0x20
Apr  9 01:37:55 www kernel: [48120.492235]  [<ffffffff81078070>] ? kthread+0x0/0xb0
Apr  9 01:37:55 www kernel: [48120.492241]  [<ffffffff81013120>] ? child_rip+0x0/0x20
Apr  9 01:37:55 www kernel: [48120.492255] INFO: task dd:558 blocked for more than 120 seconds.
Apr  9 01:37:55 www kernel: [48120.493774] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Apr  9 01:37:56 www kernel: [48120.496359] dd            D 0000000000000000     0   558      1 0x00000000
Apr  9 01:37:56 www kernel: [48120.496368]  ffff88003356dac8 0000000000000082 ffff88003356daa8 0000000000015880
Apr  9 01:37:56 www kernel: [48120.496377]  ffff88003431b110 0000000000015880 0000000000015880 0000000000015880
Apr  9 01:37:56 www kernel: [48120.496385]  0000000000015880 ffff88003431b110 0000000000015880 0000000000015880
Apr  9 01:37:56 www kernel: [48120.496393] Call Trace:
Apr  9 01:37:56 www kernel: [48120.496448]  [<ffffffff810da010>] ? sync_page+0x0/0x50
Apr  9 01:37:56 www kernel: [48120.496455]  [<ffffffff81528488>] io_schedule+0x28/0x40
Apr  9 01:37:56 www kernel: [48120.496462]  [<ffffffff810da04d>] sync_page+0x3d/0x50
Apr  9 01:37:56 www kernel: [48120.496469]  [<ffffffff81528862>] __wait_on_bit_lock+0x52/0xb0
Apr  9 01:37:56 www kernel: [48120.496476]  [<ffffffff810d9ff2>] __lock_page+0x62/0x70
Apr  9 01:37:56 www kernel: [48120.496483]  [<ffffffff81078540>] ? wake_bit_function+0x0/0x40
Apr  9 01:37:56 www kernel: [48120.496511]  [<ffffffff810f8132>] do_swap_page+0x402/0x410
Apr  9 01:37:56 www kernel: [48120.496520]  [<ffffffff8105b238>] ? check_preempt_wakeup+0x1d8/0x210
Apr  9 01:37:56 www kernel: [48120.496527]  [<ffffffff81053668>] ? try_to_wake_up+0x118/0x340
Apr  9 01:37:56 www kernel: [48120.496534]  [<ffffffff810f840b>] handle_mm_fault+0x2cb/0x3c0
Apr  9 01:37:56 www kernel: [48120.496563]  [<ffffffff81036419>] ? default_spin_lock_flags+0x9/0x10
Apr  9 01:37:56 www kernel: [48120.496571]  [<ffffffff8152ccf5>] do_page_fault+0x165/0x360
Apr  9 01:37:56 www kernel: [48120.496579]  [<ffffffff8152a675>] page_fault+0x25/0x30
Apr  9 01:37:56 www kernel: [48120.496587]  [<ffffffff8105fa3e>] ? do_syslog+0x33e/0x4c0
Apr  9 01:37:56 www kernel: [48120.496593]  [<ffffffff8105fa33>] ? do_syslog+0x333/0x4c0
Apr  9 01:37:56 www kernel: [48120.496601]  [<ffffffff81078500>] ? autoremove_wake_function+0x0/0x40
Apr  9 01:37:56 www kernel: [48120.496630]  [<ffffffff8117c7a0>] ? kmsg_read+0x0/0x60
Apr  9 01:37:56 www kernel: [48120.496636]  [<ffffffff8117c7cd>] kmsg_read+0x2d/0x60
Apr  9 01:37:56 www kernel: [48120.496655]  [<ffffffff81171e5c>] proc_reg_read+0x7c/0xc0
Apr  9 01:37:56 www kernel: [48120.496705]  [<ffffffff8111f005>] vfs_read+0xb5/0x1a0
Apr  9 01:37:56 www kernel: [48120.496713]  [<ffffffff8111f5dc>] sys_read+0x4c/0x80
Apr  9 01:37:56 www kernel: [48120.496732]  [<ffffffff81012042>] system_call_fastpath+0x16/0x1b
Apr  9 01:37:56 www kernel: [48120.496750] INFO: task apache2:1098 blocked for more than 120 seconds.
Apr  9 01:37:56 www kernel: [48120.498312] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Apr  9 01:37:56 www kernel: [48120.500912] apache2       D 0000000000000000     0  1098   1038 0x00000000
Apr  9 01:37:56 www kernel: [48120.500921]  ffff8800349e7a18 0000000000000086 ffff8800349e7a48 0000000000015880
Apr  9 01:37:56 www kernel: [48120.500929]  ffff8800340c03b0 0000000000015880 0000000000015880 0000000000015880
Apr  9 01:37:56 www kernel: [48120.500937]  0000000000015880 ffff8800340c03b0 0000000000015880 0000000000015880
Apr  9 01:37:56 www kernel: [48120.500945] Call Trace:
Apr  9 01:37:56 www kernel: [48120.500965]  [<ffffffff81145b30>] ? sync_buffer+0x0/0x50
Apr  9 01:37:56 www kernel: [48120.500973]  [<ffffffff81528488>] io_schedule+0x28/0x40
Apr  9 01:37:56 www kernel: [48120.500981]  [<ffffffff81145b6b>] sync_buffer+0x3b/0x50
Apr  9 01:37:56 www kernel: [48120.500987]  [<ffffffff815289a7>] __wait_on_bit+0x57/0x80
Apr  9 01:37:56 www kernel: [48120.500995]  [<ffffffff81145b30>] ? sync_buffer+0x0/0x50
Apr  9 01:37:56 www kernel: [48120.501003]  [<ffffffff81528a43>] out_of_line_wait_on_bit+0x73/0x90
Apr  9 01:37:56 www kernel: [48120.501011]  [<ffffffff81078540>] ? wake_bit_function+0x0/0x40
Apr  9 01:37:56 www kernel: [48120.501019]  [<ffffffff81145b26>] __wait_on_buffer+0x26/0x30
Apr  9 01:37:56 www kernel: [48120.501037]  [<ffffffff81194364>] ext3_find_entry+0xf4/0x420
Apr  9 01:37:56 www kernel: [48120.501046]  [<ffffffff811946dd>] ext3_lookup+0x4d/0x130
Apr  9 01:37:56 www kernel: [48120.501054]  [<ffffffff811280ba>] real_lookup+0xda/0x150
Apr  9 01:37:56 www kernel: [48120.501063]  [<ffffffff81129cb0>] do_lookup+0xb0/0xe0
Apr  9 01:37:56 www kernel: [48120.501071]  [<ffffffff8112a305>] __link_path_walk+0x155/0xdc0
Apr  9 01:37:56 www kernel: [48120.501079]  [<ffffffff8112b157>] path_walk+0x57/0xb0
Apr  9 01:37:56 www kernel: [48120.501086]  [<ffffffff8112b203>] do_path_lookup+0x53/0xa0
Apr  9 01:37:56 www kernel: [48120.501094]  [<ffffffff8112bea2>] user_path_at+0x52/0xa0
Apr  9 01:37:56 www kernel: [48120.501158]  [<ffffffff8141baeb>] ? aa_get_task_policy+0x1b/0x30
Apr  9 01:37:56 www kernel: [48120.501165]  [<ffffffff81078500>] ? autoremove_wake_function+0x0/0x40
Apr  9 01:37:56 www kernel: [48120.501173]  [<ffffffff81123017>] vfs_fstatat+0x37/0x70
Apr  9 01:37:56 www kernel: [48120.501179]  [<ffffffff81123176>] vfs_stat+0x16/0x20
Apr  9 01:37:56 www kernel: [48120.501186]  [<ffffffff8112319f>] sys_newstat+0x1f/0x50
Apr  9 01:37:56 www kernel: [48120.501204]  [<ffffffff81081bb5>] ? do_gettimeofday+0x15/0x50
Apr  9 01:37:56 www kernel: [48120.501212]  [<ffffffff810639db>] ? sys_gettimeofday+0x3b/0x80
Apr  9 01:37:56 www kernel: [48120.501221]  [<ffffffff81012042>] system_call_fastpath+0x16/0x1b
Apr  9 01:37:56 www kernel: [48120.501251] INFO: task cron:3354 blocked for more than 120 seconds.
Apr  9 01:37:56 www kernel: [48120.502786] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Apr  9 01:37:56 www kernel: [48120.505340] cron          D 0000000000000000     0  3354    684 0x00000000
Apr  9 01:37:56 www kernel: [48120.505350]  ffff88002542ba38 0000000000000082 ffff88002542b9b8 0000000000015880
Apr  9 01:37:56 www kernel: [48120.505358]  ffff88003400c7c0 0000000000015880 0000000000015880 0000000000015880
Apr  9 01:37:56 www kernel: [48120.505366]  0000000000015880 ffff88003400c7c0 0000000000015880 0000000000015880
Apr  9 01:37:56 www kernel: [48120.505374] Call Trace:
Apr  9 01:37:56 www kernel: [48120.505382]  [<ffffffff81145b30>] ? sync_buffer+0x0/0x50
Apr  9 01:37:56 www kernel: [48120.505390]  [<ffffffff81528488>] io_schedule+0x28/0x40
Apr  9 01:37:56 www kernel: [48120.505397]  [<ffffffff81145b6b>] sync_buffer+0x3b/0x50
Apr  9 01:37:56 www kernel: [48120.505404]  [<ffffffff815289a7>] __wait_on_bit+0x57/0x80
Apr  9 01:37:56 www kernel: [48120.505412]  [<ffffffff81145b30>] ? sync_buffer+0x0/0x50
Apr  9 01:37:56 www kernel: [48120.505419]  [<ffffffff81528a43>] out_of_line_wait_on_bit+0x73/0x90
Apr  9 01:37:56 www kernel: [48120.505427]  [<ffffffff81078540>] ? wake_bit_function+0x0/0x40
Apr  9 01:37:56 www kernel: [48120.505435]  [<ffffffff81145b26>] __wait_on_buffer+0x26/0x30
Apr  9 01:37:56 www kernel: [48120.505443]  [<ffffffff8118ded7>] __ext3_get_inode_loc+0x2a7/0x330
Apr  9 01:37:56 www kernel: [48120.505450]  [<ffffffff8118dfb5>] ext3_iget+0x55/0x3f0
Apr  9 01:37:56 www kernel: [48120.505458]  [<ffffffff81194738>] ext3_lookup+0xa8/0x130
Apr  9 01:37:56 www kernel: [48120.505466]  [<ffffffff811280ba>] real_lookup+0xda/0x150
Apr  9 01:37:56 www kernel: [48120.505473]  [<ffffffff81129cb0>] do_lookup+0xb0/0xe0
Apr  9 01:37:56 www kernel: [48120.505481]  [<ffffffff8112a85d>] __link_path_walk+0x6ad/0xdc0
Apr  9 01:37:57 www kernel: [48120.505489]  [<ffffffff8112b157>] path_walk+0x57/0xb0
Apr  9 01:37:57 www kernel: [48120.505497]  [<ffffffff8112b203>] do_path_lookup+0x53/0xa0
Apr  9 01:37:57 www kernel: [48120.505504]  [<ffffffff8112025c>] ? get_empty_filp+0x9c/0x170
Apr  9 01:37:57 www kernel: [48120.505512]  [<ffffffff8112c25e>] do_filp_open+0xfe/0xac0
Apr  9 01:37:57 www kernel: [48120.505519]  [<ffffffff810f3f39>] ? __do_fault+0x419/0x4e0
Apr  9 01:37:57 www kernel: [48120.505538]  [<ffffffff81036419>] ? default_spin_lock_flags+0x9/0x10
Apr  9 01:37:57 www kernel: [48120.505547]  [<ffffffff81136da2>] ? alloc_fd+0x102/0x150
Apr  9 01:37:57 www kernel: [48120.505555]  [<ffffffff8111c894>] do_sys_open+0x64/0x160
Apr  9 01:37:57 www kernel: [48120.505563]  [<ffffffff8111c9bb>] sys_open+0x1b/0x20
Apr  9 01:37:57 www kernel: [48120.505570]  [<ffffffff81012042>] system_call_fastpath+0x16/0x1b
Apr  9 01:37:57 www kernel: [48121.100140] ata1: device not ready (errno=-16), forcing hardreset
Apr  9 01:37:57 www kernel: [48121.100207] ata1: soft resetting link
Apr  9 01:37:57 www kernel: [48121.262690] ata1.00: configured for PIO2
Apr  9 01:37:57 www kernel: [48121.262703] ata1.00: device reported invalid CHS sector 0
Apr  9 01:37:57 www kernel: [48121.262749] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr  9 01:37:57 www kernel: [48121.262778] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
Apr  9 01:37:57 www kernel: [48121.262798] Descriptor sense data with sense descriptors (in hex):
Apr  9 01:37:57 www kernel: [48121.262802]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00
Apr  9 01:37:57 www kernel: [48121.262820]         00 00 00 00
Apr  9 01:37:57 www kernel: [48121.262827] sd 0:0:0:0: [sda] Add. Sense: No additional sense information
Apr  9 01:37:57 www kernel: [48121.262846] end_request: I/O error, dev sda, sector 33031512
Apr  9 01:37:57 www kernel: [48121.264328] Buffer I/O error on device sda1, logical block 4128935
Apr  9 01:37:57 www kernel: [48121.265851] lost page write due to I/O error on sda1
Apr  9 01:37:57 www kernel: [48121.265868] Buffer I/O error on device sda1, logical block 4128936
Apr  9 01:37:57 www kernel: [48121.267362] lost page write due to I/O error on sda1
Apr  9 01:37:57 www kernel: [48121.267371] Buffer I/O error on device sda1, logical block 4128937
Apr  9 01:37:57 www kernel: [48121.268864] lost page write due to I/O error on sda1
Apr  9 01:37:57 www kernel: [48121.268872] Buffer I/O error on device sda1, logical block 4128938
Apr  9 01:37:57 www kernel: [48121.270464] lost page write due to I/O error on sda1
Apr  9 01:37:57 www kernel: [48121.270471] Buffer I/O error on device sda1, logical block 4128939
Apr  9 01:37:57 www kernel: [48121.271961] lost page write due to I/O error on sda1
Apr  9 01:37:57 www kernel: [48121.271969] Buffer I/O error on device sda1, logical block 4128940
Apr  9 01:37:57 www kernel: [48121.273468] lost page write due to I/O error on sda1
Apr  9 01:37:57 www kernel: [48121.273475] Buffer I/O error on device sda1, logical block 4128941
Apr  9 01:37:57 www kernel: [48121.274968] lost page write due to I/O error on sda1
Apr  9 01:37:57 www kernel: [48121.274976] Buffer I/O error on device sda1, logical block 4128942
Apr  9 01:37:57 www kernel: [48121.276707] lost page write due to I/O error on sda1
Apr  9 01:37:57 www kernel: [48121.276717] Buffer I/O error on device sda1, logical block 4128943
Apr  9 01:37:57 www kernel: [48121.278212] lost page write due to I/O error on sda1
Apr  9 01:37:57 www kernel: [48121.278219] Buffer I/O error on device sda1, logical block 4128944
Apr  9 01:37:57 www kernel: [48121.279714] lost page write due to I/O error on sda1
Apr  9 01:37:57 www kernel: [48121.279763] ata1: EH complete
Apr  9 01:45:30 www kernel: [48578.517306] EXT3-fs error (device sda1): ext3_lookup: deleted inode referenced: 1035105
Apr  9 01:45:37 www kernel: [48584.927522] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr  9 01:45:37 www kernel: [48584.929152] ata1.00: cmd c5/00:58:88:05:f8/00:00:00:00:00/e1 tag 0 pio 45056 out
Apr  9 01:45:37 www kernel: [48584.929155]          res 41/04:08:d8:05:f8/00:00:00:00:00/e1 Emask 0x1 (device error)
Apr  9 01:45:37 www kernel: [48584.934277] ata1.00: status: { DRDY ERR }
Apr  9 01:45:37 www kernel: [48584.935583] ata1.00: error: { ABRT }
Apr  9 01:45:37 www kernel: [48584.938928] ata1.00: configured for PIO2
Apr  9 01:45:37 www kernel: [48584.938945] ata1: EH complete
Apr  9 01:45:37 www kernel: [48584.978826] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr  9 01:45:37 www kernel: [48584.980514] ata1.00: cmd c5/00:58:88:05:f8/00:00:00:00:00/e1 tag 0 pio 45056 out
Apr  9 01:45:37 www kernel: [48584.980519]          res 41/04:08:d8:05:f8/00:00:00:00:00/e1 Emask 0x1 (device error)
Apr  9 01:45:37 www kernel: [48584.985442] ata1.00: status: { DRDY ERR }
Apr  9 01:45:37 www kernel: [48584.986701] ata1.00: error: { ABRT }
Apr  9 01:45:37 www kernel: [48584.990026] ata1.00: configured for PIO2
Apr  9 01:45:37 www kernel: [48584.990047] ata1: EH complete
Apr  9 01:45:37 www kernel: [48584.995177] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr  9 01:45:37 www kernel: [48584.996795] ata1.00: cmd c5/00:58:88:05:f8/00:00:00:00:00/e1 tag 0 pio 45056 out
Apr  9 01:45:37 www kernel: [48584.996798]          res 41/04:08:d8:05:f8/00:00:00:00:00/e1 Emask 0x1 (device error)
Apr  9 01:45:37 www kernel: [48585.001875] ata1.00: status: { DRDY ERR }
Apr  9 01:45:37 www kernel: [48585.003141] ata1.00: error: { ABRT }
Apr  9 01:45:37 www kernel: [48585.006474] ata1.00: configured for PIO2
Apr  9 01:45:37 www kernel: [48585.006491] ata1: EH complete
Apr  9 01:45:37 www kernel: [48585.012253] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr  9 01:45:37 www kernel: [48585.013834] ata1.00: cmd c5/00:58:88:05:f8/00:00:00:00:00/e1 tag 0 pio 45056 out
Apr  9 01:45:37 www kernel: [48585.013837]          res 41/04:08:d8:05:f8/00:00:00:00:00/e1 Emask 0x1 (device error)
Apr  9 01:45:37 www kernel: [48585.018886] ata1.00: status: { DRDY ERR }
Apr  9 01:45:37 www kernel: [48585.020182] ata1.00: error: { ABRT }
Apr  9 01:45:37 www kernel: [48585.023582] ata1.00: configured for PIO2
Apr  9 01:45:37 www kernel: [48585.023594] ata1: EH complete
Apr  9 01:45:37 www kernel: [48585.059177] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr  9 01:45:37 www kernel: [48585.060863] ata1.00: cmd c5/00:58:88:05:f8/00:00:00:00:00/e1 tag 0 pio 45056 out
Apr  9 01:45:37 www kernel: [48585.060866]          res 41/04:08:d8:05:f8/00:00:00:00:00/e1 Emask 0x1 (device error)
Apr  9 01:45:37 www kernel: [48585.065888] ata1.00: status: { DRDY ERR }
Apr  9 01:45:37 www kernel: [48585.067170] ata1.00: error: { ABRT }
Apr  9 01:45:37 www kernel: [48585.070570] ata1.00: configured for PIO2
Apr  9 01:45:37 www kernel: [48585.070586] ata1: EH complete
Apr  9 01:45:37 www kernel: [48585.075572] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr  9 01:45:37 www kernel: [48585.077132] ata1.00: cmd c5/00:58:88:05:f8/00:00:00:00:00/e1 tag 0 pio 45056 out
Apr  9 01:45:37 www kernel: [48585.077135]          res 41/04:08:d8:05:f8/00:00:00:00:00/e1 Emask 0x1 (device error)
Apr  9 01:45:37 www kernel: [48585.082074] ata1.00: status: { DRDY ERR }
Apr  9 01:45:37 www kernel: [48585.083344] ata1.00: error: { ABRT }
Apr  9 01:45:37 www kernel: [48585.086614] ata1.00: configured for PIO2
Apr  9 01:45:37 www kernel: [48585.086641] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr  9 01:45:37 www kernel: [48585.086649] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
Apr  9 01:45:37 www kernel: [48585.086659] Descriptor sense data with sense descriptors (in hex):
Apr  9 01:45:37 www kernel: [48585.086663]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00
Apr  9 01:45:37 www kernel: [48585.086681]         01 f8 05 d8
Apr  9 01:45:37 www kernel: [48585.086688] sd 0:0:0:0: [sda] Add. Sense: No additional sense information
Apr  9 01:45:37 www kernel: [48585.086697] end_request: I/O error, dev sda, sector 33031560
Apr  9 01:45:37 www kernel: [48585.088119] __ratelimit: 8 callbacks suppressed
Apr  9 01:45:37 www kernel: [48585.088125] Buffer I/O error on device sda1, logical block 4128941
Apr  9 01:45:37 www kernel: [48585.089614] lost page write due to I/O error on sda1
Apr  9 01:45:37 www kernel: [48585.089628] Buffer I/O error on device sda1, logical block 4128942
Apr  9 01:45:37 www kernel: [48585.091167] lost page write due to I/O error on sda1
Apr  9 01:45:37 www kernel: [48585.091175] Buffer I/O error on device sda1, logical block 4128943
Apr  9 01:45:37 www kernel: [48585.092654] lost page write due to I/O error on sda1
Apr  9 01:45:37 www kernel: [48585.092662] Buffer I/O error on device sda1, logical block 4128944
Apr  9 01:45:37 www kernel: [48585.094537] lost page write due to I/O error on sda1
Apr  9 01:45:37 www kernel: [48585.094548] Buffer I/O error on device sda1, logical block 4128945
Apr  9 01:45:37 www kernel: [48585.096020] lost page write due to I/O error on sda1
Apr  9 01:45:37 www kernel: [48585.096027] Buffer I/O error on device sda1, logical block 4128946
Apr  9 01:45:37 www kernel: [48585.097514] lost page write due to I/O error on sda1
Apr  9 01:45:37 www kernel: [48585.097522] Buffer I/O error on device sda1, logical block 4128947
Apr  9 01:45:37 www kernel: [48585.098993] lost page write due to I/O error on sda1
Apr  9 01:45:37 www kernel: [48585.099001] Buffer I/O error on device sda1, logical block 4128948
Apr  9 01:45:37 www kernel: [48585.100526] lost page write due to I/O error on sda1
Apr  9 01:45:37 www kernel: [48585.100534] Buffer I/O error on device sda1, logical block 4128949
Apr  9 01:45:37 www kernel: [48585.102002] lost page write due to I/O error on sda1
Apr  9 01:45:37 www kernel: [48585.102009] Buffer I/O error on device sda1, logical block 4128950
Apr  9 01:45:37 www kernel: [48585.103529] lost page write due to I/O error on sda1
Apr  9 01:45:37 www kernel: [48585.103560] ata1: EH complete
Apr  9 01:49:34 www kernel: [48822.365470] hrtimer: interrupt too slow, forcing clock min delta to 111970110 ns
Apr  9 01:53:07 www kernel: [49035.350423] EXT3-fs error (device sda1): ext3_lookup: deleted inode referenced: 1035105
Apr  9 01:53:07 www kernel: [49035.416650] EXT3-fs error (device sda1): ext3_lookup: deleted inode referenced: 1035105
Apr  9 01:53:07 www kernel: [49035.478615] EXT3-fs error (device sda1): ext3_lookup: deleted inode referenced: 1035105
Apr  9 01:53:17 www kernel: [49045.283115] ata1.00: limiting speed to PIO1
Apr  9 01:53:17 www kernel: [49045.283126] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
Apr  9 01:53:17 www kernel: [49045.284732] ata1.00: cmd 39/00:f8:f0:03:f8/00:01:01:00:00/e0 tag 0 pio 258048 out
Apr  9 01:53:17 www kernel: [49045.284735]          res 41/04:18:d0:05:f8/04:18:d0:05:f8/e0 Emask 0x1 (device error)
Apr  9 01:53:17 www kernel: [49045.289785] ata1.00: status: { DRDY ERR }
Apr  9 01:53:17 www kernel: [49045.291156] ata1.00: error: { ABRT }
Apr  9 01:53:17 www kernel: [49045.292650] ata1: soft resetting link
Apr  9 01:53:17 www kernel: [49045.451340] ata1.01: NODEV after polling detection
Apr  9 01:53:17 www kernel: [49045.453547] ata1.00: configured for PIO1
Apr  9 01:53:17 www kernel: [49045.453630] ata1: EH complete
Apr  9 01:53:17 www kernel: [49045.476880] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr  9 01:53:17 www kernel: [49045.478428] ata1.00: cmd 39/00:f8:f0:03:f8/00:01:01:00:00/e0 tag 0 pio 258048 out
Apr  9 01:53:17 www kernel: [49045.478431]          res 41/04:18:d0:05:f8/04:18:d0:05:f8/e0 Emask 0x1 (device error)
Apr  9 01:53:17 www kernel: [49045.483297] ata1.00: status: { DRDY ERR }
Apr  9 01:53:17 www kernel: [49045.484540] ata1.00: error: { ABRT }
Apr  9 01:53:17 www kernel: [49045.486544] ata1.00: configured for PIO1
Apr  9 01:53:17 www kernel: [49045.486544] ata1: EH complete
Apr  9 01:53:17 www kernel: [49045.510401] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr  9 01:53:17 www kernel: [49045.511973] ata1.00: cmd 39/00:f8:f0:03:f8/00:01:01:00:00/e0 tag 0 pio 258048 out
Apr  9 01:53:17 www kernel: [49045.511976]          res 41/04:18:d0:05:f8/04:18:d0:05:f8/e0 Emask 0x1 (device error)
Apr  9 01:53:17 www kernel: [49045.516967] ata1.00: status: { DRDY ERR }
Apr  9 01:53:17 www kernel: [49045.518259] ata1.00: error: { ABRT }
Apr  9 01:53:17 www kernel: [49045.521662] ata1.00: configured for PIO1
Apr  9 01:53:17 www kernel: [49045.521679] ata1: EH complete
Apr  9 01:53:17 www kernel: [49045.546332] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr  9 01:53:17 www kernel: [49045.547931] ata1.00: cmd 39/00:f8:f0:03:f8/00:01:01:00:00/e0 tag 0 pio 258048 out
Apr  9 01:53:17 www kernel: [49045.547934]          res 41/04:18:d0:05:f8/04:18:d0:05:f8/e0 Emask 0x1 (device error)
Apr  9 01:53:17 www kernel: [49045.553057] ata1.00: status: { DRDY ERR }
Apr  9 01:53:17 www kernel: [49045.554342] ata1.00: error: { ABRT }
Apr  9 01:53:17 www kernel: [49045.557680] ata1.00: configured for PIO1
Apr  9 01:53:17 www kernel: [49045.557699] ata1: EH complete
Apr  9 01:53:17 www kernel: [49045.580728] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr  9 01:53:17 www kernel: [49045.582321] ata1.00: cmd 39/00:f8:f0:03:f8/00:01:01:00:00/e0 tag 0 pio 258048 out
Apr  9 01:53:17 www kernel: [49045.582324]          res 41/04:18:d0:05:f8/04:18:d0:05:f8/e0 Emask 0x1 (device error)
Apr  9 01:53:17 www kernel: [49045.587381] ata1.00: status: { DRDY ERR }
Apr  9 01:53:17 www kernel: [49045.588667] ata1.00: error: { ABRT }
Apr  9 01:53:17 www kernel: [49045.592054] ata1.00: configured for PIO1
Apr  9 01:53:17 www kernel: [49045.592071] ata1: EH complete
Apr  9 01:53:17 www kernel: [49045.616647] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr  9 01:53:17 www kernel: [49045.618235] ata1.00: cmd 39/00:f8:f0:03:f8/00:01:01:00:00/e0 tag 0 pio 258048 out
Apr  9 01:53:17 www kernel: [49045.618238]          res 41/04:18:d0:05:f8/04:18:d0:05:f8/e0 Emask 0x1 (device error)
Apr  9 01:53:17 www kernel: [49045.623408] ata1.00: status: { DRDY ERR }
Apr  9 01:53:17 www kernel: [49045.624685] ata1.00: error: { ABRT }
Apr  9 01:53:17 www kernel: [49045.628015] ata1.00: configured for PIO1
Apr  9 01:53:17 www kernel: [49045.628047] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr  9 01:53:17 www kernel: [49045.628055] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
Apr  9 01:53:17 www kernel: [49045.628065] Descriptor sense data with sense descriptors (in hex):
Apr  9 01:53:17 www kernel: [49045.628070]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 f8 05
Apr  9 01:53:17 www kernel: [49045.628087]         d0 f8 05 d0
Apr  9 01:53:17 www kernel: [49045.628095] sd 0:0:0:0: [sda] Add. Sense: No additional sense information
Apr  9 01:53:17 www kernel: [49045.628103] end_request: I/O error, dev sda, sector 33031152
Apr  9 01:53:17 www kernel: [49045.629547] __ratelimit: 1 callbacks suppressed
Apr  9 01:53:17 www kernel: [49045.629554] Buffer I/O error on device sda1, logical block 4128890
Apr  9 01:53:17 www kernel: [49045.631114] lost page write due to I/O error on sda1
Apr  9 01:53:17 www kernel: [49045.631130] Buffer I/O error on device sda1, logical block 4128891
Apr  9 01:53:17 www kernel: [49045.632659] lost page write due to I/O error on sda1
Apr  9 01:53:17 www kernel: [49045.632666] Buffer I/O error on device sda1, logical block 4128892
Apr  9 01:53:17 www kernel: [49045.634200] lost page write due to I/O error on sda1
Apr  9 01:53:17 www kernel: [49045.634208] Buffer I/O error on device sda1, logical block 4128893
Apr  9 01:53:17 www kernel: [49045.635765] lost page write due to I/O error on sda1
Apr  9 01:53:17 www kernel: [49045.635773] Buffer I/O error on device sda1, logical block 4128894
Apr  9 01:53:17 www kernel: [49045.637306] lost page write due to I/O error on sda1
Apr  9 01:53:17 www kernel: [49045.637313] Buffer I/O error on device sda1, logical block 4128895
Apr  9 01:53:17 www kernel: [49045.638847] lost page write due to I/O error on sda1
Apr  9 01:53:17 www kernel: [49045.638854] Buffer I/O error on device sda1, logical block 4128896
Apr  9 01:53:17 www kernel: [49045.640430] lost page write due to I/O error on sda1
Apr  9 01:53:17 www kernel: [49045.640439] Buffer I/O error on device sda1, logical block 4128897
Apr  9 01:53:17 www kernel: [49045.641965] lost page write due to I/O error on sda1
Apr  9 01:53:17 www kernel: [49045.641973] Buffer I/O error on device sda1, logical block 4128898
Apr  9 01:53:17 www kernel: [49045.643508] lost page write due to I/O error on sda1
Apr  9 01:53:17 www kernel: [49045.643515] Buffer I/O error on device sda1, logical block 4128899
Apr  9 01:53:17 www kernel: [49045.645048] lost page write due to I/O error on sda1
Apr  9 01:53:17 www kernel: [49045.645185] ata1: EH complete

```

---

