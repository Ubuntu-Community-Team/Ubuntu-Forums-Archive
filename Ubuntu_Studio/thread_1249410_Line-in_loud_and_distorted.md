---
title: "Line-in loud and distorted"
date: 2009-08-25
forum: Ubuntu Studio
---

### Post by goldenratiophi on 2009-08-25
I'm using Ubuntu 9.04 on a Gateway md7818u to try to digitize some records.  I've done this on other computers and it's been fine, so I know it's not a problem with my turntable or preamp.  When I connect the preamp to my laptop's line in, it sounds extremely loud and distorted.

I can't upload a sample (too big), apparently, but imagine this:

[http://www.youtube.com/watch?v=O3CkfvYMCWM](http://www.youtube.com/watch?v=O3CkfvYMCWM)

sounding like this:

[http://www.youtube.com/watch?v=VLi3H39qnuA](http://www.youtube.com/watch?v=VLi3H39qnuA)

What should I try?  I've gone to System -> Prefs -> Sound and tried every combination of dropdowns to no avail :(

---

### Post by bry_melvin on 2009-08-25
Find the mixer on your version of ubuntu and decrease the slider on the input/capture etc. Some sound cards also have a mic boost function that may be engaged.

If you can't FIND a mixer you may need to go into the package manager you use and install one.

I am not familiar with gateway. I also don;t know what recording software you are using.

Audacity or Ardour will let you adjust the level coming in and use a number of plugins including eq etc.

---

### Post by goldenratiophi on 2009-08-25
Thanks, but all messing with the volume sliders does is make it more or less loud; it doesn't change the compressed distortedness.

Extra info:

```
carlos@carlos-laptop:~$ lspci -v
...
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
	Subsystem: Gateway 2000 Device 0704
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at f0900000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

```

Also, in Audacity, the recording devices are listed as:

```

ALSA: HDA Intel: CONEXANT Analog (hw:0,0)
ALSA: pulse
ALSA: default
OSS: /dev/dsp

```

The first one is the only one that gives any input at all.

---

### Post by goldenratiophi on 2009-08-27
Erm, bump?

---

