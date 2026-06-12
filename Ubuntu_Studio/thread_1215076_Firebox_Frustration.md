---
title: "Firebox Frustration"
date: 2009-07-16
forum: Ubuntu Studio
---

### Post by zymos on 2009-07-16
Been trying for hours to get this to work! The blue light will not even come on. It works flawlessly in Windows XP. Dell Inspiron, Ubuntu Studio 9.04.
If tried everything I can find on Google, but most of the posts I've seen are starting with the blue light already on.
(I also can't get my PCMCIA Echo indigo i/o to work either...light doesn't come on, though lspci shows the chip in it being detected.)

Any tips greatly appreciated...TIA!

---

### Post by Stochastic on 2009-07-16
What are the outputs of these commands:

```
grep raw1394 /lib/udev/rules.d/*
```
```
grep raw1394 /etc/udev/rules.d/*
```

and what's the error message you get when you try to start Jack with the ffado driver?

---

### Post by kayosiii on 2009-07-16
Using a firewire soundcard on linux currently involves a couple of security tradeoffs which is why it isn't enabled by default (as stupid as I think that is).

The first is that normal users don't have permission to access raw firewire devices... The easiest way to give yourself access to these is to use the ubuntustudio control panel - you can install this component from apt-get if you are using regular ubuntu or any other variant.

With 9.04 you will want to stick to the regular kernel (the realtime kernel has issues), it is very good latency wise.

The other security setting you will want to play with will allow you to set the priority of your audio programs higher than what is normally allowed. I think this can also be done using the ubuntu studio control tool - otherwise search these forums for /etc/security/limits.conf

---

### Post by zymos on 2009-07-17
> **Stochastic said:**
> What are the outputs of these commands:

```
grep raw1394 /lib/udev/rules.d/*
``````
grep raw1394 /etc/udev/rules.d/*
```and what's the error message you get when you try to start Jack with the ffado driver?

Thanks for taking a shot at my problem-

phil@ubuntu:~$ grep raw1394 /lib/udev/rules.d/*
/lib/udev/rules.d/50-udev-default.rules:KERNEL=="raw1394",        GROUP="video"

if I invoke jack thusly: jackd -v -R -d freebob

I get:
getting driver descriptor from /usr/lib/jack/jack_dummy.so
getting driver descriptor from /usr/lib/jack/jack_net.so
getting driver descriptor from /usr/lib/jack/jack_freebob.so
getting driver descriptor from /usr/lib/jack/jack_oss.so
getting driver descriptor from /usr/lib/jack/jack_firewire.so
no message buffer overruns
getting driver descriptor from /usr/lib/jack/jack_alsa.so
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
server `default' registered
registered builtin port type 32 bit float mono audio
registered builtin port type 8 bit raw midi
clock source = system clock via clock_gettime
start poll on 3 fd's
loading driver ..
new client: freebob_pcm, id = 1 type 1 @ 0x9428dc0 fd = -1
Freebob using Firewire port 0, node -1
new buffer size 1024
LibFreeBoB MSG: FreeBoB Streaming Device Init
LibFreeBoB MSG:  Using FreeBoB lib version libfreebob 1.0.11
LibFreeBoB MSG:  Device information:
LibFreeBoB MSG:  Device options:
LibFreeBoB MSG:   Port                     : 0
LibFreeBoB MSG:   Device Node Id           : -1
LibFreeBoB MSG:   Samplerate               : 48000
LibFreeBoB MSG:   Period Size              : 1024
LibFreeBoB MSG:   Nb Buffers               : 3
LibFreeBoB MSG:   Directions               : 0
Root node has no children!
Root node has no children!
LibFreeBoB ERR: No connections specified, bailing out
FreeBoB ERR: FREEBOB: Error creating virtual device
cannot load driver module freebob
starting server engine shutdown
server thread back from poll
freeing shared port segments
stopping server thread
last xrun delay: 0.000 usecs
max delay reported by backend: 0.000 usecs
freeing engine shared memory
max usecs: 0.000, engine deleted
cleaning up shared memory
cleaning up files
unregistering server `default'

---

### Post by kayosiii on 2009-07-17
you want to be using the ffado (called firewire) driver rather than the freebob one in Jaunty.

---

