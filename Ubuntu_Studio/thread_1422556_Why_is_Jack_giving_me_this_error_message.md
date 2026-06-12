---
title: "Why is Jack giving me this error message?"
date: 2010-03-05
forum: Ubuntu Studio
---

### Post by Macfunky on 2010-03-05
Every time i open up Jack i get the following message -

19:11:09.970 Patchbay deactivated.
19:11:09.973 Statistics reset.
19:11:10.407 Startup script...
19:11:10.410 artsshell -q terminate
19:11:10.540 ALSA connection graph change.
sh: artsshell: not found
19:11:10.961 Startup script terminated with exit status=32512.
19:11:10.962 JACK is starting...
19:11:10.964 /usr/bin/jackd -R -dalsa -dhw:0 -r44100 -p1024 -n2
19:11:10.999 JACK was started with PID=11348.
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
cannot use real-time scheduling (FIFO at priority 10) [for thread -1211783488, from thread -1211783488] (1: Operation not permitted)
cannot create engine
19:11:11.053 JACK was stopped successfully.
19:11:11.055 Post-shutdown script...
19:11:11.056 killall jackd
19:11:11.201 ALSA connection change.
jackd: no process killed
19:11:11.498 Post-shutdown script terminated with exit status=256.
19:11:13.219 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.

Why isn't it starting up correctly? Any help at all would be great thank you

---

### Post by AutoStatic on 2010-03-05
Untick the 'Realtime' option in QjackCtl or modify your */etc/security/limits.conf* file: [https://help.ubuntu.com/community/Ub...Time%20Support](https://help.ubuntu.com/community/Ub...Time%20Support)

---

### Post by raboofje on 2010-03-07
Also, [http://trac.jackaudio.org/wiki/Troubleshooting](http://trac.jackaudio.org/wiki/Troubleshooting)

---

