---
title: "FluidSynth doesn't run"
date: 2016-05-07
forum: Ubuntu/Debian BASED
---

### Post by James_Tobin on 2016-05-07
FluidSynth installs on terminal but does not run. Here is terminal error logs. Help!

```
james@Zorin:~$ sudo apt-get remove fluidsynth
[sudo] password for james: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  fluidsynth
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 60.4 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 368631 files and directories currently installed.)
Removing fluidsynth (1.1.6-2build1) ...
Processing triggers for man-db (2.7.4-1) ...
```

```
james@Zorin:~$ sudo apt-get install FluidSynth
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  fluidsynth
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/19.4 kB of archives.
After this operation, 60.4 kB of additional disk space will be used.
Selecting previously unselected package fluidsynth.
(Reading database ... 368624 files and directories currently installed.)
Preparing to unpack .../fluidsynth_1.1.6-2build1_amd64.deb ...
Unpacking fluidsynth (1.1.6-2build1) ...
Processing triggers for man-db (2.7.4-1) ...
Setting up fluidsynth (1.1.6-2build1) ...
```

```
james@Zorin:~$ fluidsynth
FluidSynth version 1.1.6
Copyright (C) 2000-2012 Peter Hanappe and others.
Distributed under the LGPL license.
SoundFont(R) is a registered trademark of E-mu Systems, Inc.

Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jackdmp 1.9.10
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2014 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
Cannot create RT messagebuffer thread: Operation not permitted (1)
Retrying messagebuffer thread without RT scheduling
Messagebuffer not realtime; consider enabling RT scheduling for user
no message buffer overruns
Cannot create RT messagebuffer thread: Operation not permitted (1)
Retrying messagebuffer thread without RT scheduling
Messagebuffer not realtime; consider enabling RT scheduling for user
no message buffer overruns
Cannot create RT messagebuffer thread: Operation not permitted (1)
Retrying messagebuffer thread without RT scheduling
Messagebuffer not realtime; consider enabling RT scheduling for user
no message buffer overruns
JACK server starting in realtime mode with priority 10
self-connect-mode is "Don't restrict self connect requests"
Cannot lock down 82274202 byte memory area (Cannot allocate memory)
audio_reservation_init
Acquire audio card Audio0
creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|-|32bit
ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
JackTemporaryException : now quits...
Cannot initialize driver
JackServer::Open failed with -1
Failed to open server
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
fluidsynth: error: Failed to connect to Jack server.
Failed to create the audio driver
```

---

### Post by howefield on 2016-05-08
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by James_Tobin on 2016-05-08
@howefield: Oh you moved it.. took me a long time to find my post, why moved to ubuntu/debian BASED?

---

### Post by Rob Sayer on 2016-05-11
The fact that your machine name is 'Zorin' is a dead giveaway that you're running Zorin instead of Ubuntu.  Ubuntu based distros aren't supported here, just Ubuntu.

---

### Post by James_Tobin on 2016-05-12
good grief.. this is just a terminal quesiton but alright, now i know the kind of people i am dealing with

---

### Post by rewyllys on 2016-05-14
> **James_Tobin said:**
> good grief.. this is just a terminal quesiton but alright, now i know the kind of people i am dealing with
Pardon my candor, but your response is truly a great way to win friends, influence people, and invite help.

---

### Post by lisati on 2016-05-14
Thread closed at OP's request

---

