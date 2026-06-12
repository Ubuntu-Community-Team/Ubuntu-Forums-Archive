---
title: "Enable sound on server (10.04 x64)"
date: 2010-08-27
forum: Server Platforms
---

### Post by sortia on 2010-08-27
Hi guys! I am stuck trying to enable sound in Ubuntu Server! :-(

I have 10.04 Server x64 on an atom (Dell A100) that I need to enable sound for a legacy device that is running in a Windows VM through a com port (all working fine bar sound)

I have followed these instructions for sound issues guide, with no joy! [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

I actually have 2 identical machines, with Ubuntu Desktop on the 2nd the sound works fine, but I'd rather not install gnome etc to fix the sound!

On the server:
```
user@server:~$ aplay -l
aplay: device_list:223 no soundcards found...
```

On the 2nd machine:
```
ubuntu@ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

And on both machines identical output:
```
ubuntu@ubuntu:~$ lspci -v
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
	Subsystem: Dell Device 02b4
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at fea38000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
```

Im not sure I am doing this right but in the guide it says thy this, both machines output the same:
```
ubuntu@ubuntu:~$ sudo modprobe snd-
FATAL: Module snd_ not found.
```

I presume the 'Kernel modules: snd-hda-intel' means the Intel driver is actually installed but I tried rebuilding the alsa driver from source anyway (selected hda-intel) it compiled successfully. But the server still says no soundcards found with the command: aplay -l

I also tried adding snd-hda-intel to the bottom of /etc/modules but still no joy!

Any help greatly appreciated! :-)

---

### Post by arrrghhh on 2010-08-27
You probably have to install some pieces of alsa... not sure which tho.  By default, ubuntu-desktop uses pulse but that would probably make things more complicated than they need to be.

I have sound working on my server, but I just play music on mpd straight out of the server itself.  Using alsa - I tried playing with pulse to get network audio streaming, but kinda gave up on that dream.

---

### Post by sortia on 2010-08-27
Hi thanks for the reply
I do have alsa-utils, alsa-base, linux-sound-base and libasound2 installed. That looked to me like all the important alsa bits that are installed on the desktop!

---

### Post by arrrghhh on 2010-08-27
Yea, that should be all you need... On the [Sound Troubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting) doc it has you run aplay -l with sudo... Have you tried that?

However, if it doesn't recognize the card, that's not a good sign...

---

### Post by sortia on 2010-08-27
Ha ha ok im officially an idiot! It does work with sudo!

I just need to set the permissions for sound for virtualbox!

Thank you!! :-)

---

