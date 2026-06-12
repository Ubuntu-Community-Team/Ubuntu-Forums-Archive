---
title: "Kernel Crash"
date: 2014-10-07
forum: Server Platforms
---

### Post by mike253 on 2014-10-07
Hello Community,

I need your help with a kernel crash. I installed a new 12.04.05 and I get a lot of kernel crashes. Also with the newest version 14.04.01 I get these kernel crashes. I hope you can help me fixing the issue. By the way: with 12.04.05 the kernel crashes and the system doesn't "hang up" as with release 14.04.01.

/var/log/syslog
```

Oct  7 15:14:11 nas kernel: [63260.309307] ------------[ cut here ]------------
Oct  7 15:14:11 nas kernel: [63260.309328] WARNING: CPU: 1 PID: 1541 at /build/buildd/linux-lts-trusty-3.13.0/drivers/usb/host/xhci-ring.c:613 xhci_find_new_dequeue_state+0x191/0x2e0()
Oct  7 15:14:11 nas kernel: [63260.309332] Modules linked in: snd_hda_codec_hdmi nfsd eeepc_wmi asus_wmi nfs_acl auth_rpcgss nfs sparse_keymap fscache lockd sunrpc snd_hda_codec_realtek i915 psmouse snd_hda_intel snd_hda_codec serio_raw drm_kms_helper snd_hwdep drm snd_pcm snd_timer lpc_ich snd mei_me soundcore snd_page_alloc mei wmi i2c_algo_bit video mac_hid lp parport raid10 raid456 async_pq async_xor xor async_memcpy async_raid6_recov raid6_pq async_tx e1000e raid1 ptp raid0 ahci libahci multipath pps_core linear
Oct  7 15:14:11 nas kernel: [63260.309406] CPU: 1 PID: 1541 Comm: mediasrv Not tainted 3.13.0-32-generic #57~precise1-Ubuntu
Oct  7 15:14:11 nas kernel: [63260.309410] Hardware name: ASUS All Series/H87I-PLUS, BIOS 0803 09/29/2013
Oct  7 15:14:11 nas kernel: [63260.309413]  0000000000000265 ffff8800c66a5be8 ffffffff81752c9e 0000000000000007
Oct  7 15:14:11 nas kernel: [63260.309421]  0000000000000000 ffff8800c66a5c28 ffffffff8106af7c ffffffff81590ca0
Oct  7 15:14:11 nas kernel: [63260.309427]  ffff8801163ec000 ffff8800c66a5cb0 ffff8800c7a53080 0000000115eb5400
Oct  7 15:14:11 nas kernel: [63260.309434] Call Trace:
Oct  7 15:14:11 nas kernel: [63260.309447]  [<ffffffff81752c9e>] dump_stack+0x46/0x58
Oct  7 15:14:11 nas kernel: [63260.309457]  [<ffffffff8106af7c>] warn_slowpath_common+0x8c/0xc0
Oct  7 15:14:11 nas kernel: [63260.309466]  [<ffffffff81590ca0>] ? trace_xhci_dbg_quirks+0x70/0x70
Oct  7 15:14:11 nas kernel: [63260.309473]  [<ffffffff8106afca>] warn_slowpath_null+0x1a/0x20
Oct  7 15:14:11 nas kernel: [63260.309480]  [<ffffffff8159eaf1>] xhci_find_new_dequeue_state+0x191/0x2e0
Oct  7 15:14:11 nas kernel: [63260.309489]  [<ffffffff81594d58>] xhci_cleanup_stalled_ring+0x78/0x100
Oct  7 15:14:11 nas kernel: [63260.309497]  [<ffffffff81594f16>] xhci_endpoint_reset+0x136/0x190
Oct  7 15:14:11 nas kernel: [63260.309505]  [<ffffffff815669d5>] usb_hcd_reset_endpoint+0x25/0x70
Oct  7 15:14:11 nas kernel: [63260.309513]  [<ffffffff81569ac8>] usb_enable_endpoint+0xa8/0xb0
Oct  7 15:14:11 nas kernel: [63260.309520]  [<ffffffff81569b12>] usb_enable_interface+0x42/0x60
Oct  7 15:14:11 nas kernel: [63260.309527]  [<ffffffff8156a006>] usb_set_interface+0x1f6/0x340
Oct  7 15:14:11 nas kernel: [63260.309535]  [<ffffffff81574339>] usbdev_do_ioctl+0x589/0xc50
Oct  7 15:14:11 nas kernel: [63260.309545]  [<ffffffff811182cc>] ? acct_account_cputime+0x1c/0x20
Oct  7 15:14:11 nas kernel: [63260.309555]  [<ffffffff810a25e9>] ? account_user_time+0x99/0xb0
Oct  7 15:14:11 nas kernel: [63260.309562]  [<ffffffff81574a2e>] usbdev_ioctl+0xe/0x20
Oct  7 15:14:11 nas kernel: [63260.309570]  [<ffffffff811dc5c5>] do_vfs_ioctl+0x75/0x2c0
Oct  7 15:14:11 nas kernel: [63260.309577]  [<ffffffff81022735>] ? syscall_trace_enter+0x165/0x280
Oct  7 15:14:11 nas kernel: [63260.309583]  [<ffffffff811dc8a1>] SyS_ioctl+0x91/0xb0
Oct  7 15:14:11 nas kernel: [63260.309594]  [<ffffffff8176847f>] tracesys+0xe1/0xe6
Oct  7 15:14:11 nas kernel: [63260.309598] ---[ end trace b1ac25bda621b6e9 ]---
Oct  7 15:14:11 nas kernel: [63260.309614] BUG: unable to handle kernel NULL pointer dereference at 0000000000000010
Oct  7 15:14:11 nas kernel: [63260.312266] IP: [<ffffffff8159ecac>] xhci_queue_new_dequeue_state+0x6c/0xe0
Oct  7 15:14:11 nas kernel: [63260.314595] PGD c7940067 PUD 36abc067 PMD 0 
Oct  7 15:14:11 nas kernel: [63260.316085] Oops: 0000 [#1] SMP 
Oct  7 15:14:11 nas kernel: [63260.317196] Modules linked in: snd_hda_codec_hdmi nfsd eeepc_wmi asus_wmi nfs_acl auth_rpcgss nfs sparse_keymap fscache lockd sunrpc snd_hda_codec_realtek i915 psmouse snd_hda_intel snd_hda_codec serio_raw drm_kms_helper snd_hwdep drm snd_pcm snd_timer lpc_ich snd mei_me soundcore snd_page_alloc mei wmi i2c_algo_bit video mac_hid lp parport raid10 raid456 async_pq async_xor xor async_memcpy async_raid6_recov raid6_pq async_tx e1000e raid1 ptp raid0 ahci libahci multipath pps_core linear
Oct  7 15:14:11 nas kernel: [63260.333177] CPU: 1 PID: 1541 Comm: mediasrv Tainted: G        W    3.13.0-32-generic #57~precise1-Ubuntu
Oct  7 15:14:11 nas kernel: [63260.336319] Hardware name: ASUS All Series/H87I-PLUS, BIOS 0803 09/29/2013
Oct  7 15:14:11 nas kernel: [63260.338582] task: ffff8800c64597f0 ti: ffff8800c66a4000 task.ti: ffff8800c66a4000
Oct  7 15:14:11 nas kernel: [63260.341053] RIP: 0010:[<ffffffff8159ecac>]  [<ffffffff8159ecac>] xhci_queue_new_dequeue_state+0x6c/0xe0
Oct  7 15:14:11 nas kernel: [63260.344197] RSP: 0018:ffff8800c66a5c38  EFLAGS: 00010046
Oct  7 15:14:11 nas kernel: [63260.345942] RAX: 0000000000000000 RBX: ffff8800c66a5cb0 RCX: 0000000000000040
Oct  7 15:14:11 nas kernel: [63260.348296] RDX: 0000000000000000 RSI: ffff880115eb58e0 RDI: 0000000000000000
Oct  7 15:14:11 nas kernel: [63260.350650] RBP: ffff8800c66a5c98 R08: ffff8800c66a5cb0 R09: ffff880115eb58e0
Oct  7 15:14:11 nas kernel: [63260.352999] R10: 0000000000000001 R11: 0000000000000390 R12: ffff8801163ec000
Oct  7 15:14:11 nas kernel: [63260.355348] R13: ffff8800369081e8 R14: 0000000000000000 R15: 0000000000000002
Oct  7 15:14:11 nas kernel: [63260.357707] FS:  00007f7324f1f700(0000) GS:ffff88011fa80000(0000) knlGS:0000000000000000
Oct  7 15:14:11 nas kernel: [63260.360386] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Oct  7 15:14:11 nas kernel: [63260.362279] CR2: 0000000000000010 CR3: 00000000c7ae2000 CR4: 00000000001407e0
Oct  7 15:14:11 nas kernel: [63260.364632] Stack:
Oct  7 15:14:11 nas kernel: [63260.365275]  ffff8800c66a5ca8 ffff8800c66a5c58 ffffffff81abfdb1 ffff880115eb58e0
Oct  7 15:14:11 nas kernel: [63260.367834]  ffff880000000001 0000000015eb5401 ffff8801163ec000 ffff8800369081e8
Oct  7 15:14:11 nas kernel: [63260.370397]  ffff8801163ec000 ffff880036822000 0000000000000002 ffff8801163ec048
Oct  7 15:14:11 nas kernel: [63260.372964] Call Trace:
Oct  7 15:14:11 nas kernel: [63260.373759]  [<ffffffff81594dd9>] xhci_cleanup_stalled_ring+0xf9/0x100
Oct  7 15:14:11 nas kernel: [63260.375915]  [<ffffffff81594f16>] xhci_endpoint_reset+0x136/0x190
Oct  7 15:14:11 nas kernel: [63260.377924]  [<ffffffff815669d5>] usb_hcd_reset_endpoint+0x25/0x70
Oct  7 15:14:11 nas kernel: [63260.379962]  [<ffffffff81569ac8>] usb_enable_endpoint+0xa8/0xb0
Oct  7 15:14:11 nas kernel: [63260.381910]  [<ffffffff81569b12>] usb_enable_interface+0x42/0x60
Oct  7 15:14:11 nas kernel: [63260.383886]  [<ffffffff8156a006>] usb_set_interface+0x1f6/0x340
Oct  7 15:14:11 nas kernel: [63260.385841]  [<ffffffff81574339>] usbdev_do_ioctl+0x589/0xc50
Oct  7 15:14:11 nas kernel: [63260.387737]  [<ffffffff811182cc>] ? acct_account_cputime+0x1c/0x20
Oct  7 15:14:11 nas kernel: [63260.389773]  [<ffffffff810a25e9>] ? account_user_time+0x99/0xb0
Oct  7 15:14:11 nas kernel: [63260.391720]  [<ffffffff81574a2e>] usbdev_ioctl+0xe/0x20
Oct  7 15:14:11 nas kernel: [63260.393441]  [<ffffffff811dc5c5>] do_vfs_ioctl+0x75/0x2c0
Oct  7 15:14:11 nas kernel: [63260.395217]  [<ffffffff81022735>] ? syscall_trace_enter+0x165/0x280
Oct  7 15:14:11 nas kernel: [63260.397284]  [<ffffffff811dc8a1>] SyS_ioctl+0x91/0xb0
Oct  7 15:14:11 nas kernel: [63260.398950]  [<ffffffff8176847f>] tracesys+0xe1/0xe6
Oct  7 15:14:11 nas kernel: [63260.400579] Code: 03 84 d7 10 01 00 00 4d 8b 48 08 4c 89 c3 49 89 fc 44 89 55 c0 4c 89 f7 4c 89 ce 4c 8d 68 28 4c 89 4d b8 e8 27 ec ff ff 8b 53 10 <4d> 8b 46 10 4c 89 f1 4c 8b 4d b8 48 89 04 24 4c 89 e7 48 c7 c6 
Oct  7 15:14:11 nas kernel: [63260.408823] RIP  [<ffffffff8159ecac>] xhci_queue_new_dequeue_state+0x6c/0xe0
Oct  7 15:14:11 nas kernel: [63260.411181]  RSP <ffff8800c66a5c38>
Oct  7 15:14:11 nas kernel: [63260.412317] CR2: 0000000000000010
Oct  7 15:14:11 nas kernel: [63260.852200] ---[ end trace b1ac25bda621b6ea ]---

```

After the "crash" the following lines repeat several times:
```

Oct  7 15:25:41 nas kernel: [63941.547657] INFO: rcu_sched detected stalls on CPUs/tasks: { 3} (detected by 1, t=15002 jiffies, g=1614617, c=1614616, q=0)
Oct  7 15:25:41 nas kernel: [63941.633818] sending NMI to all CPUs:
Oct  7 15:25:41 nas kernel: [63941.718445] NMI backtrace for cpu 1
Oct  7 15:25:41 nas kernel: [63941.803052] CPU: 1 PID: 0 Comm: swapper/1 Tainted: G      D W    3.13.0-32-generic #57~precise1-Ubuntu
Oct  7 15:25:41 nas kernel: [63941.888813] Hardware name: ASUS All Series/H87I-PLUS, BIOS 0803 09/29/2013
Oct  7 15:25:41 nas kernel: [63941.972805] task: ffff880119eac7d0 ti: ffff880119eba000 task.ti: ffff880119eba000
Oct  7 15:25:41 nas kernel: [63942.055673] RIP: 0010:[<ffffffff813834c6>]  [<ffffffff813834c6>] __const_udelay+0x26/0x30
Oct  7 15:25:41 nas kernel: [63942.137630] RSP: 0018:ffff88011fa83d08  EFLAGS: 00000807
Oct  7 15:25:41 nas kernel: [63942.217480] RAX: 0000000047681200 RBX: 0000000000002710 RCX: 0000000001613050
Oct  7 15:25:41 nas kernel: [63942.296894] RDX: 00000000002bcbb5 RSI: 0000000000000100 RDI: 00000000002bcbb6
Oct  7 15:25:41 nas kernel: [63942.375107] RBP: ffff88011fa83d08 R08: 0000000000000000 R09: 0000000000000001
Oct  7 15:25:41 nas kernel: [63942.451547] R10: 00000000000003bf R11: 0000000000008000 R12: 0000000000000001
Oct  7 15:25:41 nas kernel: [63942.526363] R13: 0000000000000000 R14: ffffffff81d12080 R15: 0000000000000087
Oct  7 15:25:41 nas kernel: [63942.600263] FS:  0000000000000000(0000) GS:ffff88011fa80000(0000) knlGS:0000000000000000
Oct  7 15:25:41 nas kernel: [63942.675460] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Oct  7 15:25:41 nas kernel: [63942.750275] CR2: 00007f8728b3a000 CR3: 0000000001c0d000 CR4: 00000000001407e0
Oct  7 15:25:41 nas kernel: [63942.826022] Stack:
Oct  7 15:25:41 nas kernel: [63942.900989]  ffff88011fa83d28 ffffffff810477e3 000000000018a318 ffffffff81c4d000
Oct  7 15:25:41 nas kernel: [63942.977876]  ffff88011fa83d78 ffffffff810cf617 0000000100000000 0000000000000082
Oct  7 15:25:41 nas kernel: [63943.053837]  ffffffff81c1a500 ffff88011fa8e7a0 ffffffff81c4d000 ffffffff81c4d000
Oct  7 15:25:41 nas kernel: [63943.129888] Call Trace:
Oct  7 15:25:41 nas kernel: [63943.204301]  <IRQ> 
Oct  7 15:25:41 nas kernel: [63943.204974]  [<ffffffff810477e3>] arch_trigger_all_cpu_backtrace+0x93/0xb0
Oct  7 15:25:41 nas kernel: [63943.352069]  [<ffffffff810cf617>] print_other_cpu_stall+0x1f7/0x230
Oct  7 15:25:41 nas kernel: [63943.426918]  [<ffffffff810cf6ef>] check_cpu_stall.isra.45+0x9f/0xb0
Oct  7 15:25:41 nas kernel: [63943.500901]  [<ffffffff810cf738>] __rcu_pending+0x38/0x160
Oct  7 15:25:41 nas kernel: [63943.573984]  [<ffffffff810d053d>] rcu_check_callbacks+0xed/0x1a0
Oct  7 15:25:41 nas kernel: [63943.647326]  [<ffffffff8107a158>] update_process_times+0x48/0x80
Oct  7 15:25:41 nas kernel: [63943.720695]  [<ffffffff810dbca3>] tick_sched_handle.isra.12+0x33/0x70
Oct  7 15:25:41 nas kernel: [63943.794524]  [<ffffffff810dbdcc>] tick_sched_timer+0x4c/0x80
Oct  7 15:25:41 nas kernel: [63943.868301]  [<ffffffff81092df6>] __run_hrtimer+0x76/0x230
Oct  7 15:25:41 nas kernel: [63943.942076]  [<ffffffff810dbd80>] ? tick_nohz_handler+0xa0/0xa0
Oct  7 15:25:41 nas kernel: [63944.016110]  [<ffffffff810935e7>] hrtimer_interrupt+0x107/0x260
Oct  7 15:25:41 nas kernel: [63944.090091]  [<ffffffff81045b1b>] local_apic_timer_interrupt+0x3b/0x60
Oct  7 15:25:41 nas kernel: [63944.164591]  [<ffffffff8176a665>] smp_apic_timer_interrupt+0x45/0x60
Oct  7 15:25:41 nas kernel: [63944.239265]  [<ffffffff81768fdd>] apic_timer_interrupt+0x6d/0x80
Oct  7 15:25:41 nas kernel: [63944.314368]  <EOI> 
Oct  7 15:25:41 nas kernel: [63944.315041]  [<ffffffff815f8351>] ? cpuidle_enter_state+0x61/0xe0
Oct  7 15:25:41 nas kernel: [63944.464615]  [<ffffffff815f8347>] ? cpuidle_enter_state+0x57/0xe0
Oct  7 15:25:41 nas kernel: [63944.540010]  [<ffffffff815f8490>] cpuidle_idle_call+0xc0/0x210
Oct  7 15:25:41 nas kernel: [63944.613724]  [<ffffffff8101e52e>] arch_cpu_idle+0xe/0x30
Oct  7 15:25:41 nas kernel: [63944.685660]  [<ffffffff810c3c48>] cpu_idle_loop+0x78/0x270
Oct  7 15:25:41 nas kernel: [63944.756142]  [<ffffffff810d95b2>] ? clockevents_register_device+0xe2/0x140
Oct  7 15:25:41 nas kernel: [63944.826689]  [<ffffffff810c3eab>] cpu_startup_entry+0x6b/0x70
Oct  7 15:25:41 nas kernel: [63944.897639]  [<ffffffff810441a8>] start_secondary+0xc8/0xd0
Oct  7 15:25:41 nas kernel: [63944.968375] Code: 00 00 00 00 00 55 48 8d 04 bd 00 00 00 00 65 48 8b 14 25 60 3c 01 00 48 8d 0c 12 48 c1 e2 06 48 89 e5 48 29 ca f7 e2 48 8d 7a 01 <ff> 15 ac 96 90 00 5d c3 66 90 0f 1f 44 00 00 55 65 48 8b 14 25 
Oct  7 15:25:41 nas kernel: [63945.119087] NMI backtrace for cpu 3
Oct  7 15:25:41 nas kernel: [63945.119094] INFO: NMI handler (arch_trigger_all_cpu_backtrace_handler) took too long to run: 3400.641 msecs
Oct  7 15:25:41 nas kernel: [63945.266057] CPU: 3 PID: 0 Comm: swapper/3 Tainted: G      D W    3.13.0-32-generic #57~precise1-Ubuntu
Oct  7 15:25:41 nas kernel: [63945.342173] Hardware name: ASUS All Series/H87I-PLUS, BIOS 0803 09/29/2013
Oct  7 15:25:41 nas kernel: [63945.417760] task: ffff880119ec8000 ti: ffff880119ebe000 task.ti: ffff880119ebe000
Oct  7 15:25:41 nas kernel: [63945.493039] RIP: 0010:[<ffffffff8175f2a2>]  [<ffffffff8175f2a2>] _raw_spin_lock+0x32/0x50
Oct  7 15:25:41 nas kernel: [63945.568878] RSP: 0018:ffff88011fb83e68  EFLAGS: 00000002
Oct  7 15:25:41 nas kernel: [63945.643440] RAX: 0000000000006e56 RBX: ffff8801163ec000 RCX: 00000000000027f0
Oct  7 15:25:41 nas kernel: [63945.718356] RDX: 00000000000027f2 RSI: 00000000000027f2 RDI: ffff8801163ec048
Oct  7 15:25:41 nas kernel: [63945.792926] RBP: ffff88011fb83e68 R08: ffff880116332400 R09: ffff88011b000160
Oct  7 15:25:41 nas kernel: [63945.868019] R10: 0000000000000000 R11: 0000000000000002 R12: ffff8801163ec048
Oct  7 15:25:41 nas kernel: [63945.943511] R13: ffff880115cb9000 R14: ffff880119ebfd48 R15: 0000000000000005
Oct  7 15:25:41 nas kernel: [63946.019649] FS:  0000000000000000(0000) GS:ffff88011fb80000(0000) knlGS:0000000000000000
Oct  7 15:25:41 nas kernel: [63946.097330] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Oct  7 15:25:41 nas kernel: [63946.174518] CR2: 00007fee85905c62 CR3: 0000000001c0d000 CR4: 00000000001407e0
Oct  7 15:25:41 nas kernel: [63946.252118] Stack:
Oct  7 15:25:41 nas kernel: [63946.328172]  ffff88011fb83e98 ffffffff815a1b93 ffff880115caf200 0000000000000029
Oct  7 15:25:41 nas kernel: [63946.406233]  ffff880115caf200 ffff880119ebfd48 ffff88011fb83ea8 ffffffff815a1d61
Oct  7 15:25:41 nas kernel: [63946.483637]  ffff88011fb83f08 ffffffff810c485d ffff88011fb83ec8 ffff880116332400
Oct  7 15:25:41 nas kernel: [63946.561111] Call Trace:
Oct  7 15:25:41 nas kernel: [63946.637158]  <IRQ> 
Oct  7 15:25:41 nas kernel: [63946.637833]  [<ffffffff815a1b93>] xhci_irq+0x33/0x1f0
Oct  7 15:25:41 nas kernel: [63946.787666]  [<ffffffff815a1d61>] xhci_msi_irq+0x11/0x20
Oct  7 15:25:41 nas kernel: [63946.862675]  [<ffffffff810c485d>] handle_irq_event_percpu+0x5d/0x210
Oct  7 15:25:41 nas kernel: [63946.937855]  [<ffffffff8101d0b9>] ? sched_clock+0x9/0x10
Oct  7 15:25:41 nas kernel: [63947.012816]  [<ffffffff810c4a58>] handle_irq_event+0x48/0x70
Oct  7 15:25:41 nas kernel: [63947.087807]  [<ffffffff810c7457>] handle_edge_irq+0x77/0x110
Oct  7 15:25:41 nas kernel: [63947.162416]  [<ffffffff81016f32>] handle_irq+0x22/0x40
Oct  7 15:25:41 nas kernel: [63947.236528]  [<ffffffff8176a59a>] do_IRQ+0x5a/0xe0
Oct  7 15:25:41 nas kernel: [63947.310213]  [<ffffffff8175f76d>] common_interrupt+0x6d/0x6d
Oct  7 15:25:41 nas kernel: [63947.384298]  <EOI> 
Oct  7 15:25:41 nas kernel: [63947.384973]  [<ffffffff815f8351>] ? cpuidle_enter_state+0x61/0xe0
Oct  7 15:25:41 nas kernel: [63947.532751]  [<ffffffff815f8347>] ? cpuidle_enter_state+0x57/0xe0
Oct  7 15:25:41 nas kernel: [63947.607012]  [<ffffffff815f8490>] cpuidle_idle_call+0xc0/0x210
Oct  7 15:25:41 nas kernel: [63947.681002]  [<ffffffff8101e52e>] arch_cpu_idle+0xe/0x30
Oct  7 15:25:41 nas kernel: [63947.754480]  [<ffffffff810c3c48>] cpu_idle_loop+0x78/0x270
Oct  7 15:25:41 nas kernel: [63947.827675]  [<ffffffff810d95b2>] ? clockevents_register_device+0xe2/0x140
Oct  7 15:25:41 nas kernel: [63947.901174]  [<ffffffff810c3eab>] cpu_startup_entry+0x6b/0x70
Oct  7 15:25:41 nas kernel: [63947.974178]  [<ffffffff810441a8>] start_secondary+0xc8/0xd0
Oct  7 15:25:41 nas kernel: [63948.047828] Code: 89 e5 b8 00 00 02 00 f0 0f c1 07 89 c2 c1 ea 10 66 39 c2 75 02 5d c3 83 e2 fe 0f b7 f2 b8 00 80 00 00 eb 0c 0f 1f 44 00 00 f3 90 <83> e8 01 74 0a 0f b7 0f 66 39 ca 75 f1 5d c3 0f 1f 80 00 00 00 
Oct  7 15:25:41 nas kernel: [63948.204645] NMI backtrace for cpu 0
Oct  7 15:25:41 nas kernel: [63948.204651] INFO: NMI handler (arch_trigger_all_cpu_backtrace_handler) took too long to run: 6486.197 msecs

```

I hope you find a solution.
Thank you very much in advance!

---

### Post by Michael_McKenney on 2014-10-07
WARNING: CPU: 1 PID: 1541 at /build/buildd/linux-lts-trusty-3.13.0/drivers/usb/host/xhci-ring.c

I found a bug report for Red Hat that was similar to this error in google.

---

### Post by mike253 on 2014-10-07
Hello Michael,

how can i fix the issue?
Can you post the bug report or is there posted a solution for this bug?

Best regards,
Mike

---

### Post by Michael_McKenney on 2014-10-07
I did a google search on it and found this bug report.  Not sure how to fix it.  

[https://bugzilla.redhat.com/show_bug.cgi?id=789066](https://bugzilla.redhat.com/show_bug.cgi?id=789066)

---

### Post by mike253 on 2014-10-14
Hello at all,

did anyone know a solution or can I post something else here to find a fix?

Best regards,
Mike

---

