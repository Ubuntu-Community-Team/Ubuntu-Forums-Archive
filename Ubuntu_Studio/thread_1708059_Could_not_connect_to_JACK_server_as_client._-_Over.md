---
title: "Could not connect to JACK server as client. - Overall operation failed. - Unable to c"
date: 2011-03-16
forum: Ubuntu Studio
---

### Post by endlessfields on 2011-03-16
Hello.  

I&#7743; trying to use my emu 1616m with Ubuntu Studio 10.04 64bit using the linux rt kernel.  After having it working on my Kubuntu 10.04 installation (also using rt kernel) jack suddenly stopped working.  The computer seems to detect the emu without any problems, and the card still works in windows.  After spending several days trying to fix it, I gave up and installed Ubuntu Studio on a separate partition, and I still have the same problem.  

This is what jack says when I try to start it using the emu 1616m:


[COLOR=#999999]06:14:24.912 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]06:14:24.939 Statistics reset.[/COLOR]
 [COLOR=#66cc99]06:14:24.959 ALSA connection graph change.[/COLOR]
 [COLOR=#cccc99]06:14:25.184 ALSA connection change.[/COLOR]
 [COLOR=#999999]06:14:27.189 Startup script...[/COLOR]
 [COLOR=#990099]06:14:27.189 artsshell -q terminate[/COLOR]
 sh: artsshell: not found
 [COLOR=#999999]06:14:27.591 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]06:14:27.591 JACK is starting...[/COLOR]
 [COLOR=#990099]06:14:27.591 /usr/bin/jackd -u -dalsa -dhw:2,2 -r44100 -p512 -n2[/COLOR]
 [COLOR=#999999]06:14:27.593 JACK was started with PID=6468.[/COLOR]
 jackd 0.118.0
 Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 Memory locking is unlimited - this is dangerous. You should probably alter the line:
      @audio   -  memlock    unlimited
 in your /etc/limits.conf to read:
      @audio   -  memlock    3037191
 no message buffer overruns
 JACK compiled with System V SHM support.
 loading driver ..
 SSE2 detected
 apparent rate = 44100
 creating alsa driver ... hw:2,2|hw:2,2|512|2|44100|0|0|nomon|swmeter|-|32bit
 control device hw:2
 ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
 configuring for 44100Hz, period = 512 frames (11.6 ms), buffer = 2 periods
 ALSA: final selected sample format for capture: 32bit integer little-endian
 ALSA: use 2 periods for capture
 impossible sample width (1) discovered!
 [COLOR=#999999]06:14:27.952 JACK was stopped with exit status=1.[/COLOR]
 [COLOR=#999999]06:14:27.953 Post-shutdown script...[/COLOR]
 [COLOR=#990099]06:14:27.953 killall jackd[/COLOR]
 jackd: no process found
 [COLOR=#999999]06:14:28.365 Post-shutdown script terminated with exit status=256.[/COLOR]
 [COLOR=#ff0000]06:14:29.617 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]


...by the way, I have already edited the @audio line in /etc/security/limits.conf to say 3037191, but that message keeps coming up anyway.  (I had the same situation when using Kubuntu, didnt notice any problems)

Ive looked everywhere to try to fix this, and even recruited the help of friends.  We&#341;e all stumped!  Any help will be greatly appreciated!

---

### Post by Pablo_F on 2011-03-20
Hi, 

Please, can you give the output of the following informative commands?

[B]arecord -l && aplay -l

cat /proc/asound/cards

cat /proc/asound/modules

cat /etc/security/limits.conf /etc/secutiry/limits.d/audio.conf |grep -v "#"

ulimit -r -l[/B]
[B]
lsusb[/B]

**lspci |grep -i usb**

Cheers, Pablo

---

### Post by endlessfields on 2011-03-20
Actually, after some fiddling around with Jack setup I was able to get audio recording & playback to work by leaving the Interface setting at default and instead setting Input Device to hw:2,2 (Multichannel Capture/PT Playback) and Output Device to hw:2,3 (Multichannel Playback).  

Midi works as well.

Thanks for your help though.

---

### Post by ailo.at on 2011-03-20
> **endlessfields said:**
> 
...by the way, I have already edited the @audio line in /etc/security/limits.conf to say 3037191, but that message keeps coming up anyway.  (I had the same situation when using Kubuntu, didnt notice any problems)

Unfortunately the message is lying. When installing jackd it will add a file /etc/security/limits.d/audio.conf which holds those parameters. 
According to the jack people there should be no danger in using memlock unlimited, why they say those warning messages are going to be removed.

You should remove the lines you have added into /etc/security/limits.conf (any that begin with @audio), and make sure corresponding lines in /etc/security/limits.d/audio.conf look like this (by default):
@audio - rtprio 95
@audio   -  memlock unlimited

And, don't use ubuntustudio-controls, because that will edit the wrong file as well :/.

---

