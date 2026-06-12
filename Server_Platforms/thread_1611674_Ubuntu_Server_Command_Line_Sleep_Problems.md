---
title: "Ubuntu Server Command Line Sleep Problems"
date: 2010-11-02
forum: Server Platforms
---

### Post by SeanDS on 2010-11-02
Hello all,

I am having trouble with my new install of Ubuntu Server Edition 10.10. I am using a Philips Freevents media centre PC which I bought with Windows Vista on it (built in TV tuner, etc.) and have since installed Ubuntu over the top of. I am using the server primarily for CVS and FTP, for development and backups.

Essentially the issue I am having is that whenever I leave the server idling for a long period of time, upon trying to 'wake' the computer (I say 'wake', but I'm not sure if the server has gone in to sleep mode or if it has just turned the display off) I can't get anything to display. I've not modified any settings from their default values apart from adding the CVS server stuff into the xinetd configuration.

Similarly, whenever I try and SSH into the server from another machine, upon logging in I am not given the ability to type commands. Either the line with the computer name and your current working directory, after which you type a command, appears, or nothing at all on that line. (See the attached image)

I think this is the same issue I had with Ubuntu Desktop Edition. In the desktop edition I had a problem with the sleep function, again whereby I'd leave it running and it would enter sleep mode and then refuse to wake up. With the desktop edition, however, I'd get a blinking cursor as opposed to nothing at all.

The FTP and CVS servers remain accessable and operational over the network, but I have to restart the server if I want to use the command line.

Any help would be appreciated.

---

### Post by SeanDS on 2010-11-02
As I said, on occasions, the 'sean@sean-server:~$' bit would come up when SSHing in to the server (see attachment). However, I still can't type anything in; it appears to be hanging or waiting for some process to finish that never does.

Interestingly, when the 'sean@sean-server:~$' bit does appear, the SSH window changes from the IP address I'm connecting to to 'sean@sean-server'. This seems to suggest that, on occasions, I am technically logged in (and hence the 'sean@sean-server:~$' bit appears), whereas some times I am not (where nothing appears, as in the attached image on the first post).

---

### Post by cipherboy_loc on 2010-11-02
Correct me if I am wrong, but when you say you have a display connected to your server, I assume that you have a window manager (Gnome, KDE, Fluxbox, etc)? If you don't mind wasting power when the computer is not in use, I would recommend disabling all sleeping and hibernating. 


Other than that, the only other thing that I can suggest is that you might have a corrupted package installed.

---

### Post by cipherboy_loc on 2010-11-02
Another thing I just remembered. I often boot Ubuntu (10.04LTS) from a flash drive. I have removed most of the graphical system (so that might be the cause of it), but when I log in to a tty and startx, if I switch back to a tty, the X server hangs. Not hangs, actually, but just leaves me with a white screen with my cursor on it.


Thus, I have to ask you, is the image displayed white when you turn the monitor on, or is it black, or some other color (Like your wallpaper, any open applications, etc)?


Cipherboy

---

### Post by SeanDS on 2010-11-02
Don't think I have a window manager. It's just the command line out-of-the-box version of Ubuntu Server.

I don't even know if the server is actually sleeping at all. Does Ubuntu Server come with a sleep function enabled by default? I think it's just turning the display off after a while and something to do with that is causing it not to turn the display back on again when I shake the mouse or press a key.

I redownloaded Ubuntu Server and reburned the CD and reinstalled it before posting this thread, and I encountered the same issue. So I think it's either some sort of configuration error, an error caused by xinetd (which I installed in order to have the CVS server start at boot) or an incompatibility with my server hardware (which is just a glorified mini desktop PC).

---

### Post by SeanDS on 2010-11-02
As I say, I'm just using the command line and there is no installed window system.

When I come back to the server after leaving it for a while, it has since switched the display output off and I have to shake the mouse or press a key to start the display again. However having done this, it doesn't switch the display back on. Similarly if I try and SSH in from another computer I encounter the issues I've described in my previous posts with not being able to type any commands.

---

### Post by Ryan Dwyer on 2010-11-02
Log in using whatever means you can (eg. reboot) then check your /var/log/syslog and /var/log/messages. Try to wake the machine or log in via SSH beforehand and note the time when you do so you know where to look in the logs. There could be something there which hints as to why you experience this behaviour.

The SSH login could be caused by internet connectivity problems. When you log in it tries to contact archive.ubuntu.com or something to check if updates are available. If you have a slow or non-replying DNS server that could delay your login. You can test this by logging in as per above, then run "dig archive.ubuntu.com" and "wget http://archive.ubuntu.com/". If either take more than a couple of seconds then that's probably the cause.

You said you try to wake it from sleep mode by moving the mouse. Ubuntu Server doesn't use the mouse as it's CLI so I don't think moving it would have any effect at all. The keyboard should be fine though. It could be an issue with your video driver maybe. You could try disabling sleep mode (Google: ubuntu server disable sleep). Just make sure you turn off the monitor when you're done using it.

Also, if you're going to resort to downloading the ISO again, you should md5sum the first one (and any others you download) to make sure it's correct. See [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by SeanDS on 2010-11-02
Thanks Ryan.

I noted the times and looked in the logs. It seems the system started causing the problems I've described when I turned the monitor off. I guess Linux notices that there is no video output and does something which is causing the problems.

Anyway, I looked in the log files and found some stuff. Around the time I reckon I switched the monitor off, this appears in /var/log/syslog:

[FONT=Courier New]Nov  2 16:22:30 sean-server kernel: [ 3739.120081] kernel BUG at /build/buildd/linux-2.6.35/drivers/gpu/drm/i915/i915_gem.c:4209![/FONT]

Here's the whole set of messages for time 16:22:30:

[FONT=Courier New]Nov  2 16:22:30 sean-server kernel: [ 3739.120040] ------------[ cut here ]------------
Nov  2 16:22:30 sean-server kernel: [ 3739.120081] kernel BUG at /build/buildd/linux-2.6.35/drivers/gpu/drm/i915/i915_gem.c:4209!
Nov  2 16:22:30 sean-server kernel: [ 3739.120134] invalid opcode: 0000 [#1] SMP 
Nov  2 16:22:30 sean-server kernel: [ 3739.120176] last sysfs file: /sys/devices/pci0000:00/0000:00:1c.2/0000:03:00.0/irq
Nov  2 16:22:30 sean-server kernel: [ 3739.120224] CPU 1 
Nov  2 16:22:30 sean-server kernel: [ 3739.120242] Modules linked in: snd_hda_codec_realtek saa7134_alsa mt352 saa7134_dvb videobuf_dvb dvb_core ir_lirc_codec lirc_dev tuner_xc2028 arc4 tuner snd_hda_intel iwl3945 ir_sony_decoder ir_jvc_decoder ir_rc6_decoder ir_rc5_decoder snd_hda_codec iwlcore saa7134 ir_nec_decoder i915 mac80211 snd_hwdep v4l2_common videodev v4l1_compat v4l2_compat_ioctl32 videobuf_dma_sg drm_kms_helper snd_pcm snd_timer videobuf_core ir_common ir_core tveeprom cfg80211 led_class snd soundcore drm i2c_algo_bit video snd_page_alloc output intel_agp lp parport usbhid hid e100 firewire_ohci mii firewire_core crc_itu_t
Nov  2 16:22:30 sean-server kernel: [ 3739.120909] 
Nov  2 16:22:30 sean-server kernel: [ 3739.120925] Pid: 689, comm: kslowd001 Not tainted 2.6.35-22-server #35-Ubuntu TGDII Series/Little LLUON S2
Nov  2 16:22:30 sean-server kernel: [ 3739.120984] RIP: 0010:[<ffffffffa01e9dc1>]  [<ffffffffa01e9dc1>] i915_gem_object_unpin+0xc1/0xd0 [i915]
Nov  2 16:22:30 sean-server kernel: [ 3739.121062] RSP: 0018:ffff88003d363810  EFLAGS: 00010282
Nov  2 16:22:30 sean-server kernel: [ 3739.121098] RAX: 00000000fffffff8 RBX: ffff88003bfb2800 RCX: ffff88003bef1800
Nov  2 16:22:30 sean-server kernel: [ 3739.121142] RDX: 000000000002047e RSI: 0000000000020000 RDI: ffff88003b28c400
Nov  2 16:22:30 sean-server kernel: [ 3739.121186] RBP: ffff88003d363810 R08: ffff88002f0fa000 R09: 0000000000000000
Nov  2 16:22:30 sean-server kernel: [ 3739.121230] R10: 0000036a6383e05e R11: 0000000000000001 R12: ffff88003bef1800
Nov  2 16:22:30 sean-server kernel: [ 3739.121274] R13: 0000000000000001 R14: ffffc90004e71188 R15: ffffc90004e71184
Nov  2 16:22:30 sean-server kernel: [ 3739.121319] FS:  0000000000000000(0000) GS:ffff880001f00000(0000) knlGS:0000000000000000
Nov  2 16:22:30 sean-server kernel: [ 3739.121369] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
Nov  2 16:22:30 sean-server kernel: [ 3739.121406] CR2: 00007f0435168000 CR3: 000000003b2f7000 CR4: 00000000000006e0
Nov  2 16:22:30 sean-server kernel: [ 3739.121450] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Nov  2 16:22:30 sean-server kernel: [ 3739.121494] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Nov  2 16:22:30 sean-server kernel: [ 3739.121539] Process kslowd001 (pid: 689, threadinfo ffff88003d362000, task ffff88002f132dc0)
Nov  2 16:22:30 sean-server kernel: [ 3739.121591] Stack:
Nov  2 16:22:30 sean-server kernel: [ 3739.121608]  ffff88003d3638c0 ffffffffa01fb632 0000000100000000 ffff880000000000
Nov  2 16:22:30 sean-server kernel: [ 3739.121672] <0> ffffffff00001400 ffff88002f132dc0 0000000000071180 000000000007119c
Nov  2 16:22:30 sean-server kernel: [ 3739.121748] <0> 00000000000711a4 00000000007e0000 ffff88003b03b8b0 0000000000000000
Nov  2 16:22:30 sean-server kernel: [ 3739.121829] Call Trace:
Nov  2 16:22:30 sean-server kernel: [ 3739.121862]  [<ffffffffa01fb632>] intel_pipe_set_base+0x2e2/0x480 [i915]
Nov  2 16:22:30 sean-server kernel: [ 3739.121917]  [<ffffffffa01fc38f>] intel_crtc_mode_set+0xbbf/0x1ab0 [i915]
Nov  2 16:22:30 sean-server kernel: [ 3739.121971]  [<ffffffffa01f716d>] ? intel_crtc_dpms+0x3d/0x130 [i915]
Nov  2 16:22:30 sean-server kernel: [ 3739.122017]  [<ffffffffa01a13be>] drm_crtc_helper_set_mode+0x2ae/0x3f0 [drm_kms_helper]
Nov  2 16:22:30 sean-server kernel: [ 3739.122070]  [<ffffffffa01a22ec>] drm_crtc_helper_set_config+0x83c/0x8e0 [drm_kms_helper]
Nov  2 16:22:30 sean-server kernel: [ 3739.122126]  [<ffffffff812b71e1>] ? idr_get_new_above+0x11/0x50
Nov  2 16:22:30 sean-server kernel: [ 3739.122168]  [<ffffffffa01a04dc>] drm_fb_helper_set_par+0x7c/0xf0 [drm_kms_helper]
Nov  2 16:22:30 sean-server kernel: [ 3739.122219]  [<ffffffffa01a06a0>] drm_fb_helper_single_fb_probe+0x150/0x2d0 [drm_kms_helper]
Nov  2 16:22:30 sean-server kernel: [ 3739.122274]  [<ffffffffa01a0424>] drm_fb_helper_hotplug_event+0x104/0x140 [drm_kms_helper]
Nov  2 16:22:30 sean-server kernel: [ 3739.122337]  [<ffffffffa020702c>] intel_fb_output_poll_changed+0x1c/0x20 [i915]
Nov  2 16:22:30 sean-server kernel: [ 3739.122386]  [<ffffffffa01a0ff4>] output_poll_execute+0x144/0x150 [drm_kms_helper]
Nov  2 16:22:30 sean-server kernel: [ 3739.122437]  [<ffffffff810f5725>] slow_work_execute+0x225/0x310
Nov  2 16:22:30 sean-server kernel: [ 3739.122476]  [<ffffffff810f596e>] slow_work_thread+0x15e/0x390
Nov  2 16:22:30 sean-server kernel: [ 3739.124348]  [<ffffffff8107f080>] ? autoremove_wake_function+0x0/0x40
Nov  2 16:22:30 sean-server kernel: [ 3739.126212]  [<ffffffff810f5810>] ? slow_work_thread+0x0/0x390
Nov  2 16:22:30 sean-server kernel: [ 3739.128079]  [<ffffffff8107eb26>] kthread+0x96/0xa0
Nov  2 16:22:30 sean-server kernel: [ 3739.129928]  [<ffffffff8100aee4>] kernel_thread_helper+0x4/0x10
Nov  2 16:22:30 sean-server kernel: [ 3739.130002]  [<ffffffff8107ea90>] ? kthread+0x0/0xa0
Nov  2 16:22:30 sean-server kernel: [ 3739.130002]  [<ffffffff8100aee0>] ? kernel_thread_helper+0x0/0x10
Nov  2 16:22:30 sean-server kernel: [ 3739.130002] Code: 81 c0 40 13 00 00 4c 89 87 90 00 00 00 48 89 87 98 00 00 00 48 89 10 f0 ff 89 70 06 00 00 48 8b 47 60 f0 29 81 74 06 00 00 c9 c3 <0f> 0b eb fe 0f 0b eb fe eb 05 90 90 90 90 90 55 48 89 e5 48 83 
Nov  2 16:22:30 sean-server kernel: [ 3739.130002] RIP  [<ffffffffa01e9dc1>] i915_gem_object_unpin+0xc1/0xd0 [i915]
Nov  2 16:22:30 sean-server kernel: [ 3739.130002]  RSP <ffff88003d363810>
Nov  2 16:22:30 sean-server kernel: [ 3739.143212] ---[ end trace 9335277ba31339cc ]---[/FONT]

Also, in /var/log/messages, similar stuff occurs at the same time:

[FONT=Courier New]Nov  2 16:22:30 sean-server kernel: [ 3739.120224] CPU 1 
Nov  2 16:22:30 sean-server kernel: [ 3739.120242] Modules linked in: snd_hda_codec_realtek saa7134_alsa mt352 saa7134_dvb videobuf_dvb dvb_core ir_lirc_codec lirc_dev tuner_xc2028 arc4 tuner snd_hda_intel iwl3945 ir_sony_decoder ir_jvc_decoder ir_rc6_decoder ir_rc5_decoder snd_hda_codec iwlcore saa7134 ir_nec_decoder i915 mac80211 snd_hwdep v4l2_common videodev v4l1_compat v4l2_compat_ioctl32 videobuf_dma_sg drm_kms_helper snd_pcm snd_timer videobuf_core ir_common ir_core tveeprom cfg80211 led_class snd soundcore drm i2c_algo_bit video snd_page_alloc output intel_agp lp parport usbhid hid e100 firewire_ohci mii firewire_core crc_itu_t
Nov  2 16:22:30 sean-server kernel: [ 3739.120909] 
Nov  2 16:22:30 sean-server kernel: [ 3739.120925] Pid: 689, comm: kslowd001 Not tainted 2.6.35-22-server #35-Ubuntu TGDII Series/Little LLUON S2
Nov  2 16:22:30 sean-server kernel: [ 3739.120984] RIP: 0010:[<ffffffffa01e9dc1>]  [<ffffffffa01e9dc1>] i915_gem_object_unpin+0xc1/0xd0 [i915]
Nov  2 16:22:30 sean-server kernel: [ 3739.121062] RSP: 0018:ffff88003d363810  EFLAGS: 00010282
Nov  2 16:22:30 sean-server kernel: [ 3739.121098] RAX: 00000000fffffff8 RBX: ffff88003bfb2800 RCX: ffff88003bef1800
Nov  2 16:22:30 sean-server kernel: [ 3739.121142] RDX: 000000000002047e RSI: 0000000000020000 RDI: ffff88003b28c400
Nov  2 16:22:30 sean-server kernel: [ 3739.121186] RBP: ffff88003d363810 R08: ffff88002f0fa000 R09: 0000000000000000
Nov  2 16:22:30 sean-server kernel: [ 3739.121230] R10: 0000036a6383e05e R11: 0000000000000001 R12: ffff88003bef1800
Nov  2 16:22:30 sean-server kernel: [ 3739.121274] R13: 0000000000000001 R14: ffffc90004e71188 R15: ffffc90004e71184
Nov  2 16:22:30 sean-server kernel: [ 3739.121319] FS:  0000000000000000(0000) GS:ffff880001f00000(0000) knlGS:0000000000000000
Nov  2 16:22:30 sean-server kernel: [ 3739.121369] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
Nov  2 16:22:30 sean-server kernel: [ 3739.121406] CR2: 00007f0435168000 CR3: 000000003b2f7000 CR4: 00000000000006e0
Nov  2 16:22:30 sean-server kernel: [ 3739.121450] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Nov  2 16:22:30 sean-server kernel: [ 3739.121494] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Nov  2 16:22:30 sean-server kernel: [ 3739.121539] Process kslowd001 (pid: 689, threadinfo ffff88003d362000, task ffff88002f132dc0)
Nov  2 16:22:30 sean-server kernel: [ 3739.121608]  ffff88003d3638c0 ffffffffa01fb632 0000000100000000 ffff880000000000
Nov  2 16:22:30 sean-server kernel: [ 3739.121672] <0> ffffffff00001400 ffff88002f132dc0 0000000000071180 000000000007119c
Nov  2 16:22:30 sean-server kernel: [ 3739.121748] <0> 00000000000711a4 00000000007e0000 ffff88003b03b8b0 0000000000000000
Nov  2 16:22:30 sean-server kernel: [ 3739.121862]  [<ffffffffa01fb632>] intel_pipe_set_base+0x2e2/0x480 [i915]
Nov  2 16:22:30 sean-server kernel: [ 3739.121917]  [<ffffffffa01fc38f>] intel_crtc_mode_set+0xbbf/0x1ab0 [i915]
Nov  2 16:22:30 sean-server kernel: [ 3739.121971]  [<ffffffffa01f716d>] ? intel_crtc_dpms+0x3d/0x130 [i915]
Nov  2 16:22:30 sean-server kernel: [ 3739.122017]  [<ffffffffa01a13be>] drm_crtc_helper_set_mode+0x2ae/0x3f0 [drm_kms_helper]
Nov  2 16:22:30 sean-server kernel: [ 3739.122070]  [<ffffffffa01a22ec>] drm_crtc_helper_set_config+0x83c/0x8e0 [drm_kms_helper]
Nov  2 16:22:30 sean-server kernel: [ 3739.122126]  [<ffffffff812b71e1>] ? idr_get_new_above+0x11/0x50
Nov  2 16:22:30 sean-server kernel: [ 3739.122168]  [<ffffffffa01a04dc>] drm_fb_helper_set_par+0x7c/0xf0 [drm_kms_helper]
Nov  2 16:22:30 sean-server kernel: [ 3739.122219]  [<ffffffffa01a06a0>] drm_fb_helper_single_fb_probe+0x150/0x2d0 [drm_kms_helper]
Nov  2 16:22:30 sean-server kernel: [ 3739.122274]  [<ffffffffa01a0424>] drm_fb_helper_hotplug_event+0x104/0x140 [drm_kms_helper]
Nov  2 16:22:30 sean-server kernel: [ 3739.122337]  [<ffffffffa020702c>] intel_fb_output_poll_changed+0x1c/0x20 [i915]
Nov  2 16:22:30 sean-server kernel: [ 3739.122386]  [<ffffffffa01a0ff4>] output_poll_execute+0x144/0x150 [drm_kms_helper]
Nov  2 16:22:30 sean-server kernel: [ 3739.122437]  [<ffffffff810f5725>] slow_work_execute+0x225/0x310
Nov  2 16:22:30 sean-server kernel: [ 3739.122476]  [<ffffffff810f596e>] slow_work_thread+0x15e/0x390
Nov  2 16:22:30 sean-server kernel: [ 3739.124348]  [<ffffffff8107f080>] ? autoremove_wake_function+0x0/0x40
Nov  2 16:22:30 sean-server kernel: [ 3739.126212]  [<ffffffff810f5810>] ? slow_work_thread+0x0/0x390
Nov  2 16:22:30 sean-server kernel: [ 3739.128079]  [<ffffffff8107eb26>] kthread+0x96/0xa0
Nov  2 16:22:30 sean-server kernel: [ 3739.129928]  [<ffffffff8100aee4>] kernel_thread_helper+0x4/0x10
Nov  2 16:22:30 sean-server kernel: [ 3739.130002]  [<ffffffff8107ea90>] ? kthread+0x0/0xa0
Nov  2 16:22:30 sean-server kernel: [ 3739.130002]  [<ffffffff8100aee0>] ? kernel_thread_helper+0x0/0x10
Nov  2 16:22:30 sean-server kernel: [ 3739.130002]  RSP <ffff88003d363810>
Nov  2 16:22:30 sean-server kernel: [ 3739.143212] ---[ end trace 9335277ba31339cc ]---[/FONT]

The kernel seems to be saying there's a bug at [FONT=Courier New]/build/buildd/linux-2.6.35/drivers/gpu/drm/i915/i915_gem.c:4209[/FONT]. Looks like we're getting closer to the problem, as this seems to be a problem with the GPU which would make sense as the issue occurs when I turn the monitor off... Can anyone yield any light on this issue? Thanks for your replies so far.

---

### Post by Ryan Dwyer on 2010-11-02
You should consider installing 10.04. The problem is not likely to be present as it's an LTS release.

Or if you want to keep your current installation you could upgrade the kernel to one of the latest. The latest ones aren't ready for primetime though. For a home server this is OK, but I wouldn't recommend this for important production servers where uptime is critical.

---

### Post by SeanDS on 2010-11-02
I might try that. Thanks.

It seems weird that the kernel would know it has encountered a bug and then point to the place where the bug is. Is this normal?

---

### Post by Ryan Dwyer on 2010-11-03
Completely normal. It's called error handling ;-)

---

