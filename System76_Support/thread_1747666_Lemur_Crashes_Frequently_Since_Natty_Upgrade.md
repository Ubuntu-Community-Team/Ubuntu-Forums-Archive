---
title: "Lemur Crashes Frequently Since Natty Upgrade"
date: 2011-05-02
forum: System76 Support
---

### Post by distortedstar on 2011-05-02
Hello. Since the Natty upgrade my Lemu2 crashes about 3 times a day to console, mouse doesn't work, and keyboard seems unresponsive (can't switch virtual terminals or anything).

Here are what seem to be the relevant bits from the sys logs:

```
May  2 14:45:40 the-raft kernel: [12067.261134]  <EOI> 
May  2 14:45:40 the-raft kernel: [12067.261173]  [<ffffffff8133685a>] ? intel_idle+0xca/0x120
May  2 14:45:40 the-raft kernel: [12067.264661]  [<ffffffff81336839>] ? intel_idle+0xa9/0x120
May  2 14:45:40 the-raft kernel: [12067.268081]  [<ffffffff814a3bda>] cpuidle_idle_call+0xaa/0x1b0
May  2 14:45:41 the-raft kernel: [12067.272392]  [<ffffffff8100a266>] cpu_idle+0xa6/0xf0
May  2 14:45:41 the-raft kernel: [12067.276792]  [<ffffffff815a9205>] rest_init+0x75/0x80
May  2 14:45:41 the-raft kernel: [12067.280252]  [<ffffffff81acac8b>] start_kernel+0x3f5/0x400
May  2 14:45:41 the-raft kernel: [12067.283926]  [<ffffffff81aca388>] x86_64_start_reservations+0x132/0x136
May  2 14:45:41 the-raft kernel: [12067.287521]  [<ffffffff81aca253>] ? zap_identity_mappings+0x3e/0x41
May  2 14:45:41 the-raft kernel: [12067.290728]  [<ffffffff81aca458>] x86_64_start_kernel+0xcc/0xdb
May  2 14:45:41 the-raft kernel: [12067.293776] Code: 1f 44 00 00 48 89 f0 48 89 d3 0f b6 72 40 0f b6 52 3f 4c 89 45 c0 4c 8d a7 c8 a1 00 00 48 89 4d c8 48 01 d6 48 03 b0 e0 00 00 00 <44> 0f b7 06 48 8d 4e 04 44 89 c0 83 e0 0c 66 83 f8 04 0f 84 b0 
May  2 14:45:41 the-raft kernel: [12067.300924] RIP  [<ffffffffa0221a48>] rtl8192se_TranslateRxSignalStuff+0x48/0x220 [r8192se_pci]
May  2 14:45:41 the-raft kernel: [12067.305380]  RSP <ffff880077003cd0>
May  2 14:45:41 the-raft kernel: [12067.308978] CR2: 000000ff00000020
May  2 14:45:41 the-raft kernel: [12067.312332] BUG: scheduling while atomic: swapper/0/0x10000100
May  2 14:45:41 the-raft kernel: [12067.315633] Modules linked in: michael_mic arc4 binfmt_misc parport_pc ppdev dm_crypt joydev snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi uvcvideo snd_rawmidi snd_seq_midi_event snd_seq snd_timer r8192se_pci snd_seq_device videodev v4l2_compat_ioctl32 cfg80211 intel_ips jmb38x_ms snd psmouse serio_raw memstick soundcore snd_page_alloc lp parport dm_raid45 xor usb_storage uas i915 drm_kms_helper ahci drm sdhci_pci libahci jme sdhci i2c_algo_bit video
May  2 14:45:41 the-raft kernel: [12067.330472] CPU 0 
May  2 14:45:41 the-raft kernel: [12067.330502] Modules linked in: michael_mic arc4 binfmt_misc parport_pc ppdev dm_crypt joydev snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi uvcvideo snd_rawmidi snd_seq_midi_event snd_seq snd_timer r8192se_pci snd_seq_device videodev v4l2_compat_ioctl32 cfg80211 intel_ips jmb38x_ms snd psmouse serio_raw memstick soundcore snd_page_alloc lp parport dm_raid45 xor usb_storage uas i915 drm_kms_helper ahci drm sdhci_pci libahci jme sdhci i2c_algo_bit video
May  2 14:45:41 the-raft kernel: [12067.350324] 
May  2 14:45:41 the-raft kernel: [12067.354344] Pid: 0, comm: swapper Not tainted 2.6.38-8-generic #42-Ubuntu System76, Inc.                        Lemur UltraThin                      /Lemur UltraThin                      
May  2 14:45:41 the-raft kernel: [12067.362631] RIP: 0010:[<ffffffff8133685a>]  [<ffffffff8133685a>] intel_idle+0xca/0x120
May  2 14:45:41 the-raft kernel: [12067.366764] RSP: 0018:ffffffff81a01e38  EFLAGS: 00000206
May  2 14:45:41 the-raft kernel: [12067.370921] RAX: 0000000000000000 RBX: ffff880077010108 RCX: 0000000000000000
May  2 14:45:41 the-raft kernel: [12067.375110] RDX: 0000000000000027 RSI: 0000000000000000 RDI: 0000000000009938
May  2 14:45:41 the-raft kernel: [12067.379298] RBP: ffffffff81a01e88 R08: 0000000000000ed8 R09: 00000000fffffffd
May  2 14:45:41 the-raft kernel: [12067.383512] R10: 00000000000014fd R11: 0000000000000001 R12: ffffffff815c320e
May  2 14:45:41 the-raft kernel: [12067.387671] R13: ffffffff81a01db8 R14: ffffffff8108b909 R15: ffffffff81a01db8
May  2 14:45:41 the-raft kernel: [12067.391867] FS:  0000000000000000(0000) GS:ffff880077000000(0000) knlGS:0000000000000000
May  2 14:45:41 the-raft kernel: [12067.396070] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
May  2 14:45:41 the-raft kernel: [12067.400305] CR2: 000000ff00000020 CR3: 0000000001a03000 CR4: 00000000000006f0
May  2 14:45:41 the-raft kernel: [12067.404508] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
May  2 14:45:41 the-raft kernel: [12067.408795] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
May  2 14:45:41 the-raft kernel: [12067.413029] Process swapper (pid: 0, threadinfo ffffffff81a00000, task ffffffff81a0b020)
May  2 14:45:41 the-raft kernel: [12067.417322] Stack:
May  2 14:45:41 the-raft kernel: [12067.421611]  0000000000000000 0000000000000027 0000000000000000 0000000000000027
May  2 14:45:41 the-raft kernel: [12067.425966]  ffffffff81a01e88 00000000814a4e89 ffffe8ffffc00000 ffffe8ffffc00000
May  2 14:45:41 the-raft kernel: [12067.430386]  ffffe8ffffc000d0 ffffffff81a00000 ffffffff81a01ed8 ffffffff814a3bda
May  2 14:45:41 the-raft kernel: [12067.434835] Call Trace:
May  2 14:45:41 the-raft kernel: [12067.439251]  [<ffffffff814a3bda>] cpuidle_idle_call+0xaa/0x1b0
May  2 14:45:41 the-raft kernel: [12067.443726]  [<ffffffff8100a266>] cpu_idle+0xa6/0xf0
May  2 14:45:41 the-raft kernel: [12067.448175]  [<ffffffff815a9205>] rest_init+0x75/0x80
May  2 14:45:41 the-raft kernel: [12067.452639]  [<ffffffff81acac8b>] start_kernel+0x3f5/0x400
May  2 14:45:41 the-raft kernel: [12067.457093]  [<ffffffff81aca388>] x86_64_start_reservations+0x132/0x136
May  2 14:45:41 the-raft kernel: [12067.461610]  [<ffffffff81aca253>] ? zap_identity_mappings+0x3e/0x41
May  2 14:45:41 the-raft kernel: [12067.466093]  [<ffffffff81aca458>] x86_64_start_kernel+0xcc/0xdb
May  2 14:45:41 the-raft kernel: [12067.470604] Code: 29 e8 48 89 c7 e8 07 51 d3 ff 4c 69 e0 40 42 0f 00 48 89 45 b0 48 89 55 b8 48 89 45 c0 48 89 55 c8 49 01 d4 fb 66 0f 1f 44 00 00 <85> 1d e0 66 72 00 75 0e 48 8d 75 dc bf 05 00 00 00 e8 10 03 d6 
May  2 14:45:41 the-raft kernel: [12067.480800] Call Trace:
May  2 14:45:41 the-raft kernel: [12067.485709]  [<ffffffff814a3bda>] cpuidle_idle_call+0xaa/0x1b0
May  2 14:45:41 the-raft kernel: [12067.490681]  [<ffffffff8100a266>] cpu_idle+0xa6/0xf0
May  2 14:45:41 the-raft kernel: [12067.495419]  [<ffffffff815a9205>] rest_init+0x75/0x80
May  2 14:45:41 the-raft kernel: [12067.499875]  [<ffffffff81acac8b>] start_kernel+0x3f5/0x400
May  2 14:45:41 the-raft kernel: [12067.504329]  [<ffffffff81aca388>] x86_64_start_reservations+0x132/0x136
May  2 14:45:41 the-raft kernel: [12067.508752]  [<ffffffff81aca253>] ? zap_identity_mappings+0x3e/0x41
May  2 14:45:41 the-raft kernel: [12067.513172]  [<ffffffff81aca458>] x86_64_start_kernel+0xcc/0xdb
May  2 14:45:46 the-raft kernel: [12072.538682] ===>rtl819x_watchdog_wqcallback(): AP is power off,chan:1, connect another one
May  2 14:45:46 the-raft kernel: [12072.545473] ===========>RemovePeerTS,00:24:b2:16:54:8c
May  2 14:45:46 the-raft kernel: [12072.552022] ====>remove Tx_TS_admin_list
May  2 14:45:46 the-raft kernel: [12072.558386] ====>remove Tx_TS_admin_list
May  2 14:45:46 the-raft kernel: [12072.564454] ====>remove Tx_TS_admin_list
May  2 14:45:46 the-raft kernel: [12072.570502] ===>rtl8192se_link_change():ieee->iw_mode is 2
May  2 14:45:46 the-raft kernel: [12072.576409] notify_wx_assoc_event(): Tell user space disconnected
May  2 14:45:46 the-raft wpa_supplicant[912]: CTRL-EVENT-DISCONNECTED bssid=00:24:b2:16:54:8c reason=0
May  2 14:45:46 the-raft NetworkManager[758]: <info> (wlan1): supplicant connection state:  completed -> disconnected
```

---

### Post by isantop on 2011-05-05
This sounds like a botched upgrade to me. Can you try running from a LiveUSB for a while and see if the problem recurs there?

---

### Post by distortedstar on 2011-05-05
Thanks for reply. No crashes yesterday! Wondering if it was bug squashed in the last round of updates? If it happens again I will definately try to run from a live usb.

---

