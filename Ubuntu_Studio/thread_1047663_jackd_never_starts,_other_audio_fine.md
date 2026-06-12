---
title: "jackd never starts, other audio fine"
date: 2009-01-22
forum: Ubuntu Studio
---

### Post by OPMartin on 2009-01-22
Hi,

How are you?

I have never been able to get jackd to start, no matter what settings, neither under dapper 6.06 LTS nor under hardy 8.04.1 LTS.  The audio works fine in non-jack apps such as audacity.  I have an hp media pc that I had hoped would be pretty standard: win xp says the sound card is a "Creative SB Audigy 4 (WDM)" but I think linux thinks it is an audigy 2.

Here is a typical error message when trying to start jack:

```
12:41:53.362 Patchbay deactivated.
12:41:53.451 Statistics reset.
12:41:53.483 ALSA connection graph change.
12:41:53.698 ALSA connection change.
12:43:52.988 Startup script...
12:43:52.989 artsshell -q terminate
12:43:53.766 Startup script terminated with exit status=256.
12:43:53.767 JACK is starting...
12:43:53.767 /usr/bin/jackd -dalsa -dhw:0,0 -r44100 -p256 -n2 -P -m
12:43:53.770 JACK was started with PID=6358.
jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0,0|-|256|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
ALSA lib confmisc.c:1286:(snd_func_refer) Unable to find definition 'defaults.namehint.extended'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM hw:0,0
ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
cannot load driver module alsa
no message buffer overruns
12:43:53.885 JACK was stopped successfully.
12:43:53.885 Post-shutdown script...
12:43:53.886 killall jackd
jackd: no process killed
12:43:54.300 Post-shutdown script terminated with exit status=256.
12:43:55.777 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
```


The only time it started was with the 'dummy' driver.

May the Lord bless you,
Philip

---

### Post by Hooya on 2009-01-22
Run the qjackctl program to start jack.  It's a GUI that lets you set various settings.  Change your options, open the message screen and attempt to start the server.  If you get errors stop the server right away and try new settings.

The same resourse pointed to you in your other thread has tips on setting up the Jack server using qjackctl.

---

### Post by OPMartin on 2009-01-22
Yes, I did use qjackctl, trying all kinds of settings, following the advice for example [here]("http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/"), to no avail.

Question: what is 'defaults.namehint.extended'?  That seems to be the line where the problems start.

May the Lord bless you,
Philip

---

