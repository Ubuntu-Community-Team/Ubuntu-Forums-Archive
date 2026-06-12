---
title: "Virtualbox 4.0.8 Stacktrace Problem"
date: 2011-05-23
forum: Virtualisation
---

### Post by TDrakeHI on 2011-05-23
I am having a serious problem with Virtualbox.  It started in v 4.0 and has continued in the most recent upgrade to 4.0.8.  It didn't start until after the upgrade to Natty.  The first time I run VB after a reboot, there is no problem whatsoever.  I can start it, do what I need to do in it, yada yada yada.  The problem doesn't occur until after I shut it down and restart it.  Now I have tried both saving the current state and sending the shutdown signal.  But without fail, when i go to start it back up it invariably stacktraces, the only way to get back to Gnome is to Ctrl-Alt-F7, and then VB is hung.  The menu pops up when hovered over, and will close when forced.  If I try to restart VB it does the same thing.  The only way I can get it to work, is to do a full reboot of the computer.

What info do I need to post here that will help someone figure out my problem.

Here is a copy of the stacktrace.

> [ 5305.118170] divide error: 0000 [#2] SMP 
[ 5305.119852] last sysfs file: /sys/devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0/block/sda/sda3/stat
[ 5305.121564] CPU 0 
[ 5305.121575] Modules linked in: vboxnetadp vboxnetflt vboxdrv cryptd aes_x86_64 aes_generic binfmt_misc parport_pc ppdev snd_hda_codec_hdmi snd_hda_codec_realtek arc4 snd_hda_intel snd_hda_codec snd_hwdep snd_pcm iwlagn uvcvideo snd_seq_midi videodev v4l2_compat_ioctl32 snd_rawmidi joydev snd_seq_midi_event snd_seq iwlcore snd_timer i915 snd_seq_device mac80211 snd jmb38x_ms psmouse serio_raw memstick cfg80211 drm_kms_helper sparse_keymap soundcore intel_ips drm snd_page_alloc i2c_algo_bit video lp parport usbhid hid ahci sdhci_pci libahci r8169 sdhci [last unloaded: vboxdrv]
[ 5305.128139] 
[ 5305.128139] Pid: 7246, comm: VirtualBox Tainted: G      D     2.6.38-8-generic #42-Ubuntu TOSHIBA Satellite A665/NWQAA
[ 5305.128139] RIP: 0010:[<ffffffffa061718d>]  [<ffffffffa061718d>] 0xffffffffa061718d
[ 5305.128139] RSP: 0018:ffff88001d76dd08  EFLAGS: 00010a47
[ 5305.128139] RAX: 2a4aa79e1099c2c0 RBX: ffffc90023226000 RCX: 000000003b9aca00
[ 5305.128139] RDX: 000000009cfea15c RSI: 000000009cfea3f0 RDI: 0000000000000000
[ 5305.128139] RBP: ffff88001d76dd38 R08: 000004d331af0fd3 R09: 0000006f08f5e1dc
[ 5305.128139] R10: ffff880061ea3680 R11: 000000000000a3f0 R12: ffffc90023226fe0
[ 5305.128139] R13: ffffc9002320b000 R14: ffffc9002320b000 R15: 0000000060000030
[ 5305.128139] FS:  00007f84907b1700(0000) GS:ffff8800bb000000(0000) knlGS:0000000000000000
[ 5305.128139] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
[ 5305.128139] CR2: 0000000000000000 CR3: 000000005569f000 CR4: 00000000000026f0
[ 5305.128139] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[ 5305.128139] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[ 5305.128139] Process VirtualBox (pid: 7246, threadinfo ffff88001d76c000, task ffff88012f94c4a0)
[ 5305.128139] Stack:
[ 5305.128139]  ffff88001d76de08 0000000000000000 ffff88001d76dd68 0000000000000082
[ 5305.128139]  ffffc90023226900 ffffc90023226000 ffff88001d76dd98 ffffffffa05df86b
[ 5305.128139]  ffff88001d76de08 ffffffffa05df29e 8800bb004000007f 010000000000ffff
[ 5305.128139] Call Trace:
[ 5305.128139]  [<ffffffff81164682>] ? do_sync_write+0xd2/0x110
[ 5305.128139]  [<ffffffff81099f9a>] ? get_futex_key+0x15a/0x1d0
[ 5305.128139]  [<ffffffffa04478ea>] ? supdrvIOCtlFast+0x6a/0x70 [vboxdrv]
[ 5305.128139]  [<ffffffffa0444389>] ? VBoxDrvLinuxIOCtl+0x49/0x200 [vboxdrv]
[ 5305.128139]  [<ffffffff8117648f>] ? do_vfs_ioctl+0x8f/0x360
[ 5305.128139]  [<ffffffff81164e53>] ? vfs_write+0x123/0x180
[ 5305.128139]  [<ffffffff811767f1>] ? sys_ioctl+0x91/0xa0
[ 5305.128139]  [<ffffffff8100c002>] ? system_call_fastpath+0x16/0x1b
[ 5305.128139] Code: c9 c3 0f 1f 40 00 48 8d 75 d8 4c 89 ef e8 8c 16 00 00 48 3d 00 ca 9a 3b b9 00 ca 9a 3b 74 12 41 8b b5 d0 84 00 00 31 d2 48 f7 e6 <48> f7 f1 48 89 c1 48 2b 8b 48 2a 00 00 0f 31 4c 8b 45 d8 48 c1 
[ 5305.128139] RIP  [<ffffffffa061718d>] 0xffffffffa061718d
[ 5305.128139]  RSP <ffff88001d76dd08>
[ 5305.193842] ---[ end trace 4eaba671df7ea2f8 ]---

If there is anything else that could help, let me know.

TDrakeHI

---

