---
title: "Rosegarden can't connect to jack;"
date: 2009-12-03
forum: Ubuntu Studio
---

### Post by the_waka on 2009-12-03
rosegarden can't connect to jack. when i check for the error, i get:

 p, li { white-space: pre-wrap; }  [COLOR=#999999]05:59:59.263 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]05:59:59.380 Statistics reset.[/COLOR]
 [COLOR=#999999]05:59:59.439 Startup script...[/COLOR]
 [COLOR=#990099]05:59:59.440 artsshell -q terminate[/COLOR]
 [COLOR=#66cc99]05:59:59.442 ALSA connection graph change.[/COLOR]
 sh: artsshell: not found
 [COLOR=#999999]06:00:00.313 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]06:00:00.313 JACK is starting...[/COLOR]
 [COLOR=#990099]06:00:00.314 /usr/bin/jackd -R -dalsa -dhw:0 -r44100 -p1024 -n3[/COLOR]
 [COLOR=#999999]06:00:00.318 JACK was started with PID=7574.[/COLOR]
 no message buffer overruns
 jackd 0.116.1
 Copyright 2001-2005 Paul Davis and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK compiled with System V SHM support.
 cannot use real-time scheduling (FIFO at priority 10) [for thread -1215703360, from thread -1215703360] (1: Operation not permitted)
 cannot create engine
 [COLOR=#999999]06:00:00.379 JACK was stopped successfully.[/COLOR]
 [COLOR=#999999]06:00:00.379 Post-shutdown script...[/COLOR]
 [COLOR=#990099]06:00:00.380 killall jackd[/COLOR]
 [COLOR=#cccc99]06:00:00.520 ALSA connection change.[/COLOR]
 jackd: no process found
 [COLOR=#999999]06:00:00.787 Post-shutdown script terminated with exit status=256.[/COLOR]


any ways to get a full fix, rather than a workaround?
i'm going to be using rosegarden a lot in the next year for our game in the Indie Game Challenge... help help help....

---

### Post by VertexPusher on 2009-12-03
Turn off realtime scheduling in Jack's configuration or prepare your system for realtime scheduling by installing the RT kernel.

---

### Post by the_waka on 2009-12-03
now when i select rosegarden from the menu, nothing happens.
i have to goto a terminal, sudo rosegarden, but i don't get any audio output.....
btw, i have to use sudo. rosegarden can't make its modifications otherwise apparently..

---

### Post by VertexPusher on 2009-12-03
> **the_waka said:**
> now when i select rosegarden from the menu, nothing happens.
i have to goto a terminal, sudo rosegarden, but i don't get any audio output.....
btw, i have to use sudo. rosegarden can't make its modifications otherwise apparently..
This is not surprising.

If you run an application with sudo, all the files written by that application will be owned by root. Once they are owned by root, they cannot be accessed by any other user. That is just one of the reasons why you should **_never_** use sudo to run normal applications.

Now you need to log in as root, find Rosegarden's configuration files and delete them (or at least change their ownership).

---

### Post by the_waka on 2009-12-03
thank you  VP, that works beautifully.  :D

---

### Post by Vojta01 on 2010-02-13
Can you please advise where can I find these configuration files which needs to be deleted. Thanks.

---

