---
title: "Jack cannot access realtime kernel"
date: 2008-08-31
forum: Ubuntu Studio
---

### Post by dwinstonm on 2008-08-31
I've been using 8.04 since just after it's release for audio production, with the ubuntustudio packages and RT kernel (2.6.24-19-rt).  Everything was working just fine, but just today Jack is unable to access the kernel (i'm assuming).  I'm getting the same error messages as I was before I ran the commands in the [ubuntu studio preparation guide]("https://help.ubuntu.com/community/UbuntuStudioPreparation") to allow application access to the kernel.  I made sure that the rt-kernel was the default kernel, and even ran those commands again, no luck.    I can run Jack without RT just fine, but the latency is ridiculous.  
This is the Jack message output when it cannot connect

00:09:19.740 Startup script...
00:09:19.741 artsshell -q terminate
00:09:20.175 Startup script terminated with exit status=256.
00:09:20.176 JACK is starting...
00:09:20.177 /usr/bin/jackd -R -P10 -dalsa -r48000 -p256 -n3 -D -Chw:1 -Phw:1 -i4 -o2
00:09:20.180 JACK was started with PID=7505.
jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
cannot use real-time scheduling (FIFO at priority 10) [for thread -1210685776, from thread -1210685776] (1: Operation not permitted)
cannot create engine
00:09:20.193 JACK was stopped successfully.
00:09:20.194 Post-shutdown script...
00:09:20.195 killall jackd
jackd: no process killed
00:09:20.608 Post-shutdown script terminated with exit status=256.
00:09:22.387 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.

Anyone with a similar issue or potential fix?

---

### Post by rafafredd on 2008-08-31
Had this problem, and it was solved here:

[http://www.ardour.org/node/2037](http://www.ardour.org/node/2037)

---

### Post by dwinstonm on 2008-09-02
Stuff started working again, without doing anything.  I still don't know what caused it, but if it starts acting up again ill try that fix. Thanks.

---

