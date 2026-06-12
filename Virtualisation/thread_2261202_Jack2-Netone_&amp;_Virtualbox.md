---
title: "Jack2-Netone &amp; Virtualbox"
date: 2015-01-17
forum: Virtualisation
---

### Post by darkmatter2 on 2015-01-17
I'm running a Win8 VBox environment inside my Linux box.  Trying to route my audio from netjack inside the VBox to my alsa drivers.  I can ust the net (netjack2) drivers, but after some time (30 secs) I get an xrun and the stream can never get back on track.  It's almost as if it keeps trying to make up for the 1 underrun instead of just dropping it and moving on.  If I can fix this, it would be great.
In either case, I'm trying to give a crack at the netone driver.  But I get this response:


```
C:\Program Files (x86)\Jack>jackd -R -dnetone
jackdmp 1.9.11
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2014 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
Drivers/internals found in : C:\Windows
Drivers/internals found in : C:\Windows
JACK server starting in realtime mode with priority 10
self-connect-mode is "Don't restrict self connect requests"
InitTime : multimedia timer resolution set to 1 milliseconds
MMCSS API not used...
NetOne driver started
netjack_poll not implemented
Waiting aborted
Initing net driver fails...

```

What is netjack_poll and how do I implement it so I can run netone?  I can actually run netjack ([http://netjack.sourceforge.net/](http://netjack.sourceforge.net/)) if the Jackd package is uninstalled, but then I don't have the option of running JackRouter in my audio app because netjack doesn't install it.  I've tried everything!  Any ideas?  Oh, or if I can get low latency from Jackd without routing it through the net drivers, I'm all ears!

---

