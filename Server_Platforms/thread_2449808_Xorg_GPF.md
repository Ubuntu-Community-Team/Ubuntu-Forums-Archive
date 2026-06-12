---
title: "Xorg GPF"
date: 2020-09-02
forum: Server Platforms
---

### Post by DigiAngel on 2020-09-02
Sigh....I get these every so often and I have to completely reboot the box.  Ubuntu 18 server using fluxbox:

```
[1656760.786327] general protection fault: 0000 [#1] SMP PTI
[1656760.786330] Modules linked in: vsock_diag vsock sctp_diag sctp dccp_diag dccp tcp_diag udp_diag raw_diag inet_diag unix_diag xt_nat xt_TARPIT(OE) xt_limit xt_connbytes authenc echainiv xfrm6_mode_tunnel xfrm4_mode_tunnel twofish_generic twofish_avx_x86_64 twofish_x86_64_3way twofish_x86_64 twofish_common serpent_avx2 serpent_avx_x86_64 serpent_sse2_x86_64 serpent_generic nfnetlink_queue nfnetlink_log nfnetlink bluetooth ecdh_generic blowfish_generic blowfish_x86_64 blowfish_common cast5_avx_x86_64 cast5_generic cast_common des_generic algif_skcipher camellia_generic camellia_aesni_avx2 camellia_aesni_avx_x86_64 ablk_helper camellia_x86_64 lrw xcbc md4 algif_hash af_alg xfrm_user xfrm4_tunnel tunnel4 ipcomp ipt_MASQUERADE nf_nat_masquerade_ipv4 xfrm_ipcomp esp4 xt_REDIRECT nf_nat_redirect ah4 af_key
[1656760.786347]  xfrm_algo ipt_REJECT nf_reject_ipv4 xt_helper xt_conntrack ts_bm xt_string nf_log_ipv4 nf_log_common xt_LOG xt_TCPMSS xt_tcpmss xt_tcpudp iptable_mangle iptable_nat nf_conntrack_ipv4 nf_defrag_ipv4 nf_nat_ipv4 nf_nat nf_conntrack iptable_filter pppoe pppox xfs intel_rapl x86_pkg_temp_thermal intel_powerclamp coretemp kvm_intel kvm irqbypass intel_cstate intel_rapl_perf snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_codec_generic snd_hda_intel dell_wmi dell_smbios snd_hda_codec dcdbas snd_hda_core snd_hwdep dell_wmi_descriptor snd_pcm wmi_bmof intel_wmi_thunderbolt snd_seq_midi snd_seq_midi_event serio_raw sparse_keymap snd_rawmidi snd_seq snd_seq_device snd_timer snd mac_hid mei_me mei soundcore ie31200_edac shpchp intel_pch_thermal acpi_pad sch_fq_codel ib_iser rdma_cm iw_cm ib_cm
[1656760.786365]  ib_core iscsi_tcp libiscsi_tcp libiscsi scsi_transport_iscsi ip_tables x_tables autofs4 btrfs zstd_compress raid10 raid456 async_raid6_recov async_memcpy async_pq async_xor async_tx xor raid6_pq libcrc32c raid1 raid0 multipath linear crct10dif_pclmul crc32_pclmul ghash_clmulni_intel pcbc i915 e1000e i2c_algo_bit aesni_intel drm_kms_helper uas ptp aes_x86_64 crypto_simd glue_helper r8169 syscopyarea cryptd psmouse pps_core mii sysfillrect sysimgblt fb_sys_fops ahci drm usb_storage libahci wmi video
[1656760.786380] CPU: 1 PID: 3734 Comm: Xorg Tainted: G           OE    4.15.0-112-generic #113-Ubuntu
[1656760.786381] Hardware name: Dell Inc. PowerEdge T30/07T4MC, BIOS 1.0.15 07/12/2018
[1656760.786412] RIP: 0010:gen8_ppgtt_set_pde.isra.27+0x45/0x60 [i915]
[1656760.786413] RSP: 0018:ffffa1c3826cf8c8 EFLAGS: 00010206
[1656760.786414] RAX: ea6907be27226600 RBX: 0000fffe98038000 RCX: ffff91c88a1ede00
[1656760.786415] RDX: 0000000100291003 RSI: ffff91c664204e60 RDI: ffff91c65cae8000
[1656760.786416] RBP: ffffa1c3826cf8c8 R08: 0000000000000000 R09: 0000000000000000
[1656760.786417] R10: 0000000000000000 R11: 0000000000000000 R12: 00000000000000c0
[1656760.786418] R13: 0000000000008000 R14: ffff91c65cae8000 R15: ffff91c88a69e000
[1656760.786419] FS:  00007f88ec820600(0000) GS:ffff91c8adc80000(0000) knlGS:0000000000000000
[1656760.786420] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
[1656760.786421] CR2: 00007f1b3a047058 CR3: 000000044a8f6002 CR4: 00000000003606e0
[1656760.786422] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[1656760.786423] DR3: 0000000000000000 DR6: 00000000fffe0ff0 DR7: 0000000000000400
[1656760.786423] Call Trace:
[1656760.786441]  gen8_ppgtt_alloc_pdp+0x1c2/0x340 [i915]
[1656760.786455]  gen8_ppgtt_alloc_4lvl+0x56/0x150 [i915]
[1656760.786468]  ppgtt_bind_vma+0x39/0x70 [i915]
[1656760.786484]  i915_vma_bind+0x75/0xd0 [i915]
[1656760.786499]  __i915_vma_do_pin+0x2ce/0x480 [i915]
[1656760.786513]  eb_lookup_vmas+0x7b0/0xb40 [i915]
[1656760.786516]  ? _cond_resched+0x19/0x40
[1656760.786518]  ? __pm_runtime_resume+0x5b/0x80
[1656760.786531]  i915_gem_do_execbuffer+0x4a2/0x1230 [i915]
[1656760.786533]  ? unix_stream_read_generic+0x22e/0x900
[1656760.786536]  ? radix_tree_lookup_slot+0x22/0x50
[1656760.786537]  ? find_get_entry+0x1e/0x110
[1656760.786539]  ? _cond_resched+0x19/0x40
[1656760.786540]  ? find_lock_entry+0x4f/0xc0
[1656760.786552]  i915_gem_execbuffer2+0x1b8/0x390 [i915]
[1656760.786565]  ? i915_gem_execbuffer+0x2d0/0x2d0 [i915]
[1656760.786579]  drm_ioctl_kernel+0x5f/0xb0 [drm]
[1656760.786585]  drm_ioctl+0x38e/0x460 [drm]
[1656760.786597]  ? i915_gem_execbuffer+0x2d0/0x2d0 [i915]
[1656760.786600]  do_vfs_ioctl+0xa8/0x630
[1656760.786603]  ? handle_mm_fault+0xb1/0x210
[1656760.786605]  ? __do_page_fault+0x2a1/0x4b0
[1656760.786606]  SyS_ioctl+0x79/0x90
[1656760.786608]  do_syscall_64+0x73/0x130
[1656760.786610]  entry_SYSCALL_64_after_hwframe+0x41/0xa6
[1656760.786611] RIP: 0033:0x7f88e9c126d7
[1656760.786612] RSP: 002b:00007ffdb4ea2188 EFLAGS: 00000246 ORIG_RAX: 0000000000000010
[1656760.786613] RAX: ffffffffffffffda RBX: 000055954039b0d0 RCX: 00007f88e9c126d7
[1656760.786614] RDX: 00007ffdb4ea21e0 RSI: 0000000040406469 RDI: 000000000000000c
[1656760.786615] RBP: 00007ffdb4ea21e0 R08: 0000000000000047 R09: 00005595403de2f0
[1656760.786616] R10: 00007ffdb4ea21b0 R11: 0000000000000246 R12: 0000000040406469
[1656760.786617] R13: 000000000000000c R14: ffffffffffffffff R15: 00005595402712e0
[1656760.786618] Code: 01 00 83 81 78 12 00 00 01 48 2b 05 be 61 fc e4 48 c1 f8 06 48 c1 e0 0c 48 8d 04 d0 48 8b 56 10 48 03 05 b7 61 fc e4 48 83 ca 03 <48> 89 10 83 a9 78 12 00 00 01 5d c3 0f 1f 44 00 00 66 2e 0f 1f 
[1656760.786641] RIP: gen8_ppgtt_set_pde.isra.27+0x45/0x60 [i915] RSP: ffffa1c3826cf8c8
[1656760.786642] ---[ end trace 0666fb0620e5c98b ]---

```

anyone know of a way to reset the xorg session (frozen screen) or am I just out of luck?  Thanks.

---

