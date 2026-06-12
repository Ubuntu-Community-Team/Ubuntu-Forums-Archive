---
title: "Jack Could not connect to JACK server as client. - Overall operation failed."
date: 2010-09-12
forum: Ubuntu Studio
---

### Post by Sylos on 2010-09-12
Hello everyone.
Following a new install of Ubuntu Studio 10.04 I attempted to install Jack1.9.5 by downloading it from the Jack website and compiling it. All seemed to go well and the server started fine when I tested it (although I didnt remove the old Jack first so not sure whether it was Jack 2 or not).

I then did the raft of updates from the Update Manager and rebooted. I then enabled the NVIDIA driver and rebooted again to test out the set up. At this point I am getting the error in the title of this post.

The output of the Verbose message window is as follows:

```
20:00:27.000 Patchbay deactivated.
20:00:27.095 Statistics reset.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
20:00:27.207 ALSA connection graph change.
20:00:27.394 ALSA connection change.
20:00:35.668 Startup script...
20:00:35.669 artsshell -q terminate
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
sh: artsshell: not found
20:00:36.073 Startup script terminated with exit status=32512.
20:00:36.074 JACK is starting...
20:00:36.075 /usr/bin/jackd -v -dalsa -dhw:0 -r96000 -p1024 -n3
/usr/bin/jackd: symbol lookup error: /usr/bin/jackd: undefined symbol: clock_source
20:00:36.091 JACK was started with PID=2224.
20:00:36.107 JACK was stopped with exit status=127.
20:00:36.108 Post-shutdown script...
20:00:36.108 killall jackd lashd ladishd
jackd: no process found
lashd: no process found
ladishd: no process found
20:00:36.521 Post-shutdown script terminated with exit status=256.
20:00:38.229 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
```

Not sure what the fix for this is.

As always I am eternally grateful to anyone who can offer insight.

---

### Post by Pablo_F on 2010-09-12
Hi, 

Afaik, you can't have both versions of jack installed at the same time. Remove one of them. Stick to the official version, I recommend.

Cheers! Pablo

---

### Post by Sylos on 2010-09-13
Cheers Pablo_F. I have just finished reinstalling the distro from the DVD so Hopefully I'll be all set. Im gonna keep the thread open unti I have tested Jack out a little as the reason for my attempted upgrade was due to Jack doing Xruns under very little load and then leaving zombie processes that forced me to reboot the system. 

Cheers

---

### Post by AutoStatic on 2010-09-13
> **Sylos said:**
> Im gonna keep the thread open unti I have tested Jack out a little as the reason for my attempted upgrade was due to Jack doing Xruns under very little load and then leaving zombie processes that forced me to reboot the system.Then it's better to troubleshoot the version of JACK that comes with your distro then trying to compile and install a newer version and run in all kinds of complications. Besides, JACK 1.9.5 is not a higher version of JACK 0.118 that comes with Lucid. It's a totally different implementation, written in another programming language and with a focus on multithreading so it better uses CPU's with multiple cores.

---

### Post by genmi on 2011-01-29
I am having a nearly identical problem. Just upgraded to 10.04 LTS from 9.10 and have been trying to figure out how to install JACK2. Had not realized I needed to delete JACK1 before building from the source. Now I have been attempting to delete everything and rebuild, but cannot seem to get past this same error each time I start a JACK server:

```
11:51:16.976 Patchbay deactivated.
 11:51:17.071 Statistics reset.
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 11:51:17.088 ALSA connection graph change.
 11:51:17.283 ALSA connection change.
 11:51:19.672 JACK is starting...
 11:51:19.673 /usr/bin/jackd -r -t2000 -dalsa -dhw:0 -r44100 -p1024 -n3
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 /usr/bin/jackd: symbol lookup error: /usr/bin/jackd: undefined symbol: clock_source
 11:51:19.746 JACK was started with PID=16073.
 11:51:19.761 JACK was stopped with exit status=127.
 11:51:19.763 Post-shutdown script...
 11:51:19.764 killall jackd
 jackd: no process found
 11:51:20.176 Post-shutdown script terminated with exit status=256.
 11:51:21.760 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started

```Any help on this would be very much appreciated.

---

### Post by Sylos on 2011-01-31
Hello.

How have you gone about deleting all the JACK stuff before re-installing?

---

### Post by genmi on 2011-01-31
sudo apt-get remove

---

### Post by Sylos on 2011-02-01
Could you try launching Jack from the terminal with the following command

```
jackd -d alsa
```

 And then launch Qjackctl in the normal way.

Please post back with whatever result you get from this.

Also, if you only did the apt-get remove method then there will still be some refeerences to jack contained in /usr/local/lib that wont help.

Try reading here if you havent already

[http://ubuntuforums.org/archive/index.php/t-1569450.html](http://ubuntuforums.org/archive/index.php/t-1569450.html)

Keep me posted with the results. As you may have guessed by my original post Im no expert but I'll help if I can.

---

### Post by keantoken on 2011-05-08
I have the same problem. Here is the output from that line:

```
$ jackd -d alsa
jackdmp 1.9.6
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
no message buffer overruns
no message buffer overruns
JACK server starting in realtime mode with priority 10
audio_reservation_init
Acquire audio card Audio0
creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|-|32bit
Using ALSA driver HDA-Intel running on card 0 - HDA Intel at 0xb3220000 irq 46
configuring for 48000Hz, period = 1024 frames (21.3 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 32bit integer little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: use 2 periods for playback
```

I've also been trying to get Pulseaudio to run with it using pulseaudio-module-jack. Whenever I edit /home/.pulse/default.pa to insert the Jack modules, pulseaudio continually gets "connection refused" and continually respawns, causing everything to slow down until I can do "killall pulseaudio". From google searches this seems to be a persistent error no one can solve. I wonder if this Jack error is related?

 - keantoken

---

### Post by keantoken on 2011-05-09
This Jack error seems to be caused by a conflict between Pulseaudio and Jack trying to access the same card. In my case at least.

I suspected this might indicate that one of the steps to making Pulseaudio and Jack work together is missing; the part where you redirect ALSA to Pulsaudio. I'm not sure really what that means anyways, but in this step you edit asound.conf. I though it was strange that asound.conf didn't already exist. But after some suspicion I installed asoundconf-gtk:

```
$ asoundconf-gtk
sh: /usr/bin/asoundconf: not found
You need to make sure asoundconf is active!
By default, asoundconf's configuration file is ~/.asoundrc.asoundconf
and must be included in ~/.asoundrc. Open this file to make sure it is!
$ asoundconf
asoundconf: command not found
```

So it looks like I need to install asoundconf. It would make lots of sense if this was the big problem, because it's nowhere in Synaptic; so it couldn't be installed for 10.04.

Now where can I find asoundconf, and if I install it will it work the same way it used to?

 - keantoken

---

### Post by Sylos on 2011-05-09
Hello there.

As you can see Im not all that knowledgable but I think the gtk still exists but not the asoundconf script itself - hence you can install the gtk from synaptic but cant find asoundconf itself.

I think you would only really need asoundconf if you are switching between two different sound cards (I may be wrong). If you are just trying to get sound working from your apps again I dont think you need it. You have a couple of options:

1. (what I did). I only use Ustudio for recording audio so I just removed pulse audio and only use jack. System sounds dont work and neither does stuff in firefox etc but that doesnt bother me. If it is a problem for you try...

2. You can try to make pulseaudio shunt everything through jack. You need to have the correct pulse-jack package installed for this. See the thread below:

[http://ubuntuforums.org/showthread.php?t=1717272](http://ubuntuforums.org/showthread.php?t=1717272)    Not sure if this is what you are already trying.

3. You can jackify a lot of sound producing progs to try and make them use jack directly.

Jack and pulse will be a pain together without some work around. Pulse is started automatically when you boot so it will constantly be hogging the card. You could try some kind of kill command like

```
sudo killall pulseaudio
```

and then restart alsa with

```
sudo alsa force-reload
```

That might work. If it does you could put a script on your desktop for it and use when you need. Not sure when Pulse will respawn so it maty keep comming back anyway. It would be more elegant to follow one of the proper work arounds above. If you can stand it then I would just bin Pulse all together.

Hope that helps. Keep posting if you still have issues.

---

