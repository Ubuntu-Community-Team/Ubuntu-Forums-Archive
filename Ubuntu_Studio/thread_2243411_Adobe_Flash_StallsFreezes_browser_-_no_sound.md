---
title: "Adobe Flash Stalls/Freezes browser - no sound"
date: 2014-09-08
forum: Ubuntu Studio
---

### Post by jed-elkins on 2014-09-08
Hello!

I'm running Ubuntu Studio (Ubuntu 14.04.1 LTS) with Xfce 4.10
Kernel: Linux 3.13.0-35-lowlatency (x86_64)
[SUB]-Computer-
Processor: AMD Athlon(tm) 64 X2 Dual Core Processor 5600+
Memory: 6111MB
Video Card: NVIDIA Corporation GF116 [GeForce GTX 550 Ti] (rev a1)
Audio device: NVIDIA Corporation GF116 High Definition Audio Controller (rev a1)
[/SUB]
When I try to watch a video (adobe flash) in Firefox or Chromium, either one, the video starts playing with no sound but then hangs after about 3-12 seconds and a few seconds after that the whole browser will freeze up and I connot get it to respond to anything except for window minimizing and restore. If I wait a while it will unfreeze and give me control a bit longer before freezing again. If I leave the page with the flash video, the browser does not freeze anymore. When the video stalls (and before the browser freezes), I'm able to click earlier in the video timeline to get it to play again, but it stalls again after the same amount of seconds. 

I have installed the latest 64bit version (11,2,202,400) of Flash for Firefox from the Ubuntu repository, and also the latest pepper-flash (14.0.0.177) for Chromium.

I'm fairly new to Linux. I've searched the forums (and google) 1st to find this issue to no avail.
I would greatly appreciate some help!

Just in case...
Here are some of my Kernal Modules: (drivers?)
[SUB]-Loaded Modules-
snd_hda_codec_hdmi: HDMI HD-audio codec
snd_hda_codec_realtek: Realtek HD-audio codec
nouveau: nVidia Riva/TNT/GeForce/Quadro/Tesla
mxm_wmi: MXM WMI Driver
wmi: ACPI-WMI Mapping Driver
video: ACPI Video Driver
ttm: TTM memory manager subsystem (for DRM device)
snd_hda_intel: Intel HDA driver
snd_hda_codec: HDA codec core
snd_hwdep: Hardware dependent layer
drm_kms_helper: DRM KMS helper
[/SUB]

---

### Post by jed-elkins on 2014-09-08
OK!! NEVERMIND! LOL

I restarted and it's working now....

I did a restart when I replaced the drivers one other time, but I guess I overlooked it the since I messed with them again when I was troubleshooting this.

**Lesson:** Restart after every change just in case!

---

