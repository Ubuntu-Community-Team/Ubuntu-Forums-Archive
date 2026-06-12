---
title: "alsamixer opening problem"
date: 2009-02-07
forum: Ubuntu Studio
---

### Post by dontiego on 2009-02-07
Hi all!

Going slowly towards a working sound here. Only slowly.

alsamixer was working fine, but all of a sudden it stopped working.
```
$ alsamixer
ALSA lib control.c:874:(snd_ctl_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_ctl_pulse.so

alsamixer: function snd_ctl_open failed for default: No such file or directory

```

However, this seems to be working:
```
@ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: EMU1010 [E-mu 1010 [4001]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 0: EMU1010 [E-mu 1010 [4001]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1

$ alsamixer -c 0


```
used help from [http://linux.derkeiler.com/Mailing-Lists/Ubuntu/2008-12/msg01840.html]("http://linux.derkeiler.com/Mailing-Lists/Ubuntu/2008-12/msg01840.html")

I wonder why "alsamixer" alone wouldn't work?

In System->Preferences->Sound->Devices I set everything as PulseAudio Sound Server (it wouldn't work when I put ALSA).

Running alsamixer seems to miss some kind of pulseaudio related stuff, but how could I fix it?

---

### Post by dontiego on 2009-02-21
bump!

alsamixer
not working.


alsamixer -c 0
working.

Is that a bug?

---

### Post by Reeman on 2009-02-21
> **dontiego said:**
> bump!

alsamixer
not working.


alsamixer -c 0
working.

Is that a bug?
Yup sounds like he just found one..alsamixer through pulse should just show the volume level if the default mixer is set to pulse. Could be a reporting error from the card driver. This is a good one to send to the alsa devs. Sounds like the sb emu1010 driver borks with oss and pulse.
If he is reading alsamixer -c 0 with the actual card and not the gnome pulse melange of Ubuntu then it is most likely not an Ubuntu issue.

---

