---
title: "Lenovo X220 DisplayPort issue 14.04 beta"
date: 2014-03-30
forum: Ubuntu Development Version
---

### Post by robvas on 2014-03-30
VGA output on this laptop works fine - but connecting a monitor over DisplayPort gives me this in syslog

```
Mar 30 10:50:26 diablo kernel: [ 2245.728915] ------------[ cut here ]------------Mar 30 10:50:26 diablo kernel: [ 2245.728948] WARNING: CPU: 0 PID: 477 at /build/buildd/linux-3.13.0/drivers/gpu/drm/i915/intel_dp.c:2747 intel_dp_link_down+0x1d2/0x210 [i915]()
Mar 30 10:50:26 diablo kernel: [ 2245.728949] Modules linked in: cmac rmd160 crypto_null camellia_generic camellia_aesni_avx_x86_64 camellia_x86_64 cast6_avx_x86_64 cast6_generic cast5_avx_x86_64 cast5_generic cast_common deflate cts ctr gcm ccm serpent_avx_x86_64 serpent_sse2_x86_64 serpent_generic blowfish_generic blowfish_x86_64 blowfish_common twofish_generic twofish_avx_x86_64 twofish_x86_64_3way xts twofish_x86_64 twofish_common xcbc sha256_ssse3 sha512_ssse3 des_generic xfrm_user ah6 ah4 esp6 esp4 xfrm4_mode_beet xfrm4_tunnel tunnel4 xfrm4_mode_tunnel xfrm4_mode_transport xfrm6_mode_transport xfrm6_mode_ro xfrm6_mode_beet xfrm6_mode_tunnel ipcomp ipcomp6 xfrm6_tunnel tunnel6 xfrm_ipcomp af_key xfrm_algo snd_hda_codec_hdmi snd_hda_codec_conexant intel_rapl snd_hda_intel x86_pkg_temp_thermal intel_powerclamp rfcomm coretemp snd_hda_codec kvm_intel bnep kvm snd_hwdep bluetooth crct10dif_pclmul crc32_pclmul snd_pcm ghash_clmulni_intel aesni_intel aes_x86_64 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core arc4 videodev lrw gf128mul glue_helper ablk_helper iwldvm thinkpad_acpi cryptd psmouse mac80211 nvram snd_page_alloc serio_raw snd_seq_midi snd_seq_midi_event snd_rawmidi iwlwifi snd_seq cfg80211 snd_seq_device i915 lpc_ich snd_timer wmi drm_kms_helper snd drm soundcore i2c_algo_bit mei_me mac_hid video mei binfmt_misc lp parport ahci e1000e libahci sdhci_pci ptp sdhci pps_core
Mar 30 10:50:26 diablo kernel: [ 2245.729001] CPU: 0 PID: 477 Comm: kworker/0:2 Not tainted 3.13.0-19-generic #40-Ubuntu
Mar 30 10:50:26 diablo kernel: [ 2245.729002] Hardware name: LENOVO 4290FZ9/4290FZ9, BIOS 8DET65WW (1.35 ) 10/03/2012
Mar 30 10:50:26 diablo kernel: [ 2245.729010] Workqueue: events i915_hotplug_work_func [i915]
Mar 30 10:50:26 diablo kernel: [ 2245.729012]  0000000000000009 ffff8800d5885ce0 ffffffff81711075 0000000000000000
Mar 30 10:50:26 diablo kernel: [ 2245.729014]  ffff8800d5885d18 ffffffff810662cd ffff8802125b20c8 ffff8800362bc800
Mar 30 10:50:26 diablo kernel: [ 2245.729016]  ffff88020ea34000 0000000080080304 ffff8800d5844000 ffff8800d5885d28
Mar 30 10:50:26 diablo kernel: [ 2245.729018] Call Trace:
Mar 30 10:50:26 diablo kernel: [ 2245.729024]  [<ffffffff81711075>] dump_stack+0x45/0x56
Mar 30 10:50:26 diablo kernel: [ 2245.729027]  [<ffffffff810662cd>] warn_slowpath_common+0x7d/0xa0
Mar 30 10:50:26 diablo kernel: [ 2245.729029]  [<ffffffff810663aa>] warn_slowpath_null+0x1a/0x20
Mar 30 10:50:26 diablo kernel: [ 2245.729040]  [<ffffffffa01a7092>] intel_dp_link_down+0x1d2/0x210 [i915]
Mar 30 10:50:26 diablo kernel: [ 2245.729052]  [<ffffffffa01ac038>] intel_dp_check_link_status+0xf8/0x1c0 [i915]
Mar 30 10:50:26 diablo kernel: [ 2245.729062]  [<ffffffffa01ad222>] ? intel_hdmi_detect+0x82/0x120 [i915]
Mar 30 10:50:26 diablo kernel: [ 2245.729072]  [<ffffffffa01ac115>] intel_dp_hot_plug+0x15/0x20 [i915]
Mar 30 10:50:26 diablo kernel: [ 2245.729080]  [<ffffffffa01617e8>] i915_hotplug_work_func+0x1c8/0x360 [i915]
Mar 30 10:50:26 diablo kernel: [ 2245.729085]  [<ffffffff810824a2>] process_one_work+0x182/0x450
Mar 30 10:50:26 diablo kernel: [ 2245.729087]  [<ffffffff81083344>] worker_thread+0x224/0x410
Mar 30 10:50:26 diablo kernel: [ 2245.729089]  [<ffffffff81083120>] ? rescuer_thread+0x3e0/0x3e0
Mar 30 10:50:26 diablo kernel: [ 2245.729091]  [<ffffffff81089ed2>] kthread+0xd2/0xf0
Mar 30 10:50:26 diablo kernel: [ 2245.729093]  [<ffffffff81089e00>] ? kthread_create_on_node+0x190/0x190
Mar 30 10:50:26 diablo kernel: [ 2245.729095]  [<ffffffff817219bc>] ret_from_fork+0x7c/0xb0
Mar 30 10:50:26 diablo kernel: [ 2245.729097]  [<ffffffff81089e00>] ? kthread_create_on_node+0x190/0x190
Mar 30 10:50:26 diablo kernel: [ 2245.729099] ---[ end trace 92f6f59a4c11c681 ]---
Mar 30 10:50:26 diablo kernel: [ 2245.779806] ------------[ cut here ]------------
Mar 30 10:50:26 diablo kernel: [ 2245.779846] WARNING: CPU: 0 PID: 1032 at /build/buildd/linux-3.13.0/drivers/gpu/drm/i915/intel_dp.c:2747 intel_dp_link_down+0x1d2/0x210 [i915]()
Mar 30 10:50:26 diablo kernel: [ 2245.779848] Modules linked in: cmac rmd160 crypto_null camellia_generic camellia_aesni_avx_x86_64 camellia_x86_64 cast6_avx_x86_64 cast6_generic cast5_avx_x86_64 cast5_generic cast_common deflate cts ctr gcm ccm serpent_avx_x86_64 serpent_sse2_x86_64 serpent_generic blowfish_generic blowfish_x86_64 blowfish_common twofish_generic twofish_avx_x86_64 twofish_x86_64_3way xts twofish_x86_64 twofish_common xcbc sha256_ssse3 sha512_ssse3 des_generic xfrm_user ah6 ah4 esp6 esp4 xfrm4_mode_beet xfrm4_tunnel tunnel4 xfrm4_mode_tunnel xfrm4_mode_transport xfrm6_mode_transport xfrm6_mode_ro xfrm6_mode_beet xfrm6_mode_tunnel ipcomp ipcomp6 xfrm6_tunnel tunnel6 xfrm_ipcomp af_key xfrm_algo snd_hda_codec_hdmi snd_hda_codec_conexant intel_rapl snd_hda_intel x86_pkg_temp_thermal intel_powerclamp rfcomm coretemp snd_hda_codec kvm_intel bnep kvm snd_hwdep bluetooth crct10dif_pclmul crc32_pclmul snd_pcm ghash_clmulni_intel aesni_intel aes_x86_64 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core arc4 videodev lrw gf128mul glue_helper ablk_helper iwldvm thinkpad_acpi cryptd psmouse mac80211 nvram snd_page_alloc serio_raw snd_seq_midi snd_seq_midi_event snd_rawmidi iwlwifi snd_seq cfg80211 snd_seq_device i915 lpc_ich snd_timer wmi drm_kms_helper snd drm soundcore i2c_algo_bit mei_me mac_hid video mei binfmt_misc lp parport ahci e1000e libahci sdhci_pci ptp sdhci pps_core
Mar 30 10:50:26 diablo kernel: [ 2245.779922] CPU: 0 PID: 1032 Comm: Xorg Tainted: G        W    3.13.0-19-generic #40-Ubuntu
Mar 30 10:50:26 diablo kernel: [ 2245.779924] Hardware name: LENOVO 4290FZ9/4290FZ9, BIOS 8DET65WW (1.35 ) 10/03/2012
Mar 30 10:50:26 diablo kernel: [ 2245.779926]  0000000000000009 ffff8800d3edfa80 ffffffff81711075 0000000000000000
Mar 30 10:50:26 diablo kernel: [ 2245.779930]  ffff8800d3edfab8 ffffffff810662cd ffff8802125b20c8 ffff8800362bc800
Mar 30 10:50:26 diablo kernel: [ 2245.779933]  ffff88020ea34000 0000000080080304 ffff8800d5844000 ffff8800d3edfac8
Mar 30 10:50:26 diablo kernel: [ 2245.779936] Call Trace:
Mar 30 10:50:26 diablo kernel: [ 2245.779944]  [<ffffffff81711075>] dump_stack+0x45/0x56
Mar 30 10:50:26 diablo kernel: [ 2245.779948]  [<ffffffff810662cd>] warn_slowpath_common+0x7d/0xa0
Mar 30 10:50:26 diablo kernel: [ 2245.779951]  [<ffffffff810663aa>] warn_slowpath_null+0x1a/0x20
Mar 30 10:50:26 diablo kernel: [ 2245.779967]  [<ffffffffa01a7092>] intel_dp_link_down+0x1d2/0x210 [i915]
Mar 30 10:50:26 diablo kernel: [ 2245.779983]  [<ffffffffa01ab410>] intel_disable_dp+0x70/0x80 [i915]
Mar 30 10:50:26 diablo kernel: [ 2245.779997]  [<ffffffffa01904ee>] ironlake_crtc_disable+0x1ae/0x940 [i915]
Mar 30 10:50:26 diablo kernel: [ 2245.780000]  [<ffffffff817158a9>] ? _cond_resched+0x29/0x40
Mar 30 10:50:26 diablo kernel: [ 2245.780014]  [<ffffffffa0197139>] __intel_set_mode+0x2c9/0x9c0 [i915]
Mar 30 10:50:26 diablo kernel: [ 2245.780028]  [<ffffffffa019a376>] intel_set_mode+0x16/0x30 [i915]
Mar 30 10:50:26 diablo kernel: [ 2245.780042]  [<ffffffffa019ac2b>] intel_crtc_set_config+0x7ab/0x9a0 [i915]
Mar 30 10:50:26 diablo kernel: [ 2245.780058]  [<ffffffffa00d4e2d>] drm_mode_set_config_internal+0x5d/0xe0 [drm]
Mar 30 10:50:26 diablo kernel: [ 2245.780071]  [<ffffffffa00d7d17>] drm_mode_setcrtc+0xf7/0x5e0 [drm]
Mar 30 10:50:26 diablo kernel: [ 2245.780076]  [<ffffffff811cc670>] ? poll_select_copy_remaining+0x130/0x130
Mar 30 10:50:26 diablo kernel: [ 2245.780085]  [<ffffffffa00c8c22>] drm_ioctl+0x502/0x630 [drm]
Mar 30 10:50:26 diablo kernel: [ 2245.780091]  [<ffffffff811cba30>] do_vfs_ioctl+0x2e0/0x4c0
Mar 30 10:50:26 diablo kernel: [ 2245.780095]  [<ffffffff8109c944>] ? vtime_account_user+0x54/0x60
Mar 30 10:50:26 diablo kernel: [ 2245.780098]  [<ffffffff811cbc91>] SyS_ioctl+0x81/0xa0
Mar 30 10:50:26 diablo kernel: [ 2245.780101]  [<ffffffff81721c7f>] tracesys+0xe1/0xe6
Mar 30 10:50:26 diablo kernel: [ 2245.780103] ---[ end trace 92f6f59a4c11c682 ]---
Mar 30 10:50:27 diablo colord: device removed: xrandr-Acer Technologies-S211HL-LP30D0028513
Mar 30 10:50:27 diablo wpa_supplicant[1089]: nl80211: send_and_recv->nl_recvmsgs failed: -33
Mar 30 10:50:31 diablo colord: Automatic metadata add icc-9e5c4d5e3765aa6e8278720ee862b98c to xrandr-Acer Technologies-S211HL-LP30D0028513
Mar 30 10:50:31 diablo colord: Device added: xrandr-Acer Technologies-S211HL-LP30D0028513
Mar 30 10:50:32 diablo kernel: [ 2250.970625] [drm:intel_dp_complete_link_train] *ERROR* failed to train DP, aborting
Mar 30 10:50:34 diablo dbus[446]: [system] Reloaded configuration

```

Any suggestions? This did not work in 12.04 either, pretty much the same error back then.

---

