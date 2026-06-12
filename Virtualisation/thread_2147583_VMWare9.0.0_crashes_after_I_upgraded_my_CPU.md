---
title: "VMWare9.0.0 crashes after I upgraded my CPU"
date: 2013-05-22
forum: Virtualisation
---

### Post by zhujf553 on 2013-05-22
Ubuntu 12.04.02 64bit
I upgraded my CPU from T6600 to P9600. And VMWare crashes in the login screen. My computer stuck in a black screen for a while, then it comes back.

---

### Post by gordintoronto on 2013-05-22
The P9600 includes "virtualization technology." I suspect VMWare is very confused. Can you reinstall it?

---

### Post by zhujf553 on 2013-05-22
I tried to reinstall it, but the it crashed again while installing...Is there any method to clean its settings completely?

> **gordintoronto said:**
> The P9600 includes "virtualization technology." I suspect VMWare is very confused. Can you reinstall it?

---

### Post by zhujf553 on 2013-05-23
The log is following:


May 23 19:34:29 lenovo-Rev-1-0 kernel: [  172.186173] general protection fault: 0000 [#1] SMP 
May 23 19:34:29 lenovo-Rev-1-0 kernel: [  172.186192] CPU 1 
May 23 19:34:29 lenovo-Rev-1-0 kernel: [  172.186195] Modules linked in: vmnet(O) parport_pc vsock(O) vmci(O) vmmon(O) joydev arc4 coretemp kvm_intel kvm ir_lirc_codec lirc_dev ir_mce_kbd_decoder ir_sanyo_decoder ir_sony_decoder ir_jvc_decoder ir_rc6_decoder ir_rc5_decoder ir_nec_decoder rc_rc6_mce ppdev ite_cir uvcvideo videobuf2_core bnep rfcomm rc_core snd_hda_codec_hdmi ideapad_laptop videodev videobuf2_vmalloc videobuf2_memops sparse_keymap microcode snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq mac_hid psmouse serio_raw nouveau snd_timer snd_seq_device snd btusb bluetooth lpc_ich ttm drm_kms_helper drm iwlwifi i2c_algo_bit mxm_wmi mac80211 jmb38x_ms video memstick cfg80211 wmi soundcore snd_page_alloc lp parport hid_generic usbhid hid tg3 firewire_ohci firewire_core crc_itu_t sdhci_pci sdhci [last unloaded: vmnet]
May 23 19:34:29 lenovo-Rev-1-0 kernel: [  172.186347] 
May 23 19:34:29 lenovo-Rev-1-0 kernel: [  172.186350] Pid: 5640, comm: vmware-hostd Tainted: G           O 3.5.0-23-generic #35~precise1-Ubuntu LENOVO                           IdeaPad Y450                    /KL1                             
May 23 19:34:29 lenovo-Rev-1-0 kernel: [  172.186533] RIP: 0010:[<ffffffffa044e284>]  [<ffffffffa044e284>] HostIF_SafeRDMSR+0x14/0x30 [vmmon]
May 23 19:34:29 lenovo-Rev-1-0 kernel: [  172.186551] RSP: 0018:ffff880036cedb48  EFLAGS: 00010246
May 23 19:34:29 lenovo-Rev-1-0 kernel: [  172.186556] RAX: 0000000000000000 RBX: 0000000000000001 RCX: 000000000000048c
May 23 19:34:29 lenovo-Rev-1-0 kernel: [  172.186562] RDX: 0000000000000000 RSI: ffff880036ce9210 RDI: 000000000000048c
May 23 19:34:29 lenovo-Rev-1-0 kernel: [  172.186568] RBP: ffff880036cedb48 R08: 0000000000000000 R09: 0000000000000060
May 23 19:34:29 lenovo-Rev-1-0 kernel: [  172.186576] R10: 00000000069366a0 R11: 0000000000000246 R12: ffff880036ce9200
May 23 19:34:29 lenovo-Rev-1-0 kernel: [  172.186582] R13: 0000000000000000 R14: ffff880036ce9200 R15: ffff88015e671500
May 23 19:34:29 lenovo-Rev-1-0 kernel: [  172.186588] FS:  00007f46b0fcf740(0000) GS:ffff88017fd00000(0000) knlGS:0000000000000000
May 23 19:34:29 lenovo-Rev-1-0 kernel: [  172.186597] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
May 23 19:34:29 lenovo-Rev-1-0 kernel: [  172.186602] CR2: 0000000000db93e0 CR3: 0000000036e6f000 CR4: 00000000000407e0
May 23 19:34:29 lenovo-Rev-1-0 kernel: [  172.186615] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
May 23 19:34:29 lenovo-Rev-1-0 kernel: [  172.186621] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
May 23 19:34:29 lenovo-Rev-1-0 kernel: [  172.186632] Process vmware-hostd (pid: 5640, threadinfo ffff880036cec000, task ffff880169775c00)
May 23 19:34:29 lenovo-Rev-1-0 kernel: [  172.186643] Stack:
May 23 19:34:29 lenovo-Rev-1-0 kernel: [  172.186646]  ffff880036cedb78 ffffffffa0451c34 ffffffffa0451bb0 ffff880036cedba8
May 23 19:34:29 lenovo-Rev-1-0 kernel: [  172.186667]  00000000000007f1 00000000fffffff4 ffff880036cedb98 ffffffffa044da20
May 23 19:34:29 lenovo-Rev-1-0 kernel: [  172.186691]  ffff880036ce9200 ffff880036ce9200 ffff880036cedbc8 ffffffffa04539fc
May 23 19:34:29 lenovo-Rev-1-0 kernel: [  172.186709] Call Trace:
May 23 19:34:29 lenovo-Rev-1-0 kernel: [  172.186716]  [<ffffffffa0451c34>] Vmx86GetMSR+0x84/0xd0 [vmmon]
May 23 19:34:29 lenovo-Rev-1-0 kernel: [  172.186732]  [<ffffffffa0451bb0>] ? Vmx86GetUnavailPerfCtrsOnCPU+0x150/0x150 [vmmon]
May 23 19:34:29 lenovo-Rev-1-0 kernel: [  172.186745]  [<ffffffffa044da20>] HostIF_CallOnEachCPU+0x20/0x40 [vmmon]
May 23 19:34:29 lenovo-Rev-1-0 kernel: [  172.186753]  [<ffffffffa04539fc>] Vmx86_GetAllMSRs+0x2c/0x50 [vmmon]
May 23 19:34:29 lenovo-Rev-1-0 kernel: [  172.186760]  [<ffffffffa044b57e>] LinuxDriver_Ioctl+0x73e/0xd70 [vmmon]
May 23 19:34:29 lenovo-Rev-1-0 kernel: [  172.186776]  [<ffffffff81080b08>] ? __wake_up_common+0x58/0x90
May 23 19:34:29 lenovo-Rev-1-0 kernel: [  172.186783]  [<ffffffff8133522e>] ? radix_tree_lookup_slot+0xe/0x10
May 23 19:34:29 lenovo-Rev-1-0 kernel: [  172.186790]  [<ffffffff81127e3e>] ? find_get_page+0x1e/0x90
May 23 19:34:29 lenovo-Rev-1-0 kernel: [  172.186804]  [<ffffffff81129b6e>] ? filemap_fault+0xee/0x3e0
May 23 19:34:29 lenovo-Rev-1-0 kernel: [  172.186811]  [<ffffffff81181bef>] ? mem_cgroup_update_page_stat+0x1f/0x60
May 23 19:34:29 lenovo-Rev-1-0 kernel: [  172.186824]  [<ffffffff811272a7>] ? unlock_page+0x27/0x30
May 23 19:34:29 lenovo-Rev-1-0 kernel: [  172.186839]  [<ffffffff8114c4a1>] ? __do_fault+0x421/0x520
May 23 19:34:29 lenovo-Rev-1-0 kernel: [  172.186851]  [<ffffffff81192282>] ? path_put+0x22/0x30
May 23 19:34:29 lenovo-Rev-1-0 kernel: [  172.186860]  [<ffffffff8114fb0a>] ? handle_pte_fault+0xfa/0x200
May 23 19:34:29 lenovo-Rev-1-0 kernel: [  172.186875]  [<ffffffff81196e6e>] ? path_openat+0x10e/0x440
May 23 19:34:29 lenovo-Rev-1-0 kernel: [  172.186893]  [<ffffffff81150d69>] ? handle_mm_fault+0x269/0x340
May 23 19:34:29 lenovo-Rev-1-0 kernel: [  172.186907]  [<ffffffff816a2670>] ? do_page_fault+0x210/0x520
May 23 19:34:29 lenovo-Rev-1-0 kernel: [  172.186929]  [<ffffffffa044bbc8>] LinuxDriver_UnlockedIoctl+0x18/0x20 [vmmon]
May 23 19:34:29 lenovo-Rev-1-0 kernel: [  172.186941]  [<ffffffff811996fa>] do_vfs_ioctl+0x8a/0x340
May 23 19:34:29 lenovo-Rev-1-0 kernel: [  172.187765]  [<ffffffff811928e5>] ? putname+0x35/0x50
May 23 19:34:29 lenovo-Rev-1-0 kernel: [  172.188462]  [<ffffffff81186ec0>] ? do_sys_open+0x180/0x240
May 23 19:34:29 lenovo-Rev-1-0 kernel: [  172.188568]  [<ffffffff81199a41>] sys_ioctl+0x91/0xa0
May 23 19:34:29 lenovo-Rev-1-0 kernel: [  172.188568]  [<ffffffff816a7029>] system_call_fastpath+0x16/0x1b
May 23 19:34:29 lenovo-Rev-1-0 kernel: [  172.188568] Code: 64 ce e0 44 89 e0 48 3b 43 08 72 e9 48 89 df e8 53 5f d2 e0 eb 9e 90 55 48 89 e5 66 66 66 66 90 45 31 c0 44 89 c0 44 89 c2 89 f9 <0f> 32 31 ff 41 89 c0 48 c1 e2 20 89 f8 4c 09 c2 48 89 16 5d c3 
May 23 19:34:29 lenovo-Rev-1-0 kernel: [  172.188568] RIP  [<ffffffffa044e284>] HostIF_SafeRDMSR+0x14/0x30 [vmmon]
May 23 19:34:29 lenovo-Rev-1-0 kernel: [  172.188568]  RSP <ffff880036cedb48>
May 23 19:34:29 lenovo-Rev-1-0 kernel: [  172.199130] ---[ end trace 6e1b10631234c5eb ]---
May 23 19:34:29 lenovo-Rev-1-0 kernel: [  172.412192] [drm] nouveau 0000:01:00.0: EvoCh 1 Mthd 0x0080 Data 0x00000000 (0x0006 0x05)
May 23 19:35:39 lenovo-Rev-1-0 kernel: [  241.900017] [drm] nouveau 0000:01:00.0: Failed to idle channel 2.

---

