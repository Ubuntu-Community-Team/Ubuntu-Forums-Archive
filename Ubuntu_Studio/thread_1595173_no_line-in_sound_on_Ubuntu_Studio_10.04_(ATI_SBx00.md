---
title: "no line-in sound on Ubuntu Studio 10.04 (ATI SBx00 Azalia)"
date: 2010-10-13
forum: Ubuntu Studio
---

### Post by potiphera on 2010-10-13
I'm running Ubuntu Studio 10.04 on a new computer, and I can't get any sound from the line-in jack.  The microphone jack works (I got sound into adc~ in Pd), but I couldn't get the line-in to work even after trying the various input options in qjackctl.  If I connect a really loud input to the line-in, I do hear some distorted buzzing, but that happens even if I mute everything, so I'm thinking it's interference, as I can't get anything at a normal volume.  My motherboard is an ASRock 880GXH.  lspci says that the audio device is an ATI Technologies Inc SBx00 Azalia (Intel HDA).  How should I troubleshoot this?  The problem could be the hardware, but I'm not sure how to figure that out.  Thanks!

---

### Post by Pablo_F on 2010-10-13
Hi, 

look at alsamixer.

Cheers! Pablo

---

### Post by potiphera on 2010-10-13
In alsamixer, I see the same options as in the Sound Preferences GUI, and in both places there is only one control for input/capture volume, with no ability to switch between mic and line in.  Is there anything else I should be looking for?

---

### Post by Pablo_F on 2010-10-14
Hi, 

Can you give the terminal output of the following commands?

cat /proc/asound/cards
cat /proc/asound/modules
cat /proc/asound/card0/codec#0 |grep -i codec
amixer

Cheers! Pablo

---

### Post by potiphera on 2010-10-15
cat /proc/asound/cards
 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xfe7f4000 irq 16

cat /proc/asound/modules
 0 snd_hda_intel

cat /proc/asound/card0/codec#0 |grep -i codec
Codec: Realtek ID 892

amixer
Simple mixer control 'Master',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 37 [58%] [-27.00dB]
  Front Right: Playback 37 [58%] [-27.00dB]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 253 [99%] [0.40dB]
  Front Right: Playback 253 [99%] [0.40dB]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 46
  Front Left: Capture 16 [35%] [0.00dB] [on]
  Front Right: Capture 16 [35%] [0.00dB] [on]

---

### Post by Pablo_F on 2010-10-15
Hi,

I suggest you ask in the Multimedia and Video subforum where there are more experts in these kind of problems. To complete the info and get help quicker you might want to run the alsa-info script. With a command like this one: 

wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh

You will be asked if you want to upload the info. Default is No. Choose yes and give the URL to the person helping you.

That said, you can try this trick in the meanwhile:

$ sudo gedit /etc/modprobe.d/alsa-base.conf

Add the line:

options snd-hda-intel position_fix=1

And reload alsa modules with:

$ sudo alsa force-reload

Cheers! Pablo

---

### Post by AutoStatic on 2010-10-15
Try installing the **linux-backports-modules-alsa-lucid-generic** package.

---

### Post by potiphera on 2010-10-18
Excellent, I installed linux-backports-modules-alsa-lucid-generic and it works great! Thanks, AutoStatic and Pablo!

---

### Post by potiphera on 2010-11-01
I noticed that installing that package changed JACK's behavior so now I can't increase the period size to over 1024 frames.  The same thing happened in the preempt kernel: I could originally choose 2048 frames/period in JACK, but then I installed linux-backports-modules-alsa-lucid-preempt so line-in would work in that kernel, and now I get these messages when I try to run JACK at 2048 frames/period:

```
10:00:35.934 Patchbay deactivated.
10:00:35.939 Statistics reset.
10:00:36.024 ALSA connection graph change.
10:00:36.218 ALSA connection change.
10:00:37.748 Startup script...
10:00:37.749 artsshell -q terminate
sh: artsshell: not found
10:00:38.155 Startup script terminated with exit status=32512.
10:00:38.155 JACK is starting...
10:00:38.155 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p2048 -n2
10:00:38.160 JACK was started with PID=2311.
jackd 0.118.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
Memory locking is unlimited - this is dangerous. You should probably alter the line:
     @audio   -  memlock    unlimited
in your /etc/limits.conf to read:
     @audio   -  memlock    2849871
no message buffer overruns
JACK compiled with System V SHM support.
loading driver ..
Enhanced3DNow! detected
SSE2 detected
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|2048|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 44100Hz, period = 2048 frames (46.4 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 32bit integer little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: cannot set period size to 2048 frames for playback
ALSA: cannot configure playback channel
cannot load driver module alsa
10:00:38.805 JACK was stopped successfully.
10:00:38.806 Post-shutdown script...
10:00:38.806 killall jackd
jackd: no process found
10:00:39.231 Post-shutdown script terminated with exit status=256.
10:00:40.245 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
```

Is there a way to fix this?

---

### Post by potiphera on 2010-11-04
(bump -- I might ask in the Multimedia & Video forum if nobody here knows)

---

