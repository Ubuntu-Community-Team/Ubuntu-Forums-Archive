---
title: "Random hangs on Wild Dog"
date: 2009-08-22
forum: System76 Support
---

### Post by Ed.Corcoran on 2009-08-22
I've been having some random hangs on my Wild Dog that require a hard reboot. All of the sudden, the computer stops responding to mouse or keyboard input. If music is playing, it will finish the song but not move on to the next one. Ctrl+Alt+Backspace does not restart X (I re-enabled it earlier using dontzap), so I have to do a hard restart.

I had problems earlier with the machine not booting if my Logitech mouse and keyboard were plugged in, so maybe this is related. However, I tried plugging in a different keyboard after it hung the most recent time, and I didn't get any response from that keyboard.

---

### Post by Ed.Corcoran on 2009-08-23
It just did it again. Here's the relevant part of the syslog.

```

Aug 23 10:11:46 system76-pc kernel: [67800.871402] BUG: unable to handle kernel paging request at fffffbff80b41140
Aug 23 10:11:46 system76-pc kernel: [67800.871408] IP: [<ffffffff802e4f3d>] __mem_cgroup_uncharge_common+0xcd/0x1f0
Aug 23 10:11:46 system76-pc kernel: [67800.871416] PGD 0 
Aug 23 10:11:46 system76-pc kernel: [67800.871418] Oops: 0000 [#2] SMP 
Aug 23 10:11:46 system76-pc kernel: [67800.871421] last sysfs file: /sys/devices/pci0000:00/0000:00:1d.2/pools
Aug 23 10:11:46 system76-pc kernel: [67800.871424] CPU 2 
Aug 23 10:11:46 system76-pc kernel: [67800.871425] Modules linked in: nls_iso8859_1 nls_cp437 vfat fat usb_storage binfmt_misc ppdev bridge stp bnep snd_atiixp_modem snd_via82xx_modem snd_intel8x0m snd_ac97_codec ac97_bus video output input_polldev lp parport snd_pcm_oss snd_hda_intel snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device psmouse snd soundcore snd_page_alloc serio_raw iTCO_wdt iTCO_vendor_support fglrx(P) intel_agp joydev usbhid ohci1394 ieee1394 e1000e fbcon tileblit font bitblit softcursor
Aug 23 10:11:46 system76-pc kernel: [67800.871457] Pid: 3060, comm: Xorg Tainted: P      D    2.6.28-15-generic #49-Ubuntu
Aug 23 10:11:46 system76-pc kernel: [67800.871459] RIP: 0010:[<ffffffff802e4f3d>]  [<ffffffff802e4f3d>] __mem_cgroup_uncharge_common+0xcd/0x1f0
Aug 23 10:11:46 system76-pc kernel: [67800.871463] RSP: 0018:ffff88012d527bf8  EFLAGS: 00210206
Aug 23 10:11:46 system76-pc kernel: [67800.871465] RAX: ffffe2000164bb18 RBX: ffff88002dbecec8 RCX: 0000000000000180
Aug 23 10:11:46 system76-pc kernel: [67800.871467] RDX: 0000000000065ec5 RSI: ffff880028000180 RDI: ffffe2000164bb18
Aug 23 10:11:46 system76-pc kernel: [67800.871469] RBP: ffff88012d527c38 R08: 000000000000000e R09: ffff88012d527e08
Aug 23 10:11:46 system76-pc kernel: [67800.871470] R10: 0000000000000000 R11: 0000000000203246 R12: 0000000000000004
Aug 23 10:11:46 system76-pc kernel: [67800.871472] R13: 4000000000080068 R14: 0000000000000000 R15: fffffbff80b41100
Aug 23 10:11:46 system76-pc kernel: [67800.871475] FS:  00007f359a353700(0000) GS:ffff88012f802d00(0000) knlGS:0000000000000000
Aug 23 10:11:46 system76-pc kernel: [67800.871477] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Aug 23 10:11:46 system76-pc kernel: [67800.871478] CR2: fffffbff80b41140 CR3: 000000012cc58000 CR4: 00000000000406a0
Aug 23 10:11:46 system76-pc kernel: [67800.871480] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Aug 23 10:11:46 system76-pc kernel: [67800.871482] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Aug 23 10:11:46 system76-pc kernel: [67800.871484] Process Xorg (pid: 3060, threadinfo ffff88012d526000, task ffff88012ccc8000)
Aug 23 10:11:46 system76-pc kernel: [67800.871486] Stack:
Aug 23 10:11:46 system76-pc kernel: [67800.871487]  ffff88010dc81680 ffff88012f822280 0000000000200286 ffffe2000164bb18
Aug 23 10:11:46 system76-pc kernel: [67800.871491]  ffff8800cece7d20 ffff88012d527e08 00007f35715f6000 ffff880059d6dfb0
Aug 23 10:11:46 system76-pc kernel: [67800.871494]  ffff88012d527c48 ffffffff802e528c ffff88012d527c68 ffffffff802ce8dd
Aug 23 10:11:46 system76-pc kernel: [67800.871498] Call Trace:
Aug 23 10:11:46 system76-pc kernel: [67800.871500]  [<ffffffff802e528c>] mem_cgroup_uncharge_page+0x2c/0x40
Aug 23 10:11:46 system76-pc kernel: [67800.871503]  [<ffffffff802ce8dd>] page_remove_rmap+0x4d/0x150
Aug 23 10:11:46 system76-pc kernel: [67800.871508]  [<ffffffff802c2ff2>] zap_pte_range+0x212/0x420
Aug 23 10:11:46 system76-pc kernel: [67800.871511]  [<ffffffff802c427a>] unmap_page_range+0x2da/0x360
Aug 23 10:11:46 system76-pc kernel: [67800.871514]  [<ffffffff802c4b10>] unmap_vmas+0x180/0x2c0
Aug 23 10:11:46 system76-pc kernel: [67800.871516]  [<ffffffff802badc3>] ? drain_cpu_pagevecs+0xa3/0xb0
Aug 23 10:11:46 system76-pc kernel: [67800.871521]  [<ffffffff802c4d02>] zap_page_range+0xb2/0x110
Aug 23 10:11:46 system76-pc kernel: [67800.871523]  [<ffffffff802c1ec5>] madvise_vma+0xf5/0x380
Aug 23 10:11:46 system76-pc kernel: [67800.871526]  [<ffffffff8024662b>] ? finish_task_switch+0x2b/0xf0
Aug 23 10:11:46 system76-pc kernel: [67800.871529]  [<ffffffff8069b741>] ? _spin_lock_irq+0x11/0x20
Aug 23 10:11:46 system76-pc kernel: [67800.871534]  [<ffffffff8069b643>] ? __down_read+0xc3/0xce
Aug 23 10:11:46 system76-pc kernel: [67800.871537]  [<ffffffff8069982c>] ? thread_return+0x37/0x36b
Aug 23 10:11:46 system76-pc kernel: [67800.871540]  [<ffffffff802c2300>] sys_madvise+0x1b0/0x270
Aug 23 10:11:46 system76-pc kernel: [67800.871542]  [<ffffffff802e8a60>] ? sys_writev+0x50/0xb0
Aug 23 10:11:46 system76-pc kernel: [67800.871545]  [<ffffffff8021253a>] system_call_fastpath+0x16/0x1b
Aug 23 10:11:46 system76-pc kernel: [67800.871549] Code: 65 0c 45 85 e4 79 e9 0f 1f 80 00 00 00 00 eb d8 66 0f 1f 44 00 00 f0 80 23 fb 48 8b 43 10 4c 8b 7b 08 41 bc 04 00 00 00 4c 8b 28 <4d> 8b 77 40 49 c1 ed 3e 4c 89 e8 48 c1 e0 07 49 8d 04 06 48 89 
Aug 23 10:11:46 system76-pc kernel: [67800.871578] RIP  [<ffffffff802e4f3d>] __mem_cgroup_uncharge_common+0xcd/0x1f0
Aug 23 10:11:46 system76-pc kernel: [67800.871581]  RSP <ffff88012d527bf8>
Aug 23 10:11:46 system76-pc kernel: [67800.871583] CR2: fffffbff80b41140
Aug 23 10:11:46 system76-pc kernel: [67800.871585] ---[ end trace b8441a67ff49dc51 ]---
Aug 23 10:12:28 system76-pc avahi-daemon[3131]: Invalid query packet.
Aug 23 10:12:28 system76-pc last message repeated 2 times
Aug 23 10:12:51 system76-pc kernel: [67865.852999] BUG: soft lockup - CPU#2 stuck for 61s! [Xorg:3060]
Aug 23 10:12:51 system76-pc kernel: [67865.853001] Modules linked in: nls_iso8859_1 nls_cp437 vfat fat usb_storage binfmt_misc ppdev bridge stp bnep snd_atiixp_modem snd_via82xx_modem snd_intel8x0m snd_ac97_codec ac97_bus video output input_polldev lp parport snd_pcm_oss snd_hda_intel snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device psmouse snd soundcore snd_page_alloc serio_raw iTCO_wdt iTCO_vendor_support fglrx(P) intel_agp joydev usbhid ohci1394 ieee1394 e1000e fbcon tileblit font bitblit softcursor
Aug 23 10:12:51 system76-pc kernel: [67865.853001] CPU 2:
Aug 23 10:12:51 system76-pc kernel: [67865.853001] Modules linked in: nls_iso8859_1 nls_cp437 vfat fat usb_storage binfmt_misc ppdev bridge stp bnep snd_atiixp_modem snd_via82xx_modem snd_intel8x0m snd_ac97_codec ac97_bus video output input_polldev lp parport snd_pcm_oss snd_hda_intel snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device psmouse snd soundcore snd_page_alloc serio_raw iTCO_wdt iTCO_vendor_support fglrx(P) intel_agp joydev usbhid ohci1394 ieee1394 e1000e fbcon tileblit font bitblit softcursor
Aug 23 10:12:51 system76-pc kernel: [67865.853001] Pid: 3060, comm: Xorg Tainted: P      D    2.6.28-15-generic #49-Ubuntu
Aug 23 10:12:51 system76-pc kernel: [67865.853001] RIP: 0010:[<ffffffff8022f564>]  [<ffffffff8022f564>] __ticket_spin_lock+0x14/0x20
Aug 23 10:12:51 system76-pc kernel: [67865.853001] RSP: 0018:ffff88012d5276d8  EFLAGS: 00200297
Aug 23 10:12:51 system76-pc kernel: [67865.853001] RAX: 0000000000007776 RBX: ffff88012d5276d8 RCX: 00000000013a6fd8
Aug 23 10:12:51 system76-pc kernel: [67865.853001] RDX: ffff88012d572c50 RSI: 00003ffffffff000 RDI: ffffe200013a6fe8
Aug 23 10:12:51 system76-pc kernel: [67865.853001] RBP: ffff88012d5276d8 R08: 00007f3571600000 R09: ffff88012d527888
Aug 23 10:12:51 system76-pc kernel: [67865.853001] R10: 0000000000000002 R11: 0000000000000000 R12: ffffffff80291326
Aug 23 10:12:51 system76-pc kernel: [67865.853001] R13: ffff88012d527668 R14: 0000000000200286 R15: 0000000000200286
Aug 23 10:12:51 system76-pc kernel: [67865.853001] FS:  00007f359a353700(0000) GS:ffff88012f802d00(0000) knlGS:0000000000000000
Aug 23 10:12:51 system76-pc kernel: [67865.853001] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Aug 23 10:12:51 system76-pc kernel: [67865.853001] CR2: fffffbff80b41140 CR3: 0000000000201000 CR4: 00000000000406a0
Aug 23 10:12:51 system76-pc kernel: [67865.853001] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Aug 23 10:12:51 system76-pc kernel: [67865.853001] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Aug 23 10:12:51 system76-pc kernel: [67865.853001] Call Trace:
Aug 23 10:12:51 system76-pc kernel: [67865.853001]  [<ffffffff802ce8f0>] ? page_remove_rmap+0x60/0x150
Aug 23 10:12:51 system76-pc kernel: [67865.853001]  [<ffffffff8069b839>] _spin_lock+0x9/0x10
Aug 23 10:12:51 system76-pc kernel: [67865.853001]  [<ffffffff802c2e8e>] zap_pte_range+0xae/0x420
Aug 23 10:12:51 system76-pc kernel: [67865.853001]  [<ffffffff802c427a>] unmap_page_range+0x2da/0x360
Aug 23 10:12:51 system76-pc kernel: [67865.853001]  [<ffffffff802c4b10>] unmap_vmas+0x180/0x2c0
Aug 23 10:12:51 system76-pc kernel: [67865.853001]  [<ffffffff802c9853>] exit_mmap+0xb3/0x170
Aug 23 10:12:51 system76-pc kernel: [67865.853001]  [<ffffffff8024eca8>] mmput+0x38/0xd0
Aug 23 10:12:51 system76-pc kernel: [67865.853001]  [<ffffffff80253106>] exit_mm+0x116/0x150
Aug 23 10:12:51 system76-pc kernel: [67865.853001]  [<ffffffff8069b741>] ? _spin_lock_irq+0x11/0x20
Aug 23 10:12:51 system76-pc kernel: [67865.853001]  [<ffffffff8025508c>] do_exit+0x16c/0x3b0
Aug 23 10:12:51 system76-pc kernel: [67865.853001]  [<ffffffff8069caee>] oops_end+0xbe/0xc0
Aug 23 10:12:51 system76-pc kernel: [67865.853001]  [<ffffffff8069e57e>] do_page_fault+0x22e/0x780
Aug 23 10:12:51 system76-pc kernel: [67865.853001]  [<ffffffff8024885b>] ? enqueue_task_fair+0x7b/0x80
Aug 23 10:12:51 system76-pc kernel: [67865.853001]  [<ffffffff8024829d>] ? resched_task+0x2d/0x90
Aug 23 10:12:51 system76-pc kernel: [67865.853001]  [<ffffffff80249455>] ? check_preempt_wakeup+0x1e5/0x250
Aug 23 10:12:51 system76-pc kernel: [67865.853001]  [<ffffffff8024a53c>] ? try_to_wake_up+0x12c/0x2e0
Aug 23 10:12:51 system76-pc kernel: [67865.853001]  [<ffffffff805a9cde>] ? __alloc_skb+0x6e/0x150
Aug 23 10:12:51 system76-pc kernel: [67865.853001]  [<ffffffff8024a6fd>] ? default_wake_function+0xd/0x10
Aug 23 10:12:51 system76-pc kernel: [67865.853001]  [<ffffffff8023ec6a>] ? __wake_up_common+0x5a/0x90
Aug 23 10:12:51 system76-pc kernel: [67865.853001]  [<ffffffff8069bc3a>] error_exit+0x0/0x70
Aug 23 10:12:51 system76-pc kernel: [67865.853001]  [<ffffffff802e4f3d>] ? __mem_cgroup_uncharge_common+0xcd/0x1f0
Aug 23 10:12:51 system76-pc kernel: [67865.853001]  [<ffffffff802e4ebd>] ? __mem_cgroup_uncharge_common+0x4d/0x1f0
Aug 23 10:12:51 system76-pc kernel: [67865.853001]  [<ffffffff802e528c>] mem_cgroup_uncharge_page+0x2c/0x40
Aug 23 10:12:51 system76-pc kernel: [67865.853001]  [<ffffffff802ce8dd>] page_remove_rmap+0x4d/0x150
Aug 23 10:12:51 system76-pc kernel: [67865.853001]  [<ffffffff802c2ff2>] zap_pte_range+0x212/0x420
Aug 23 10:12:51 system76-pc kernel: [67865.853001]  [<ffffffff802c427a>] unmap_page_range+0x2da/0x360
Aug 23 10:12:51 system76-pc kernel: [67865.853001]  [<ffffffff802c4b10>] unmap_vmas+0x180/0x2c0
Aug 23 10:12:51 system76-pc kernel: [67865.853001]  [<ffffffff802badc3>] ? drain_cpu_pagevecs+0xa3/0xb0
Aug 23 10:12:51 system76-pc kernel: [67865.853001]  [<ffffffff802c4d02>] zap_page_range+0xb2/0x110
Aug 23 10:12:51 system76-pc kernel: [67865.853001]  [<ffffffff802c1ec5>] madvise_vma+0xf5/0x380
Aug 23 10:12:51 system76-pc kernel: [67865.853001]  [<ffffffff8024662b>] ? finish_task_switch+0x2b/0xf0
Aug 23 10:12:51 system76-pc kernel: [67865.853001]  [<ffffffff8069b741>] ? _spin_lock_irq+0x11/0x20
Aug 23 10:12:51 system76-pc kernel: [67865.853001]  [<ffffffff8069b643>] ? __down_read+0xc3/0xce
Aug 23 10:12:51 system76-pc kernel: [67865.853001]  [<ffffffff8069982c>] ? thread_return+0x37/0x36b
Aug 23 10:12:51 system76-pc kernel: [67865.853001]  [<ffffffff802c2300>] sys_madvise+0x1b0/0x270
Aug 23 10:12:51 system76-pc kernel: [67865.853001]  [<ffffffff802e8a60>] ? sys_writev+0x50/0xb0
Aug 23 10:12:51 system76-pc kernel: [67865.853001]  [<ffffffff8021253a>] system_call_fastpath+0x16/0x1b
Aug 23 10:13:06 system76-pc avahi-daemon[3131]: Invalid query packet.
Aug 23 10:13:06 system76-pc last message repeated 2 times
Aug 23 10:13:56 system76-pc kernel: [67930.577028] usb 4-1: USB disconnect, address 2
Aug 23 10:13:56 system76-pc kernel: [67931.352998] BUG: soft lockup - CPU#2 stuck for 61s! [Xorg:3060]
Aug 23 10:13:56 system76-pc kernel: [67931.353001] Modules linked in: nls_iso8859_1 nls_cp437 vfat fat usb_storage binfmt_misc ppdev bridge stp bnep snd_atiixp_modem snd_via82xx_modem snd_intel8x0m snd_ac97_codec ac97_bus video output input_polldev lp parport snd_pcm_oss snd_hda_intel snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device psmouse snd soundcore snd_page_alloc serio_raw iTCO_wdt iTCO_vendor_support fglrx(P) intel_agp joydev usbhid ohci1394 ieee1394 e1000e fbcon tileblit font bitblit softcursor
Aug 23 10:13:56 system76-pc kernel: [67931.353001] CPU 2:
Aug 23 10:13:56 system76-pc kernel: [67931.353001] Modules linked in: nls_iso8859_1 nls_cp437 vfat fat usb_storage binfmt_misc ppdev bridge stp bnep snd_atiixp_modem snd_via82xx_modem snd_intel8x0m snd_ac97_codec ac97_bus video output input_polldev lp parport snd_pcm_oss snd_hda_intel snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device psmouse snd soundcore snd_page_alloc serio_raw iTCO_wdt iTCO_vendor_support fglrx(P) intel_agp joydev usbhid ohci1394 ieee1394 e1000e fbcon tileblit font bitblit softcursor
Aug 23 10:13:56 system76-pc kernel: [67931.353001] Pid: 3060, comm: Xorg Tainted: P      D    2.6.28-15-generic #49-Ubuntu
Aug 23 10:13:56 system76-pc kernel: [67931.353001] RIP: 0010:[<ffffffff8022f564>]  [<ffffffff8022f564>] __ticket_spin_lock+0x14/0x20
Aug 23 10:13:56 system76-pc kernel: [67931.353001] RSP: 0018:ffff88012d5276d8  EFLAGS: 00200297
Aug 23 10:13:56 system76-pc kernel: [67931.353001] RAX: 0000000000007776 RBX: ffff88012d5276d8 RCX: 00000000013a6fd8
Aug 23 10:13:56 system76-pc kernel: [67931.353001] RDX: ffff88012d572c50 RSI: 00003ffffffff000 RDI: ffffe200013a6fe8
Aug 23 10:13:56 system76-pc kernel: [67931.353001] RBP: ffff88012d5276d8 R08: 00007f3571600000 R09: ffff88012d527888
Aug 23 10:13:56 system76-pc kernel: [67931.353001] R10: 0000000000000002 R11: 0000000000000000 R12: ffffffff80291326
Aug 23 10:13:56 system76-pc kernel: [67931.353001] R13: ffff88012d527668 R14: 0000000000200286 R15: 0000000000200286
Aug 23 10:13:56 system76-pc kernel: [67931.353001] FS:  00007f359a353700(0000) GS:ffff88012f802d00(0000) knlGS:0000000000000000
Aug 23 10:13:56 system76-pc kernel: [67931.353001] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Aug 23 10:13:56 system76-pc kernel: [67931.353001] CR2: fffffbff80b41140 CR3: 0000000000201000 CR4: 00000000000406a0
Aug 23 10:13:56 system76-pc kernel: [67931.353001] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Aug 23 10:13:56 system76-pc kernel: [67931.353001] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Aug 23 10:13:56 system76-pc kernel: [67931.353001] Call Trace:
Aug 23 10:13:56 system76-pc kernel: [67931.353001]  [<ffffffff802ce8f0>] ? page_remove_rmap+0x60/0x150
Aug 23 10:13:56 system76-pc kernel: [67931.353001]  [<ffffffff8069b839>] _spin_lock+0x9/0x10
Aug 23 10:13:56 system76-pc kernel: [67931.353001]  [<ffffffff802c2e8e>] zap_pte_range+0xae/0x420
Aug 23 10:13:56 system76-pc kernel: [67931.353001]  [<ffffffff802c427a>] unmap_page_range+0x2da/0x360
Aug 23 10:13:56 system76-pc kernel: [67931.353001]  [<ffffffff802c4b10>] unmap_vmas+0x180/0x2c0
Aug 23 10:13:56 system76-pc kernel: [67931.353001]  [<ffffffff802c9853>] exit_mmap+0xb3/0x170
Aug 23 10:13:56 system76-pc kernel: [67931.353001]  [<ffffffff8024eca8>] mmput+0x38/0xd0
Aug 23 10:13:56 system76-pc kernel: [67931.353001]  [<ffffffff80253106>] exit_mm+0x116/0x150
Aug 23 10:13:56 system76-pc kernel: [67931.353001]  [<ffffffff8069b741>] ? _spin_lock_irq+0x11/0x20
Aug 23 10:13:56 system76-pc kernel: [67931.353001]  [<ffffffff8025508c>] do_exit+0x16c/0x3b0
Aug 23 10:13:56 system76-pc kernel: [67931.353001]  [<ffffffff8069caee>] oops_end+0xbe/0xc0
Aug 23 10:13:56 system76-pc kernel: [67931.353001]  [<ffffffff8069e57e>] do_page_fault+0x22e/0x780
Aug 23 10:13:56 system76-pc kernel: [67931.353001]  [<ffffffff8024885b>] ? enqueue_task_fair+0x7b/0x80
Aug 23 10:13:56 system76-pc kernel: [67931.353001]  [<ffffffff8024829d>] ? resched_task+0x2d/0x90
Aug 23 10:13:56 system76-pc kernel: [67931.353001]  [<ffffffff80249455>] ? check_preempt_wakeup+0x1e5/0x250
Aug 23 10:13:56 system76-pc kernel: [67931.353001]  [<ffffffff8024a53c>] ? try_to_wake_up+0x12c/0x2e0
Aug 23 10:13:56 system76-pc kernel: [67931.353001]  [<ffffffff805a9cde>] ? __alloc_skb+0x6e/0x150
Aug 23 10:13:56 system76-pc kernel: [67931.353001]  [<ffffffff8024a6fd>] ? default_wake_function+0xd/0x10
Aug 23 10:13:56 system76-pc kernel: [67931.353001]  [<ffffffff8023ec6a>] ? __wake_up_common+0x5a/0x90
Aug 23 10:13:56 system76-pc kernel: [67931.353001]  [<ffffffff8069bc3a>] error_exit+0x0/0x70
Aug 23 10:13:56 system76-pc kernel: [67931.353001]  [<ffffffff802e4f3d>] ? __mem_cgroup_uncharge_common+0xcd/0x1f0
Aug 23 10:13:56 system76-pc kernel: [67931.353001]  [<ffffffff802e4ebd>] ? __mem_cgroup_uncharge_common+0x4d/0x1f0
Aug 23 10:13:56 system76-pc kernel: [67931.353001]  [<ffffffff802e528c>] mem_cgroup_uncharge_page+0x2c/0x40
Aug 23 10:13:56 system76-pc kernel: [67931.353001]  [<ffffffff802ce8dd>] page_remove_rmap+0x4d/0x150
Aug 23 10:13:56 system76-pc kernel: [67931.353001]  [<ffffffff802c2ff2>] zap_pte_range+0x212/0x420
Aug 23 10:13:56 system76-pc kernel: [67931.353001]  [<ffffffff802c427a>] unmap_page_range+0x2da/0x360
Aug 23 10:13:56 system76-pc kernel: [67931.353001]  [<ffffffff802c4b10>] unmap_vmas+0x180/0x2c0
Aug 23 10:13:56 system76-pc kernel: [67931.353001]  [<ffffffff802badc3>] ? drain_cpu_pagevecs+0xa3/0xb0
Aug 23 10:13:56 system76-pc kernel: [67931.353001]  [<ffffffff802c4d02>] zap_page_range+0xb2/0x110
Aug 23 10:13:56 system76-pc kernel: [67931.353001]  [<ffffffff802c1ec5>] madvise_vma+0xf5/0x380
Aug 23 10:13:56 system76-pc kernel: [67931.353001]  [<ffffffff8024662b>] ? finish_task_switch+0x2b/0xf0
Aug 23 10:13:56 system76-pc kernel: [67931.353001]  [<ffffffff8069b741>] ? _spin_lock_irq+0x11/0x20
Aug 23 10:13:56 system76-pc kernel: [67931.353001]  [<ffffffff8069b643>] ? __down_read+0xc3/0xce
Aug 23 10:13:56 system76-pc kernel: [67931.353001]  [<ffffffff8069982c>] ? thread_return+0x37/0x36b
Aug 23 10:13:56 system76-pc kernel: [67931.353001]  [<ffffffff802c2300>] sys_madvise+0x1b0/0x270
Aug 23 10:13:56 system76-pc kernel: [67931.353001]  [<ffffffff802e8a60>] ? sys_writev+0x50/0xb0
Aug 23 10:13:56 system76-pc kernel: [67931.353001]  [<ffffffff8021253a>] system_call_fastpath+0x16/0x1b
Aug 23 10:16:26 system76-pc syslogd 1.5.0#5ubuntu3: restart.

```

---

### Post by thomasaaron on 2009-08-24
Carl, mentioned your issue to me this morning. Could you please try running memtest86 on your machine and see if it throws any errors?

> Reboot your computer. When you see the grub countdown menu, press the 'Esc' key. When you see the grub menu, press your 'down' arrow until Memtest86 is highlighted. Then press 'Enter' to start testing.

Please start Ubuntu in the evening before going to bed and let it run all night long. Memory card problems can be subtle, and sometimes they will not show up until the cards start heating up. Often it will take several passes before errors appear.

---

### Post by thomasaaron on 2009-08-24
We have seen some circumstances where the current ATI driver in Ubuntu's repositories acts somewhat lethargic. There are new drivers that perform far better. To give it a try run the following commands in your terminal one at a time - they are rather long commands - you can cut and paste them (Applications > Accessories > Terminal)

echo deb [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) `lsb_release -cs` main | sudo tee -a /etc/apt/sources.list.d/x-updates.list

echo deb-src [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) `lsb_release -cs` main | sudo tee -a /etc/apt/sources.list.d/x-updates.list

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 3B22AB97AF1CDFA9 && sudo apt-get update

sudo apt-get upgrade

Let me know if this stops the freezing.

---

### Post by Ed.Corcoran on 2009-08-24
My computer crashed again about an hour ago. I ran memtest and it gave no errors. I've attached the logs tarball generated by the System76 driver.

I'm about to try updating the ATI driver, too.

---

### Post by thomasaaron on 2009-08-25
You have a bunch of errors in there that I'm unfamiliar with. They could be ATI related, but they could be hardware related too.

Since you had some problems with this computer right out of the box, I think you should try reseating your memory cards and your video card, just in case something got bumped loose in shipping.

But before you do that, let's see if the ATI fix solves the problem.

On another note, you have this error too...
> npviewer.bin[20059]: segfault at ff99cd48 ip 00000000ff99cd48 sp 00000000ff916cac error 14
...which is probably not related to the crashing at all, but it is Flash crashing. Please follow these instructions to install 64-bit flash...

> 1. Shut down Firefox

2. Run the following commands from a terminal...

sudo apt-get remove flashplugin-*
sudo apt-get remove nspluginwrapper

3. Click the link at the very bottom of this page...
[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)
...to download the latest 64-bit Flash plugin. Save it to your Desktop and extract it to your Desktop.
Drag libflashplayer.so from the extracted folder onto your Desktop.

4. Run these commands from the terminal...
mkdir -p .mozilla/plugins
mv ~/Desktop/libflashplayer.so .mozilla/plugins

5. Restart Firefox

---

### Post by Ed.Corcoran on 2009-08-25
I followed the instructions to install Flash 64bit, but Firefox gave a segmentation fault a few seconds after booting. I probably had a flash ad on one of the tabs I had open and that caused the crash.

When I removed libflashplayer.so, Firefox loaded fine, but with no Flash obviously.

---

### Post by thomasaaron on 2009-08-25
Thanks. 

I guess I need to do some in house testing on this! It was working fine, but you're the second person to report this particular problem recently. Maybe something has changed that I'm missing.

Below are instructions for going back to the nspluggin-wrapper version. But before you do, could you please try re-installing the 64-bit plugin per my instructions. Then open firefox and type this in the URL bar...

about:plugins

...and see what plugins it lists for flash?

Here are the instructions to revert back to the 32-bit plugin...
> 
Open a terminal and run these commands:

rm -r .mozilla/plugins
sudo apt-get install flashplugin-installer

---

### Post by Ed.Corcoran on 2009-08-25
Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 10.0 r32

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes

---

### Post by Ed.Corcoran on 2009-08-25
Also, its working now. Weird. I did almost the exact same thing last time, and it didn't work.

The difference is that the first time, when I uninstalled nspluginwrapper it uninstalled acroread. So I reinstalled acroread before I opened Firefox. This time, I didn't do that.

---

### Post by Ed.Corcoran on 2009-08-25
Okay, so now Firefox is crashing when I visit Gmail.

---

### Post by Ed.Corcoran on 2009-08-26
So it crashed again some time last night while I was sleeping. Here are the logs.

---

### Post by jdb on 2009-08-26
> **Ed.Corcoran said:**
> So it crashed again some time last night while I was sleeping. Here are the logs.

I don't know if it will help you much, but at least you'll know you're not alone.

Google: 

```
BUG: soft lockup - CPU#2 stuck for 61s!
```

and you'll get a whole lot of hits.

It looks like the "soft lockup" is sometimes a hard lockup.

jdb

---

### Post by thomasaaron on 2009-08-26
Yes, we're definitely dealing with a major league kernel panic.

Both of these...

BUG: soft lockup - CPU#2 stuck for 61s! [Xorg:2971]
BUG: unable to handle kernel paging request at fffffbff80b41140

...pull up a ton of hits. The interesting thing to me is that I've not seen this on a Wild Dog before. Given the popularity of these messages, I'm betting that we're dealing with a software related issue and not a hardware issue.

A few things that I've seen in my initial research point to:

Firefox (Are you running the version that came with the machine?)

Virtual Machines (Are you running any?)

ATI proprietary drivers (Other than my suggestion above, have you made any other driver modifications?)

A defective memory card (How long did you previously run memtest86 for? Sometimes it takes many passes for it to start registering errors -- a heat thing, maybe.)

Could you please give me a full account of any software you've installed, configuration changes you've made, etc...

Also, if you press 'Esc' when you see the grub countdown (grub...3...2...1...) when booting, is there a previous kernel available on your machine? Maybe the *-14 kernel. If you boot into the previous kernel, do the freezes occur?

---

### Post by Ed.Corcoran on 2009-08-26
I'm running the stock firefox. The only addons I have installed are DownThemAll, Ubiquity, XMarks and Zotero.
The only stuff I've installed from non-Ubuntu or non-System76 repos is a version of Amarok 1.4 for Jaunty, some codecs from Medibuntu and the gnome-colors theme (which I haven't even enabled yet).

I'm not sure if the crash has happened when I wasn't running Firefox, as Firefox is running almost every second my computer is on. Ditto for Amarok.

No virtual machines.
The only driver modification is the one you advised earlier in the thread.
I ran one pass of memtest86. I'll run it longer when I have a chance.
I'll also try an earlier kernel, if there is one.

---

### Post by Ed.Corcoran on 2009-08-26
It crashed again and here's the new log file.

I had Firefox open with two tabs, Amarok 1.4 was moving some files to my collection, and I was running a diff between two large directories of binary files. The diff had been running for about an hour.

---

### Post by Ed.Corcoran on 2009-08-26
Oh, and I had just installed the  linux-backports-modules-jaunty package. 
Also, I tried to check to see what earlier kernels I had, but I didn't get the keyboard plugged in in time. My computer freezes at POST when I boot with either of my logitech wireless USB mouse and keyboard plugged in.

---

### Post by thomasaaron on 2009-08-27
You have a flash segfault about 40 minutes before the crash. In a previous case, I've seen npviewer segfaults cause xorg to slowly become less and less responsive until it crashes.

> kernel: [37137.588916] npviewer.bin[4242]: segfault at ff99cd48 ip 00000000ff99cd48 sp 00000000ff987d1c error 14

Looks like your DHCP renewed about 20 minutes before the crash, and your Networkmanager *may* not have been able to re-establish a connection. Not exactly sure if I'm reading that right yet.

> g 26 20:25:25 system76-pc NetworkManager: <info>    address 192.168.1.75 
Aug 26 20:25:25 system76-pc NetworkManager: <info>    prefix 24 (255.255.255.0) 
Aug 26 20:25:25 system76-pc NetworkManager: <info>    gateway 192.168.1.254 
Aug 26 20:25:25 system76-pc NetworkManager: <info>    nameserver '192.168.1.254' 
Aug 26 20:25:25 system76-pc NetworkManager: <info>    domain name 'gateway.2wire.net' 
Aug 26 20:25:33 system76-pc avahi-daemon[3088]: Invalid query packet.

Other than that, nothing suspicious.

I'd still like to see what a prolonged memtest run shows.

---

### Post by Ed.Corcoran on 2009-08-27
I ran memtest for 8 passes, and it gave no errors.

---

### Post by Ed.Corcoran on 2009-08-28
Happened again over night. I was running a large diff operation overnight, and it got through the Ks.

---

### Post by thomasaaron on 2009-08-28
OK, this may be starting to come together...

In the most recent batch of logs, you have this line...
> Aug 28 03:54:56 system76-pc avahi-daemon[3015]: Invalid query packet.
...right before the crash. But there isn't much else that's helpful.

Early on, you posted some log entries that had the invalid query packet error as well. However, there was a lot of other weird stuff in the logs that matches up nicely with this bug...
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/347711](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/347711)
...which pertains to a networking bug. You have a different mobo, but that doesn't mean the problem doesn't affect it.

Then recently, I pointed out these errors, which indicated a networking failure during lease renewal...
> g 26 20:25:25 system76-pc NetworkManager: <info> address 192.168.1.75
Aug 26 20:25:25 system76-pc NetworkManager: <info> prefix 24 (255.255.255.0)
Aug 26 20:25:25 system76-pc NetworkManager: <info> gateway 192.168.1.254
Aug 26 20:25:25 system76-pc NetworkManager: <info> nameserver '192.168.1.254'
Aug 26 20:25:25 system76-pc NetworkManager: <info> domain name 'gateway.2wire.net'
Aug 26 20:25:33 system76-pc avahi-daemon[3088]: Invalid query packet. 

...as well as the invalid query packet line.

So, I think a pattern may be starting to emerge. A few more questions...

1. Are you using that 'down them all' plugin when the crash occurs?
2. Are you using samba?
3. When you're doing the diffs, does that involve any heavy file transfers?
4. On your router, how often does your DHCP lease renew? I'm wondering if the crashes coincide with renewal.

Anything else you can think of that might link your network connectivity to the crashes?

Another thing, does your computer freeze during boot if you use a USB keyboard/mouse?

---

### Post by Ed.Corcoran on 2009-08-28
I have DownThemAll installed, but I don't think I've been using it during any of the crashes. However, Firefox was running during all the crashes because I essentially never close Firefox.

I use Samba for my home network, but I don't think my computer has crashed during any file transfers across Samba.

The diffs didn't involve heavy file transfers, just lots of reads. However, the computer did crash several times when I was doing bulk renames of files last week. However, it has also crashed when I was doing nothing more than checking my email.

DHCP lease time is 24 hours. However, I just changed my computer to have a permanent lease from the router. We'll see if that helps.

---

### Post by Ed.Corcoran on 2009-08-28
And yes, it does freeze during POST if the USB keyboard is plugged in. It will book if the USB mouse is plugged in, though.

---

### Post by thomasaaron on 2009-08-28
Hi, Ed.

OK, I just want to make sure I'm understanding this correctly...

1. With *only* the USB keyboard plugged in during boot, it will not finish posting.
2. With *only* a USB mouse plugged in during boot, it will post and boot.
3. With wireless keyboard/mouse plugged in, it freezes during post.

So, I'll assume it freezes during post with USB keyboard and mouse both installed?

One last question, can you *please* test with a different USB keyboard and mouse, just to rule out a bad USB keyboard and mouse. If it freezes with a known good USB keyboard, we've got a hardware problem (and all the rest of this might just be chasing our tails).

---

### Post by Ed.Corcoran on 2009-08-28
With my logitech wireless keyboard plugged in, it does not boot. With my logitech wireless mouse plugged in, it boots. With both plugged in, it does not boot. Each device has a separate reciever. They worked together fine on my old computer.

With a wired Apple USB mouse and wired Apple USB keyboard plugged in, it does boot. The Apple mouse and keyboard is the only wired keyboard and mouse in my house. I have an additional wireless USB keyboard made by MS that I can also try, if you'd like. 

Also, it just froze again. I had just started another diff operation, and after it froze the hard drive still made active sounds for a while. After 10 minutes or so, I hard rebooted to test the Apple mouse and keyboard. I looked at the output of the diff operation (which I had piped to a text file) and the end of the file had some random garbage. Not sure if that's relevant or not. I can attach the output of diff if you'd like.

---

### Post by Ed.Corcoran on 2009-08-28
I just froze again. This time, I was running diff and watching a youtube video. when it froze, the audio started skipping until I rebooted. Usually the audio either finishes playing or just stops.

---

### Post by jdb on 2009-08-28
> **Ed.Corcoran said:**
> I just froze again. This time, I was running diff and watching a youtube video. when it froze, the audio started skipping until I rebooted. Usually the audio either finishes playing or just stops.

It sounds like the kernel is still active when it freezes.
If you've got another linux machine it might be interesting to ssh into it next time it freezes & run top.

jdb

---

### Post by thomasaaron on 2009-08-28
Both logs show the invalid query packet error right before the freeze/crash.

FIRST LOG
```
Aug 28 13:08:59 system76-pc kernel: [10348.697032] usb 4-1: USB disconnect, address 2
Aug 28 13:09:01 system76-pc kernel: [10351.176031] usb 4-2: USB disconnect, address 3
Aug 28 13:09:01 system76-pc chipcardd[3517]: devicemanager.c: 3373: Changes in hardware list
Aug 28 13:10:04 system76-pc /USR/SBIN/CRON[12369]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 28 13:11:20 system76-pc avahi-daemon[3245]: Invalid query packet.
```

SECOND LOG
> 
Aug 28 13:28:19 system76-pc avahi-daemon[3204]: Invalid query packet.

BUT... :popcorn:

I'm getting pretty seriously confused here. 

Earlier you said...
> And yes, it **does freeze** during POST if the USB keyboard is plugged in. 

Then, you just said...

> With a wired Apple USB mouse and wired Apple USB keyboard plugged in, it **does boot**. 

...and since you said...
> The Apple mouse and keyboard is the **only** wired keyboard and mouse in my house.
...I'm assuming they are the same keyboard.

I'm not trying to be a pain, I'm just trying to understand the situation. My contention is this: If this computer will not boot with a USB keyboard, you have a hardware problem that makes pretty much every other problem you've reported moot.

Please try booting with the MS wired keyboard. If it freezes, we'll need to bring it in and figure out what is going on.

It would be ideal to eliminate anything Apple and anything wireless from the picture for testing purposes, if that is at all possible. At least until we establish that the problem persists without either.

---

### Post by Ed.Corcoran on 2009-08-28
Sorry for the confusion.

It won't boot when my Logitech wireless keyboard is plugged in.

It will boot when the Logitech wireless mouse, the Apple wired mouse or the Apple wired keyboard is plugged in.

The only other keyboard I have is a wireless Microsoft keyboard. I will try that as soon as I can.

---

### Post by Ed.Corcoran on 2009-08-28
Also, when I said 

> And yes, it does freeze during POST if the USB keyboard is plugged in.

I was referring to the wireless Logitech USB keyboard, not the wired Apple keyboard.

---

### Post by Ed.Corcoran on 2009-08-29
Okay, I just rebooted my computer with the Logitech wireless mouse plugged in, but no keyboard plugged in and it hung during POST. It booted fine with no mouse or keyboard plugged in.

---

### Post by Ed.Corcoran on 2009-08-30
Another crash. This time, all I had open was Firefox (just using Facebook, nothing complicated) and Quod Libet (which was open, but not playing any music). When it crashed, I tried to ssh in. I realized that I hadn't installed ssh server, though. So I got "connection refused". Still, I did get a response from my computer over the network.

Also, when I rebooted, I had the Logitech mouse plugged in and it POSTed fine this time.

---

### Post by Ed.Corcoran on 2009-08-30
So it crashed again. This time, all I had open was Firefox (three tabs open: ebay and two tabs of Facebook).

When it crashed, I sshed in from my laptop. I was able to access it, so clearly the problem is related to X somehow. There were no processes hogging the CPU, but npviewer.bin and chipcardd4 were the only things not owned by root that would get 1% of the CPU and show up at the top of top.

I killed both, but my screen was still frozen.

I tried /etc/init.d/x11 restart. It did nothing. I tried /etc/init.d/gdm restart. It said that it successfully stopped Gnome, but hung when it tried to start it again. I couldn't even kill it with a ^C. Then I opened a new terminal, sshed in again, and tried a command line reboot, but it hung. I couldn't ^C it either, so I hard rebooted.

I've attached my log tarball, of course.

---

### Post by jdb on 2009-08-30
> **Ed.Corcoran said:**
> So it crashed again. This time, all I had open was Firefox (three tabs open: ebay and two tabs of Facebook).

When it crashed, I sshed in from my laptop. I was able to access it, so clearly the problem is related to X somehow. There were no processes hogging the CPU, but npviewer.bin and chipcardd4 were the only things not owned by root that would get 1% of the CPU and show up at the top of top.

I killed both, but my screen was still frozen.

I tried /etc/init.d/x11 restart. It did nothing. I tried /etc/init.d/gdm restart. It said that it successfully stopped Gnome, but hung when it tried to start it again. I couldn't even kill it with a ^C. Then I opened a new terminal, sshed in again, and tried a command line reboot, but it hung. I couldn't ^C it either, so I hard rebooted.

I've attached my log tarball, of course.

If you get a chance to ssh in again, you might try:

```
ps -ef
```

It will give a chronological list of things running.
The ones that don't scroll off the top of the screen are the most recent.

jdb

edit:

```
ps -eo user,pid,ppid,stat,ni,stime,c,rss,cmd
```

will give a little more info.

From "man ps" this is what the stat field means:

```
PROCESS STATE CODES
Here are the different values that the s, stat and state output specifiers
(header "STAT" or "S") will display to describe the state of a process.
D    Uninterruptible sleep (usually IO)
R    Running or runnable (on run queue)
S    Interruptible sleep (waiting for an event to complete)
T    Stopped, either by a job control signal or because it is being traced.
W    paging (not valid since the 2.6.xx kernel)
X    dead (should never be seen)
Z    Defunct ("zombie") process, terminated but not reaped by its parent.

For BSD formats and when the stat keyword is used, additional characters may
be displayed:
<    high-priority (not nice to other users)
N    low-priority (nice to other users)
L    has pages locked into memory (for real-time and custom IO)
s    is a session leader
l    is multi-threaded (using CLONE_THREAD, like NPTL pthreads do)
+    is in the foreground process group

```

jdb

---

### Post by Ed.Corcoran on 2009-09-01
Had another crash earlier today. Logs are attached. I was just using Firefox and had GnuCash open in the background.

When I tried to log into my machine remotely, it did not work. When I had ssh be verbose, this was what I got:

```

OpenSSH_5.1p1 Debian-3ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to system76-pc [192.168.1.75] port 22.
debug1: Connection established.
debug1: identity file /home/ed/.ssh/identity type -1
debug1: identity file /home/ed/.ssh/id_rsa type -1
debug1: identity file /home/ed/.ssh/id_dsa type -1

```

SSH didn't get any further than that, even if I waited for a while.
When my computer isn't hung, I can log in remotely as normal.

---

### Post by thomasaaron on 2009-09-02
Ed, could you please give me a call at your convenience...
[http://system76.com/article_info.php?articles_id=24](http://system76.com/article_info.php?articles_id=24)
(Just use the sales number.)

---

### Post by iosif on 2009-09-05
I believe the ATI / Catalyst / Radeon drivers that came with my Wild Dog (wilp6) are the source of my particular freezing / crashing.

---

### Post by iosif on 2009-09-05
> **thomasaaron said:**
> We have seen some circumstances where the current ATI driver in Ubuntu's repositories acts somewhat lethargic. There are new drivers that perform far better. To give it a try run the following commands in your terminal one at a time - they are rather long commands - you can cut and paste them (Applications > Accessories > Terminal)

echo deb [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) `lsb_release -cs` main | sudo tee -a /etc/apt/sources.list.d/x-updates.list

echo deb-src [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) `lsb_release -cs` main | sudo tee -a /etc/apt/sources.list.d/x-updates.list

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 3B22AB97AF1CDFA9 && sudo apt-get update

sudo apt-get upgrade

Let me know if this stops the freezing.

What ATI drivers are these?  Are they proprietary?

---

### Post by thomasaaron on 2009-09-07
I believe they are open source (which is why they are in the launchpad ppas). However, there is work being done on them to work out some bugs.

---

