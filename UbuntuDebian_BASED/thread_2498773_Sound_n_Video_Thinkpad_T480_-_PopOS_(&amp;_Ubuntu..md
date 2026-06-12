---
title: "Sound n Video: Thinkpad T480 - PopOS (&amp; Ubuntu...)"
date: 2024-06-26
forum: Ubuntu/Debian BASED
---

### Post by matt9 on 2024-06-26
[FONT=arial][COLOR=#353535]Running Pop OS on my T480 i7 (although I ran Ubuntu off a USB drive to test to see if it was a Pop-quirk) and in either case am having the following issues:
[/COLOR]
[/FONT]
[LIST=1]
[*][FONT=arial]No audio in - internal mic is getting nothing. Connected a wired headset with mic yesterday, also nothing (not even in the drop-down as an option as it was with Audio Out)[/FONT]
[*][FONT=arial]No webcam. Did some googling and see that this can be bios disabled - it is not. Other than that, I just don't know. Not coming up in Cheese, not coming up in Zoom - "Unable to Detect".[/FONT]
[/LIST]
[FONT=arial][COLOR=#353535]
Are there drivers lurking out there that I need to install? Anyone able to help?[/COLOR][/FONT]

---

### Post by him610 on 2024-06-26
```
inxi -AGx
```
Please show results between code brackets

---

### Post by matt9 on 2024-06-26
Thanks for the assist...here's what it said.

```
matt@pop-os:~$ inxi -AGx
Graphics:
  Device-1: Intel UHD Graphics 620 vendor: Lenovo driver: i915 v: kernel
    bus-ID: 00:02.0
  Display: x11 server: X.Org v: 1.21.1.4 driver: X: loaded: modesetting
    unloaded: fbdev,vesa gpu: i915 resolution: 1920x1080~60Hz
  OpenGL: renderer: Mesa Intel UHD Graphics 620 (KBL GT2)
    v: 4.6 Mesa 24.0.3-1pop1~1711635559~22.04~7a9f319 direct render: Yes
Audio:
  Device-1: Intel Sunrise Point-LP HD Audio vendor: Lenovo ThinkPad T480
    driver: snd_hda_intel v: kernel bus-ID: 00:1f.3
  Sound Server-1: ALSA v: k6.9.3-76060903-generic running: yes
  Sound Server-2: PulseAudio v: 15.99.1 running: no
  Sound Server-3: PipeWire v: 1.0.3 running: yes

```

---

### Post by matt9 on 2024-06-27
Any ideas guys?  Is that PulseAudio not running thing responsible for the audio side?

---

