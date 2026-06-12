---
title: "Sound card gone, dummy output only Ubuntu 13.04 i686 on intel HDMI"
date: 2013-04-17
forum: Ubuntu Development Version
---

### Post by timrichardson on 2013-04-17
I have an intel NUC machine connected to my TV. After the last 13.04 kernel update (two days ago) the sound stopped working. 
I haven't changed the sound config as far as I know, so it should be a standard unity/pulseaudio set up.

The sound setting control panel shows only DummyOutput.
Normally it should show Intel HDA.  It affects the two user acconts on the machine. 


The kernel modules appear to be loaded ok

```
tim@whitlam:~$ cat /proc/asound/card0/codec* | grep Codec
Codec: Intel PantherPoint HDMI
```


```

tim@whitlam:~$ uname -r
3.8.0-18-generic
```


```

tim@whitlam:~$ lsmod | grep intel
kvm_intel             126842  0 
kvm                   376505  1 kvm_intel
snd_hda_intel          38307  0 
snd_hda_codec         117580  2 snd_hda_codec_hdmi,snd_hda_intel
snd_pcm                80890  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd                    56485  9 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device

```

---

### Post by timrichardson on 2013-04-17
in a shell, I can run alsamixer, hit F6 to view sound cards, and I see HDA Intel PCH with chip Intel Pantherpoint HDMI

---

### Post by mloebl on 2013-04-17
It may be related the bug i logged yesterday where HDMI audio stopped working with 3.8.0-18 kernel - [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1169761](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1169761)

Rolling back to 3.8.0-17 worked for me.

---

### Post by timrichardson on 2013-04-18
Rolling back to 3.8.0-17 also works for me.

---

### Post by screaminj3sus on 2013-04-21
I have the same problem only it only happens "at random". I've seen it on two different intel laptops. Sometimes when I boot up I get the dummy output. Rebooting always fixes it. Another issue is whenever I boot and get the "dummy output" bug, when I reboot it just hangs infinitely. This hang only happens when the dummy output bug happens. My theory is pulseaudio sometimes fails to start correctly or something, and when I try to to reboot it also fails to quit causing a hang.

My HDMI audio does work with the current kernel though, but my laptop is all intel, no nvidia.

---

### Post by mukareste on 2013-04-27
> **screaminj3sus said:**
> I have the same problem only it only happens "at random". I've seen it on two different intel laptops. Sometimes when I boot up I get the dummy output. Rebooting always fixes it. Another issue is whenever I boot and get the "dummy output" bug, when I reboot it just hangs infinitely. This hang only happens when the dummy output bug happens. My theory is pulseaudio sometimes fails to start correctly or something, and when I try to to reboot it also fails to quit causing a hang.

My HDMI audio does work with the current kernel though, but my laptop is all intel, no nvidia.

Same thing happens on my Lenovo laptop with Intel HDMI. After I get the dummy output device, the computer fails to reboot, and I have to power it off from the button. When I boot the laptop after that, there is no problem with the sound.

When the problem occurs, the following is logged in the syslog:

```
 Apr 27 11:26:30 traceroot kernel: [   22.639087] Modules linked in: snd_hda_codec_hdmi btusb snd_hda_codec_realtek bluetooth thinkpad_acpi snd_hda_intel(+) snd_hda_codec snd_hwdep(F) nvram(F) snd_pcm(F) iwlwifi snd_page_allo
 Apr 27 11:26:30 traceroot kernel: [   22.639268] CPU 3 
 Apr 27 11:26:30 traceroot kernel: [   22.639276] Pid: 605, comm: modprobe Tainted: GF            3.8.0-19-generic #29-Ubuntu LENOVO 23444ZG/23444ZG
 Apr 27 11:26:30 traceroot kernel: [   22.639301] RIP: 0010:[<ffffffffa032d820>]  [<ffffffffa032d820>] patch_generic_hdmi+0xe0/0x550 [snd_hda_codec_hdmi]
 Apr 27 11:26:30 traceroot kernel: [   22.639329] RSP: 0018:ffff88021030dac0  EFLAGS: 00010283
 Apr 27 11:26:30 traceroot kernel: [   22.639343] RAX: 0000000000000008 RBX: 0000000000000002 RCX: 0000000000000002
 Apr 27 11:26:30 traceroot kernel: [   22.639362] RDX: ffff880210207fd8 RSI: ffff880210207fe0 RDI: ffff880211555420
 Apr 27 11:26:30 traceroot kernel: [   22.639380] RBP: ffff88021030daf8 R08: 0000000000000001 R09: 0000000000000007
 Apr 27 11:26:30 traceroot kernel: [   22.639397] R10: 0000000000000004 R11: 0000000000000014 R12: ffff880211555000
 Apr 27 11:26:30 traceroot kernel: [   22.639415] R13: 0000000000000000 R14: 0000000000000002 R15: ffff880210208000
 Apr 27 11:26:30 traceroot kernel: [   22.639433] FS:  00007f97aff3a740(0000) GS:ffff88021e2c0000(0000) knlGS:0000000000000000
 Apr 27 11:26:30 traceroot kernel: [   22.639453] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
 Apr 27 11:26:30 traceroot kernel: [   22.639469] CR2: ffff880210207fe0 CR3: 000000020c2c0000 CR4: 00000000001407e0
 Apr 27 11:26:30 traceroot kernel: [   22.639487] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
 Apr 27 11:26:30 traceroot kernel: [   22.639505] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
 Apr 27 11:26:30 traceroot kernel: [   22.639525] Process modprobe (pid: 605, threadinfo ffff88021030c000, task ffff88020c8445c0)
 Apr 27 11:26:30 traceroot kernel: [   22.639545] Stack:
 Apr 27 11:26:30 traceroot kernel: [   22.639552]  00000000ffffffff ffffffffa0330002 ffffffffa032f8d0 0000000000000001
 Apr 27 11:26:30 traceroot kernel: [   22.639575]  ffff880211555000 00000000ffffffff ffffffffa0331000 ffff88021030db58
 Apr 27 11:26:30 traceroot kernel: [   22.639596]  ffffffffa02e0186 2d6164682d646e73 64692d6365646f63 303832363830383a
 Apr 27 11:26:30 traceroot kernel: [   22.639616] Call Trace:
 Apr 27 11:26:30 traceroot kernel: [   22.639629]  [<ffffffffa02e0186>] snd_hda_codec_configure+0x146/0x440 [snd_hda_codec]
 Apr 27 11:26:30 traceroot kernel: [   22.639652]  [<ffffffffa02772f0>] azx_probe_continue+0x3a0/0x4f0 [snd_hda_intel]
 Apr 27 11:26:30 traceroot kernel: [   22.639672]  [<ffffffffa02758b0>] ? azx_attach_pcm_stream+0x1e0/0x1e0 [snd_hda_intel]
 Apr 27 11:26:30 traceroot kernel: [   22.639694]  [<ffffffffa0276cb0>] ? azx_halt+0x30/0x30 [snd_hda_intel]
 Apr 27 11:26:30 traceroot kernel: [   22.639713]  [<ffffffffa02756d0>] ? azx_pcm_trigger+0x580/0x580 [snd_hda_intel]
 Apr 27 11:26:30 traceroot kernel: [   22.639733]  [<ffffffffa0276810>] ? azx_runtime_suspend+0x30/0x30 [snd_hda_intel]
 Apr 27 11:26:30 traceroot kernel: [   22.639753]  [<ffffffffa0273670>] ? azx_pcm_free+0x50/0x50 [snd_hda_intel]
 Apr 27 11:26:30 traceroot kernel: [   22.639773]  [<ffffffffa027779a>] azx_probe+0x35a/0x940 [snd_hda_intel]
 Apr 27 11:26:30 traceroot kernel: [   22.639793]  [<ffffffff8137b47b>] local_pci_probe+0x4b/0x80
 Apr 27 11:26:30 traceroot kernel: [   22.639809]  [<ffffffff8137b7a1>] pci_device_probe+0x111/0x120
 Apr 27 11:26:30 traceroot kernel: [   22.639826]  [<ffffffff814556c7>] driver_probe_device+0x77/0x230
 Apr 27 11:26:30 traceroot kernel: [   22.639842]  [<ffffffff8145592b>] __driver_attach+0xab/0xb0
 Apr 27 11:26:30 traceroot kernel: [   22.639857]  [<ffffffff81455880>] ? driver_probe_device+0x230/0x230
 Apr 27 11:26:30 traceroot kernel: [   22.639874]  [<ffffffff814539dd>] bus_for_each_dev+0x5d/0xa0
 Apr 27 11:26:30 traceroot kernel: [   22.639890]  [<ffffffff814551ce>] driver_attach+0x1e/0x20
 Apr 27 11:26:30 traceroot kernel: [   22.639904]  [<ffffffff81454da0>] bus_add_driver+0x190/0x280
 Apr 27 11:26:30 traceroot kernel: [   22.639921]  [<ffffffffa0300000>] ? 0xffffffffa02fffff
 Apr 27 11:26:30 traceroot kernel: [   22.639936]  [<ffffffff81455ff7>] driver_register+0x77/0x170
 Apr 27 11:26:30 traceroot kernel: [   22.639951]  [<ffffffffa0300000>] ? 0xffffffffa02fffff
 Apr 27 11:26:30 traceroot kernel: [   22.639966]  [<ffffffff8137a66c>] __pci_register_driver+0x4c/0x50
 Apr 27 11:26:30 traceroot kernel: [   22.639983]  [<ffffffffa030001e>] azx_driver_init+0x1e/0x1000 [snd_hda_intel]
 Apr 27 11:26:30 traceroot kernel: [   22.640003]  [<ffffffff8100215a>] do_one_initcall+0x12a/0x180
 Apr 27 11:26:30 traceroot kernel: [   22.640020]  [<ffffffff810bfec7>] load_module+0x10c7/0x1520
 Apr 27 11:26:30 traceroot kernel: [   22.640036]  [<ffffffff810bb830>] ? unset_module_init_ro_nx+0x80/0x80
 Apr 27 11:26:30 traceroot kernel: [   22.640054]  [<ffffffff810c03e5>] sys_init_module+0xc5/0xf0
 Apr 27 11:26:30 traceroot kernel: [   22.640071]  [<ffffffff816d379d>] system_call_fastpath+0x1a/0x1f
 Apr 27 11:26:30 traceroot kernel: [   22.640087] Code: 0f 1f 00 4d 8b bc 24 c0 00 00 00 25 00 e0 00 00 c1 e8 0c 83 c8 01 49 63 17 83 c0 01 83 f8 10 48 8d 14 92 49 8d 14 d7 48 8d 72 08 <66> 89 5a 08 c7 46 08 02 00 00 00 0f 86
 Apr 27 11:26:30 traceroot kernel: [   22.641195] RIP  [<ffffffffa032d820>] patch_generic_hdmi+0xe0/0x550 [snd_hda_codec_hdmi]
 Apr 27 11:26:30 traceroot kernel: [   22.642238]  RSP <ffff88021030dac0>
 Apr 27 11:26:30 traceroot kernel: [   22.643298] CR2: ffff880210207fe0
 Apr 27 11:26:30 traceroot kernel: [   22.700499] ---[ end trace aa6c13668eae0285 ]---
```

---

### Post by pqwoerituytrueiwoq on 2013-04-27
Using the [mainline kernel](https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater#readme) works as a workaround for this

---

### Post by dnarnold on 2013-05-01
I seem to have the same problem as post #5 and #6.  I have a Dell XPS L321X (XPS 13) which has HDA Intel PCH audio .  Since upgrading to 13.04 yesterday, I find that *occasionally* after booting up there will be no sound.  Only "Dummy Output" shows in the Output tab of Sound Settings.  If I power off to reboot, then the power off hangs at the purple screen with the blinking dots, apparently forever, and I am forced to power off with the power button.  After that the machine boots up and sound works.

> **screaminj3sus said:**
> I have the same problem only it only happens "at random". I've seen it on two different intel laptops. Sometimes when I boot up I get the dummy output. Rebooting always fixes it. Another issue is whenever I boot and get the "dummy output" bug, when I reboot it just hangs infinitely. This hang only happens when the dummy output bug happens. My theory is pulseaudio sometimes fails to start correctly or something, and when I try to to reboot it also fails to quit causing a hang.

My HDMI audio does work with the current kernel though, but my laptop is all intel, no nvidia.

---

### Post by matt7195 on 2013-05-06
Yep.  Looks like this is a flaw in 13.04.  Or maybe with dual booting against Windows 8.  

I'm having the same issue.  On random boots, "Dummy Output".

I'm running an Asus S500C.  Windows 8 factory installed. Initially dual booted 12.10 and upgraded to 13.04.  Didn't have this issue with 12.10.

Have to say, I'm a little disappointed with the bugginess of 13.04.  Especially with all the hype leading up to it.  I got my parents on Ubuntu when back Cinnamon came out.  But now with 13.04, Cinnamon sometimes fails.  Sometimes all the text on the main panel fails to load.  Sometimes it just crashes.  Also, Firefox has a major bug right now that doesn't let Yahoo Mail work correctly (tested on multiple computers and UI's).  The parents are going back to Windows 7 now.  Since I don't have any fix for them, I just had to wish them luck and recommend installing some powerful antivirus software. 

Sorry to be unloading.  I know this isn't the right part of the forum.  I'm just throwing all this out there, because I'm feeling that the Dummy Sound is part of a larger set of problems.  Love to hear more experienced users' takes on it though.

---

### Post by cariboo on 2013-05-06
This the U+1 development sub-forum if you have a problem with Raring, please post it in the appropriate place.

For General questions try [General Help]("http://ubuntuforums.org/forumdisplay.php?f=331"), for comments, complaints and experiences try [Ubuntu, Linux and OS Chat]("http://ubuntuforums.org/forumdisplay.php?f=434").

Thread closed.

---

