---
title: "Problems Starting Jack"
date: 2009-09-01
forum: Ubuntu Studio
---

### Post by junglejuice on 2009-09-01
hi
i have the same problem, jack will not start up the message i get is
```
21:03:35.770 Patchbay deactivated.
21:03:35.888 Statistics reset.
21:03:35.994 Startup script...
21:03:35.995 artsshell -q terminate
21:03:36.030 ALSA connection graph change.
sh: artsshell: not found
21:03:36.396 Startup script terminated with exit status=32512.
21:03:36.396 JACK is starting...
21:03:36.397 /usr/bin/jackd -dalsa -r44100 -p1024 -n3 -D -Chw:0 -Phw:0 -S -Xseq
21:03:36.399 JACK was started with PID=28650.
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|1024|3|44100|0|0|nomon|swmeter|-|16bit
control device hw:0
configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 3 periods
ALSA: final selected sample format for capture: 16bit little-endian
ALSA: got smaller periods 2 than 3 for capture
ALSA: cannot configure capture channel
cannot load driver module alsa
21:03:36.599 ALSA connection change.
21:03:36.623 JACK was stopped successfully.
21:03:36.624 Post-shutdown script...
21:03:36.624 killall jackd
jackd: no process killed
21:03:37.067 Post-shutdown script terminated with exit status=256.
21:03:38.607 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
```
i am running ubuntu 9.04 (not ubuntustudio because i can't get ubuntu to stop laggin' when i try running it with the realtime kernel, so i have a desktop enviroment that looks like ubuntu studio but does not use the realtime kernel, hope that makes sense)
the soundcard i am using is soundblaster audigy DE (it's the old one, not the new soundblaster audigy).
i never had a problem with jack on ubuntu 8.10 however i was never able to use the realtime kernel either. 8.04 as worked best thus far as both the realtime kernel and jack worked perfectly. however i would prefer to stick with 9.04 as it works better with my modem. if anyone out there can make a suggestion as to how to fix this issue i'd be really grateful. thanx. btw i have tried disabling the realtime option in jack but this has had not effect jack still seems to be unable to start

---

### Post by trulan on 2009-09-01
> **junglejuice said:**
> hi
i have the same problem, jack will not start up the message i get is
```

configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 3 periods
ALSA: final selected sample format for capture: 16bit little-endian
ALSA: got smaller periods 2 than 3 for capture
ALSA: cannot configure capture channel
cannot load driver module alsa

```
It looks like your sound card will only work with 2 buffer periods, and you are trying to use 3.  Try setting your buffer to 2 periods.

---

### Post by dawiba on 2009-09-02
@junglejuice - First of all, try Trulan's suggestion.

Just out of interest, what are you trying to do on your computer?

For example, are you recording instruments/vocals into Ardour or Audacity?

Are you importing loops and samples into LMMS?

Are you recording sounds through the onboard soundcard line-in, playing back the sounds through the computer speakers?

I ask because I'm not sure that every situation needs Jack for all users. For example, if you're importing loops and samples into LMMS and playing around with them to make a song or arrangement *_and_* you're doing this through your onboard soundcard, I don't think you even need to use Jack at all. In fact, you can use Ardour without Jack in a similar fashion. Many of the Linux audio programs run fine without Jack.

In my experience, Jack works best in conjunction with a real time kernel and particularly if you are using two or more programs at the same time. It's perfect for connecting instruments, both real and virtual, for connecting applications and routing your audio and midi in a situation where you have multiple sources.

---

### Post by Stochastic on 2009-09-02
Moved these posts to their own thread as the issue was a different Jack problem than the original thread.

---

