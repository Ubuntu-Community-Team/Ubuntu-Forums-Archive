---
title: "JACK, ALSA Problem"
date: 2011-02-09
forum: Ubuntu Studio
---

### Post by genmi on 2011-02-09
I had JACK working decently on Ubuntu Studio, 10.10 with jackd -d alsa -P

Today, for no apparent reason, it stopped being able to start the server and this is the output of messages:

```
 p, li { white-space: pre-wrap; } [COLOR=#999999]12:07:52.630 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]12:07:52.724 Statistics reset.[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 [COLOR=#66cc99]12:07:52.746 ALSA connection graph change.[/COLOR]
 [COLOR=#cccc99]12:07:53.006 ALSA connection change.[/COLOR]
 [COLOR=#999999]12:07:55.011 JACK is starting...[/COLOR]
 [COLOR=#990099]12:07:55.012 /usr/bin/jackd -d alsa -P -dalsa -r48000 -p1024 -n2 -D -Chw:0 -Phw:0[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 no message buffer overruns
 [COLOR=#999999]12:07:55.155 JACK was started with PID=2841.[/COLOR]
 no message buffer overruns
 jackdmp 1.9.6
 Copyright 2001-2005 Paul Davis and others.
 Copyright 2004-2010 Grame.
 jackdmp comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK server starting in realtime mode with priority 10
 ALSA lib control.c:882:(snd_ctl_open_noupdate) Invalid CTL alsa
 control open "alsa" (No such file or directory)
 audio_reservation_init
 Acquire audio card Audio0
 Acquire audio card Audio-1
 creating alsa driver ... alsa|hw:0|1024|2|48000|0|0|nomon|swmeter|-|32bit
 ALSA lib control.c:882:(snd_ctl_open_noupdate) Invalid CTL alsa
 control open "alsa" (No such file or directory)
 Cannot initialize driver
 JackServer::Open() failed with -1
 Failed to start server
 [COLOR=#999999]12:07:55.477 JACK was stopped with exit status=255.[/COLOR]
 [COLOR=#999999]12:07:55.478 Post-shutdown script...[/COLOR]
 [COLOR=#990099]12:07:55.479 killall jackd[/COLOR]
 jackd: no process found
 [COLOR=#999999]12:07:55.893 Post-shutdown script terminated with exit status=256.[/COLOR]
 [COLOR=#ff0000]12:07:57.162 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started

```The only thing I did was install Aqualung. As an experiment I uninstalled this and the libraries it installed along with it, but with no luck of getting Jack back to working.

---

### Post by Pablo_F on 2011-02-09
Hi, 

You are starting the jack server with this command:

/usr/bin/jackd -d alsa -P -dalsa -r48000 -p1024 -n2 -D -Chw:0 -Phw:0

which is broken. 

-dalsa means jackd will use the alsa driver, but the following -d is for specifying the hardware device. "alsa" is not a such thing, you would need something like "hw:0", or "hw:0,0", or "hw:Name_of_the_audio_card".

There are more things that are broken or at least incorrect in this command. For example, you say -P (only playback for the alsa driver) and then choose a capture device and a playback device. Normally, you use one device for capture and playback, in duplex mode, and in this case you don't need to specify any capture or playback device. Even if you use playback only, fill the interface field or leave it as default if you have one only card and don't bother with capture and playback devices. (default) for them.


See *man jackd*, do a *rm ~/.jackdrc*,  and, in case you want to start the server by means of qjackctl instead of a command line in the terminal, look at the resulting jackd command in the messages window (below "JACK is starting...") so that you have something like the one it works for you:

jackd -d alsa -P ("jackd with the alsa driver in playback only" which also defaults to: realtime mode, -dhw:0, -p1024, -n2, -r48000...) 

As you are running jackd2 (jackdmp 1.9.x), -S (synchronous mode) option is sometimes a good idea. In qjackctl you don't have a field for this, so you have to append it to the "server path" like this: */usr/bin/jackd -S*

Or, in the command line, just:

jackd -S -d alsa -P

Cheers, Pablo

---

