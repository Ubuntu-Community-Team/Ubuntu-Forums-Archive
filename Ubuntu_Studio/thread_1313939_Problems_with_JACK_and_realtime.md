---
title: "Problems with JACK and realtime"
date: 2009-11-04
forum: Ubuntu Studio
---

### Post by eeter on 2009-11-04
I cannot use JACK with realtime option turned on...

12:24:48.568 Patchbay deactivated.
12:24:48.641 Statistics reset.
12:24:48.708 ALSA connection graph change.
12:24:48.904 ALSA connection change.
12:24:50.349 Startup script...
12:24:50.351 artsshell -q terminate
sh: artsshell: not found
12:24:50.755 Startup script terminated with exit status=32512.
12:24:50.755 JACK is starting...
12:24:50.756 /usr/bin/jackd -R -m -dalsa -dhw:0 -r44100 -p1024 -n2
12:24:50.771 JACK was started with PID=3942.
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
cannot use real-time scheduling (FIFO at priority 10) [for thread -780323088, from thread -780323088] (1: Operation not permitted)
cannot create engine
12:24:50.790 JACK was stopped successfully.
12:24:50.790 Post-shutdown script...
12:24:50.791 killall jackd
jackd: no process found
12:24:51.243 Post-shutdown script terminated with exit status=256.
12:24:52.923 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.

---

### Post by AutoStatic on 2009-11-04
Hello eeter,
```
cannot use real-time scheduling (FIFO at priority 10) [for thread -780323088, from thread -780323088] (1: Operation not permitted)
cannot create engine
```
This is because you are apparently not a member of the 'audio' group on your system and you probably did not modify your */etc/security/limits.conf*. Which version of Ubuntu are you using?

---

### Post by eeter on 2009-11-04
> **AutoStatic said:**
> Hello eeter,
```
cannot use real-time scheduling (FIFO at priority 10) [for thread -780323088, from thread -780323088] (1: Operation not permitted)
cannot create engine
```
This is because you are apparently not a member of the 'audio' group on your system and you probably did not modify your . Which version of Ubuntu are you using?

But I AM a member of 'audio' group and I HAVE configured */etc/security/limits.conf* file. I'm using Karmic. 
Jack was working for a while some time ago, but now when I need it again it's not...

---

### Post by trulan on 2009-11-04
What is the output of
```
groups
```
If you've been using Karmic for a while (ie, from the Alpha or Beta stages), it may have 'forgotten' your settings with an upgrade.

---

### Post by eeter on 2009-11-04
I checked my group settings and /etc/security/limits.conf file right after I discovered that JACK is not working. From that side everything should be set.

---

### Post by AutoStatic on 2009-11-04
Did you log out and log in again after adding yourself to the 'audio' group and modifying limits.conf?

---

### Post by eeter on 2009-11-04
> **AutoStatic said:**
> Did you log out and log in again after adding yourself to the 'audio' group and modifying limits.conf?

Yes, I did.

---

### Post by AutoStatic on 2009-11-04
Could you post the relevant content of your */etc/security/limits.conf* file? I just installed Karmic myself and I got the same error as you with JACK after adding my account to the 'audio' group and modifying limits.conf. Logging out and logging back in resolved that issue, that's why I asked.

---

### Post by eeter on 2009-11-04
As it seemed that this discussion doesn't lead me to any solution and I`m really in a hurry because of a deadline, so I decided to do a clean installation. I decided to try out UbuntuStudio Karmic because everybody is claiming it to be quite good. Which means I don't have this problem anymore...

(but will introduce several other problems and ill open a new topic about that right now)

---

### Post by trulan on 2009-11-05
That makes it sound like the line
```
@audio          -       rtprio          99
```
would have been missing in limits.conf.  I have heard from several people that this line isn't always added properly when using Ubuntu Studio Controls in regular Ubuntu.  That may not have been your problem but it may be useful information to someone.

---

