---
title: "Sound Card Not being Detective"
date: 2018-06-29
forum: System76 Support
---

### Post by Cowchip7 on 2018-06-29
Can anyone provide some advise?

john@john-N24-25BU:~$ sudo alsa force-reload
Unloading ALSA sound driver modules: snd-hda-intel snd-hda-codec snd-hda-core snd-hwdep snd-pcm snd-seq-midi snd-seq-midi-event snd-rawmidi snd-seq snd-seq-device snd-timer.
Loading ALSA sound driver modules: snd-hda-intel snd-hda-codec snd-hda-core snd-hwdep snd-pcm snd-seq-midi snd-seq-midi-event snd-rawmidi snd-seq snd-seq-device snd-timer.
john@john-N24-25BU:~$ pulseaudio --start
N: [pulseaudio] main.c: User-configured server at {1c58dff011e237e46b2dc972e4c860a5}unix:/run/user/1000/pulse/native, which appears to be local. Probing deeper.
john@john-N24-25BU:~$ lspci -v | grep -A6 Audio
00:1f.3 Audio device: Intel Corporation Device 9d71 (rev 21)
	Subsystem: CLEVO/KAPOK Computer Device 2410
	Flags: bus master, fast devsel, latency 32, IRQ 128
	Memory at df220000 (64-bit, non-prefetchable) [size=16K]
	Memory at df200000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
john@john-N24-25BU:~$ aplay -l
aplay: device_list:268: no soundcards found...
john@john-N24-25BU:~$

---

