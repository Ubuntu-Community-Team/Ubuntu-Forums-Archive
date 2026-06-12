---
title: "Huge instability after upgrade from Lucid Desktop to Studio/rt"
date: 2010-06-01
forum: Ubuntu Studio
---

### Post by markhadman on 2010-06-01
Hi,
This is weird but I'm hopeful that at least someone else out there has experienced similar.

Having upgraded a quite stable-seeming Ubuntu Lucid Desktop to 'Studio, I have severe instability.

After bootup and initial log-in, qjackctl and jack behave normally (with Ardour at least). I can stop and restart the jack server multiple times with no problems. However, after going away and doing other stuff (Firefox, synaptic, etc) then coming back to audio work, (q)jack(ctl) starts throwing a very uninformative crash error (see messages log below).

Furthermore, with qjackctl now open I am often unable to start a terminal or firefox, and random pieces of Gnome start dying ('Workspace switcher has quick unexpectedly' or some such annoyance, or the WM/decorations disappear).

Stopping qjackctl (if possible) and/or restarting X get Gnome back to normal, but I have to reboot the machine to get jack working again.

So, I guess the question is - does this look familiar to anyone? Is it a pulse/delta1010 problem? A bug in qjackctl/jack? A memory leak? A problem with the rt kernel? There are too many possibilities for me to know where to start with this one!

Begin very unhelpful error message:
```
03:41:53.064 Patchbay deactivated.
03:41:53.108 Statistics reset.
03:41:53.309 Startup script...
03:41:53.310 artsshell -q terminate
03:41:53.314 ALSA connection graph change.
sh: artsshell: not found
03:41:53.713 Startup script terminated with exit status=32512.
03:41:53.714 JACK is starting...
03:41:53.714 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p512 -n2
jackd 0.118.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
Memory locking is unlimited - this is dangerous. You should probably alter the line:
     @audio   -  memlock    unlimited
in your /etc/limits.conf to read:
     @audio   -  memlock    957144
03:41:53.739 JACK was started with PID=6846.
no message buffer overruns
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|512|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
03:41:53.924 ALSA connection change.
03:41:54.943 JACK was stopped successfully.
03:41:54.944 Post-shutdown script...
03:41:54.944 killall jackd
03:41:54.945 JACK has crashed.
jackd: no process found
03:41:55.421 Post-shutdown script terminated with exit status=256.
03:41:56.175 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
```

---

### Post by sgx on 2010-06-01
Not an informed opinion on anything specific, but if you are in a
position to revert, or do a new full Ubuntu Studio install, you might
save a lot of time and trouble. I'm leery of the new way limits.conf
is implemented, with odd permissions problems that keep reappearing,
and might be more common in upgrades, than full installs.

I installed Mint9, non-mint KDE, and Ubuntu Studio meta package on a
laptop this weekend, so far so good, knocks on wood (does formica count?)

Cheers

---

