---
title: "CPU Lockup related to xhci/DMA"
date: 2023-03-30
forum: Ubuntu Development Version
---

### Post by the-domino-engineer on 2023-03-30
CPU lockup problems have been encountered on a number of computers running kernel 5.15 or later, but this problem could've been introduced in an earlier version.  Three of these systems are running a light weight version of Ubuntu.  The kernels that have been tested are 4.19, 5.15, 5.18, 5.19, 6.0, and 6.1.  The basic setup that's running and causing problems  is a program that starts several (4+) distinct processes and communicates with different ACM/USB concurrently.  This problem can be encountered a few minutes after starting this program  up to about a week later, but it generally happens after ~1-3 days.  When the lock up occurs, if there are the same number or fewer CPU cores than the running number of running processes doing ACM/USB device communication, nothing else will execute due to all of the CPU cores being locked up until the watchdog frees things up.  The longest lockup that has been encountered was over 20 minutes!  The computers that this problem has been tested and verified to be present on are the NUC7i5BNK, the ASRock NUC BOX-1260P, and the LattePanda Delta 3.  Although, this problem appears to be system agnostic; if kernel version ~5.15 or later is being used, it'll likely happen if this program is setup and run on any system when enough known ACM/USB devices are connected to it and communicated with concurrently from different processes.  The main reason "this program" is being stated in a broad sense is because multiple different setups fitting that description have been tested trying to get around encountered problems in various clever ways and this problem has persisted regardless of what's been done.

Here's a short snippet from the LattePanda Delta 3's syslog:
```

Mar 21 15:35:59 LattePanda kernel: [437064.977491] NMI watchdog: Watchdog detected hard LOCKUP on cpu 1
Mar 21 15:35:59 LattePanda kernel: [437064.977496] Modules linked in: tls binfmt_misc snd_sof_pci_intel_icl snd_sof_intel_hda_common soundwire_intel soundwire_generic_allocation soundwire_cadence intel_rapl_msr snd_sof_intel_hda mei_hdcp snd_sof_pci snd_sof_xtensa_dsp snd_sof snd_soc_hdac_hda snd_hda_ext_core snd_soc_acpi_intel_match snd_soc_acpi intel_rapl_common soundwire_bus x86_pkg_temp_thermal intel_powerclamp snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_codec_generic coretemp ledtrig_audio snd_soc_core nls_iso8859_1 snd_compress ac97_bus kvm_intel snd_pcm_dmaengine snd_hda_intel snd_intel_dspcfg kvm snd_intel_sdw_acpi intel_cstate snd_hda_codec snd_hda_core btusb rtsx_usb_ms btrtl btbcm snd_hwdep btintel bluetooth memstick iwlmvm snd_pcm ecdh_generic snd_timer ecc wmi_bmof mac80211 snd libarc4 soundcore 8250_dw mei_me mei iwlwifi ftdi_sio pl2303 cp210x cdc_acm usbserial cfg80211 goodix acpi_tad mac_hid acpi_pad dm_multipath scsi_dh_rdac scsi_dh_emc scsi_dh_alua sch_fq_codel ramoops efi_pstore reed_solomon
Mar 21 15:35:59 LattePanda kernel: [437064.977544]  pstore_blk pstore_zone ip_tables x_tables autofs4 btrfs blake2b_generic xor zstd_compress raid6_pq libcrc32c rtsx_usb_sdmmc rtsx_usb mmc_block i915 ttm drm_kms_helper syscopyarea sysfillrect igb sysimgblt fb_sys_fops spi_pxa2xx_platform cec dca crct10dif_pclmul rc_core dw_dmac i2c_i801 crc32_pclmul dw_dmac_core ghash_clmulni_intel aesni_intel crypto_simd cryptd i2c_smbus i2c_algo_bit sdhci_pci ahci cqhci drm libahci intel_lpss_pci sdhci intel_lpss xhci_pci idma64 xhci_pci_renesas wmi video pinctrl_jasperlake
Mar 21 15:35:59 LattePanda kernel: [437064.977572] CPU: 1 PID: 0 Comm: swapper/1 Tainted: G             L    5.15.0-67-lowlatency #74-Ubuntu
Mar 21 15:35:59 LattePanda kernel: [437064.977575] Hardware name: LattePanda LattePanda 3 Delta/LattePanda 3 Delta, BIOS LP-BS-7-S70JR120-CN51G-D 08/15/2022
Mar 21 15:35:59 LattePanda kernel: [437064.977576] RIP: 0010:native_queued_spin_lock_slowpath.part.0+0x4f/0x200
Mar 21 15:35:59 LattePanda kernel: [437064.977584] Code: 0f ba 2b 08 0f 92 c2 8b 03 0f b6 d2 c1 e2 08 30 e4 09 d0 a9 00 01 ff ff 0f 85 2a 01 00 00 85 c0 74 0e 8b 03 84 c0 74 08 f3 90 <8b> 03 84 c0 75 f8 b8 01 00 00 00 66 89 03 5b 41 5c 41 5d 41 5e 41
Mar 21 15:35:59 LattePanda kernel: [437064.977586] RSP: 0018:ffffb42d4007ce80 EFLAGS: 00000002
Mar 21 15:35:59 LattePanda kernel: [437064.977587] RAX: 00000000000c0101 RBX: ffff9737c026c2ac RCX: 0000000000000017
Mar 21 15:35:59 LattePanda kernel: [437064.977589] RDX: 0000000000000000 RSI: 0000000000000000 RDI: ffff9737c026c2ac
Mar 21 15:35:59 LattePanda kernel: [437064.977590] RBP: ffffb42d4007cea8 R08: 0000000000000000 R09: 0000000000000000
Mar 21 15:35:59 LattePanda kernel: [437064.977591] R10: 0000000000000000 R11: ffffb42d4007cff8 R12: ffff9737c026c000
Mar 21 15:35:59 LattePanda kernel: [437064.977592] R13: ffff9737c026c260 R14: 0000000000000079 R15: ffff9737c026c2ac
Mar 21 15:35:59 LattePanda kernel: [437064.977594] FS:  0000000000000000(0000) GS:ffff973938080000(0000) knlGS:0000000000000000
Mar 21 15:35:59 LattePanda kernel: [437064.977595] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Mar 21 15:35:59 LattePanda kernel: [437064.977596] CR2: 000000c000586000 CR3: 0000000266810000 CR4: 0000000000350ee0
Mar 21 15:35:59 LattePanda kernel: [437064.977598] Call Trace:
Mar 21 15:35:59 LattePanda kernel: [437064.977600]  <IRQ>
Mar 21 15:35:59 LattePanda kernel: [437064.977603]  native_queued_spin_lock_slowpath+0x2c/0x40
Mar 21 15:35:59 LattePanda kernel: [437064.977606]  _raw_spin_lock+0x29/0x40
Mar 21 15:35:59 LattePanda kernel: [437064.977610]  xhci_irq+0x40/0x1a0
Mar 21 15:35:59 LattePanda kernel: [437064.977612]  xhci_msi_irq+0x11/0x20
Mar 21 15:35:59 LattePanda kernel: [437064.977614]  __handle_irq_event_percpu+0x3f/0x1a0
Mar 21 15:35:59 LattePanda kernel: [437064.977617]  handle_irq_event+0x57/0xb0
Mar 21 15:35:59 LattePanda kernel: [437064.977620]  handle_edge_irq+0x8c/0x240
Mar 21 15:35:59 LattePanda kernel: [437064.977622]  __common_interrupt+0x4f/0xe0
Mar 21 15:35:59 LattePanda kernel: [437064.977625]  common_interrupt+0x89/0xa0
Mar 21 15:35:59 LattePanda kernel: [437064.977627]  </IRQ>
Mar 21 15:35:59 LattePanda kernel: [437064.977628]  <TASK>
Mar 21 15:35:59 LattePanda kernel: [437064.977628]  asm_common_interrupt+0x27/0x40
Mar 21 15:35:59 LattePanda kernel: [437064.977630] RIP: 0010:cpuidle_enter_state+0xd9/0x640
Mar 21 15:35:59 LattePanda kernel: [437064.977634] Code: 3d 84 b6 98 69 e8 47 c1 67 ff 49 89 c7 0f 1f 44 00 00 31 ff e8 b8 ce 67 ff 80 7d d0 00 0f 85 e2 01 00 00 fb 66 0f 1f 44 00 00 <45> 85 f6 0f 88 77 01 00 00 4d 63 ee 49 83 fd 09 0f 87 31 04 00 00
Mar 21 15:35:59 LattePanda kernel: [437064.977635] RSP: 0018:ffffb42d40123e28 EFLAGS: 00000246
Mar 21 15:35:59 LattePanda kernel: [437064.977637] RAX: ffff9739380b0d40 RBX: ffff9739380bc700 RCX: 000000000000001f
Mar 21 15:35:59 LattePanda kernel: [437064.977638] RDX: 0000000000000000 RSI: 0000000000000000 RDI: 0000000000000000
Mar 21 15:35:59 LattePanda kernel: [437064.977639] RBP: ffffb42d40123e78 R08: 00018d7e6ec10948 R09: 0000000000022e80
Mar 21 15:35:59 LattePanda kernel: [437064.977640] R10: 0000000000000001 R11: fffffffffffffffe R12: ffffffff97ce1e20
Mar 21 15:35:59 LattePanda kernel: [437064.977640] R13: 0000000000000003 R14: 0000000000000003 R15: 00018d7e6ec10948
Mar 21 15:35:59 LattePanda kernel: [437064.977643]  ? cpuidle_enter_state+0xc8/0x640
Mar 21 15:35:59 LattePanda kernel: [437064.977646]  ? tick_nohz_stop_tick+0x16a/0x1f0
Mar 21 15:35:59 LattePanda kernel: [437064.977648]  cpuidle_enter+0x2e/0x50
Mar 21 15:35:59 LattePanda kernel: [437064.977650]  cpuidle_idle_call+0x142/0x1e0
Mar 21 15:35:59 LattePanda kernel: [437064.977653]  do_idle+0x83/0xf0
Mar 21 15:35:59 LattePanda kernel: [437064.977654]  cpu_startup_entry+0x20/0x30
Mar 21 15:35:59 LattePanda kernel: [437064.977656]  start_secondary+0x12a/0x180
Mar 21 15:35:59 LattePanda kernel: [437064.977659]  secondary_startup_64_no_verify+0xc2/0xcb
Mar 21 15:35:59 LattePanda kernel: [437064.977662]  </TASK>
Mar 21 15:35:59 LattePanda kernel: [437065.377567] NMI watchdog: Watchdog detected hard LOCKUP on cpu 2
Mar 21 15:35:59 LattePanda kernel: [437065.377571] Modules linked in: tls binfmt_misc snd_sof_pci_intel_icl snd_sof_intel_hda_common soundwire_intel soundwire_generic_allocation soundwire_cadence intel_rapl_msr snd_sof_intel_hda mei_hdcp snd_sof_pci snd_sof_xtensa_dsp snd_sof snd_soc_hdac_hda snd_hda_ext_core snd_soc_acpi_intel_match snd_soc_acpi intel_rapl_common soundwire_bus x86_pkg_temp_thermal intel_powerclamp snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_codec_generic coretemp ledtrig_audio snd_soc_core nls_iso8859_1 snd_compress ac97_bus kvm_intel snd_pcm_dmaengine snd_hda_intel snd_intel_dspcfg kvm snd_intel_sdw_acpi intel_cstate snd_hda_codec snd_hda_core btusb rtsx_usb_ms btrtl btbcm snd_hwdep btintel bluetooth memstick iwlmvm snd_pcm ecdh_generic snd_timer ecc wmi_bmof mac80211 snd libarc4 soundcore 8250_dw mei_me mei iwlwifi ftdi_sio pl2303 cp210x cdc_acm usbserial cfg80211 goodix acpi_tad mac_hid acpi_pad dm_multipath scsi_dh_rdac scsi_dh_emc scsi_dh_alua sch_fq_codel ramoops efi_pstore reed_solomon
Mar 21 15:35:59 LattePanda kernel: [437065.377616]  pstore_blk pstore_zone ip_tables x_tables autofs4 btrfs blake2b_generic xor zstd_compress raid6_pq libcrc32c rtsx_usb_sdmmc rtsx_usb mmc_block i915 ttm drm_kms_helper syscopyarea sysfillrect igb sysimgblt fb_sys_fops spi_pxa2xx_platform cec dca crct10dif_pclmul rc_core dw_dmac i2c_i801 crc32_pclmul dw_dmac_core ghash_clmulni_intel aesni_intel crypto_simd cryptd i2c_smbus i2c_algo_bit sdhci_pci ahci cqhci drm libahci intel_lpss_pci sdhci intel_lpss xhci_pci idma64 xhci_pci_renesas wmi video pinctrl_jasperlake
Mar 21 15:35:59 LattePanda kernel: [437065.377644] CPU: 2 PID: 22601 Comm: python3.8 Tainted: G             L    5.15.0-67-lowlatency #74-Ubuntu
Mar 21 15:35:59 LattePanda kernel: [437065.377647] Hardware name: LattePanda LattePanda 3 Delta/LattePanda 3 Delta, BIOS LP-BS-7-S70JR120-CN51G-D 08/15/2022
Mar 21 15:35:59 LattePanda kernel: [437065.377649] RIP: 0010:native_queued_spin_lock_slowpath.part.0+0x156/0x200
Mar 21 15:35:59 LattePanda kernel: [437065.377655] Code: 81 c5 c0 1a 03 00 49 81 ff ff 1f 00 00 0f 87 a8 00 00 00 4e 03 2c fd e0 7a 2f 97 4d 89 65 00 41 8b 44 24 08 85 c0 75 0b f3 90 <41> 8b 44 24 08 85 c0 74 f5 49 8b 14 24 48 85 d2 74 1d 0f 0d 0a eb
Mar 21 15:35:59 LattePanda kernel: [437065.377657] RSP: 0018:ffffb42d42527940 EFLAGS: 00000046
Mar 21 15:35:59 LattePanda kernel: [437065.377659] RAX: 0000000000000000 RBX: ffff9737c026c2ac RCX: 0000000000000000
Mar 21 15:35:59 LattePanda kernel: [437065.377660] RDX: 0000000000000004 RSI: 0000000000000002 RDI: ffff9737c026c2ac
Mar 21 15:35:59 LattePanda kernel: [437065.377661] RBP: ffffb42d42527968 R08: 0000000000000c00 R09: ffff9737c026c260
Mar 21 15:35:59 LattePanda kernel: [437065.377662] R10: 0000000000000000 R11: 0000000000000000 R12: ffff973938131ac0
Mar 21 15:35:59 LattePanda kernel: [437065.377663] R13: ffff9739381b1ac0 R14: 00000000000c0000 R15: 0000000000000003
Mar 21 15:35:59 LattePanda kernel: [437065.377664] FS:  00007ff5f88c6640(0000) GS:ffff973938100000(0000) knlGS:0000000000000000
Mar 21 15:35:59 LattePanda kernel: [437065.377665] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Mar 21 15:35:59 LattePanda kernel: [437065.377667] CR2: 000000c000577000 CR3: 000000011e3f4000 CR4: 0000000000350ee0
Mar 21 15:35:59 LattePanda kernel: [437065.377668] Call Trace:
Mar 21 15:35:59 LattePanda kernel: [437065.377670]  <TASK>
Mar 21 15:35:59 LattePanda kernel: [437065.377673]  native_queued_spin_lock_slowpath+0x2c/0x40
Mar 21 15:35:59 LattePanda kernel: [437065.377676]  _raw_spin_lock_irqsave+0x44/0x60
Mar 21 15:35:59 LattePanda kernel: [437065.377680]  xhci_urb_enqueue+0x177/0x4b0
Mar 21 15:35:59 LattePanda kernel: [437065.377683]  usb_hcd_submit_urb+0xa2/0x300
Mar 21 15:35:59 LattePanda kernel: [437065.377685]  usb_submit_urb+0x254/0x6d0
Mar 21 15:35:59 LattePanda kernel: [437065.377687]  usb_start_wait_urb+0x71/0x180
Mar 21 15:35:59 LattePanda kernel: [437065.377689]  usb_control_msg+0xe3/0x150
Mar 21 15:35:59 LattePanda kernel: [437065.377692]  ftdi_get_modem_status+0x90/0x110 [ftdi_sio]
Mar 21 15:35:59 LattePanda kernel: [437065.377696]  ftdi_tx_empty+0x25/0x60 [ftdi_sio]
Mar 21 15:35:59 LattePanda kernel: [437065.377700]  usb_serial_generic_wait_until_sent+0x85/0x110 [usbserial]
Mar 21 15:35:59 LattePanda kernel: [437065.377705]  serial_wait_until_sent+0xa0/0xb0 [usbserial]
Mar 21 15:35:59 LattePanda kernel: [437065.377708]  tty_wait_until_sent+0x13f/0x190
Mar 21 15:35:59 LattePanda kernel: [437065.377712]  tty_port_close_start.part.0+0x10f/0x1f0
Mar 21 15:35:59 LattePanda kernel: [437065.377714]  tty_port_close+0x36/0xb0
Mar 21 15:35:59 LattePanda kernel: [437065.377717]  serial_close+0x2c/0x60 [usbserial]
Mar 21 15:35:59 LattePanda kernel: [437065.377720]  tty_release+0xe6/0x420
Mar 21 15:35:59 LattePanda kernel: [437065.377722]  __fput+0x9c/0x280
Mar 21 15:35:59 LattePanda kernel: [437065.377724]  ____fput+0xe/0x20
Mar 21 15:35:59 LattePanda kernel: [437065.377726]  task_work_run+0x61/0xa0
Mar 21 15:35:59 LattePanda kernel: [437065.377729]  exit_to_user_mode_loop+0x157/0x160
Mar 21 15:35:59 LattePanda kernel: [437065.377731]  exit_to_user_mode_prepare+0xa0/0xb0
Mar 21 15:35:59 LattePanda kernel: [437065.377733]  syscall_exit_to_user_mode+0x27/0x50
Mar 21 15:35:59 LattePanda kernel: [437065.377736]  ? __x64_sys_close+0x11/0x50
Mar 21 15:35:59 LattePanda kernel: [437065.377738]  do_syscall_64+0x69/0xc0
Mar 21 15:35:59 LattePanda kernel: [437065.377740]  ? exit_to_user_mode_prepare+0x37/0xb0
Mar 21 15:35:59 LattePanda kernel: [437065.377742]  ? syscall_exit_to_user_mode+0x27/0x50
Mar 21 15:35:59 LattePanda kernel: [437065.377744]  ? do_syscall_64+0x69/0xc0
Mar 21 15:35:59 LattePanda kernel: [437065.377746]  ? switch_fpu_return+0x4e/0xe0
Mar 21 15:35:59 LattePanda kernel: [437065.377749]  ? exit_to_user_mode_prepare+0x96/0xb0
Mar 21 15:35:59 LattePanda kernel: [437065.377750]  ? syscall_exit_to_user_mode+0x27/0x50
Mar 21 15:35:59 LattePanda kernel: [437065.377752]  ? do_syscall_64+0x69/0xc0
Mar 21 15:35:59 LattePanda kernel: [437065.377754]  ? do_syscall_64+0x69/0xc0
Mar 21 15:35:59 LattePanda kernel: [437065.377755]  entry_SYSCALL_64_after_hwframe+0x61/0xcb
Mar 21 15:35:59 LattePanda kernel: [437065.377757] RIP: 0033:0x7ff60603a13b
Mar 21 15:35:59 LattePanda kernel: [437065.377760] Code: 03 00 00 00 0f 05 48 3d 00 f0 ff ff 77 41 c3 48 83 ec 18 89 7c 24 0c e8 43 b9 f7 ff 8b 7c 24 0c 41 89 c0 b8 03 00 00 00 0f 05 <48> 3d 00 f0 ff ff 77 35 44 89 c7 89 44 24 0c e8 91 b9 f7 ff 8b 44
Mar 21 15:35:59 LattePanda kernel: [437065.377761] RSP: 002b:00007ff5f88c4fd0 EFLAGS: 00000293 ORIG_RAX: 0000000000000003
Mar 21 15:35:59 LattePanda kernel: [437065.377763] RAX: 0000000000000000 RBX: 00007ff605e272c0 RCX: 00007ff60603a13b
Mar 21 15:35:59 LattePanda kernel: [437065.377764] RDX: 0000000000000000 RSI: 0000000000000000 RDI: 0000000000000005
Mar 21 15:35:59 LattePanda kernel: [437065.377764] RBP: 0000000000000005 R08: 0000000000000000 R09: 0000000000000000
Mar 21 15:35:59 LattePanda kernel: [437065.377765] R10: 0000558826edef20 R11: 0000000000000293 R12: 00007ff5f4001280
Mar 21 15:35:59 LattePanda kernel: [437065.377766] R13: 00007ff5fa180d70 R14: 00007ff5fa180d8a R15: 00007ff5fa0d2838
Mar 21 15:35:59 LattePanda kernel: [437065.377768]  </TASK>
Mar 21 15:35:59 LattePanda kernel: [437068.082251] NMI watchdog: Watchdog detected hard LOCKUP on cpu 0
Mar 21 15:35:59 LattePanda kernel: [437068.082255] Modules linked in: tls binfmt_misc snd_sof_pci_intel_icl snd_sof_intel_hda_common soundwire_intel soundwire_generic_allocation soundwire_cadence intel_rapl_msr snd_sof_intel_hda mei_hdcp snd_sof_pci snd_sof_xtensa_dsp snd_sof snd_soc_hdac_hda snd_hda_ext_core snd_soc_acpi_intel_match snd_soc_acpi intel_rapl_common soundwire_bus x86_pkg_temp_thermal intel_powerclamp snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_codec_generic coretemp ledtrig_audio snd_soc_core nls_iso8859_1 snd_compress ac97_bus kvm_intel snd_pcm_dmaengine snd_hda_intel snd_intel_dspcfg kvm snd_intel_sdw_acpi intel_cstate snd_hda_codec snd_hda_core btusb rtsx_usb_ms btrtl btbcm snd_hwdep btintel bluetooth memstick iwlmvm snd_pcm ecdh_generic snd_timer ecc wmi_bmof mac80211 snd libarc4 soundcore 8250_dw mei_me mei iwlwifi ftdi_sio pl2303 cp210x cdc_acm usbserial cfg80211 goodix acpi_tad mac_hid acpi_pad dm_multipath scsi_dh_rdac scsi_dh_emc scsi_dh_alua sch_fq_codel ramoops efi_pstore reed_solomon
Mar 21 15:35:59 LattePanda kernel: [437068.082304]  pstore_blk pstore_zone ip_tables x_tables autofs4 btrfs blake2b_generic xor zstd_compress raid6_pq libcrc32c rtsx_usb_sdmmc rtsx_usb mmc_block i915 ttm drm_kms_helper syscopyarea sysfillrect igb sysimgblt fb_sys_fops spi_pxa2xx_platform cec dca crct10dif_pclmul rc_core dw_dmac i2c_i801 crc32_pclmul dw_dmac_core ghash_clmulni_intel aesni_intel crypto_simd cryptd i2c_smbus i2c_algo_bit sdhci_pci ahci cqhci drm libahci intel_lpss_pci sdhci intel_lpss xhci_pci idma64 xhci_pci_renesas wmi video pinctrl_jasperlake
Mar 21 15:35:59 LattePanda kernel: [437068.082333] CPU: 0 PID: 22650 Comm: python3.8 Tainted: G             L    5.15.0-67-lowlatency #74-Ubuntu
Mar 21 15:35:59 LattePanda kernel: [437068.082337] Hardware name: LattePanda LattePanda 3 Delta/LattePanda 3 Delta, BIOS LP-BS-7-S70JR120-CN51G-D 08/15/2022
Mar 21 15:35:59 LattePanda kernel: [437068.082338] RIP: 0010:dma_pool_alloc+0x57/0x220
Mar 21 15:35:59 LattePanda kernel: [437068.082345] Code: 8d 7b 10 4c 89 ff e8 78 b7 a8 00 4c 8b 23 48 89 c6 4c 39 e3 74 6c 48 8b 4b 28 eb 09 4d 8b 24 24 4c 39 e3 74 5d 41 8b 54 24 24 <48> 39 ca 73 ed 4d 8b 74 24 10 41 83 44 24 20 01 4c 89 ff 49 01 d6
Mar 21 15:35:59 LattePanda kernel: [437068.082347] RSP: 0018:ffffb42d409976b0 EFLAGS: 00000083
Mar 21 15:35:59 LattePanda kernel: [437068.082348] RAX: 0000000000000046 RBX: ffff9737d85d9a80 RCX: 0000000000001000
Mar 21 15:35:59 LattePanda kernel: [437068.082350] RDX: 0000000000001000 RSI: 0000000000000046 RDI: ffff9737d85d9a90
Mar 21 15:35:59 LattePanda kernel: [437068.082351] RBP: ffffb42d409976e0 R08: 0000000000000040 R09: ffff9738bfc1d780
Mar 21 15:35:59 LattePanda kernel: [437068.082352] R10: 0000000000000093 R11: ffff9739380376d0 R12: ffff9738c8904940
Mar 21 15:35:59 LattePanda kernel: [437068.082353] R13: 0000000000000b20 R14: ffff9737c10670d0 R15: ffff9737d85d9a90
Mar 21 15:35:59 LattePanda kernel: [437068.082354] FS:  00007f53511c4640(0000) GS:ffff973938000000(0000) knlGS:0000000000000000
Mar 21 15:35:59 LattePanda kernel: [437068.082356] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Mar 21 15:35:59 LattePanda kernel: [437068.082357] CR2: 000000c000589000 CR3: 000000010afb2000 CR4: 0000000000350ef0
Mar 21 15:35:59 LattePanda kernel: [437068.082358] Call Trace:
Mar 21 15:35:59 LattePanda kernel: [437068.082360]  <TASK>
Mar 21 15:35:59 LattePanda kernel: [437068.082364]  xhci_segment_alloc+0x9e/0x190
Mar 21 15:35:59 LattePanda kernel: [437068.082368]  xhci_alloc_segments_for_ring+0xde/0x1c0
Mar 21 15:35:59 LattePanda kernel: [437068.082371]  xhci_ring_expansion+0x67/0x360
Mar 21 15:35:59 LattePanda kernel: [437068.082374]  prepare_ring+0x66/0x1b0
Mar 21 15:35:59 LattePanda kernel: [437068.082375]  prepare_transfer+0x6c/0x150
Mar 21 15:35:59 LattePanda kernel: [437068.082377]  xhci_queue_bulk_tx+0x10a/0x690
Mar 21 15:35:59 LattePanda kernel: [437068.082380]  xhci_urb_enqueue+0x374/0x4b0
Mar 21 15:35:59 LattePanda kernel: [437068.082382]  usb_hcd_submit_urb+0xa2/0x300
Mar 21 15:35:59 LattePanda kernel: [437068.082384]  usb_submit_urb+0x254/0x6d0
Mar 21 15:35:59 LattePanda kernel: [437068.082387]  usb_serial_generic_submit_read_urb+0x47/0xc0 [usbserial]
Mar 21 15:35:59 LattePanda kernel: [437068.082393]  usb_serial_generic_open+0x4f/0xa0 [usbserial]
Mar 21 15:35:59 LattePanda kernel: [437068.082397]  cp210x_open+0x51/0x90 [cp210x]
Mar 21 15:35:59 LattePanda kernel: [437068.082401]  serial_port_activate+0x68/0xa0 [usbserial]
Mar 21 15:35:59 LattePanda kernel: [437068.082404]  tty_port_open+0x87/0xd0
Mar 21 15:35:59 LattePanda kernel: [437068.082408]  ? tty_ldisc_lock+0x50/0x70
Mar 21 15:35:59 LattePanda kernel: [437068.082411]  serial_open+0x2c/0x60 [usbserial]
Mar 21 15:35:59 LattePanda kernel: [437068.082414]  tty_open+0x15b/0x6f0
Mar 21 15:35:59 LattePanda kernel: [437068.082416]  chrdev_open+0xc4/0x240
Mar 21 15:35:59 LattePanda kernel: [437068.082419]  ? fsnotify_perm.part.0+0x6e/0x160
Mar 21 15:35:59 LattePanda kernel: [437068.082422]  ? cdev_device_add+0xa0/0xa0
Mar 21 15:35:59 LattePanda kernel: [437068.082424]  do_dentry_open+0x167/0x3f0
Mar 21 15:35:59 LattePanda kernel: [437068.082427]  vfs_open+0x2d/0x40
Mar 21 15:35:59 LattePanda kernel: [437068.082429]  do_open+0x20d/0x470
Mar 21 15:35:59 LattePanda kernel: [437068.082431]  path_openat+0x112/0x2b0
Mar 21 15:35:59 LattePanda kernel: [437068.082433]  ? try_to_wake_up+0x214/0x610
Mar 21 15:35:59 LattePanda kernel: [437068.082436]  ? ttwu_queue_wakelist+0x131/0x1c0
Mar 21 15:35:59 LattePanda kernel: [437068.082438]  do_filp_open+0xb2/0x160
Mar 21 15:35:59 LattePanda kernel: [437068.082441]  ? __check_object_size+0x1d/0x30
Mar 21 15:35:59 LattePanda kernel: [437068.082443]  do_sys_openat2+0x9f/0x160
Mar 21 15:35:59 LattePanda kernel: [437068.082445]  __x64_sys_openat+0x55/0x90
Mar 21 15:35:59 LattePanda kernel: [437068.082448]  do_syscall_64+0x59/0xc0
Mar 21 15:35:59 LattePanda kernel: [437068.082450]  ? do_syscall_64+0x69/0xc0
Mar 21 15:35:59 LattePanda kernel: [437068.082452]  ? exit_to_user_mode_prepare+0x96/0xb0
Mar 21 15:35:59 LattePanda kernel: [437068.082454]  ? syscall_exit_to_user_mode+0x27/0x50
Mar 21 15:35:59 LattePanda kernel: [437068.082456]  ? do_syscall_64+0x69/0xc0
Mar 21 15:35:59 LattePanda kernel: [437068.082458]  ? do_syscall_64+0x69/0xc0
Mar 21 15:35:59 LattePanda kernel: [437068.082459]  ? exit_to_user_mode_prepare+0x96/0xb0
Mar 21 15:35:59 LattePanda kernel: [437068.082461]  ? irqentry_exit_to_user_mode+0x9/0x20
Mar 21 15:35:59 LattePanda kernel: [437068.082463]  ? irqentry_exit+0x3b/0x50
Mar 21 15:35:59 LattePanda kernel: [437068.082465]  ? sysvec_reschedule_ipi+0x7b/0x120
Mar 21 15:35:59 LattePanda kernel: [437068.082467]  entry_SYSCALL_64_after_hwframe+0x61/0xcb
Mar 21 15:35:59 LattePanda kernel: [437068.082469] RIP: 0033:0x7f535f938764
Mar 21 15:35:59 LattePanda kernel: [437068.082473] Code: 24 20 eb 8f 66 90 44 89 54 24 0c e8 26 c3 f7 ff 44 8b 54 24 0c 44 89 e2 48 89 ee 41 89 c0 bf 9c ff ff ff b8 01 01 00 00 0f 05 <48> 3d 00 f0 ff ff 77 34 44 89 c7 89 44 24 0c e8 68 c3 f7 ff 8b 44
Mar 21 15:35:59 LattePanda kernel: [437068.082474] RSP: 002b:00007f53511c2ec0 EFLAGS: 00000293 ORIG_RAX: 0000000000000101
Mar 21 15:35:59 LattePanda kernel: [437068.082476] RAX: ffffffffffffffda RBX: 00000000000001ff RCX: 00007f535f938764
Mar 21 15:35:59 LattePanda kernel: [437068.082477] RDX: 0000000000080902 RSI: 00007f53539cae30 RDI: 00000000ffffff9c
Mar 21 15:35:59 LattePanda kernel: [437068.082478] RBP: 00007f53539cae30 R08: 0000000000000000 R09: 00005609781552c0
Mar 21 15:35:59 LattePanda kernel: [437068.082479] R10: 0000000000000000 R11: 0000000000000293 R12: 0000000000080902
Mar 21 15:35:59 LattePanda kernel: [437068.082480] R13: 0000560978048016 R14: 00007f534c001890 R15: 00007f5353a30cf0
Mar 21 15:35:59 LattePanda kernel: [437068.082482]  </TASK>
Mar 21 15:35:59 LattePanda kernel: [437793.271716] rcu: INFO: rcu_preempt detected stalls on CPUs/tasks:
Mar 21 15:35:59 LattePanda kernel: [437793.271719] rcu:     0-...!: (1 ticks this GP) idle=073/1/0x4000000000000000 softirq=150447223/150447223 fqs=1 
Mar 21 15:35:59 LattePanda kernel: [437793.271727] rcu:     1-...!: (0 ticks this GP) idle=ae1/1/0x4000000000000004 softirq=151307169/151307169 fqs=1 
Mar 21 15:35:59 LattePanda kernel: [437793.271732]     (detected by 2, t=744150 jiffies, g=247367821, q=14)
Mar 21 15:35:59 LattePanda kernel: [437793.271735] Sending NMI from CPU 2 to CPUs 0:
Mar 21 15:35:59 LattePanda kernel: [437793.271741] NMI backtrace for cpu 0
Mar 21 15:35:59 LattePanda kernel: [437793.271743] CPU: 0 PID: 22650 Comm: python3.8 Tainted: G             L    5.15.0-67-lowlatency #74-Ubuntu
Mar 21 15:35:59 LattePanda kernel: [437793.271745] Hardware name: LattePanda LattePanda 3 Delta/LattePanda 3 Delta, BIOS LP-BS-7-S70JR120-CN51G-D 08/15/2022
Mar 21 15:35:59 LattePanda kernel: [437793.271746] RIP: 0010:_raw_spin_lock_irqsave+0x2e/0x60
Mar 21 15:35:59 LattePanda kernel: [437793.271752] Code: 00 55 48 89 e5 41 54 9c 58 0f 1f 44 00 00 49 89 c4 fa 66 0f 1f 44 00 00 65 ff 05 ad 86 65 69 31 c0 ba 01 00 00 00 f0 0f b1 17 <75> 0d 4c 89 e0 4c 8b 65 f8 c9 c3 cc cc cc cc 89 c6 e8 4c 3a 37 ff
Mar 21 15:35:59 LattePanda kernel: [437793.271754] RSP: 0018:ffffb42d40003e78 EFLAGS: 00000046
Mar 21 15:35:59 LattePanda kernel: [437793.271755] RAX: 0000000000000000 RBX: ffff9737c0d14e80 RCX: 0000000000000000
Mar 21 15:35:59 LattePanda kernel: [437793.271757] RDX: 0000000000000001 RSI: 0000000000000003 RDI: ffff9737c0d15afc
Mar 21 15:35:59 LattePanda kernel: [437793.271758] RBP: ffffb42d40003e80 R08: ffff9737c0d14e80 R09: 0000000000000000
Mar 21 15:35:59 LattePanda kernel: [437793.271759] R10: 0000000000000004 R11: ffffffffe4de7fef R12: 0000000000000083
Mar 21 15:35:59 LattePanda kernel: [437793.271759] R13: ffff973938022e80 R14: ffff9737c0d15afc R15: 0000000000000003
Mar 21 15:35:59 LattePanda kernel: [437793.271760] FS:  00007f53511c4640(0000) GS:ffff973938000000(0000) knlGS:0000000000000000
Mar 21 15:35:59 LattePanda kernel: [437793.271762] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Mar 21 15:35:59 LattePanda kernel: [437793.271763] CR2: 000000c000589000 CR3: 000000010afb2000 CR4: 0000000000350ef0
Mar 21 15:35:59 LattePanda kernel: [437793.271765] Call Trace:
Mar 21 15:35:59 LattePanda kernel: [437793.271766]  <IRQ>
Mar 21 15:35:59 LattePanda kernel: [437793.271768]  try_to_wake_up+0x56/0x610
Mar 21 15:35:59 LattePanda kernel: [437793.271773]  ? ktime_get+0x43/0xc0
Mar 21 15:35:59 LattePanda kernel: [437793.271775]  ? __hrtimer_init+0x110/0x110
Mar 21 15:35:59 LattePanda kernel: [437793.271778]  wake_up_process+0x15/0x20
Mar 21 15:35:59 LattePanda kernel: [437793.271780]  hrtimer_wakeup+0x22/0x40
Mar 21 15:35:59 LattePanda kernel: [437793.271781]  __hrtimer_run_queues+0x106/0x260
Mar 21 15:35:59 LattePanda kernel: [437793.271784]  hrtimer_interrupt+0x101/0x220
Mar 21 15:35:59 LattePanda kernel: [437793.271786]  __sysvec_apic_timer_interrupt+0x61/0x110
Mar 21 15:35:59 LattePanda kernel: [437793.271789]  sysvec_apic_timer_interrupt+0x7b/0x90
Mar 21 15:35:59 LattePanda kernel: [437793.271792]  </IRQ>
Mar 21 15:35:59 LattePanda kernel: [437793.271792]  <TASK>
Mar 21 15:35:59 LattePanda kernel: [437793.271793]  asm_sysvec_apic_timer_interrupt+0x1b/0x20
Mar 21 15:35:59 LattePanda kernel: [437793.271795] RIP: 0010:_raw_spin_unlock_irqrestore+0x2e/0x40
Mar 21 15:35:59 LattePanda kernel: [437793.271797] Code: 00 55 48 89 e5 c6 07 00 0f 1f 40 00 f7 c6 00 02 00 00 75 0f 65 ff 0d 51 88 65 69 74 0f 5d c3 cc cc cc cc fb 66 0f 1f 44 00 00 <eb> e8 e8 b8 ea 23 ff 5d c3 cc cc cc cc 0f 1f 44 00 00 0f 1f 44 00
Mar 21 15:35:59 LattePanda kernel: [437793.271798] RSP: 0018:ffffb42d40997928 EFLAGS: 00000206
Mar 21 15:35:59 LattePanda kernel: [437793.271800] RAX: 0000000000000000 RBX: ffff9737c026c000 RCX: 0000000000000000
Mar 21 15:35:59 LattePanda kernel: [437793.271800] RDX: 0000000000000000 RSI: 0000000000000202 RDI: ffff9737c026c2ac
Mar 21 15:35:59 LattePanda kernel: [437793.271801] RBP: ffffb42d40997928 R08: ffff9737c026c260 R09: 0000000000000000
Mar 21 15:35:59 LattePanda kernel: [437793.271802] R10: 0000000000000424 R11: 0000000000000100 R12: 0000000000000202
Mar 21 15:35:59 LattePanda kernel: [437793.271803] R13: ffff9737c3cab180 R14: ffff9737c026c2ac R15: ffff9737c43e8380
Mar 21 15:35:59 LattePanda kernel: [437793.271805]  xhci_urb_enqueue+0x215/0x4b0
Mar 21 15:35:59 LattePanda kernel: [437793.271809]  usb_hcd_submit_urb+0xa2/0x300
Mar 21 15:35:59 LattePanda kernel: [437793.271811]  usb_submit_urb+0x254/0x6d0
Mar 21 15:35:59 LattePanda kernel: [437793.271814]  usb_serial_generic_submit_read_urb+0x47/0xc0 [usbserial]
Mar 21 15:35:59 LattePanda kernel: [437793.271820]  usb_serial_generic_open+0x4f/0xa0 [usbserial]
Mar 21 15:35:59 LattePanda kernel: [437793.271824]  cp210x_open+0x51/0x90 [cp210x]
Mar 21 15:35:59 LattePanda kernel: [437793.271828]  serial_port_activate+0x68/0xa0 [usbserial]
Mar 21 15:35:59 LattePanda kernel: [437793.271831]  tty_port_open+0x87/0xd0
Mar 21 15:35:59 LattePanda kernel: [437793.271834]  ? tty_ldisc_lock+0x50/0x70
Mar 21 15:35:59 LattePanda kernel: [437793.271837]  serial_open+0x2c/0x60 [usbserial]
Mar 21 15:35:59 LattePanda kernel: [437793.271840]  tty_open+0x15b/0x6f0
Mar 21 15:35:59 LattePanda kernel: [437793.271842]  chrdev_open+0xc4/0x240
Mar 21 15:35:59 LattePanda kernel: [437793.271845]  ? fsnotify_perm.part.0+0x6e/0x160
Mar 21 15:35:59 LattePanda kernel: [437793.271849]  ? cdev_device_add+0xa0/0xa0
Mar 21 15:35:59 LattePanda kernel: [437793.271851]  do_dentry_open+0x167/0x3f0
Mar 21 15:35:59 LattePanda kernel: [437793.271854]  vfs_open+0x2d/0x40
Mar 21 15:35:59 LattePanda kernel: [437793.271856]  do_open+0x20d/0x470
Mar 21 15:35:59 LattePanda kernel: [437793.271858]  path_openat+0x112/0x2b0
Mar 21 15:35:59 LattePanda kernel: [437793.271860]  ? try_to_wake_up+0x214/0x610
Mar 21 15:35:59 LattePanda kernel: [437793.271862]  ? ttwu_queue_wakelist+0x131/0x1c0
Mar 21 15:35:59 LattePanda kernel: [437793.271864]  do_filp_open+0xb2/0x160
Mar 21 15:35:59 LattePanda kernel: [437793.271867]  ? __check_object_size+0x1d/0x30
Mar 21 15:35:59 LattePanda kernel: [437793.271869]  do_sys_openat2+0x9f/0x160
Mar 21 15:35:59 LattePanda kernel: [437793.271872]  __x64_sys_openat+0x55/0x90
Mar 21 15:35:59 LattePanda kernel: [437793.271874]  do_syscall_64+0x59/0xc0
Mar 21 15:35:59 LattePanda kernel: [437793.271876]  ? do_syscall_64+0x69/0xc0
Mar 21 15:35:59 LattePanda kernel: [437793.271877]  ? exit_to_user_mode_prepare+0x96/0xb0
Mar 21 15:35:59 LattePanda kernel: [437793.271880]  ? syscall_exit_to_user_mode+0x27/0x50
Mar 21 15:35:59 LattePanda kernel: [437793.271882]  ? do_syscall_64+0x69/0xc0
Mar 21 15:35:59 LattePanda kernel: [437793.271883]  ? do_syscall_64+0x69/0xc0
Mar 21 15:35:59 LattePanda kernel: [437793.271884]  ? exit_to_user_mode_prepare+0x96/0xb0
Mar 21 15:35:59 LattePanda kernel: [437793.271886]  ? irqentry_exit_to_user_mode+0x9/0x20
Mar 21 15:35:59 LattePanda kernel: [437793.271888]  ? irqentry_exit+0x3b/0x50
Mar 21 15:35:59 LattePanda kernel: [437793.271890]  ? sysvec_reschedule_ipi+0x7b/0x120
Mar 21 15:35:59 LattePanda kernel: [437793.271892]  entry_SYSCALL_64_after_hwframe+0x61/0xcb
Mar 21 15:35:59 LattePanda kernel: [437793.271894] RIP: 0033:0x7f535f938764
Mar 21 15:35:59 LattePanda kernel: [437793.271896] Code: 24 20 eb 8f 66 90 44 89 54 24 0c e8 26 c3 f7 ff 44 8b 54 24 0c 44 89 e2 48 89 ee 41 89 c0 bf 9c ff ff ff b8 01 01 00 00 0f 05 <48> 3d 00 f0 ff ff 77 34 44 89 c7 89 44 24 0c e8 68 c3 f7 ff 8b 44
Mar 21 15:35:59 LattePanda kernel: [437793.271897] RSP: 002b:00007f53511c2ec0 EFLAGS: 00000293 ORIG_RAX: 0000000000000101
Mar 21 15:35:59 LattePanda kernel: [437793.271899] RAX: ffffffffffffffda RBX: 00000000000001ff RCX: 00007f535f938764
Mar 21 15:35:59 LattePanda kernel: [437793.271900] RDX: 0000000000080902 RSI: 00007f53539cae30 RDI: 00000000ffffff9c
Mar 21 15:35:59 LattePanda kernel: [437793.271901] RBP: 00007f53539cae30 R08: 0000000000000000 R09: 00005609781552c0
Mar 21 15:35:59 LattePanda kernel: [437793.271902] R10: 0000000000000000 R11: 0000000000000293 R12: 0000000000080902
Mar 21 15:35:59 LattePanda kernel: [437793.271903] R13: 0000560978048016 R14: 00007f534c001890 R15: 00007f5353a30cf0
Mar 21 15:35:59 LattePanda kernel: [437793.271904]  </TASK>
Mar 21 15:35:59 LattePanda kernel: [437793.272738] Sending NMI from CPU 2 to CPUs 1:
Mar 21 15:35:59 LattePanda kernel: [437793.272749] NMI backtrace for cpu 1
Mar 21 15:35:59 LattePanda kernel: [437793.272751] CPU: 1 PID: 671 Comm: rs:main Q:Reg Tainted: G             L    5.15.0-67-lowlatency #74-Ubuntu
Mar 21 15:35:59 LattePanda kernel: [437793.272753] Hardware name: LattePanda LattePanda 3 Delta/LattePanda 3 Delta, BIOS LP-BS-7-S70JR120-CN51G-D 08/15/2022
Mar 21 15:35:59 LattePanda kernel: [437793.272754] RIP: 0010:crypto_shash_update+0x9/0x30
Mar 21 15:35:59 LattePanda kernel: [437793.272759] Code: da ff d0 0f 1f 00 41 89 c6 eb be 0f 0b 41 be ea ff ff ff eb b4 e8 07 c8 7e 00 0f 1f 80 00 00 00 00 0f 1f 44 00 00 48 8b 07 55 <48> 8b 40 18 48 89 e5 85 70 2c 75 0f 48 8b 40 a8 ff d0 0f 1f 00 5d
Mar 21 15:35:59 LattePanda kernel: [437793.272760] RSP: 0018:ffffb42d40bd79d0 EFLAGS: 00000246
Mar 21 15:35:59 LattePanda kernel: [437793.272762] RAX: ffff9737c3154240 RBX: ffff9739380f3900 RCX: ffff9737c3154240
Mar 21 15:35:59 LattePanda kernel: [437793.272763] RDX: 0000000000000002 RSI: ffffb42d40bd79e6 RDI: ffffb42d40bd79e8
Mar 21 15:35:59 LattePanda kernel: [437793.272764] RBP: ffffb42d40bd7a20 R08: 0000000000000082 R09: 0000000000000000
Mar 21 15:35:59 LattePanda kernel: [437793.272765] R10: ffff9737c50fc800 R11: ffff9738e05abcd0 R12: ffff9738e05abcd0
Mar 21 15:35:59 LattePanda kernel: [437793.272765] R13: ffff9738e05abbb8 R14: ffff9737c50f3000 R15: ffff9738e05abf50
Mar 21 15:35:59 LattePanda kernel: [437793.272767] FS:  00007f94d97e2640(0000) GS:ffff973938080000(0000) knlGS:0000000000000000
Mar 21 15:35:59 LattePanda kernel: [437793.272768] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Mar 21 15:35:59 LattePanda kernel: [437793.272769] CR2: 00007f94d0037968 CR3: 0000000118454000 CR4: 0000000000350ee0
Mar 21 15:35:59 LattePanda kernel: [437793.272770] Call Trace:
Mar 21 15:35:59 LattePanda kernel: [437793.272771]  <TASK>
Mar 21 15:35:59 LattePanda kernel: [437793.272773]  ? ext4_inode_csum+0x1c9/0x200
Mar 21 15:35:59 LattePanda kernel: [437793.272776]  ext4_inode_csum_set+0x50/0xa0
Mar 21 15:35:59 LattePanda kernel: [437793.272778]  ext4_do_update_inode.isra.0+0x519/0x910
Mar 21 15:35:59 LattePanda kernel: [437793.272780]  ? __ext4_journal_get_write_access+0x8f/0x1b0
Mar 21 15:35:59 LattePanda kernel: [437793.272782]  ext4_mark_iloc_dirty+0x56/0xc0
Mar 21 15:35:59 LattePanda kernel: [437793.272784]  __ext4_mark_inode_dirty+0x80/0x210
Mar 21 15:35:59 LattePanda kernel: [437793.272786]  ? __ext4_journal_start_sb+0x119/0x130
Mar 21 15:35:59 LattePanda kernel: [437793.272789]  ext4_dirty_inode+0x5c/0x80
Mar 21 15:35:59 LattePanda kernel: [437793.272791]  __mark_inode_dirty+0x5b/0x3a0
Mar 21 15:35:59 LattePanda kernel: [437793.272794]  generic_write_end+0xf9/0x160
Mar 21 15:35:59 LattePanda kernel: [437793.272796]  ext4_da_write_end+0x7c/0x230
Mar 21 15:35:59 LattePanda kernel: [437793.272798]  generic_perform_write+0x113/0x200
Mar 21 15:35:59 LattePanda kernel: [437793.272801]  ext4_buffered_write_iter+0xac/0x180
Mar 21 15:35:59 LattePanda kernel: [437793.272803]  ext4_file_write_iter+0x43/0x60
Mar 21 15:35:59 LattePanda kernel: [437793.272805]  new_sync_write+0x111/0x1a0
Mar 21 15:35:59 LattePanda kernel: [437793.272806]  ? enable_verity+0x80/0x3d0
Mar 21 15:35:59 LattePanda kernel: [437793.272809]  vfs_write+0x1fb/0x290
Mar 21 15:35:59 LattePanda kernel: [437793.272810]  ksys_write+0x67/0xf0
Mar 21 15:35:59 LattePanda kernel: [437793.272812]  __x64_sys_write+0x19/0x20
Mar 21 15:35:59 LattePanda kernel: [437793.272814]  do_syscall_64+0x59/0xc0
Mar 21 15:35:59 LattePanda kernel: [437793.272815]  ? vfs_write+0x183/0x290
Mar 21 15:35:59 LattePanda kernel: [437793.272817]  ? fput+0x13/0x20
Mar 21 15:35:59 LattePanda kernel: [437793.272818]  ? ksys_write+0xd2/0xf0
Mar 21 15:35:59 LattePanda kernel: [437793.272820]  ? exit_to_user_mode_prepare+0x37/0xb0
Mar 21 15:35:59 LattePanda kernel: [437793.272822]  ? syscall_exit_to_user_mode+0x27/0x50
Mar 21 15:35:59 LattePanda kernel: [437793.272824]  ? __x64_sys_write+0x19/0x20
Mar 21 15:35:59 LattePanda kernel: [437793.272826]  ? do_syscall_64+0x69/0xc0
Mar 21 15:35:59 LattePanda kernel: [437793.272827]  ? syscall_exit_to_user_mode+0x27/0x50
Mar 21 15:35:59 LattePanda kernel: [437793.272829]  ? __x64_sys_newfstatat+0x1c/0x30
Mar 21 15:35:59 LattePanda kernel: [437793.272831]  ? do_syscall_64+0x69/0xc0
Mar 21 15:35:59 LattePanda kernel: [437793.272833]  entry_SYSCALL_64_after_hwframe+0x61/0xcb
Mar 21 15:35:59 LattePanda kernel: [437793.272834] RIP: 0033:0x7f94da4b3a6f
Mar 21 15:35:59 LattePanda kernel: [437793.272836] Code: 89 54 24 18 48 89 74 24 10 89 7c 24 08 e8 19 c0 f7 ff 48 8b 54 24 18 48 8b 74 24 10 41 89 c0 8b 7c 24 08 b8 01 00 00 00 0f 05 <48> 3d 00 f0 ff ff 77 31 44 89 c7 48 89 44 24 08 e8 5c c0 f7 ff 48
Mar 21 15:35:59 LattePanda kernel: [437793.272837] RSP: 002b:00007f94d97e1710 EFLAGS: 00000293 ORIG_RAX: 0000000000000001
Mar 21 15:35:59 LattePanda kernel: [437793.272839] RAX: ffffffffffffffda RBX: 0000000000001000 RCX: 00007f94da4b3a6f
Mar 21 15:35:59 LattePanda kernel: [437793.272840] RDX: 0000000000001000 RSI: 00007f94d0035950 RDI: 0000000000000009
Mar 21 15:35:59 LattePanda kernel: [437793.272841] RBP: 00007f94d0035950 R08: 0000000000000000 R09: 00000000ffffffff
Mar 21 15:35:59 LattePanda kernel: [437793.272842] R10: 0000000000000000 R11: 0000000000000293 R12: 0000000000000000
Mar 21 15:35:59 LattePanda kernel: [437793.272843] R13: 0000000000000051 R14: 0000000000001000 R15: 00007f94d00106a0
Mar 21 15:35:59 LattePanda kernel: [437793.272845]  </TASK>

```

I've attached this remainder of this log and the syslog from the ASRock NUC BOX-1260P.

Also, to verify that kernel version 5.15 and later contains this problem apart from other potential USB problems, the NUC7i5BNK computer was running a variant of this program nonstop on kernel version 4.19 for months on an Ubuntu 18.04 without any problems. Then, after it was updated to kernel 5.15 and nothing else was changed, the system ran into this CPU hard lockup problem after a little more than a day of running.  Another interesting observation was that the CPU load and usage appeared much higher and things were boggier with later kernels.  The average load on version 4.19 was ~1-2, and on version 5.15 was ~17-21+.  Version 5.4 was installed and tested on this computer to see how it would run in a quick test.  Things were less boggy and the average load dropped to ~5-7, but it still wasn't as good as version 4.19.  Although, it should be mentioned that other things were setup and running alongside this default program so it may not be a 1 to 1 conversion.

These computers would've been tested further on other kernel versions to determine on what version this problem arose, but as of right now all of them are being used for other purposes, such as trying to reproduce the problem on a bare-bones arch install to get support from that community also.

---

### Post by the-domino-engineer on 2023-03-30
Created bug report on launchpad: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/2013390](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/2013390)

---

### Post by the-domino-engineer on 2023-04-01
It's been verified that this bug is present in kernel version 6.2 on a system running Arch Linux.
 Here are links to other posts in regards to this:

Kernel.org Bugzilla -> [https://bugzilla.kernel.org/show_bug.cgi?id=217242](https://bugzilla.kernel.org/show_bug.cgi?id=217242)
archlinux Forums -> [https://bbs.archlinux.org/viewtopic.php?pid=2092955#p2092955](https://bbs.archlinux.org/viewtopic.php?pid=2092955#p2092955)

---

### Post by the-domino-engineer on 2023-04-01
Here's a log file from a lockup that lasted almost 5 minutes until the computer was hard reset due to unresponsiveness: [ATTACH]292003[/ATTACH]

---

