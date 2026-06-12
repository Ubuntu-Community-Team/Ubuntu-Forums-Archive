---
title: "jack crashes when starting other audio apps (firewire)"
date: 2010-03-13
forum: Ubuntu Studio
---

### Post by pip-le-pip on 2010-03-13
HI :)

I've been trying for days to get my** terratec phase 24x** going, hope you can help me out with this one:

jack seems fine after starting, but when i then open other apps like patchage or zynappsubfx it crashes:

> 11:37:08.340 Patchbay deactivated.
11:37:08.343 Statistics reset.
11:37:08.414 ALSA connection graph change.
11:37:08.603 ALSA connection change.
11:37:11.925 Startup script...
11:37:11.926 artsshell -q terminate
sh: artsshell: not found
11:37:12.333 Startup script terminated with exit status=32512.
11:37:12.333 JACK is starting...
11:37:12.334 /usr/bin/jackd -R -dfirewire -dhw:0 -r44100 -p64 -n2
11:37:12.343 JACK was started with PID=2705.
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
00421860509:  (ffado.cpp)[  92] ffado_streaming_init: libffado 1.999.43 built Sep 17 2009 20:03:51
11:37:14.427 Server configuration saved to "/home/pip/.jackdrc".
11:37:14.428 Statistics reset.
11:37:14.482 Client activated.
11:37:14.491 JACK connection graph change.
11:37:15.043 JACK connection graph change.
11:37:15.086 JACK connection change.
11:37:34.872 JACK connection graph change.
subgraph starting at qjackctl timed out (subgraph_wait_fd=16, status = 0, state = Running, pollret = 0 revents = 0x0)
...
11:37:35.490 JACK connection graph change.
subgraph starting at qjackctl timed out (subgraph_wait_fd=16, status = 0, state = Running, pollret = 0 revents = 0x0)
...
11:37:36.173 XRUN callback (1).
firewire ERR: wait status < 0! (= -1)
DRIVER NT: could not run driver cycle
11:37:49.974 JACK connection graph change.
11:37:50.007 JACK connection change.
jack main caught signal 12
no message buffer overruns
11:37:50.079 Shutdown notification.
11:37:50.080 JACK is stopping...
11:37:50.081 JACK is being forced...
zombified - calling shutdown handler
11:37:50.282 JACK was stopped successfully.
11:37:50.282 Post-shutdown script...
11:37:50.283 killall jackd
jackd: no process found
11:37:50.692 Post-shutdown script terminated with exit status=256.


these is my 'protocol' of the changes I made after installing UbuStu from scratch:

> 1. changed syctl.conf
2. changed limits.conf
3. created 40-rtc-permissions.rules
4. added noatime parameter in etc/fstab
5. added user pip to video group
6. in UbuStu controls allowed user pip access to firewire.
7. updated rtirq and added firewire to priority list in rtirq.

what did I get wrong this time?

cheers, pip

---

### Post by trulan on 2010-03-13
Looks like you've been pretty thorough - did you disable CPU scaling and set your CPU to its highest speed?  CPU scaling can wreak havok with Jack.

---

### Post by pip-le-pip on 2010-03-13
??? okay, I'll do some research into that (and how to do it ;) ) thanks for the tip

---

### Post by trulan on 2010-03-13
Easiest way, if you're running gnome, is to add the CPU frequency scaling panel applet.  Add one for each CPU core, and set them all to their highest frequency.

[http://www.ubuntugeek.com/howto-change-cpu-frequency-scaling-in-ubuntu.html](http://www.ubuntugeek.com/howto-change-cpu-frequency-scaling-in-ubuntu.html)

You don't necessarily need to follow that whole guide.  The last half of it just eliminates the need to enter your password when changing frequencies.

---

### Post by pip-le-pip on 2010-03-13
thanks, have tried that, my hardware doesn't support this option. cpu is set to 100% though.

---

### Post by rlameiro on 2010-03-13
maybe you are asking to much from the firewire device.
try to use a bigger buffer setting on jack.

---

### Post by pip-le-pip on 2010-03-14
YAY! checked the "no memory lock" option, that did the trick. thought I had done that before though, but then something else probably went wrong.. buffer is 2, is okay, gives me 2.9 latency.

thanks for advice n stuff :)

---

### Post by kazakore on 2010-03-14
> **trulan said:**
> Easiest way, if you're running gnome, is to add the CPU frequency scaling panel applet.  Add one for each CPU core, and set them all to their highest frequency.

[http://www.ubuntugeek.com/howto-change-cpu-frequency-scaling-in-ubuntu.html](http://www.ubuntugeek.com/howto-change-cpu-frequency-scaling-in-ubuntu.html)

You don't necessarily need to follow that whole guide.  The last half of it just eliminates the need to enter your password when changing frequencies.


Have the cores all got different scaling on the Core2Duo series (I know, Google.) I've only put one applet down. When I first had a play they all seemed separate, then late seemed they all changed together but maybe it was reset on a restart and I didn't notice...

---

### Post by trulan on 2010-03-15
> **kazakore said:**
> Have the cores all got different scaling on the Core2Duo series (I know, Google.) I've only put one applet down. When I first had a play they all seemed separate, then late seemed they all changed together but maybe it was reset on a restart and I didn't notice...
They're independent on my Intel Core Duo - can't say for the Core2Duo (or any other processor for that matter)

@pip-le-pip:  Did you add the memlock line to limits.conf?  You might want to double-check that, memory locking should work.

---

### Post by pip-le-pip on 2010-03-18
yeah done that right at the beginning. but jack is happy for the moment, only got problems with hydrogen and synaddsubfx at the moment, trying to compile yoshimi but get errors all the time... :) but I've got to do loads for uni the next couple of weeks, so I'll bother you with that when I've got more time to work on it.

---

### Post by AutoStatic on 2010-03-18
You can get Yoshimi from Philip's PPA: [http://ppa.launchpad.net/philip5/extra/ubuntu/pool/main/y/yoshimi/](http://ppa.launchpad.net/philip5/extra/ubuntu/pool/main/y/yoshimi/)

---

### Post by bluesscream on 2010-03-25
and don't frustrate yourself by trying to get jack's latencies <8 ms w/o xruns on a standard pc while running more then one application/effect/instrument/vst at the same time. ](*,) That's already better then alternative osses will reach on the same machine. They just don't show you hardly audible xruns.

---

