---
title: "Jack stopped working suddenly!"
date: 2009-05-26
forum: Ubuntu Studio
---

### Post by homerj742 on 2009-05-26
Hey all, I'm on Ubuntu Studio 8.04. 

Jack was working fine all of last week, even recorded a new project w/ardour hydrogen. 

But now jack will not start, here is what's in the error window:

```
20:22:31.240 Patchbay deactivated.
20:22:31.271 Statistics reset.
20:22:31.288 ALSA connection graph change.
20:22:31.481 ALSA connection change.
20:22:45.040 Startup script...
20:22:45.040 artsshell -q terminate
20:22:45.454 Startup script terminated with exit status=256.
20:22:45.454 JACK is starting...
20:22:45.454 /usr/bin/jackd -R -dalsa -r44100 -p128 -n2 -D -Chw:0 -Phw:0 -m
20:22:45.456 JACK was started with PID=6329.
jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
cannot use real-time scheduling (FIFO at priority 10) [for thread -1210153296, from thread -1210153296] (1: Operation not permitted)
cannot create engine
20:22:45.461 JACK was stopped successfully.
20:22:45.462 Post-shutdown script...
20:22:45.462 killall jackd
jackd: no process killed
20:22:45.866 Post-shutdown script terminated with exit status=256.
20:22:47.558 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
```

Any help would be greatly appreciated! Thank you!

---

### Post by luctor on 2009-05-27
check audio settings in /etc/security/limits.conf
```

grep audio /etc/security/limits.conf
@audio - nice -19
@audio - memlock unlimited
@audio - rtprio 99

```

---

### Post by raboofje on 2009-05-27
Also, make sure you're in the 'audio' group.

See also [http://ubuntuforums.org/showthread.php?t=1161492](http://ubuntuforums.org/showthread.php?t=1161492) , [https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)

---

### Post by goodmanbrown on 2009-05-28
Did these suggested fixes help?

I'm also unable to start jack in realtime mode, and my system has long been configured according to these suggestions.  

I just noticed the problem last night, which is the first time I've tried to load jack since upgrading to Jaunty about three weeks ago.

---

