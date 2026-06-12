---
title: "Jack with FW Echo Audiofire8 xrun fun help me please"
date: 2011-01-24
forum: Ubuntu Studio
---

### Post by adamgood on 2011-01-24
Hi All, recently I posted for some help to connect Jack to my Audiofire8 and had good success. Now I'm on a clean install of ubuntu-studio 10.10 trying to make it happen again and relive the glory but unfortunately having only some success.

so here's what I have...
Ubuntu-Studio 10.10
2.6.35-24-generic kernel
Echo Audiofire8

Jack starts up but I soon get an xrun or 2 then slowly more...below is the output from Jack which I terminated after 4 xruns (took maybe 30 seconds). What's the deal, a memory issue??? Thanks to anyone who can help me out!

Adam

```
15:23:52.567 Patchbay deactivated.
15:23:52.601 Statistics reset.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
15:23:52.614 ALSA connection graph change.
15:23:52.812 ALSA connection change.
15:24:01.686 Startup script...
15:24:01.687 artsshell -q terminate
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
sh: artsshell: not found
15:24:02.089 Startup script terminated with exit status=32512.
15:24:02.089 JACK is starting...
15:24:02.089 /usr/bin/jackd -P70 -dfirewire -dhw:0 -r44100 -p128 -n2
15:24:02.092 JACK was started with PID=3663.
no message buffer overruns
no message buffer overruns
jackdmp 1.9.6
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK server starting in realtime mode with priority 70
02418274817:  (ffado.cpp)[  92] ffado_streaming_init: libffado 2.999.0- built Aug 11 2010 00:12:04
02418483835: [31mError (bebob_avdevice.cpp)[  96] probe: Number of channels command failed
[0m02418488977: [31mError (avc_avdevice.cpp)[  89] probe: Subunit info command failed
[0m02418627919: [31mWarning (fireworks_session_block.cpp)[ 257] loadFromMemory: size not correct: got 13392, should be -4 according to data
15:24:04.399 Server configuration saved to "/home/adamgood/.jackdrc".
15:24:04.400 Statistics reset.
15:24:04.405 Client activated.
15:24:04.408 JACK connection change.
15:24:04.411 JACK connection graph change.
15:24:16.404 XRUN callback (1).
[0mJackPosixMutex::Unlock res = 1
JackAudioDriver::ProcessAsync: read error, skip cycle
JackAudioDriver::ProcessAsync: read error, skip cycle
15:24:19.896 XRUN callback (2).
JackPosixMutex::Unlock res = 1
JackPosixMutex::Unlock res = 1
JackAudioDriver::ProcessAsync: read error, skip cycle
15:24:41.856 XRUN callback (3).
JackPosixMutex::Unlock res = 1
JackAudioDriver::ProcessAsync: read error, skip cycle
JackPosixMutex::Unlock res = 1
JackAudioDriver::ProcessAsync: read error, skip cycle
15:24:44.507 XRUN callback (1 skipped).
JackAudioDriver::ProcessAsync: read error, skip cycle
15:24:45.071 XRUN callback (6).
JackPosixMutex::Unlock res = 1
15:24:50.306 Client deactivated.
15:24:50.307 JACK is stopping...
jack main caught signal 15
no message buffer overruns
15:24:50.705 JACK was stopped successfully.
15:24:50.705 Post-shutdown script...
15:24:50.706 killall jackd
jackd: no process found
15:24:51.112 Post-shutdown script terminated with exit status=256.
```

---

### Post by AutoStatic on 2011-01-24
Try a Periods/Buffer setting of 3 instead of 2. And try adding the -S option to the **/usr/bin/jackd** 'Server Path' entry in the settings window of QjackCtl.

Best,

Jeremy

---

### Post by adamgood on 2011-01-24
> **AutoStatic said:**
> Try a Periods/Buffer setting of 3 instead of 2. And try adding the -S option to the **/usr/bin/jackd** 'Server Path' entry in the settings window of QjackCtl.


Jeremy thank you for taking the time to write! Your posts are very helpful.

A little bit better but still getting xruns and the same:

```
"00728328241: [31mWarning (fireworks_session_block.cpp)[ 257] loadFromMemory: size not correct: got 13392, should be -4 according to data"
```

I'm going to go ahead and show you all of the info that I know of for what I've configured. Let me know what you think if you have a chance and thanks again!

Adam

####

For what it's worth, I have a linux-swap partition on the machine whereas with previous installations I did not. It does appear that it's being recognized and used (although hanging around 0%)

```
Ubuntu Studio Controls
Enable memlock (ON) 80% of system memory
Enable raw1394 access (ON)
```

####
```
/etc/security/limits.d/audio.conf

@audio   -  rtprio     95
@audio   -  memlock    unlimited
```

####
```
/etc/modprobe.d/blacklist-firewire.conf

#blacklist ohci1394
#blacklist sbp2
#blacklist dv1394
#blacklist raw1394
#blacklist video1394

blacklist firewire-ohci
blacklist firewire-sbp2
```

####
```
Settings for qjackctl
Server Path /usr/bin/jackd -S
Driver firewire

Realtime (ON)
Priority 70
Frames/Period 128
Sample Rate 44100
Periods/Buffer 3

(Latency = 8.71 msec)
```

---

