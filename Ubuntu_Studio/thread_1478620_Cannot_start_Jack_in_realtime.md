---
title: "Cannot start Jack in realtime"
date: 2010-05-09
forum: Ubuntu Studio
---

### Post by Mr A Mouse on 2010-05-09
Hello all,

I have some Linux experience, but am a complete newbie with realtime kernels and with audio in Linux.

Platform:
IBM Thinkpad R51, .5 GB RAM
Ubuntu Karmic with Ubuntustudio software 
Shiny new 2.6.31-9-rt kernel.

If I try to start Jack via qjackctl with realtime turned off, it works like a charm. If I try to start it with realtime turned on, I get the following:

```

22:49:13.031 JACK is starting...
22:49:13.032 /usr/bin/jackd -R -dalsa -dhw:0 -r44100 -p1024 -n2
22:49:13.036 JACK was started with PID=1970.
22:49:13.341 ALSA connection change.
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
22:49:16.000 Could not connect to JACK server as client. - Overall operation failed. Please check the messages window for more info.
22:49:16.653 JACK was stopped successfully.
22:49:16.654 Post-shutdown script...
22:49:16.655 killall jackd
22:49:16.655 JACK has crashed.
jackd: no process found
22:49:17.278 Post-shutdown script terminated with exit status=256.
```

Any ideas? Is there anywhere--a logfile or the like--that I can go look at to see why Jack crashed?

---

### Post by djxcon on 2010-05-12
Did you review the Messages window in Jack? also, post the output of ```
uname -a
```

---

### Post by sgx on 2010-05-13
try this, first as normal user, then as root

jackd -R -d alsa -r 44100  

If the terminal output ends like this:

ALSA: final selected sample format for capture: 32bit integer little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: use 2 periods for playback

then start qjackctl

If not working, try

sudo jackd -R -d alsa -r 44100

If it works as root, its likely narrowed down to a permission issue somewhere.
Cheers

---

### Post by Mr A Mouse on 2010-05-13
> **djxcon said:**
> Did you review the Messages window in Jack? also, post the output of ```
uname -a
```

I've rebooted to the generic, but I think I've found the problem.

> **sgx said:**
> try this, first as normal user, then as root

jackd -R -d alsa -r 44100  

```
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
Bus error

```

I get this error as regular user or root. 

> sudo jackd -R -d alsa -r 44100

Same here.

This error led me to [this thread]("http://ubuntuforums.org/showthread.php?t=1300413"): I'll explore this as the next step in troubleshooting.

---

