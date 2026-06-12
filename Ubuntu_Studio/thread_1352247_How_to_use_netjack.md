---
title: "How to use netjack?"
date: 2009-12-11
forum: Ubuntu Studio
---

### Post by pepsifx357 on 2009-12-11
I looked at the netjack site on how to setup the master and slave machines.

I started jack on the master machine as i normally would then I typed:

Master: jack_netsource -h 192.168.2.4 <-Slave Machine's IP

Slave: jackd -R -d netone

On the master machine the output was:

> ben@HMS_Audio:~$ jack_netsource -h 192.168.2.4
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
Enhanced3DNow! detected
SSE2 detected
apparent rate = 48000
creating alsa driver ... hw:1|hw:1|64|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:1
configuring for 48000Hz, period = 64 frames (1.3 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 16bit little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 16bit little-endian
ALSA: use 2 periods for playback
Enhanced3DNow! detected
SSE2 detected
Not Connected


And on the slave the output was:

> ben@MIDI:~$ jackd -R -d netjack
no message buffer overruns
jackd: unknown driver 'netjack'

What am I doing wrong?

---

### Post by Defrector on 2010-06-01
Old thread is old. However...

The correct driver name is 'net' and not 'netjack'

Change the driver name and it should work.

---

### Post by pepsifx357 on 2010-06-07
Thanks! I'll give it a try when I get the studio back running.

---

