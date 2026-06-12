---
title: "apparmor loading failed ---&gt; mysql server cannot configure"
date: 2009-10-18
forum: Security
---

### Post by morio.kalani on 2009-10-18
hi,

first of all, I'm still using the kernel 2.6.29-1-netbook from eeebuntu

NOW...

I noticed that my apparmor wasn't loaded when i wanted to install mysql.

trying to uninstall and install all these things doesn't seem to work.

A few days ago it was a ubuntu developer asked me to look in /boot/config-2.6.29... and grep for -i security....
and amazed i was to find there was nothing of apparmor only SElinux that was disabled.

A few months ago I was messing around with the runlevels and that time I found a program I could start in the terminal... that showed me all the levels and which modules where included...

I could also put an X to modules that I wanted to include on a runlevel...

THE BIG QUESTION (s)

--> Anyone knows the name of this program??? maybe I can find a way of including apparmor in there...
--> did somebody else had this problem and had a solution for it???

thanks

---

