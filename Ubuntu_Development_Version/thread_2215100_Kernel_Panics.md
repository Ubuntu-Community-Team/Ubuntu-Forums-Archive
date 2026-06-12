---
title: "Kernel Panics"
date: 2014-04-04
forum: Ubuntu Development Version
---

### Post by cromat on 2014-04-04
Any deas?

ProblemType: KernelOops
Annotation: Your system might become unstable now and might need to be restarted.
Date: Fri Apr  4 14:48:02 2014
Failure: oops
OopsText:
 BUG: unable to handle kernel NULL pointer dereference at 0000000000000008
 IP: [<ffffffff81362e24>] __rb_insert_augmented+0x24/0x1f0
 PGD 0 
 Oops: 0000 [#3] SMP 
 Modules linked in: snd_seq_dummy hid_generic usbhid ctr ccm snd_hda_codec_hdmi snd_hda_codec_realtek joydev hid_magicmouse hidp hid dell_laptop dcdbas intel_rapl x86_pkg_temp_thermal intel_powerclamp coretemp kvm_intel kvm rfcomm crct10dif_pclmul crc32_pclmul ghash_clmulni_intel cryptd bnep psmouse serio_raw uvcvideo arc4 videobuf2_vmalloc dell_wmi sparse_keymap videobuf2_memops iwldvm videobuf2_core videodev btusb mac80211 bluetooth iwlwifi snd_hda_intel lpc_ich snd_hda_codec snd_hwdep snd_pcm cfg80211 snd_page_alloc snd_seq_midi snd_seq_midi_event wmi snd_rawmidi i915 snd_seq snd_seq_device video snd_timer drm_kms_helper snd soundcore intel_smartconnect mac_hid mei_me drm mei i2c_algo_bit lp parport ahci libahci
 CPU: 3 PID: 8733 Comm: chrome Tainted: G      D W    3.13.0-22-generic #44-Ubuntu
 Hardware name: Dell Inc.          Dell System XPS L322X/0PJHXN, BIOS A06 12/03/2012
 task: ffff880230370000 ti: ffff880076c3c000 task.ti: ffff880076c3c000
 RIP: 0010:[<ffffffff81362e24>]  [<ffffffff81362e24>] __rb_insert_augmented+0x24/0x1f0
 RSP: 0018:ffff880076c3dda8  EFLAGS: 00010246
 RAX: ffff880196b78298 RBX: 0000000000000000 RCX: 0000000000000207
 RDX: ffffffff81171f80 RSI: ffff880230d4e610 RDI: ffff880076c51598
 RBP: ffff880076c3ddc8 R08: ffff880076c51540 R09: ffff880230d4e610
 R10: 0000000000000009 R11: ffff880092e168b0 R12: ffff880092f94600
 R13: ffff880230d4e610 R14: ffff880230d4e628 R15: ffff880076c51540
 FS:  00007f3d29f60a00(0000) GS:ffff88023f2c0000(0000) knlGS:0000000000000000
 CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
 CR2: 0000000000000008 CR3: 0000000090131000 CR4: 00000000001407e0
 Stack:
  ffffffff81064cf8 ffff880092d666c0 ffff880092f94600 ffff880076c51480
  ffff880076c3ddd8 ffffffff8117243d ffff880076c3de48 ffffffff81064ddf
  ffff880092f94660 ffff88023206d7e0 ffff880230d4e5f0 ffff88023206d780
 Call Trace:
  [<ffffffff81064cf8>] ? dup_mm+0x1e8/0x650
  [<ffffffff8117243d>] vma_interval_tree_insert_after+0x7d/0x90
  [<ffffffff81064ddf>] dup_mm+0x2cf/0x650
  [<ffffffff81065bd6>] copy_process.part.27+0xa46/0x15c0
  [<ffffffff81066925>] do_fork+0xd5/0x300
  [<ffffffff81066bd6>] SyS_clone+0x16/0x20
  [<ffffffff81725649>] stub_clone+0x69/0x90
  [<ffffffff817254ff>] ? tracesys+0xe1/0xe6
 Code: 68 ff ff ff 0f 1f 00 48 8b 07 48 85 c0 0f 84 c4 01 00 00 55 48 89 e5 41 55 49 89 f5 41 54 53 48 83 ec 08 48 8b 18 f6 c3 01 75 6b <48> 8b 4b 08 49 89 d8 48 39 c8 0f 84 a7 00 00 00 48 85 c9 74 05 
 RIP  [<ffffffff81362e24>] __rb_insert_augmented+0x24/0x1f0
  RSP <ffff880076c3dda8>
 CR2: 0000000000000008
 ---[ end trace 558143fe253406c6 ]---
 
Package: linux-image-3.13.0-22-generic 3.13.0-22.44
SourcePackage: linux
Tags: kernel-oops
Uname: Linux 3.13.0-22-generic x86_64

---

### Post by cromat on 2014-04-04
I figured out the cause it is the Apple MagicTrackpad, now to find a solution.

---

