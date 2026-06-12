---
title: "Jack gives no sound :/"
date: 2008-07-28
forum: Ubuntu Studio
---

### Post by BeardOfFire on 2008-07-28
I am running Gutsy updated to Ubuntu Studio. I have two soundcards, hw1 is the on-board soundcard (OSS) and the one set on default is hw0, my Audigy 2 SE card. 

Now, I am fairly certain I have run JACK on the Default settings successfully, but since I tried changing to hw0 to experiment, now JACK only starts with hw0 and none of the other options.

Message list for 'Default':
19:44:20.165 JACK is starting...
19:44:20.175 /usr/bin/jackd -dalsa -ddefault -r44100 -p1024 -n2
19:44:20.201 JACK was started with PID=5684 (0x1634).
jackd 0.103.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... default|default|1024|2|44100|0|0|nomon|swmeter|-|32bit
configuring for 44100Hz, period = 1024 frames, buffer = 2 periods
ALSA: final selected sample format for capture: 32bit little-endian
You appear to be using the ALSA software "plug" layer, probably
a result of using the "default" ALSA device. This is less
efficient than it could be. Consider using a hardware device
instead rather than using the plug layer. Usually the name of the
hardware device that corresponds to the first soun
ALSA: cannot set period size to 1024 frames for capture
ALSA: cannot configure capture channel
cannot load driver module alsa
no message buffer overruns
19:44:20.698 JACK was stopped successfully.
19:44:20.700 Post-shutdown script...
19:44:20.702 killall jackd
jackd: no process killed
19:44:20.998 Post-shutdown script terminated with exit status=256.
19:44:22.356 Could not connect to JACK server as client. Please check the messages window for more info.
JACK tmpdir identified as [/dev/shm]
19:45:12.185 Startup script...
19:45:12.191 artsshell -q terminate
JACK tmpdir identified as [/dev/shm]
can't create mcop directory
Creating link /home/cvm/.kde/socket-lord-byron.
19:45:12.640 Startup script terminated with exit status=256.

In addition to this, JACK doesn't activate/start any other softwares (like hydrogen) and there is no sound coming out, I checked the connections and alsa out is always connected to the right places. Also softwares like hydrogen don't start with JACK, even when I set the properties to the Jack control.

Any help?

---

### Post by thorgal on 2008-07-29
in the setup window of qjackctl, you can choose which device you want jackd to talk to. According to your jackd log, your setting is the default setup :

/usr/bin/jackd -dalsa -ddefault -r44100 -p1024 -n2

However, you mentioned that you were using OSS for the onboard chip. How about the Audigy card ? is it driven at all by OSS or ALSA ?

It is my understanding (and I can be wrong) that if you have a ALSA enabled kernel, ALSA will be the default sound system unless you tell it to choose OSS explicitely.  If I understand your attempt at running jackd correctly, jackd is trying to use the ALSA backend to communicate with the low level ALSA layer driving your hardware. However, ALSA is not driving your hardware since you are using OSS. So jackd gives up. Moreover, you have 2 devices and jackd is trying the ALSA-default one, whatever it is. So in conclusion : you try to make jackd talk to a non existing device.

Advice : if you want jackd to use your Audigy, do the following :
1- make sure the audigy has an ALSA driver
2a- make sure this driver is loaded at boot time
2b- if you have no need of it, disable the onboard chip in the BIOS. This will only bring confusion.
3- when you get to that point (Audigy being the only device available, driven by ALSA), you can launch jackd with the default setting for a start. If it works, you can later tweak stuff :
- sample rate
- number of buffers/period 
- buffer length
- realtime operation

On the other hand, if you cannot use ALSA at all, you can try OSS but this is far less recommended.

---

