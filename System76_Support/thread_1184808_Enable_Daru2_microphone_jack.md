---
title: "Enable Daru2 microphone jack"
date: 2009-06-11
forum: System76 Support
---

### Post by RichardK on 2009-06-11
I've just needed to use my microphone jack for the first time with my Daru2.

The Front Mic (internal) works OK, but no matter what I do, I can't get any sound coming in via Mic (front jack).

Reading about the System76 driver, I see that it solves this problem in Ubuntu, but I'm currently using Arch. Can you give me a generic idea of what the driver is doing to solve the mike problem?

I'm loading modules snd-hda-intel and !snd_pcsp in rc.conf.

Thanks,
Richard

---
aplay -l:
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

lspci | grep Audio:
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

alsamixer -V capture:
[IMG]http://www.richard.kelly.ws/img/alsamixer.png[/IMG]

---

### Post by jdb on 2009-06-11
> **RichardK said:**
> I've just needed to use my microphone jack for the first time with my Daru2.

The Front Mic (internal) works OK, but no matter what I do, I can't get any sound coming in via Mic (front jack).

Reading about the System76 driver, I see that it solves this problem in Ubuntu, but I'm currently using Arch. Can you give me a generic idea of what the driver is doing to solve the mike problem?

I'm loading modules snd-hda-intel and !snd_pcsp in rc.conf.

Thanks,
Richard



Try puting this in /etc/modeprobe.conf

```
#
# /etc/modprobe.conf (for v2.6 kernels)
#
options snd-hda-intel model=targa-dig
options snd-pcsp index=2
```

jdb

---

### Post by RichardK on 2009-06-11
Brilliant. I was missing the snd-hda-intel line. Thanks!

Richard

---

### Post by thomasaaron on 2009-06-11
We add this line to /etc/modprobe.d/alsa-base

options snd-hda-intel model=targa-dig

---

### Post by jdb on 2009-06-11
> **thomasaaron said:**
> We add this line to /etc/modprobe.d/alsa-base

options snd-hda-intel model=targa-dig

That's how I found it in the first place :)

The downside to  Arch Linux is everything needs to be configured manually, that's also the upside.
Once you get something working it is never broken by some auto-configuration or some configuration gui.
Things like sound & wifi don't mysteriously break.

jdb

---

