---
title: "Unexpected chkrootkit output - detects its own session?"
date: 2012-10-13
forum: Security
---

### Post by maglinu on 2012-10-13
I have run chkrootkit on this machine and it gives:

Checking `chkutmp'...                                        The tty of the following user process(es) were not found
 in /var/run/utmp !
! RUID          PID TTY    CMD
! user xxxx pts/0  bash
! user xxxx pts/0  sudo chkrootkit
! root xxxx pts/0  /bin/sh /usr/sbin/chkrootkit
! root xxxx pts/0  ./chkutmp
! root xxxx pts/0  ps axk tty,ruser,args -o tty,pid,ruser,args
! root xxxx pts/0  sh -c ps axk "tty,ruser,args" -o "tty,pid,ruser,args"

I'm a numpty in these matters, but it appears to me that chkrookit is just failing to find the record of its own current session processes in utmp.

Is this right, and is it normal? I don't see it on my straight ubuntu/unity machine.

Many thanks

(I don't have any special security concerns on this machine - I'm just playing/learning linux tools)

---

### Post by maglinu on 2012-10-13
Just tried chkrootkit on my xubuntu livecd - with similar results. It appears this actually is a difference between ubuntu and xubuntu behaviour.

---

