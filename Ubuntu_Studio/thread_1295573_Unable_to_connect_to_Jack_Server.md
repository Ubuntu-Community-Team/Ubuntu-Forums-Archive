---
title: "Unable to connect to Jack Server"
date: 2009-10-19
forum: Ubuntu Studio
---

### Post by fabiotheimpaler on 2009-10-19
Hey, I'm new to Linux, and I can't figure out how the F to get Jack confyigured.  Whenever I try to start JACK, I get this message 

17:05:29.101 Patchbay deactivated.
17:05:29.141 Statistics reset.
17:05:29.294 Startup script...
17:05:29.295 artsshell -q terminate
17:05:29.299 ALSA connection graph change.
sh: artsshell: not found
17:05:29.698 Startup script terminated with exit status=32512.
17:05:29.698 JACK is starting...
17:05:29.699 /usr/bin/jackd -R -dalsa -dhw:0,0 -r44100 -p256 -n2 -m
17:05:29.701 JACK was started with PID=5233.
no message buffer overruns
17:05:29.918 ALSA connection change.
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
cannot use real-time scheduling (FIFO at priority 10) [for thread -1211484480, from thread -1211484480] (1: Operation not permitted)
cannot create engine
17:05:29.936 JACK was stopped successfully.
17:05:29.937 Post-shutdown script...
17:05:29.937 killall jackd
jackd: no process killed
17:05:30.352 Post-shutdown script terminated with exit status=256.
17:05:31.925 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.

Any suggestions?

---

### Post by martinistudio on 2009-10-19
Ubuntu 9.04?

You might want to search on the internet/ this forum first about how to configure qjackctl

---

### Post by AutoStatic on 2009-10-20
Hello fabiotheimpaler,

I think you need to configure a few things things first if you want to run jackd in real-time mode (that's the -R option):
- Install a real-time kernel if you didn't do so yet
- Add a group 'audio' on your system and add your account to it
- Modify your /etc/security/limits.conf file to add permissions for the 'audio' group, more info here: [http://wiki.linuxmusicians.com/doku.php?id=system_configuration&DokuWiki=65a55e87ac2a8f085f9c4394c8064680](http://wiki.linuxmusicians.com/doku.php?id=system_configuration&DokuWiki=65a55e87ac2a8f085f9c4394c8064680)

If you're not sure what real-time is all about than you could also try unticking the Realtime parameter in Qjackctl.

---

### Post by fabiotheimpaler on 2009-10-20
Thanks.  I read up on those threads and I got it working for the most part.  I think.  

Can anyone explain exactly what the kernel is/what it does?  And what the real-time kernel is?

---

### Post by trulan on 2009-10-20
I'll give you an uneducated idea - this may not be completely accurate, it's just the way I understand it:

The kernel is basically the core of your operating system.  It says what happens when in your computer.

The real-time kernel is the regular kernel (or generic kernel, as it is usually referred to) with some patches added to enable it to process certain things very quickly, handing information off virtually as soon as it receives it.  In the real world, this will enable you to process an audio signal, for example, measurably quicker.  Whether or not you can hear the difference depends on what you are doing.  From my limited experience, I seem to be able to shave around six milliseconds off of the time it takes my computer to process an audio signal by using the real-time kernel.  (That's just a rough approximation - I haven't scientifically tested it, just tinkered with the measurement applications).  You're not going to hear a six-millisecond lag, but you just might hear a 15 millisecond lag, and shaving six milliseconds off that can sometimes be very important.

When you enable RT in Jack, you are simply telling the computer to give the Jack server a higher priority than it would get by default.  You need proper permissions to be able to do that, which is why you were having trouble at first.  You can do that using the generic kernel, but it is much more effective if you have the RT kernel.

---

