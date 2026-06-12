---
title: "no audio when running jack sample"
date: 2011-09-17
forum: Ubuntu Studio
---

### Post by hagai_sela on 2011-09-17
Hi,
I am trying to run jack samples, but I have no audio. I tried this step by step tutorial:
[http://dis-dot-dat.net/index.cgi?item=jacktuts/](http://dis-dot-dat.net/index.cgi?item=jacktuts/)

I run qjackctl and jack seems to start OK. When I try to run the metronome sample like he did, I can see the metronome app as input in qjackctl, but when I connect it to the system->playback1 device, I can't hear anything.

I also noticed that I can't see any alsa devices, running ack_lsp produces this output:
system: capture_1
system: capture_2
system: playback_1
system: playback_2
system: playback_3
system: playback_4
system: playback_5
system: playback_6
system: playback_7
system: playback_8
metro: 120_bpm

This is the output from qjackctl:

jack server is not running or cannot be started
21:36:02.747 JACK was started with PID=19123.
no message buffer overruns
no message buffer overruns
jackdmp 1.9.7
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK server starting in realtime mode with priority 10
control device hw:0
control device hw:0
audio_reservation_init
Acquire audio card Audio0
creating alsa driver ... hw:0|hw:0|64|2|48000|0|0|nomon|swmeter|-|16bit
control device hw:0
Using ALSA driver HDA-Intel running on card 0 - HDA Intel at 0xfbff8000 irq 54
configuring for 48000Hz, period = 64 frames (1.3 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 16bit little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 16bit little-endian
ALSA: use 2 periods for playback
21:36:02.862 JACK connection change.
21:36:02.863 Server configuration saved to "/home/hagai/.jackdrc".
21:36:02.864 Statistics reset.
21:36:02.867 Client activated.
21:36:02.871 JACK connection graph change.

I can hear regular audio OK (play music).

Thanks,
Hagai.

---

