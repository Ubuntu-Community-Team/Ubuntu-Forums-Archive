---
title: "Jack exits saying no drivers found"
date: 2009-11-08
forum: Ubuntu Studio
---

### Post by bandgeek on 2009-11-08
In the Message window it says:
```
13:42:42.868 Patchbay deactivated.
13:42:42.880 Statistics reset.
13:42:42.975 ALSA connection graph change.
13:42:43.145 ALSA connection change.
13:42:44.806 Startup script...
13:42:44.806 artsshell -q terminate
sh: artsshell: not found
13:42:45.210 Startup script terminated with exit status=32512.
13:42:45.211 JACK is starting...
13:42:45.211 /usr/bin/jackd -R -p1024 -t2000 -dalsa -r48000 -p16 -n2 -D -Chw:0,0 -Phw:0,0
could not open driver directory /usr/lib/jack: No such file or directory
jackd: no drivers found; exiting
13:42:45.242 JACK was started with PID=4500.
13:42:45.266 JACK was stopped with exit status=1.
13:42:45.267 Post-shutdown script...
13:42:45.267 killall jackd
jackd: no process found
13:42:45.683 Post-shutdown script terminated with exit status=256.
13:42:47.355 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
```
I reinstalled jack and all of it's dependencies and still says the same thing.

---

### Post by AutoStatic on 2009-11-09
This is a weird warning:
```
could not open driver directory /usr/lib/jack: No such file or directory

```
Does this directory exist?

---

### Post by bandgeek on 2009-11-14
No it doesn't

---

