---
title: "nVidia woes - can't run live DE or install"
date: 2015-01-18
forum: Ubuntu Development Version
---

### Post by kansasnoob on 2015-01-18
One of my boxes has nVidia C61 [GeForce 7025 / nForce 630a] (rev a2) graphics and it's just not possible to get any actual graphics after the advanced boot option screen, all I ever get is this:

[ATTACH=CONFIG]259337[/ATTACH]

I've tried the nomodeset boot option to no avail, any thoughts?

I even thought about installing Utopic and then upgrading to Vivid but while Utopic displays the live DE OK (either Ubuntu or Ubuntu GNOME) as soon as I click on Install the screen does the same thing as I get in Vivid :(

Trusty is the last known working OS on this box, it works flawlessly with either nouveau or nvidia drivers for my purposes. I typically use the current nvidia drivers though unless a kernel update borks things, then I'll temporarily use nouveau until I get things sorted.

---

### Post by kansasnoob on 2015-01-18
Just tried Lubuntu Vivid and it works fine so I think it must be the emphasis both Ubuntu and Ubuntu GNOME put on 3D rendering - more like a Mutter and Compiz issue maybe :confused:

---

### Post by pressureman on 2015-01-18
I have a Thinkpad T530 with Nvidia Optimus graphics, which has been running Ubuntu GNOME 14.10 flawlessly, using the proprietary nvidia-331 drivers.

Yesterday I bravely decided to update it to 15.04, and immediately noticed that the built-in display was no longer working - only my external Samsung LCD connected via DisplayPort cable. Curiously, "xrandr --query" reported that the internal (LVDS) panel was disconnected. I tried various things, including using the xorg-edgers repo (installing nvidia-346), or booting the old 3.16 kernel (with the older nvidia-331 drivers). I couldn't figure out why the system thought that the LVDS panel was disconnected, because bbswitch clearly saw both adapters during bootup:

```

Jan 18 20:23:13 thinkpad kernel: [   10.804198] bbswitch: version 0.7
Jan 18 20:23:13 thinkpad kernel: [   10.804204] bbswitch: Found integrated VGA device 0000:00:02.0: \_SB_.PCI0.VID_
Jan 18 20:23:13 thinkpad kernel: [   10.804208] bbswitch: Found discrete VGA device 0000:01:00.0: \_SB_.PCI0.PEG_.VID_
Jan 18 20:23:13 thinkpad kernel: [   10.804216] ACPI Warning: \_SB_.PCI0.PEG_.VID_._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20140926/nsarguments-95)
Jan 18 20:23:13 thinkpad kernel: [   10.804461] bbswitch: detected an Optimus _DSM function
Jan 18 20:23:13 thinkpad kernel: [   10.804470] bbswitch: Succesfully loaded. Discrete card 0000:01:00.0 is on

```

The only combination that resulted in any display output at all was the one that *only* displayed on the external Samsung LCD. If I tried to get both displays working, I would just end up with a blank screen on both - however the displays *were* being driven by a signal - it just happened to be completely black.

I get the following stack trace in dmesg with kernel 3.18, which never used to occur with 3.16. This also happened with the nvidia-346 driver from xorg-edgers, which was supposed to have this bug fixed.

```

[   11.443800] ------------[ cut here ]------------
[   11.443805] WARNING: CPU: 0 PID: 1702 at /build/buildd/linux-3.18.0/drivers/gpu/drm/drm_ioctl.c:143 drm_setversion+0x17e/0x190 [drm]()
[   11.443842] No drm_driver.set_busid() implementation provided by nv_drm_driver [nvidia]. Use drm_dev_set_unique() to set the unique name explicitly.
[   11.443843] Modules linked in:
[   11.443844]  nbd snd_hda_codec_hdmi dm_crypt intel_rapl x86_pkg_temp_thermal intel_powerclamp coretemp kvm_intel kvm nvidia(POE) crct10dif_pclmul crc32_pclmul arc4 ghash_clmulni_intel snd_hda_codec_realtek iwldvm aesni_intel snd_hda_codec_generic uvcvideo aes_x86_64 lrw mac80211 gf128mul glue_helper thinkpad_acpi ablk_helper cryptd videobuf2_vmalloc nvram videobuf2_memops videobuf2_core snd_seq_midi snd_hda_intel snd_seq_midi_event v4l2_common snd_hda_controller snd_rawmidi videodev snd_hda_codec media snd_hwdep iwlwifi snd_seq drm btusb snd_pcm snd_seq_device snd_timer cfg80211 joydev serio_raw snd mei_me mei shpchp lpc_ich soundcore rfcomm bnep bluetooth wmi mac_hid parport_pc ppdev lp nls_iso8859_1 parport btrfs xor raid6_pq hid_generic usbhid hid e1000e firewire_ohci sdhci_pci psmouse ahci firewire_core
[   11.443863]  libahci sdhci ptp crc_itu_t pps_core video
[   11.443866] CPU: 0 PID: 1702 Comm: Xorg Tainted: P        W  OE  3.18.0-9-generic #10-Ubuntu
[   11.443867] Hardware name: LENOVO 2392CTO/2392CTO, BIOS G4ETA2WW (2.62 ) 08/21/2014
[   11.443867]  0000000000000009 ffff8800da72bca8 ffffffff827ad5ac 0000000000000007
[   11.443869]  ffff8800da72bcf8 ffff8800da72bce8 ffffffff82074c01 ffff8800da72bd68
[   11.443870]  ffff8800da72bdf0 ffff880306c4f000 ffff880306f12d80 ffff880306c4f000
[   11.443871] Call Trace:
[   11.443873]  [<ffffffff827ad5ac>] dump_stack+0x46/0x58
[   11.443875]  [<ffffffff82074c01>] warn_slowpath_common+0x81/0xa0
[   11.443876]  [<ffffffff82074c66>] warn_slowpath_fmt+0x46/0x50
[   11.443881]  [<ffffffffc079721e>] drm_setversion+0x17e/0x190 [drm]
[   11.443886]  [<ffffffffc0796bdc>] drm_ioctl+0x2cc/0x680 [drm]
[   11.443888]  [<ffffffff82204919>] ? putname+0x29/0x40
[   11.443892]  [<ffffffffc07970a0>] ? drm_noop+0x40/0x40 [drm]
[   11.443894]  [<ffffffff8220586a>] ? do_filp_open+0x3a/0xb0
[   11.443896]  [<ffffffff82207ec8>] do_vfs_ioctl+0x2c8/0x4a0
[   11.443897]  [<ffffffff82204676>] ? final_putname+0x26/0x50
[   11.443899]  [<ffffffff82204919>] ? putname+0x29/0x40
[   11.443901]  [<ffffffff821f2929>] ? do_sys_open+0x1b9/0x280
[   11.443902]  [<ffffffff82208121>] SyS_ioctl+0x81/0xa0
[   11.443904]  [<ffffffff827b526d>] system_call_fastpath+0x16/0x1b
[   11.443904] ---[ end trace 2f501d71accdc5ee ]---

```

With proprietary Nvidia drivers loaded, and Optimus enabled in the BIOS, the best I could get was the external display working. Everything pointed to the fact that both displays were recognised by the system, but in the Xorg.0.log, I saw some errors about not being able to open the intel display - possibly explaining why the built-in display wasn't working. I wonder if bumblebee needs to be updated for kernel 3.18.

```

[    14.854] (EE) intel(G1): [drm] failed to set drm interface version: Permission denied [13].
[    14.854] (II) intel(G1): [drm] Contents of '/sys/kernel/debug/dri/0/clients':
[    14.855] (II) intel(G1): [drm]              command   pid dev master a   uid      magic
[    14.855] (II) intel(G1): [drm]            plymouthd   231   0   n    y     0          0
[    14.855] (II) intel(G1): [drm]                 Xorg  1689   0   y    y     0          0
[    14.855] (II) intel(G1): [drm]                 Xorg  1689   0   n    y     0          0
[    14.855] (EE) intel(G1): Failed to claim DRM device.
[    14.855] (II) UnloadModule: "intel"

```

I don't know whether these errors used to be logged when things were previously working fine with Ubuntu GNOME 14.10.

So at the moment, I've had to resort to switching off Optimus in the BIOS, and just setting it to run the Nvidia card all the time. AFAIK, this won't make a lot of difference to Linux, since the Nvidia drivers required me to log out / in again, if I wanted to switch from Nvidia to Intel in the Prime profile - something which I never did, nor did I ever run individual apps using Nvidia. I have a feeling that my battery life is going to be a bit less regardless, however.

Before anyone asks why I don't simply use the Nouveau driver - it runs the notebook very hot, and causes display artefacts on the screen. In fact, I had to rename the nouveau.ko module to something rather unmentionable, because it kept getting in the way and sneaking its way into the initrd, causing all kinds of problems for the proprietary Nvidia driver.

---

### Post by kansasnoob on 2015-01-18
> **pressureman said:**
> I have a Thinkpad T530 with Nvidia Optimus graphics, which has been running Ubuntu GNOME 14.10 flawlessly, using the proprietary nvidia-331 drivers.

Yesterday I bravely decided to update it to 15.04, and immediately noticed that the built-in display was no longer working - only my external Samsung LCD connected via DisplayPort cable. Curiously, "xrandr --query" reported that the internal (LVDS) panel was disconnected. I tried various things, including using the xorg-edgers repo (installing nvidia-346), or booting the old 3.16 kernel (with the older nvidia-331 drivers). I couldn't figure out why the system thought that the LVDS panel was disconnected, because bbswitch clearly saw both adapters during bootup:

```

Jan 18 20:23:13 thinkpad kernel: [   10.804198] bbswitch: version 0.7
Jan 18 20:23:13 thinkpad kernel: [   10.804204] bbswitch: Found integrated VGA device 0000:00:02.0: \_SB_.PCI0.VID_
Jan 18 20:23:13 thinkpad kernel: [   10.804208] bbswitch: Found discrete VGA device 0000:01:00.0: \_SB_.PCI0.PEG_.VID_
Jan 18 20:23:13 thinkpad kernel: [   10.804216] ACPI Warning: \_SB_.PCI0.PEG_.VID_._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (2
0140926/nsarguments-95)
Jan 18 20:23:13 thinkpad kernel: [   10.804461] bbswitch: detected an Optimus _DSM function
Jan 18 20:23:13 thinkpad kernel: [   10.804470] bbswitch: Succesfully loaded. Discrete card 0000:01:00.0 is on

```

The only combination that resulted in any display output at all was the one that *only* displayed on the external Samsung LCD. If I tried to get both displays working, I would just end up with a blank screen on both - however the displays *were* being driven by a signal - it just happened to be completely black.

I get the following stack trace in dmesg with kernel 3.18, which never used to occur with 3.16. This also happened with the nvidia-346 driver from xorg-edgers, which was supposed to have this bug fixed.

```

[   11.443800] ------------[ cut here ]------------
[   11.443805] WARNING: CPU: 0 PID: 1702 at /build/buildd/linux-3.18.0/drivers/gpu/drm/drm_ioctl.c:143 drm_setversion+0x17e/0x190 [drm]()
[   11.443842] No drm_driver.set_busid() implementation provided by nv_drm_driver [nvidia]. Use drm_dev_set_unique() to set the unique name explicitly.
[   11.443843] Modules linked in:
[   11.443844]  nbd snd_hda_codec_hdmi dm_crypt intel_rapl x86_pkg_temp_thermal intel_powerclamp coretemp kvm_intel kvm nvidia(POE) crct10dif_pclmul crc32_pclmul arc4 ghash_clmulni_intel snd_hda_codec_realtek iwldvm aesni_intel snd_hda_codec_generic uvcvideo aes_x86_64 lrw mac80211 gf128mul glue_helper thinkpad_acpi ablk_helper cryptd videobuf2_vmalloc nvram videobuf2_memops videobuf2_core snd_seq_midi snd_hda_intel snd_seq_midi_event v4l2_common snd_hda_controller snd_rawmidi videodev snd_hda_codec media snd_hwdep iwlwifi snd_seq drm btusb snd_pcm snd_seq_device snd_timer cfg80211 joydev serio_raw snd mei_me mei shpchp lpc_ich soundcore rfcomm bnep bluetooth wmi mac_hid parport_pc ppdev lp nls_iso8859_1 parport btrfs xor raid6_pq hid_generic usbhid hid e1000e firewire_ohci sdhci_pci psmouse ahci firewire_core
[   11.443863]  libahci sdhci ptp crc_itu_t pps_core video
[   11.443866] CPU: 0 PID: 1702 Comm: Xorg Tainted: P        W  OE  3.18.0-9-generic #10-Ubuntu
[   11.443867] Hardware name: LENOVO 2392CTO/2392CTO, BIOS G4ETA2WW (2.62 ) 08/21/2014
[   11.443867]  0000000000000009 ffff8800da72bca8 ffffffff827ad5ac 0000000000000007
[   11.443869]  ffff8800da72bcf8 ffff8800da72bce8 ffffffff82074c01 ffff8800da72bd68
[   11.443870]  ffff8800da72bdf0 ffff880306c4f000 ffff880306f12d80 ffff880306c4f000
[   11.443871] Call Trace:
[   11.443873]  [<ffffffff827ad5ac>] dump_stack+0x46/0x58
[   11.443875]  [<ffffffff82074c01>] warn_slowpath_common+0x81/0xa0
[   11.443876]  [<ffffffff82074c66>] warn_slowpath_fmt+0x46/0x50
[   11.443881]  [<ffffffffc079721e>] drm_setversion+0x17e/0x190 [drm]
[   11.443886]  [<ffffffffc0796bdc>] drm_ioctl+0x2cc/0x680 [drm]
[   11.443888]  [<ffffffff82204919>] ? putname+0x29/0x40
[   11.443892]  [<ffffffffc07970a0>] ? drm_noop+0x40/0x40 [drm]
[   11.443894]  [<ffffffff8220586a>] ? do_filp_open+0x3a/0xb0
[   11.443896]  [<ffffffff82207ec8>] do_vfs_ioctl+0x2c8/0x4a0
[   11.443897]  [<ffffffff82204676>] ? final_putname+0x26/0x50
[   11.443899]  [<ffffffff82204919>] ? putname+0x29/0x40
[   11.443901]  [<ffffffff821f2929>] ? do_sys_open+0x1b9/0x280
[   11.443902]  [<ffffffff82208121>] SyS_ioctl+0x81/0xa0
[   11.443904]  [<ffffffff827b526d>] system_call_fastpath+0x16/0x1b
[   11.443904] ---[ end trace 2f501d71accdc5ee ]---

```

With proprietary Nvidia drivers loaded, and Optimus enabled in the BIOS, the best I could get was the external display working. Everything pointed to the fact that both displays were recognised by the system, but in the Xorg.0.log, I saw some errors about not being able to open the intel display - possibly explaining why the built-in display wasn't working. I wonder if bumblebee needs to be updated for kernel 3.18.

```

[    14.854] (EE) intel(G1): [drm] failed to set drm interface version: Permission denied [13].
[    14.854] (II) intel(G1): [drm] Contents of '/sys/kernel/debug/dri/0/clients':
[    14.855] (II) intel(G1): [drm]              command   pid dev master a   uid      magic
[    14.855] (II) intel(G1): [drm]            plymouthd   231   0   n    y     0          0
[    14.855] (II) intel(G1): [drm]                 Xorg  1689   0   y    y     0          0
[    14.855] (II) intel(G1): [drm]                 Xorg  1689   0   n    y     0          0
[    14.855] (EE) intel(G1): Failed to claim DRM device.
[    14.855] (II) UnloadModule: "intel"

```

I don't know whether these errors used to be logged when things were previously working fine with Ubuntu GNOME 14.10.

So at the moment, I've had to resort to switching off Optimus in the BIOS, and just setting it to run the Nvidia card all the time. AFAIK, this won't make a lot of difference to Linux, since the Nvidia drivers required me to log out / in again, if I wanted to switch from Nvidia to Intel in the Prime profile - something which I never did, nor did I ever run individual apps using Nvidia. I have a feeling that my battery life is going to be a bit less regardless, however.

Before anyone asks why I don't simply use the Nouveau driver - it runs the notebook very hot, and causes display artefacts on the screen. In fact, I had to rename the nouveau.ko module to something rather unmentionable, because it kept getting in the way and sneaking its way into the initrd, causing all kinds of problems for the proprietary Nvidia driver.

I don't have any Optimus hardware to test on but I know at one time there was a bug with 'gdm' that kept Optimus from working properly. It might be worth trying 'lightdm' with the 'lightdm-gtk-greeter' just to rule out a regression (assuming that was once fixed).

---

### Post by kansasnoob on 2015-01-19
Soooooo ............... I've been playing. Lubuntu runs OK with 'xserver-xorg-video-nouveau', but I tried installing 'gnome-shell' and the desktop 'breaks' as soon as I try to do anything. I mean as soon as I move the mouse to the upper left and display the dash the screen tears as shown in the above screenshot.

I need to do some additional playing but I'd bet nouveau is simply incapable of running either compiz or mutter which makes installing either Ubuntu or Ubuntu GNOME impossible on that otherwise great hardware :(

I need to let this rattle around in my head for a while but I'll also try Xubuntu. I'm betting that either Ubuntu or Ubuntu GNOME would run OK on this hardware after installing the 'nividia-current' drivers but installation of a pure OS would be complex for noobs.

---

### Post by ventrical on 2015-01-19
Sound like graphcs card is being deprecated by driver mods. Back a couple cycles ago I had this excellent dev kubuntu cycle working. One day I updated and it busted. Reason: The developers stopped writing patches for that hardware.

With Unity and Compiz  we know these things are going to happen. 

Regards..

---

### Post by kansasnoob on 2015-01-19
> **ventrical said:**
> Sound like graphcs card is being deprecated by driver mods. Back a couple cycles ago I had this excellent dev kubuntu cycle working. One day I updated and it busted. Reason: The developers stopped writing patches for that hardware.

With Unity and Compiz  we know these things are going to happen. 

Regards..

Apparently also GNOME Shell and Mutter.

---

### Post by kansasnoob on 2015-01-19
As expected - Xubuntu, Lubuntu, and GNOME Flashback w/Metacity run OK with the nouveau drivers, but Ubuntu, either the gnome-shell or classic sessions  in Ubuntu GNOME, and Flashback w/Compiz won't run with nouveau.

OTOH if you begin with Lubuntu or Xubuntu and install the nvidia drivers (304.25 I think) all DE's will run swell.

Now to think of an appropriate brief bug title - that's sometimes the hardest part of filing a bug report :biggrin:

---

### Post by ventrical on 2015-01-19
> **kansasnoob said:**
> As expected - Xubuntu, Lubuntu, and GNOME Flashback w/Metacity run OK with the nouveau drivers, but Ubuntu, either the gnome-shell or classic sessions  in Ubuntu GNOME, and Flashback w/Compiz won't run with nouveau.
  :biggrin:

  I have gnome-session running fine here on nouveau - but I am off topic as it is not pertinent to your particlar test case. It is an older card that produces another gedit bug (in ubuntu-unity) in another thread on this card:

```



01:00.0 VGA compatible controller: NVIDIA Corporation G98 [GeForce 8400 GS Rev. 2] (rev a1)

```

but it doesn't happen in gnome-session.

Regards..

---

### Post by kansasnoob on 2015-01-19
Bug filed:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/1412602](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/1412602)

---

### Post by grahammechanical on 2015-01-19
In your bug report I saw this

> [COLOR=#333333][FONT=monospace]I next opened the Additional drivers UI and chose nvidia-304.125 (current) and all DE's perform quite well with the proprietary drivers so I deduced that nouveau might be the culprit.[/FONT][/COLOR]

I think it strange that Nouveau should be the problem and not the newish Nvidia drivers dropping support for that Nvidia adapter, which has not happened, it seems. The Try/Install session runs on Nouveau and not a proprietary driver. It should use llvmpipe if the graphic adapter cannot support Ubuntu 3D. We see cases where the Try/Install session works fine but the installation breaks on the first reboot and I suspect that is because Install third party software was ticked and now the system is loading the proprietary driver. This problem seems to be a reversal of what I would expect to happen.

Just as we thought it safe to go back into the water. :)

Regards.

---

### Post by kansasnoob on 2015-01-26
I finally got around to doing some more testing and nouveau works OK with the 3.19.0-031900rc5-generic mainline kernel, but the nvidia module fails to build properly against that kernel. Regardless I suppose we're looking at a kernel problem, I now need to test a newer build of Ubuntu GNOME and see what happens :)

And I see that 3.19.0-031900rc6 is out already so maybe nvidia will build right with it. I wonder if we're sticking with 3.18 for Vivid or if we're going to jump to 3.19 :confused:

---

### Post by kansasnoob on 2015-02-14
It's been a while since I've tried Vivid on the affected hardware but this AM I installed Ubuntu GNOME Vivid Alpha 2, then booted with the nouveau.config=NvMSI=0 boot parameter, then applied all available updates, and it seems to be running GNOME Shell just fine with the latest Vivid kernel:

```
lance@lance-AMD-desktop:~$ uname -r
3.18.0-13-generic

```

```
lance@lance-AMD-desktop:~$ sudo lshw -c video
[sudo] password for lance: 
  *-display               
       description: VGA compatible controller
       product: C61 [GeForce 7025 / nForce 630a]
       vendor: NVIDIA Corporation
       physical id: d
       bus info: pci@0000:00:0d.0
       version: a2
       width: 64 bits
       clock: 66MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       **[COLOR="#FF0000"]configuration: driver=nouveau latency=0[/COLOR]**
       resources: irq:21 memory:fb000000-fbffffff memory:e0000000-efffffff memory:fc000000-fcffffff memory:80000000-8001ffff

```

So it's time to do some follow up bug reporting work.

---

### Post by kansasnoob on 2015-02-14
So ............... for now I moved on to testing 14.04.2, this one installed w/Ubuntu-GNOME 14.04.2 LTS "Trusty Tahr" - Release amd64 (20150203), and while 3.16.0-30-generic was affected I pulled 3.16.0-31-generic from trusty-proposed and it appeared to be OK for a while, at least I was not getting the same screen corruption. 

In fact I began this post from that Trusty install (*[COLOR="#800080"]thanks forum restore content feature[/COLOR]*) but before I was done the screen became unresponsive, but not entirely frozen because I could move the mouse pointer, then after a minute or two this appeared on the screen:

[ATTACH=CONFIG]259966[/ATTACH]

The screen then went blank before I could grab anymore pics.

**EDIT**: I did some more fiddling last night and this AM. 

3.16.0-31-generic is also available in utopic-proposed and fixes this issue in Utopic, and I was not able to reproduce the above crash in Utopic.

So I did some pic-to-text translating (which may not be 100% correct):

```
[ 1206.026900] nouveau E[     DRM] GPU lockup - switching to software fbcon

[ 1305.160013] nouveau E[Xorg[955]] failed to idle channel 0xeeee0000 [Xorg[955]]

[ 1320.160018] nouveau E[Xorg[955]] failed to idle channel 0xeeee0000 [Xorg[955]]

[ 1328.076012] BUG: soft lockup - GPU#0 stuck for 21sf [gnome-shell:1740]
```

And I think that's this bug:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/1291574](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/1291574)

And it appears not to be limited to Ubuntu:

[http://forums.fedoraforum.org/showthread.php?t=300720](http://forums.fedoraforum.org/showthread.php?t=300720)

I used the search words:

> nouveau E[     DRM] GPU lockup - switching to software fbcon

So now it's time to recap ................... arrgh, brain needs rest ;)

**EDIT #2**: So I'm back in the affected OS and I found an actual crash report in /var/log/crash but it refuses to file because it says:

> This problem report is damaged and cannot be processed.

EOF Error('Compressed file ended before the end-of-stream marker was reached',)

---

### Post by VinDSL on 2015-02-14
> **kansasnoob said:**
> I finally got around to doing some more testing and nouveau works OK with the 3.19.0-031900rc5-generic mainline kernel, but the nvidia module fails to build properly against that kernel.

Sorry for being late to the party!  

I don't know how I missed this thread, but my recent woes with the nVidia-304.125 legacy drivers mirror yours exactly.

Actually, my probs started when I tried to install the 3.19rcs.  As you stated, the nVidia drivers wouldn't survive the initial build.  This is not an uncommon occurrence for me, since I'm running legacy hardware, e.g. ancient iron by nowadays standards (gaming desktop circa 2005).

Usually, all I need to do, when this happens, is surf the web for a kernel patch -- but, this time I searched for weeks without success.  It's as if nVidia legacy support has fallen off the face of the earth.

When 3.19-rc7  came out, I finally gave up and reverted to Nouveau drivers, and BooM!  Everything started working perfectly -- in both Gnome Shell and Unity.

Here's my current config (as I type)....

```
~ VinDSL Unity Debug Script 15.02.13 (vindsl.com) ~
Current Date/Time: Sat Feb 14 16:05:48 UTC 2015
Distro Release: Ubuntu Vivid Vervet (development branch)
Kernel Release: Linux 3.19.0-031900-generic
Gnome Release: GNOME Shell 3.14.3
Unity Release: unity 7.3.1

OpenGL vendor string:   nouveau
OpenGL renderer string: Gallium 0.4 on NV4B
OpenGL version string:  2.1 Mesa 10.4.2

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

Browser Release: Chromium ver.40.0.2214.111

Package: mesa-utils
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 123
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Source: mesa-demos
Version: 8.2.0-1build1
Replaces: xbase-clients (<< 6.8.2-38)
Depends: libc6 (>= 2.4), libgl1-mesa-glx | libgl1, libx11-6
Description: Miscellaneous Mesa GL utilities
 This package provides several basic GL utilities built by Mesa, including
 glxinfo and glxgears.
Original-Maintainer: Debian X Strike Force <debian-x@lists.debian.org>
Homepage: http://mesa3d.org/

Package: mesa-common-dev
 Version: 10.4.2-2ubuntu3

Package: xserver-xorg-core
  Installed: 2:1.16.2.901-1ubuntu3

Package: xserver-common
  Installed: 2:1.16.2.901-1ubuntu3

Package: xserver-xephyr
  Installed: 2:1.16.2.901-1ubuntu3

Tree Map of PCI Devices:
-[0000:00]-+-00.0  Intel Corporation 82875P/E7210 Memory Controller Hub
           +-01.0-[01]----00.0  NVIDIA Corporation G73 [GeForce 7600 GT]
           +-03.0-[02]----01.0  Intel Corporation 82547EI Gigabit Ethernet Controller
           +-06.0  Intel Corporation 82875P/E7210 Processor to I/O Memory Interface
           +-1d.0  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
           +-1d.1  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
           +-1d.2  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3
           +-1d.3  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4
           +-1d.7  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
           +-1e.0-[03]----0c.0  Lite-On Communications Inc LNE100TX
           +-1f.0  Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge
           +-1f.2  Intel Corporation 82801EB (ICH5) SATA Controller
           +-1f.3  Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller
           \-1f.5  Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller

Display Properties:
 lcd monitor:    Dell UltraSharp 1907FP (analog input)
  dimensions:    1280x1024 pixels (338x270 millimeters)
  resolution:    96x96 dots per inch


```

Truth be told, Nouveau is working so well with GS and Unity, I'm in no hurry to hassle with seemingly unsupported nVidia drivers.

That said, I'm going to watch this thread closely for a fix.

Keep up the good fight, and please keep us updated!  If I discover anything remarkable, I'll do the same  ;)

---

### Post by ventrical on 2015-02-17
> **VinDSL said:**
> Sorry for being late to the party!  

I don't know how I missed this thread, but my recent woes with the nVidia-304.125 legacy drivers mirror yours exactly.

Actually, my probs started when I tried to install the 3.19rcs.  As you stated, the nVidia drivers wouldn't survive the initial build.  This is not an uncommon occurrence for me, since I'm running legacy hardware, e.g. ancient iron by nowadays standards (gaming desktop circa 2005).

Usually, all I need to do, when this happens, is surf the web for a kernel patch -- but, this time I searched for weeks without success.  It's as if nVidia legacy support has fallen off the face of the earth.



  Here is that 2012 reminder from Linus :) lol

[https://www.youtube.com/watch?v=IVpOyKCNZYw](https://www.youtube.com/watch?v=IVpOyKCNZYw)

---

### Post by VinDSL on 2015-02-18
> **ventrical said:**
> Here is that 2012 reminder from Linus :) lol


Well said.  :D

---

### Post by vickumar on 2015-02-26
Same issues here.

Running kernel 3.18.7 - only nvidia-331 (not from xedgers) works for me and also the legacy nvidia 304 driver.  These drivers also suck when docking my laptop (doesn't recognize the external VGA and DVI ports from the dock).

There has to be some combination of kernel/nvidia drivers that works right?

---

### Post by ventrical on 2015-02-26
I got this hunch that all this has to do with upstart. if I choose systemd at grub everything works out. I am going to try and install nvidia from additional drivers.

---

### Post by ventrical on 2015-02-26
Booted into gnomeshell /systemd with 4.x.x-x kernel and : 

Now for reboot:

---

### Post by ventrical on 2015-02-26
The above process does not remove nouveau-current so it is useless.

Trying to build for 3.18.x-x

...

edit:

Nope! It also build for 4.x.x-x.

Blackscreen.

---

### Post by vickumar on 2015-02-26
Have you tried blacklisting nouveau in modprobe?

These lines, at some point, were necessary with nvidia I think - in /etc/modeprobe.d/blacklist.conf, at the end of the file:

> blacklist nouveau
blacklist lbm-nouveau
blacklist nvidia-173
blacklist nvidia-96
blacklist nvidia-current
blacklist nvidia-173-updates
blacklist nvidia-96-updates
alias nvidia nvidia_current_updates
alias nouveau off
alias lbm-nouveau off
options nouveau modeset=0


Using the 331 drivers, it looks like everything works okay (reasonably stable), but it has trouble with docking.

My BIOS is set for optimus, and it looks like both cards, integrated and discrete come up:

> lspci |grep VGA

00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: NVIDIA Corporation GF119M [Quadro NVS 4200M] (rev a1)

And one is using the nvidia driver and one is using the i915 Intel driver.  Still haven't gotten bumblebee working.

So, turning off Optimus mode and OS detection in the BIOS results in a kernel panic.  Using Optimus with any driver higher than 331, results in a black screen, but the kernel apparently loads - I can CTL+ALT+n to other virtual terminals.  And using nvidia 331 or legacy drivers doesn't work with a docking station, only the VGA port on the laptop can connect to an external monitor.

Also, are people using the xedgers ppa's or is the better approach to run NVIDIA's installer - I can never get this thing to work, even after turning lightdm off - [http://www.nvidia.com/Download/index.aspx?lang=en-us?](http://www.nvidia.com/Download/index.aspx?lang=en-us?)

---

### Post by vickumar on 2015-02-26
@Ventrical

Looking at that screenshot, you're using the legacy 304 drivers.  Does any version of the drivers work?  The latest should be nvidia-346, and there's also nvidia-340, nvidia-331, nvidia-331-updates.

---

### Post by ventrical on 2015-02-27
> **vickumar said:**
> @Ventrical

Looking at that screenshot, you're using the legacy 304 drivers.  Does any version of the drivers work?  The latest should be nvidia-346, and there's also nvidia-340, nvidia-331, nvidia-331-updates.

[s]1. It will not build against 4.n.n.-n kernel.
2. With 3.18.n-n it uses346. The 304 is just the settings module version.[/s]

  I'll see if I can bust it.:)

edit:

Used synaptic to install 346 on 4.n.n-n. No errors . Now , reboot.

---

### Post by ventrical on 2015-02-27
reboot and now I get llvmpipe. It works and all but no anims. Nouveau is much smoother.

---

### Post by grahammechanical on 2015-02-27
> [COLOR=#000000]reboot and now I get llvmpipe. It works and all but no anims. [/COLOR]

Is it also low screen resolution? I am getting both llvmpipe and low screen resolution. I used the xorg-edgers ppa to install nvidia 346.47 but it does not build the nvidia module on kernel 4.0.

---

### Post by ventrical on 2015-02-27
> **grahammechanical said:**
> Is it also low screen resolution? I am getting both llvmpipe and low screen resolution. I used the xorg-edgers ppa to install nvidia 346.47 but it does not build the nvidia module on kernel 4.0.

I have the same screen resolution but no anims or eye candy. What I think it is , is that it obsoleted my Quattro. I 'll switch adapters  (maybe) and see what happens .... honestly .. nouveau works so well  I am getting lazy :)

---

### Post by grahammechanical on 2015-02-27
> [COLOR=#000000]that it obsoleted my Quattro.[/COLOR]

I am thinking the same thing. I installed nvidia 346.7 on a vivid with the 3.16 kernel and a GT220 adapter and I got low resolution llvmpipe and a desktop without Unity. Unless the existence of kernel 4.0 messed a lot of things up. I purged nvidia and I still could not get into a desktop with Unity even with llvmpipe and low resolution.

I went to the Nvidia web site and the only driver it would offer for my video adapter card was 340.

---

### Post by ventrical on 2015-02-27
Here is what I get with nouveau+4.x.x-x kernel.

```

 *-display
                description: VGA compatible controller
                product: G71GL [Quadro FX 3500]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: vga_controller bus_master cap_list rom
                configuration: driver=nouveau latency=0
                resources: irq:29 memory:fd000000-fdffffff memory:c0000000-cfffffff memory:fc000000-fcffffff ioport:9c00(size=128) memory:fe7e0000-fe7fffff

```

with the nVidia 346 I get <UNCLAIMED> so even though the driver installs it is not being used... or whatever .. ie; Gallium 4.N on llvmpipe shannuggins. :)

I am going to switch adpaters and re-install 346.

Regards..

---

### Post by ventrical on 2015-02-27
Here is what I get after switching cards and installing nvidia-current

```

*-display UNCLAIMED
                description: VGA compatible controller
                product: GT218 [GeForce 210]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a2
                width: 64 bits
                clock: 33MHz
                capabilities: vga_controller bus_master cap_list
                configuration: latency=0
                resources: memory:fd000000-fdffffff memory:c0000000-cfffffff memory:dc000000-ddffffff ioport:9c00(size=128) memory:fe780000-fe7fffff

```

and I have the Commadore 64 type screen resolution :)

.. will now try 346.

edit:

Just not working here.

---

### Post by ventrical on 2015-02-27
> **vickumar said:**
> Have you tried blacklisting nouveau in modprobe?

These lines, at some point, were necessary with nvidia I think - in /etc/modeprobe.d/blacklist.conf, at the end of the file:




Using the 331 drivers, it looks like everything works okay (reasonably stable), but it has trouble with docking.

My BIOS is set for optimus, and it looks like both cards, integrated and discrete come up:



And one is using the nvidia driver and one is using the i915 Intel driver.  Still haven't gotten bumblebee working.

So, turning off Optimus mode and OS detection in the BIOS results in a kernel panic.  Using Optimus with any driver higher than 331, results in a black screen, but the kernel apparently loads - I can CTL+ALT+n to other virtual terminals.  And using nvidia 331 or legacy drivers doesn't work with a docking station, only the VGA port on the laptop can connect to an external monitor.

Also, are people using the xedgers ppa's or is the better approach to run NVIDIA's installer - I can never get this thing to work, even after turning lightdm off - [http://www.nvidia.com/Download/index.aspx?lang=en-us?](http://www.nvidia.com/Download/index.aspx?lang=en-us?)

Thanks .

They just will not build against 4.n.n.-n (not supported).

---

