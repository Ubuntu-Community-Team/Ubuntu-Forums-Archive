---
title: "jack starts once, but fails the next time"
date: 2012-02-04
forum: Ubuntu Studio
---

### Post by daziel on 2012-02-04
Jack version 0.118.0
qjackctl version 0.3.4
Ubuntu version 10.04

I have been using jack with Ardour for 2+ years without problems.  After a recent software update I started having this problem;
jack will load and I can use hydrogen, ardour, etc to record and playback, and do a normal quit of all the programs without problems

When I try to start jack again it fails.  I have to reboot (soft reboot works) to get jack to run again.

The first message below is a successful start of jack and the second is a failed start.
Thanks for any help,
Marc

12:21:10.110 JACK is starting...
12:21:10.111 /usr/bin/jackd -t1000 -dalsa -r44100 -p64 -n2 -D -Chw:0,0 -Phw:0,0 -m
jackd 0.118.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
Memory locking is unlimited - this is dangerous. You should probably alter the line:
@audio - memlock unlimited
in your /etc/limits.conf to read:
@audio - memlock 715362
12:21:10.122 JACK was started with PID=4994.
12:21:10.320 ALSA connection change.
no message buffer overruns
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0,0|hw:0,0|64|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 44100Hz, period = 64 frames (1.5 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 32bit integer little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: use 2 periods for playback
12:21:12.373 Server configuration saved to "/home/jmarc/.jackdrc".
12:21:12.377 Statistics reset.
12:21:13.027 Client activated.
12:21:13.034 JACK connection change.
12:21:13.051 JACK connection graph change.

***************************************88*8
Second Start – fails

13:03:19.573 Patchbay deactivated.
13:03:19.578 Statistics reset.
13:03:19.776 Startup script...
13:03:19.779 artsshell -q terminate
13:03:19.849 ALSA connection graph change.
sh: artsshell: not found
13:03:20.190 Startup script terminated with exit status=32512.
13:03:20.190 JACK is starting...
13:03:20.191 /usr/bin/jackd -t1000 -dalsa -r44100 -p64 -n2 -D -Chw:0,0 -Phw:0,0 -m
jackd 0.118.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
Memory locking is unlimited - this is dangerous. You should probably alter the line:
@audio - memlock unlimited
in your /etc/limits.conf to read:
@audio - memlock 715362
13:03:20.197 JACK was started with PID=5161.
13:03:20.395 ALSA connection change.
no message buffer overruns
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0,0|hw:0,0|64|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
13:03:21.167 JACK was stopped successfully.
13:03:21.168 Post-shutdown script...
13:03:21.168 killall jackd
13:03:21.169 JACK has crashed.
jackd: no process found
13:03:21.576 Post-shutdown script terminated with exit status=256.
13:03:22.409 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.

---

### Post by CivilizationII on 2012-02-20
> **daziel said:**
> Jack version 0.118.0
qjackctl version 0.3.4
Ubuntu version 10.04

I have been using jack with Ardour for 2+ years without problems.  After a recent software update I started having this problem;
jack will load and I can use hydrogen, ardour, etc to record and playback, and do a normal quit of all the programs without problems

When I try to start jack again it fails.  I have to reboot (soft reboot works) to get jack to run again.

(...)



It is very likely that jack is still running.

The best is to issue the command:

> sudo kill -9 jackdA very good trick is to always adding this command as qjackctl post-shutdown script.

---

