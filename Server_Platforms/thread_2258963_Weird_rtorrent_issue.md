---
title: "Weird rtorrent issue"
date: 2014-12-31
forum: Server Platforms
---

### Post by DigiAngel on 2014-12-31
Topic says it...I think these started after the latest round of kernel updates:

```
Dec 31 17:54:18 gateway kernel: [1767281.391658] ------------[ cut here ]------------
Dec 31 17:54:18 gateway kernel: [1767281.391678] WARNING: CPU: 1 PID: 16176 at /build/buildd/linux-3.13.0/mm/truncate.c:652 pagecache_isize_extended+0x128/0x130()
Dec 31 17:54:18 gateway kernel: [1767281.391684] Modules linked in: nfnetlink_log bluetooth cls_u32 sch_hfsc nfnetlink_queue nfnetlink xt_iprange xt_mark xt_NFQUEUE ipt_MASQUERADE xt_REDIRECT xt_conntrack ipt_REJECT ts_bm xt_string xt_LOG iptable_nat nf_conntrack_ipv4 nf_defrag_ipv4 nf_nat_ipv4 nf_nat nf_conntrack iptable_filter xfrm_user xfrm4_tunnel tunnel4 ipcomp xfrm_ipcomp esp4 ah4 af_key xfrm_algo xt_TCPMSS xt_tcpmss xt_tcpudp iptable_mangle ip_tables x_tables pppoe pppox xfs libcrc32c snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_page_alloc snd_seq_midi hid_appleir hid_apple snd_seq_midi_event hid_generic adm1021 snd_rawmidi coretemp snd_seq applesmc input_polldev kvm_intel kvm b43 bcma isight_firmware snd_seq_device nouveau snd_timer mxm_wmi mac80211 asix wmi usbnet ttm mii snd drm_kms_helper usbhid lpc_ich cfg80211 firewire_sbp2 ssb_hcd hid drm i2c_algo_bit soundcore video mac_hid apple_bl lp parport sky2 ssb firewire_ohci firewire_core crc_itu_t
Dec 31 17:54:18 gateway kernel: [1767281.391850] CPU: 1 PID: 16176 Comm: main Tainted: G        W     3.13.0-43-generic #72-Ubuntu
Dec 31 17:54:18 gateway kernel: [1767281.391855] Hardware name: Apple Computer, Inc. iMac6,1/Mac-F4218FC8, BIOS     IM61.88Z.0093.B07.0706281250 06/28/07
Dec 31 17:54:18 gateway kernel: [1767281.391860]  00000000 00000000 dce99e14 c1655602 00000000 dce99e44 c105699e c18330e0
Dec 31 17:54:18 gateway kernel: [1767281.391875]  00000001 00003f30 c1847688 0000028c c112e948 c112e948 d829b844 00000000
Dec 31 17:54:18 gateway kernel: [1767281.391889]  00001000 dce99e54 c1056a62 00000009 00000000 dce99e84 c112e948 00000009
Dec 31 17:54:18 gateway kernel: [1767281.391902] Call Trace:
Dec 31 17:54:18 gateway kernel: [1767281.391916]  [<c1655602>] dump_stack+0x41/0x52
Dec 31 17:54:18 gateway kernel: [1767281.391925]  [<c105699e>] warn_slowpath_common+0x7e/0xa0
Dec 31 17:54:18 gateway kernel: [1767281.391935]  [<c112e948>] ? pagecache_isize_extended+0x128/0x130
Dec 31 17:54:18 gateway kernel: [1767281.391942]  [<c112e948>] ? pagecache_isize_extended+0x128/0x130
Dec 31 17:54:18 gateway kernel: [1767281.391951]  [<c1056a62>] warn_slowpath_null+0x22/0x30
Dec 31 17:54:18 gateway kernel: [1767281.391959]  [<c112e948>] pagecache_isize_extended+0x128/0x130
Dec 31 17:54:18 gateway kernel: [1767281.391967]  [<c112f3ec>] truncate_setsize+0x3c/0x60
Dec 31 17:54:18 gateway kernel: [1767281.392025]  [<f8836d9c>] xfs_setattr_size+0x1cc/0x3e0 [xfs]
Dec 31 17:54:18 gateway kernel: [1767281.392115]  [<f882bde1>] xfs_file_fallocate+0x1a1/0x270 [xfs]
Dec 31 17:54:18 gateway kernel: [1767281.392126]  [<c117bf37>] ? __sb_start_write+0x47/0xd0
Dec 31 17:54:18 gateway kernel: [1767281.392135]  [<c127274e>] ? security_file_permission+0x1e/0xb0
Dec 31 17:54:18 gateway kernel: [1767281.392145]  [<c11787b0>] do_fallocate+0x120/0x1a0
Dec 31 17:54:18 gateway kernel: [1767281.392154]  [<c117888c>] SyS_fallocate+0x5c/0x80
Dec 31 17:54:18 gateway kernel: [1767281.392162]  [<c166398d>] sysenter_do_call+0x12/0x12
Dec 31 17:54:18 gateway kernel: [1767281.392168] ---[ end trace 028db807797b59e3 ]---
```

Anyone else seeing this?  Linux gateway 3.13.0-43-generic #72-Ubuntu SMP Mon Dec 8 19:35:44 UTC 2014 i686 i686 i686 GNU/Linux

---

### Post by DigiAngel on 2015-01-01
I guess I can also add that I see this with both using what's in the repo, and compiling from source....same thing.

---

