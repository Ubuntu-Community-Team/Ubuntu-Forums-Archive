---
title: "cannot start jackd"
date: 2011-06-20
forum: Ubuntu Studio
---

### Post by mr.garfield on 2011-06-20
Hi,

I need help with setting up jackd and qjackctl on Ubuntu Natty 11.04 on my machine. It worked like a charm before I re-installed from Ubuntu 10.10.

After going through many forums and trying to understand what is going on I am pretty much lost. I would appreciate help in diagnosing the problem on my machine. Here is what I get when I press start in qjackctl:

```
22:08:43.682 Patchbay deactivated.
22:08:43.684 Statistics reset.
22:08:43.701 ALSA connection change.
Cannot connect to server socket err = Connection refused
Cannot connect to server socket
jack server is not running or cannot be started
22:08:43.711 ALSA connection graph change.
22:08:44.925 JACK is starting...
22:08:44.926 /usr/bin/jackd -p128 -t5000 -dalsa -dhw:0 -r44100 -p1024 -n2
Cannot connect to server socket err = Connection refused
Cannot connect to server socket
jack server is not running or cannot be started
no message buffer overruns
22:08:44.967 JACK was started with PID=2284.
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
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
Using ALSA driver HDA-Intel running on card 0 - HDA VIA VT82xx at 0xdfafc000 irq 69
configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 32bit integer little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: use 2 periods for playback
22:08:52.120 Could not connect to JACK server as client. - Overall operation failed. - Server communication error. Please check the messages window for more info.
JackProcessSync::LockedTimedWait error usec = 5000000 err = Connection timed out
Driver is not running
Cannot create new client
JackSocketClientChannel read fail
Cannot open qjackctl client
22:08:55.411 JACK is stopping...
jack main caught signal 15
```

I even went back to 32bit Ubuntu just to see if that worked out of the box. However I did not have any luck so far. The standard "realtime" settings for limits for the audio group are in place and my user belongs to the audio group.

TIA.

Cheers
Mr.Garfield

---

### Post by sgx on 2011-06-21
Can you start jackd manually with

jackd -d alsa -r 44100

then start qjackctl

[http://www.linuxdsp.co.uk/download/jack/index.html](http://www.linuxdsp.co.uk/download/jack/index.html)

jp1 from the above link is a good alternative to qjackctl, especially if you craft working jackd command lines. They can be open at the same time, connection/disconnection are easier in jp1, and qt can conflict with other apps in rare cases.

You are not alone. Better to go back to a 10.x version, and put
11.04 on a usbstick/drive so you can test/experiment 11.04, and still
enjoy a working version.
Cheers

---

### Post by mr.garfield on 2011-06-22
ok I tried to run jackd from the command line. However the outcome is the same:

```
jackd -d alsa -r 44100
jackdmp 1.9.7
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
no message buffer overruns
no message buffer overruns
`default' server already active
Failed to start server
mtd@mercury:~$ jackd -d alsa -r 44100
jackdmp 1.9.7
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
no message buffer overruns
no message buffer overruns
JACK server starting in realtime mode with priority 10
control device hw:0
control device hw:0
audio_reservation_init
Acquire audio card Audio0
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
Using ALSA driver HDA-Intel running on card 0 - HDA VIA VT82xx at 0xdfafc000 irq 69
configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 32bit integer little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: use 2 periods for playback
ALSA: poll time out, polled for 34828019 usecs
JackAudioDriver::ProcessAsync: read error, stopping...

```

The process just hangs with the last line of output.

Any other suggestions as to what I could check?

Cheers

---

### Post by Pablo_F on 2011-06-22
Maybe try in sync mode?

You do this by writing down in the "Server path" field the following:

usr/bin/jackd --sync 

or just:

usr/bin/jackd -S

Also, increase the timeout value.

If this fails, there is #jack IRC channel:

[http://webchat.freenode.net/?channels=jack](http://webchat.freenode.net/?channels=jack)

#opensourcemusicians is another good one. And there is #ubuntustudio also.

Cheers, Pablo

---

### Post by Flaggmann on 2011-06-22
I recall reading that qjackctl launches it's own instance of jackd, so if it is already running from a commandline startup and the checkmark in the setup window does not allow mutiple instances, it likely will generate an error.

I have never started jackd from commandline to begin with until after I have configured it the way I want it.

open a terminal and make sure all instances of jackd are stopped. then use the qjackctrl to start it. It may say no jackd running and halt, but it will keep the window open to allow you to do the setup changes and then restart.  remove the checkmark for single instances, add a checkmark for use soft mode  then go to the misc tab, and put a check mark in "Start Jack on Application startup, also enable system tray icon, also start minimized to system tray, 

Click OK and then click STOP and QUIT and then relaunch qjackctl and see if that helps.

I only use Jack and ALSA and have disabled pulse audio in such a way that it doesn't kill the desktop by uninstalling it completely. The method I used, posted here previously, just fools to the system into thinking pulseaudio is OK but yet disables it so jack audio and ALSA can work together without any interference from pulse audio.

---

### Post by siabost on 2011-07-05
Try System/Administration/Users and Groups.
Check that your name is ticked in the User Groups "Audio", "Users" &, strangely enough, the group under your own name!

I had a similar problem with 64bit 11.04 version and that seemed to fix it.

Hope that helps :p

Edit: it only partly worked - sometimes Jack freezes on clicking "Start", other times it's fine. More research!

---

