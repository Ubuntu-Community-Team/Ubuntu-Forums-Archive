---
title: "[URGENT] Have my systems been compramised??"
date: 2011-12-29
forum: Security
---

### Post by crashed111 on 2011-12-29
Hi All

I have noticed this recently when running chkrootkit on around 1 desktop and a laptop

Checking `chkutmp'... The tty of the following user process(es) were not found in /var/run/utmp !

The process in question is (Running as root on a tty which does not exist) - /usr/bin/X :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch -background none

Cant find any other mention online about this all systems are running a fully patched install of 11.10 which the latest repo version of chkrootkit.

From what research I have this seems to be related to remote access to X so I am not sure if there is a rootkit present. Unfortunately X is not my speciality. 

Anyone have any ideas?

---

### Post by squaregoldfish on 2011-12-29
Nothing to worry about. That's your X windows server, running to display stuff on your monitor (that's what the :0 means - X names its displays as numbers, and 0 is always the local monitor).

I have exactly the same process on my machine.

Steve.

---

