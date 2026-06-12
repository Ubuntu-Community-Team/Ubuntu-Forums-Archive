---
title: "Errors when trying to start up JACK"
date: 2016-03-09
forum: Ubuntu Studio
---

### Post by james203 on 2016-03-09
Hi, I would like to first say that I am actually only running the normal version of Ubuntu and not Ubuntu Studio but it seems that all questions about JACK are being directed here so it seems most relevant to post here.

I am inexperienced when it comes to linux and ubuntu and have had a difficult time trying to figure out how to solve the various errors I have been getting when trying to start up JACK so any help would be greatly appreciated.

I'll post the current log from the console:

```
jackd -d alsa
jackdmp 1.9.10
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2013 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
no message buffer overruns
no message buffer overruns
no message buffer overruns
JACK server starting in realtime mode with priority 10
audio_reservation_init
Acquire audio card Audio0
creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|-|32bit
ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
Cannot initialize driver
JackServer::Open failed with -1
Failed to open server

```

Thanks in advance for any help you can give me.

---

