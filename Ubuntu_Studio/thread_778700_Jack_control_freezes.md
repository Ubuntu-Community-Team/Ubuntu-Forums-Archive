---
title: "Jack control freezes"
date: 2008-05-02
forum: Ubuntu Studio
---

### Post by Hotrock on 2008-05-02
Hi all. I'm new to linux and installed ubuntu studio onto my laptop specifically for music production. Unfortunately I haven't been able to explore the delights of this promising package because qjackctl freezes as soon as I load any of the music packages.

System specs:

Intel® Celeron™ M Processor 440, 1.86GHz, FSB 533MHz, 1MB On-Die L2 Cache, 1 gig mem

I know I need more memory but surely qjackctl doesn't use it all?

Any help that gets me going would be very much appreciated.

Thank you.

Hotrock

---

### Post by warbread on 2008-05-02
Your specs look plenty good for music production.  

Try running qjackctl from terminal and see what that says.  Post the output here if you want help interpreting.  Look at the 'Messages' box in qjackctl as well.  It has some debug information, and it would help to see what it's doing at the time of the freeze.  It would also help to know what you have done so far to get it working.  Have you followed any tutorials where you un/install a program or edit a config file?  Have you enabled and are you using the real time kernel?

---

### Post by Hotrock on 2008-05-02
Thank you Warbread, As for un/installing and editing config files, I have done neither. This is a completely clean, brand new installation of Ubuntu studio. (Finally got rid of the pre-installed Vista - and it feels great!) ;D

I ran qjackcontl from terminal and I got the following message which means very little to me (AsI said, I'm completely new to linux)

Warning: no locale found:/usr/share/locale/qjackctl_en_GB.qm

The messages from within jackctl is as follows:
20:00:12.000 Patchbay deactivated
20:00:12.148 Statistics reset.
20:00:12.165 Startup script
20:00:12.166 artsshell -q terminate
20:00:12.337 ALSA connection graph change
20:00:12.654 startup scrip terminated with exit status=256
20:00:12.654 Jack is starting
20:00:12.655/usr/bin/jackd-R-dalsa=dhw:0-r44100-p1024-n2
jackd 0.109.2
(copyright stuff followed by)
cannot lock down memory for jackd(Cannot allocate memory)
20:00:12.666 Jack was started with PID=6031
loading driver..
apparent rate 44100
creating alsa driver...hw:0|hw:0|1024|2|44100|00nomon|swmeter|-|32bit
control devise hw:0
configuring for 44100,period-1024 frames (23.2ms),buffer-2 periods
ALSA final selected sample format for playbck:32bit little-endion
ALSA:use 2 periods for capture
ALSA final selected sample format for playbck:32bit little-endion
ALSA:use 2 periods for playback
JACK:unable to mlock() port buffers:cannot allocate memory

and a little more that I can't see because everything at this point freezes and I can't scroll down any further, nor can I copy and paste though that may be typical.
I hope this helps.
Thank you again.
Hotrock

---

