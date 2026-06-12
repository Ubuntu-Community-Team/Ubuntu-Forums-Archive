---
title: "Best JACK setup for ESI Juli@?"
date: 2009-06-26
forum: Ubuntu Studio
---

### Post by barisurum on 2009-06-26
Hi there folks;

I just grabbed a new ESI juli@, the card works fine with pulseaudio, I set up JACK to work with it but the best latency I get is 10.7 ms at 96khz and even that doesn't seem stable (a few xruns). Everything is set up well for a working rt setup (limits.conf rt priority at 99 nice -10). I don't use the realtime kernel since it has many bugs, I use the generic kernel. Here is my jack setup:

priority: 89
frames: 512
periods: 2
latency: 10.7

I noticed something odd in the messages window:

```
23:16:25.210 Patchbay activated.
23:16:25.213 Statistics reset.
23:16:25.251 Startup script...
23:16:25.252 artsshell -q terminate
23:16:25.323 ALSA connection graph change.
sh: artsshell: not found
23:16:25.654 Startup script terminated with exit status=32512.
23:16:25.654 JACK is starting...
23:16:25.654 /usr/bin/jackd -R -P89 -t2000 -u -dalsa -r96000 -p512 -n2 -D -Chw:0 -Phw:0 -Xseq
23:16:25.657 JACK was started with PID=4626.
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
23:16:25.856 ALSA active patchbay scan...
23:16:25.857 ALSA connection change.
loading driver ..
Enhanced3DNow! detected
SSE2 detected
apparent rate = 96000
[COLOR="Red"]creating alsa driver ... hw:0|hw:0|512|2|96000|0|0|nomon|swmeter|-|32bit[/COLOR]
control device hw:0
23:16:26.057 ALSA active patchbay scan...
configuring for 96000Hz, [COLOR="Red"]period = 512 frames (5.3 ms)[/COLOR], buffer = 2 periods
[COLOR="Red"]ALSA: final selected sample format for capture: 32bit integer little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit integer little-endian[/COLOR]
ALSA: use 2 periods for playback
23:16:26.225 ALSA connection graph change.
23:16:26.258 ALSA active patchbay scan...
23:16:26.875 Server configuration saved to "/home/baris/.jackdrc".
23:16:26.880 Statistics reset.
23:16:27.221 Client activated.
23:16:27.222 JACK connection change.
23:16:27.224 JACK connection graph change.
Enhanced3DNow! detected
SSE2 detected
23:16:27.423 JACK active patchbay scan...
```

First it says I get 5.3 ms not 10.7, how is that possible? I also see 5.3 ms latency when working with ardour. Can the latencies be different?

Second it says audio bit depth is 32 bit little endian, but the juli@ is 24 bit. So the cpu goes crazy to change the format from 24bit to 32 then send it to the card at 24bit and cpu usage goes up to %60 when only listening to a simple ogg file. Please give me advice to correctly configure the card. Thank you.

---

### Post by sgx on 2009-06-27
Not based on science, but try removing the realtime related settings,  since that may confuse a non RT kernel...just a guess, but I always do that, and have not seen adverse effects. In the end, the various latency numbers are just labels on a shirt, so its OK to ignore them, when the instrument responds fast enough. A  guitar run through rakarrack may track smoother at lower latency, but your ears are the best and final judge. I have done some things temporarily with very high latency numbers, without hearing any timing issues, yet removing the last little pop on a complex output. Taking notes is good luck! :)

There is an alsaconf program you can run as root, to configure your card for alsa, and envy24control is a mixer, seems I read your card uses the same family of chips as maudio 24/96, if so, it should work
Cheers

---

### Post by barisurum on 2009-06-27
Thanks sgx;
What makes me mad here is the amount of CPU usage even if the card is idle. It starts to exploit when jack starts. I can see about %40 CPU usage as a backend process (shadow) on the system monitor applet but I can't hunt the cpu eater with system monitor or top! What moron process steals my beloved CPU cycles? Thanks in advance for your help people!

---

### Post by sgx on 2009-06-28
> **barisurum said:**
> Thanks sgx;
What makes me mad here is the amount of CPU usage even if the card is idle. It starts to exploit when jack starts. I can see about %40 CPU usage as a backend process (shadow) on the system monitor applet but I can't hunt the cpu eater with system monitor or top! What moron process steals my beloved CPU cycles? Thanks in advance for your help people!

Hi, I always uninstall screesavers, all wifi/bluetooth things, 3d desktops, turn off networking in the services settings, turn off polling of cd/dvd devices, if using kde, there are several related services you can experiment with shutting down, kmix autostart can be uninstalled, konqueror pre-loading can be turned off, but do take notes, I reboot after
using any mozilla app. I resorted to uninstalling mazilla, as opera was faster and smaller, fewer issues, and I don't do much on the net.

I have had mysterious reconfigs of my 44,100 settings appear, and be changed lower or higher, so maybe do a system search for common speed settings like 48000, 22,050, 96,000, and see if anythings looks suspicious
A better card, having more options, may have higher defaults to deal with.

Try setting the priority in qjackctl to 50, rather than 89, see if a change occurs, go lower if you can't hear improvement...
Hope something helps...
cheers

---

### Post by barisurum on 2009-06-29
thanx sgx I will try your suggestions, I also will post this to alsa mailing lists

---

