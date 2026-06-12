---
title: "PreSonus FP10 recording help"
date: 2010-01-31
forum: Ubuntu Studio
---

### Post by Revolutionary101 on 2010-01-31
I installed Ubuntu on my friends Desktop computer today and he loves it. Although there is only one problem, it can't recored using his PreSonus FP10 FireWire Recording System. I installed Ardour on his Ubuntu desktop and it uses Jack to connect to the FP10. When I get Jack running it will stop right after I start it and it exits with this error.

20:03:35.096 Startup script...
20:03:35.097 artsshell -q terminate
sh: artsshell: not found
20:03:35.502 Startup script terminated with exit status=32512.
20:03:35.503 JACK is starting...
20:03:35.503 /usr/bin/jackd -R -dalsa -dhw:0 -r44100 -p1024 -n2
20:03:35.507 JACK was started with PID=3705.
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
cannot use real-time scheduling (FIFO at priority 10) [for thread -1218992448, from thread -1218992448] (1: Operation not permitted)
cannot create engine
20:03:36.045 JACK was stopped successfully.
20:03:36.045 Post-shutdown script...
20:03:36.046 killall jackd
jackd: no process found
20:03:36.511 Post-shutdown script terminated with exit status=256.
20:03:37.597 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.

I was able to get Jack to run using this command in terminal

```
sudo jackd -R -d freebob
```

When I run that command the FireWire indication light on the FP10 turns changes from red to blue, which indicates that it detects the computer. Then after that I run Ardour and it starts up correctly but when he tries to record, no sound is recorded. I checked to see if the freebob driver is installed and it is installed. Does anyone know how to properly use the PreSonus FP10 with Ardour?

Any advice would be appreciated.

---

### Post by trulan on 2010-01-31
> **Revolutionary101 said:**
> 
cannot use real-time scheduling (FIFO at priority 10) [for thread -1218992448, from thread -1218992448] (1: Operation not permitted)

There's the problem.  For a simple workaround, un-check the realtime option in Jack Control.  For a better and more permanent solution, follow this guide:
[https://help.ubuntu.com/community/FireWire](https://help.ubuntu.com/community/FireWire)
Good luck!  If you have more problems or questions, please post back.

When you ran jack as root (with sudo) then it connected to the firepod because root has permissions for everything.  But then there are other problems as you found out.  So follow the guide and fix it right.

---

