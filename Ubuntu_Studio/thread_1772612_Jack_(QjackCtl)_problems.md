---
title: "Jack (QjackCtl) problems"
date: 2011-05-31
forum: Ubuntu Studio
---

### Post by dancelikeaindian on 2011-05-31
Ultimately I wanted to use Ardour to record some stuff, it tells me jack isn't running, then I go to set it up and get this result. went on the jack IRC channel for help and some guy told me that i have more than one copy of jack? and to remove without removing the dependencies. i did that and nothing happened. looked vigorously on google and noticed this is a new or recent bug ([here]("https://bugs.launchpad.net/ubuntu/+source/jackd-defaults/+bug/775686"))

by more than happy if someone helped me out. thanks a bunch.

```
Platform--- Ubuntu 11.04 Kernel 2.6.38-8

Jack Version--- 1.9.7

Audio interfaces (using HDA ATI SB---
0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xfbcf4000 irq 16
 1 [ICE1724        ]: ICE1724 - ICEnsemble ICE1724
                      ICEnsemble ICE1724 at 0xec00, irq 21
 2 [Generic        ]: HDA-Intel - HD-Audio Generic
                      HD-Audio Generic at 0xfbdfc000 irq 44
 3 [U0x46d0x8d9    ]: USB-Audio - USB Device 0x46d:0x8d9
                      USB Device 0x46d:0x8d9 at usb-0000:00:12.0-2, full speed

QjackCtl Results---
18:58:19.162 Patchbay deactivated.
18:58:19.162 Statistics reset.
18:58:19.167 ALSA connection change.
Cannot connect to server socket err = Connection refused
Cannot connect to server socket
jack server is not running or cannot be started
18:58:19.172 ALSA connection graph change.
18:58:20.485 JACK is starting...
18:58:20.486 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n3
Cannot connect to server socket err = Connection refused
Cannot connect to server socket
jack server is not running or cannot be started
no message buffer overruns
18:58:20.514 JACK was started with PID=12240.
no message buffer overruns
jackdmp 1.9.7
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK server starting in realtime mode with priority 10
control device hw:0
control device hw:0
audio_reservation_init
Acquire audio card Audio0
creating alsa driver ... hw:0|hw:0|1024|3|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
Using ALSA driver HDA-Intel running on card 0 - HDA ATI SB at 0xfbcf4000 irq 16
configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 3 periods
ALSA: final selected sample format for capture: 32bit integer little-endian
ALSA: use 3 periods for capture
ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: use 3 periods for playback
18:58:27.581 Could not connect to JACK server as client. - Overall operation failed. - Server communication error. Please check the messages window for more info.
JackProcessSync::LockedTimedWait error usec = 5000000 err = Connection timed out
Driver is not running
Cannot create new client
JackSocketClientChannel read fail
Cannot open qjackctl client
18:58:29.068 JACK is stopping...
jack main caught signal 15
```

---

### Post by Pablo_F on 2011-06-01
Hi,

I don't think you have two versions of jackd installed. 

I think the default timeout value of 500 ms (IIRC) is too low. Try increasing it. 5000 should be good. 

OTOH, you have 4 audio interfaces. Which of them do you want jack (and therefore ardour) to use? Are you choosing the right one?

Another tip, jackd 1.9.7 (jackd2 in general) seems to behave better in synchronous mode. Try appending "-S" to the jackd command, in the "server path" field of qjackctl.

Cheers, Pablo

---

