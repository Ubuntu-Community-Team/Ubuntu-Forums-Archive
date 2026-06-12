---
title: "Invalid opcode"
date: 2011-06-27
forum: Server Platforms
---

### Post by Juul_Crapuul on 2011-06-27
Hello all.
I really like ubuntu, but I am dealing with an issue beyond my understanding at the moment.
At random times (usually when watching a movie in XBMC), the computer locks up. I can still sometimes SSH in and get the 'dmesg' output before that locks up too. A hard reboot is usually required to get things going again.
I have cut out the date/time/server columns for easier reading, please do ask if these seem relevant omissions...

System:
Ubuntu 11.04 (2.6.38-8-server) x64
X11 installed with IceWm (and XBMC)
Core 2 Duo E8400 @ 3.00GHz
8 GB RAM
Asus P5Q premium motherboard
Primary harddrive: OCZ Vertex 2 60 GB (SSD)
Other harddrives: various 750GB, 1TB, 1.5TB & 2TB (WD & samsung)

Any important information I am not supplying is purely a sign of my incompetence in these matters, so please do ask and excuse me for my inabilities...

```

 invalid opcode: 0000 [#1] SMP
 last sysfs file: /sys/devices/system/cpu/cpu1/cache/index2/shared_cpu_map
 CPU 0
 Modules linked in: parport_pc ppdev vesafb snd_hda_codec_analog tuner_simple tuner_types wm8775 tda9887 tda8290 tea5767 tuner cx25840 ir_lirc_codec lirc_dev snd_hda_intel snd_hda_codec snd_hwdep snd_pcm ir_sony_decoder snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq rc_rc6_mce ivtv ir_jvc_decoder cx2341x i2c_algo_bit v4l2_common mceusb videodev ir_rc6_decoder ir_rc5_decoder snd_timer ir_nec_decoder nvidia(P) btusb bluetooth rc_core v4l2_compat_ioctl32 tveeprom snd_seq_device pata_marvell psmouse shpchp serio_raw snd asus_atk0110 soundcore snd_page_alloc lp parport firewire_ohci firewire_core crc_itu_t r8169 sky2 ahci libahci

 Pid: 4597, comm: xbmc.bin Tainted: P            2.6.38-8-server #42-Ubuntu System manufacturer P5Q Premium/P5Q Premium
 RIP: 0010:[<ffffffff8119bc4a>]  [<ffffffff8119bc4a>] do_mpage_readpage+0x9a/0x510
 RSP: 0018:ffff88021f5a59d8  EFLAGS: 00210246
 RAX: 0000000000000020 RBX: ffff88021f5a5ac8 RCX: 0000000000000000
 RDX: 0000000000000001 RSI: 0000000015e36fe0 RDI: 0000000000000000
 RBP: ffff88021f5a5a98 R08: ffff88021f5a5ac8 R09: ffff88021f5a5b38
 R10: 0000000000000000 R11: 0000000000000000 R12: 0000000000000000
 R13: 000000000000b148 R14: 0000000000000001 R15: ffff8802067034b8
 FS:  00007f3f34eb1700(0000) GS:ffff8800cfc00000(0000) knlGS:0000000000000000
 CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
 CR2: 00007feb8d515000 CR3: 000000021d744000 CR4: 00000000000406f0
 DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
 DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
 Process xbmc.bin (pid: 4597, threadinfo ffff88021f5a4000, task ffff88021f63db80)
 Stack:
  ffff88021f5a5a28 ffffffff8116019d ffff88021f5a5b40 0000002000000003
  ffff88021f5a5b38 ffff880206703370 ffffea0006d800f8 0000000000000000
  ffffea0006d800f8 0000000c811270b5 ffff88021f5a5a68 ffffffff8110bdba
 Call Trace:
  [<ffffffff8116019d>] ? mem_cgroup_cache_charge+0xed/0x130
  [<ffffffff8110bdba>] ? add_to_page_cache_locked+0xea/0x160
  [<ffffffff8119c232>] mpage_readpages+0x102/0x150
  [<ffffffff812063e0>] ? ext4_get_block+0x0/0x20
  [<ffffffff812063e0>] ? ext4_get_block+0x0/0x20
  [<ffffffff81149475>] ? alloc_pages_current+0xa5/0x110
  [<ffffffff8120157d>] ext4_readpages+0x1d/0x20
  [<ffffffff81116a9b>] __do_page_cache_readahead+0x14b/0x220
  [<ffffffff81116ed1>] ra_submit+0x21/0x30
  [<ffffffff81116ff5>] ondemand_readahead+0x115/0x230
  [<ffffffff811171a0>] page_cache_async_readahead+0x90/0xc0
  [<ffffffff8110b184>] ? file_read_actor+0xd4/0x170
  [<ffffffff812de72e>] ? radix_tree_lookup_slot+0xe/0x10
  [<ffffffff8110c521>] do_generic_file_read.clone.23+0x271/0x450
  [<ffffffff8110d1ba>] generic_file_aio_read+0x1ca/0x240
  [<ffffffff8100a82e>] ? __switch_to+0x20e/0x2f0
  [<ffffffff81164c82>] do_sync_read+0xd2/0x110
  [<ffffffff8108b61c>] ? hrtimer_try_to_cancel+0x4c/0xe0
  [<ffffffff81279083>] ? security_file_permission+0x93/0xb0
  [<ffffffff81164fa1>] ? rw_verify_area+0x61/0xf0
  [<ffffffff81165463>] vfs_read+0xc3/0x180
  [<ffffffff81165571>] sys_read+0x51/0x90
  [<ffffffff8100bfc2>] system_call_fastpath+0x16/0x1b
 Code: ff ff 48 c7 85 78 ff ff ff 00 00 00 00 49 d3 ee b9 0c 00 00 00 2b 4d 8c 48 8b b2 c8 00 00 00 ba 01 00 00 00 41 0f af c6 49 d3 e5 <0f> 36 4d 8c 4c 01 e8 d3 e2 4c 8d 44 16 ff 48 8b 53 20 49 d3 f8
 RIP  [<ffffffff8119bc4a>] do_mpage_readpage+0x9a/0x510
  RSP <ffff88021f5a59d8>
 ---[ end trace ac6cd2f4692205a3 ]---


```

---

