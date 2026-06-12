---
title: "No audio output on computer after upgrading to 18.10 beta"
date: 2018-10-07
forum: Ubuntu Development Version
---

### Post by thedoctor818772 on 2018-10-07
Just a few days ago I upgraded my HP Notebook from 18.04 to 18.10 beta  and now my audio does not work at all. When I go to the audio settings,  all I see is a "dummy output". I see this in the terminal:

```

 00:1f.3 Audio device [0403]: Intel Corporation Sunrise Point-LP HD Audio [8086:9d70] (rev 21)	Subsystem: Hewlett-Packard Company Sunrise Point-LP HD Audio [103c:81eb]
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd_hda_intel, snd_soc_skl
```

and this:

```

snd_hda_intel          40960  3snd_hda_codec         126976  4 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_realtek
snd_hda_core           81920  7 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_ext_core,snd_hda_codec,snd_hda_codec_realtek,snd_soc_skl
snd_pcm                98304  9 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_ext_core,snd_hda_codec,snd_soc_core,snd_soc_skl,snd_hda_core,snd_pcm_dmaengine
snd                    81920  18 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek,snd_timer,snd_compress,snd_soc_core,snd_pcm,snd_rawmidi

```

I am not too experienced in this type of thing so I am at all sure what  to do but I would really like to be able to listen to youtube videos and  play music again. And I cannot even listen to music with headphones  either. No audio output at all.

Thanks,

Michael Dykes

---

### Post by dino99 on 2018-10-07
As it is an upgrade, think to clean the system now, with:
- gtkorphan
- bleachbit (as root,select options carefully)

and also see the output of: "journalctl -b" on next reboot.

---

### Post by thedoctor818772 on 2018-10-07
I tried blechbit and rebooted but to no avail. The results of "journalctl -b" are:

```

-- Logs begin at Sun 2018-10-07 19:43:18 EDT, end at Sun 2018-10-07 20:57:13 EDT. --
Oct 07 20:54:37 thedoctor-HP-Notebook kernel: microcode: microcode updated early to revision 0xc6, date = 2018-04-17
Oct 07 20:54:37 thedoctor-HP-Notebook kernel: Linux version 4.18.0-8-generic (buildd@lgw01-amd64-055) (gcc version 8.2.0 (Ubuntu 8.2.0-6ubuntu1)) #9-U
Oct 07 20:54:37 thedoctor-HP-Notebook kernel: Command line: BOOT_IMAGE=/boot/vmlinuz-4.18.0-8-generic root=UUID=43d6e00e-b8bd-4288-aa92-df274a17b2c6 r
Oct 07 20:54:37 thedoctor-HP-Notebook kernel: KERNEL supported cpus:
Oct 07 20:54:37 thedoctor-HP-Notebook kernel:   Intel GenuineIntel
Oct 07 20:54:37 thedoctor-HP-Notebook kernel:   AMD AuthenticAMD
Oct 07 20:54:37 thedoctor-HP-Notebook kernel:   Centaur CentaurHauls
Oct 07 20:54:37 thedoctor-HP-Notebook kernel: x86/fpu: Supporting XSAVE feature 0x001: 'x87 floating point registers'
Oct 07 20:54:37 thedoctor-HP-Notebook kernel: x86/fpu: Supporting XSAVE feature 0x002: 'SSE registers'
Oct 07 20:54:37 thedoctor-HP-Notebook kernel: x86/fpu: Supporting XSAVE feature 0x004: 'AVX registers'
Oct 07 20:54:37 thedoctor-HP-Notebook kernel: x86/fpu: Supporting XSAVE feature 0x008: 'MPX bounds registers'
Oct 07 20:54:37 thedoctor-HP-Notebook kernel: x86/fpu: Supporting XSAVE feature 0x010: 'MPX CSR'
Oct 07 20:54:37 thedoctor-HP-Notebook kernel: x86/fpu: xstate_offset[2]:  576, xstate_sizes[2]:  256
Oct 07 20:54:37 thedoctor-HP-Notebook kernel: x86/fpu: xstate_offset[3]:  832, xstate_sizes[3]:   64
Oct 07 20:54:37 thedoctor-HP-Notebook kernel: x86/fpu: xstate_offset[4]:  896, xstate_sizes[4]:   64
Oct 07 20:54:37 thedoctor-HP-Notebook kernel: x86/fpu: Enabled xstate features 0x1f, context size is 960 bytes, using 'compacted' format.
Oct 07 20:54:37 thedoctor-HP-Notebook kernel: BIOS-provided physical RAM map:
Oct 07 20:54:37 thedoctor-HP-Notebook kernel: BIOS-e820: [mem 0x0000000000000000-0x0000000000057fff] usable
Oct 07 20:54:37 thedoctor-HP-Notebook kernel: BIOS-e820: [mem 0x0000000000058000-0x0000000000058fff] reserved
Oct 07 20:54:37 thedoctor-HP-Notebook kernel: BIOS-e820: [mem 0x0000000000059000-0x0000000000085fff] usable
Oct 07 20:54:37 thedoctor-HP-Notebook kernel: BIOS-e820: [mem 0x0000000000086000-0x00000000000fffff] reserved
Oct 07 20:54:37 thedoctor-HP-Notebook kernel: BIOS-e820: [mem 0x0000000000100000-0x00000000740bcfff] usable
Oct 07 20:54:37 thedoctor-HP-Notebook kernel: BIOS-e820: [mem 0x00000000740bd000-0x00000000740bdfff] ACPI NVS
Oct 07 20:54:37 thedoctor-HP-Notebook kernel: BIOS-e820: [mem 0x00000000740be000-0x00000000740e7fff] reserved
Oct 07 20:54:37 thedoctor-HP-Notebook kernel: BIOS-e820: [mem 0x00000000740e8000-0x000000008a38dfff] usable
Oct 07 20:54:37 thedoctor-HP-Notebook kernel: BIOS-e820: [mem 0x000000008a38e000-0x000000008a58dfff] type 20
Oct 07 20:54:37 thedoctor-HP-Notebook kernel: BIOS-e820: [mem 0x000000008a58e000-0x000000008ad7dfff] reserved
Oct 07 20:54:37 thedoctor-HP-Notebook kernel: BIOS-e820: [mem 0x000000008ad7e000-0x000000008af7dfff] ACPI NVS
Oct 07 20:54:37 thedoctor-HP-Notebook kernel: BIOS-e820: [mem 0x000000008af7e000-0x000000008affdfff] ACPI data
lines 1-30



```

---

### Post by wgarcia on 2018-10-09
I'm seeing this same thing in two systems with very different audio hardware. One of the systems has the same hardware as thedoctor818772's. This is the bug report if you want  to check that it affects you:

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1781294](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1781294)

A workaround:
```
sudo alsa force-reload
```

---

### Post by thedoctor818772 on 2018-10-09
Thanks. I tried that code above but to no avail.

---

### Post by mc4man on 2018-10-10
Try a live session with latest image, if that works then try a fresh install..
If that works then it's just an issue with upgrades, file a bug specific to that. 
(- whether Ubuntu cares about that anymore I wouldn't know..

---

### Post by wgarcia on 2018-10-10
At least for servers, there should be always an upgrade path, shouldn't it?

---

### Post by mc4man on 2018-10-10
> **wgarcia said:**
> At least for servers, there should be always an upgrade path, shouldn't it?

Well the point here, (dev) would be to 1st determine if this issue is a problem for upgrades only or does also it exist in the current state of 18.10, i.e the latest available image.
If 'release' upgrades only  you might then check if a fresh 18.04 updated, then upgraded to 18.10  shows the issue. If not then it's limited to some 18.04 installs upgraded to 18.10

---

### Post by 23dornot23d on 2018-10-11
I just upgraded through the ranks from **16.04** to **18.04** (4000 files) to **18.10** (3000 files) installed and all went reasonably ok 
for (7000 files and 6 hours passing by)

So the sound was working **OK **upto **18.04** ............. but **not** working in **18.10** ........ 
whether it happens on a clean install I cannot say as I did not try that out.


I saw this thread and thought to report my problem 
(as the command posted in here by wgarcia - got mine working again)

so in 18.10 ......... Audio did not work at first  ......... but .....
[B]sudo alsa force-reload

[/B]Made it work** OK **for my system ASUS 

Intel(R) Core(TM) i7-2630QM CPU @ 2.00GHz

00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)

[B]sudo aplay -l

[/B]**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC269VB Analog [ALC269VB Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Just thought I would pop this in for information - lightdm applet for sound is usually set muted and when I have
moved that in the past sound as come on - this time the applet greys out and shows a cross on it after
doing -[B] sudo alsa force-reload

The following shows up ..........

[/B]Terminating processes: 1112.

Unloading ALSA sound driver modules: snd-hrtimer snd-hda-codec-hdmi snd-hda-codec-realtek snd-hda-codec-generic snd-hda-intel snd-hda-codec snd-hda-core snd-hwdep snd-pcm snd-seq-midi snd-seq-midi-event snd-rawmidi snd-seq snd-seq-device snd-timer (failed: modules still loaded: snd-hda-codec-hdmi snd-hda-codec-realtek snd-hda-codec-generic snd-hda-intel snd-hda-codec snd-hda-core snd-hwdep snd-pcm snd-timer).

Loading ALSA sound driver modules: snd-hrtimer snd-hda-codec-hdmi snd-hda-codec-realtek snd-hda-codec-generic snd-hda-intel snd-hda-codec snd-hda-core snd-hwdep snd-pcm snd-seq-midi snd-seq-midi-event snd-rawmidi snd-seq snd-seq-device snd-timer.

ok that is all I can tell you at the moment ....... only got it working last night late on .......

---

### Post by wgarcia on 2018-10-12
@23dornot23d I'm seeing everything exactly as you, except on what you comment on the lightdm applet. 

Your sound hardware is different from the sound hardware where I have had this issue, so this makes the third sound hardware where this upgrade problem with sound has happened.

When I have time I will try a fresh install of 18.10 on one of my hardwares and see if I can reproduce this.

---

### Post by mc4man on 2018-10-12
Had a spare 30 min. so did a fresh install of 18.04, updated fully, rebooted, sound ok.
Then did an upgrade to 18.10 (sudo do-release-upgrade -d), rebooted, sound ok
(using the laptop speakers & also thru Bluetooth.

So on at least my hardware an unadulterated 18.04 upgraded to 18.10 does not show this issue (Ubuntu images
```
inxi -ACG
CPU:       Topology: Quad Core model: Intel Core i7-4700MQ bits: 64 type: MT MCP L2 cache: 6144 KiB 
           Speed: 1497 MHz min/max: 800/3400 MHz Core speeds (MHz): 1: 1497 2: 1499 3: 1497 4: 1497 5: 1497 
           6: 1502 7: 1497 8: 1497 
Graphics:  Device-1: Intel 4th Gen Core Processor Integrated Graphics driver: i915 v: kernel 
           Device-2: NVIDIA GK107M [GeForce GT 755M] driver: nouveau v: kernel 
           Display: server: X.Org 1.19.6 driver: intel resolution: 1920x1080~60Hz 
           OpenGL: renderer: Mesa DRI Intel Haswell Mobile v: 4.5 Mesa 18.1.5 
Audio:     Device-1: Intel Xeon E3-1200 v3/4th Gen Core Processor HD Audio driver: snd_hda_intel 
           Device-2: Intel 8 Series/C220 Series High Definition Audio driver: snd_hda_intel 
           Sound Server: ALSA v: k4.15.0-33-generic
```
```

sudo aplay -l
[sudo] password for doug: 
**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA Intel HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 10: HDMI 4 [HDMI 4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 0: ALC282 Analog [ALC282 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 1: ALC282 Digital [ALC282 Digital]
  Subdevices: 1/1
```

---

### Post by 23dornot23d on 2018-10-13
@mc4man ........... is that the 64bit install ............ 

 I will try the same as you have done - downloading it now ........ takes 30 mins on my system to download the version from [http://releases.ubuntu.com/18.04/](http://releases.ubuntu.com/18.04/)  

Then I will do the upgrade the same way you have done .. (sudo do-release-upgrade -d)  Hopefully will get it done within a few hours ........ if nothing else should interrupt this.  Still not got it working properly on my 32 bit system - tried quite a lot too ....... having to stick with **sudo alsa force-reload  **for now though .....  

This came up as the 18.04 new version loaded up - sound works ok here ............ there are 209 megs of a additional update install - do you want to install them am going to say yes to this - as I want it fully uptodate before going to the next version 18.10  Well that worked better than expected 

  Sound works fine after a clean upgrade from 18.04 64bit to 18.10 ...........  

Sound is OK  Not sure if I will go through it all again for 32bit clean ........ someone else can try that out ............

The whole thing to upgrade from a clean install took almost 7 hours to complete it all ...... could not do (sudo do-release-upgrade -d) from 18,04 to 18.10
gives some message - saying that its not allowed.

Well all I can say to end this for me now - it that 18.10 (64bit) - the sound works after a clean upgrade on a 64bit system - so I will leave it alone now.

---

### Post by Frogs Hair on 2018-10-15
Just lost sound after updates on 10/15. May go back to 18.04. 

```
 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)

```

Edit: Sound back after reboot. ??

---

### Post by wgarcia on 2018-10-16
Frogs Hair, have you tried:

```
sudo alsa force-reload
```

I've lost sound (dummy output) after upgrading two systems with different audio hardware from 18.04 to 18.10. Your hardware is also different from my two systems. In both I get sound back with the above command.

---

### Post by Frogs Hair on 2018-10-16
> **wgarcia said:**
> Frogs Hair, have you tried:

```
sudo alsa force-reload
```

I've lost sound (dummy output) after upgrading two systems with different audio hardware from 18.04 to 18.10. Your hardware is also different from my two systems. In both I get sound back with the above command.

I did run the command with nothing but a loud pop as the result. Sound is working fine since reboot though.

---

