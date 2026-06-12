---
title: "Soundcard makes JACK run at 96kHz regardless of settings"
date: 2010-07-22
forum: Ubuntu Studio
---

### Post by darsu on 2010-07-22
Edit: for chrissakes... After posting the message below I decided to run QJackCtl just one more time before giving up for today *and of course it works now*. I'll leave the message there for reference but I guess you can disregard it. 










Hi,

My Edirol UA-25EX USB sound card has started acting very bizarrely. It's capable of running at 96kHz, but not in duplex mode in Linux, so I've always run it at 48kHz.

Yesterday I noticed that QJackCtl won't start JACK with capture enabled anymore:
```

18:54:00.700 /usr/bin/jackd -R -t5000 -m -dalsa -r48000 -p512 -n3 -D -Chw:1 -Phw:1 -s -Xseq
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
18:54:00.738 JACK was started with PID=2671.
loading driver ..
Enhanced3DNow! detected
SSE2 detected
apparent rate = 48000
creating alsa driver ... hw:1|hw:1|512|3|48000|0|0|nomon|swmeter|soft-mode|32bit
control device hw:1
ALSA: Cannot open PCM device alsa_pcm for capture. Falling back to playback-only mode
configuring for 48000Hz, period = 512 frames (10.7 ms), buffer = 3 periods
ALSA: final selected sample format for playback: 24bit little-endian
ALSA: use 3 periods for playback

```

After making sure that nothing is running in the background that could possibly lock JACK out, I realized that QJackCtl says it's running at 96000 Hz. The attached screenshot shows my QJackCtl settings window, main window and all the rest.

The sound card's back panel switches are set to Advanced driver=on and Sample rate=48, just as always. The switch positions make no difference: even with the advanced driver off and the sample rate set to 44.1, QJackCtl ends up running at 96000Hz in playback-only mode.

Also, JACK refuses to start in capture-only mode; in playback-only mode it runs in the above-described fashion.


Do you have any idea what can be causing this?

---

