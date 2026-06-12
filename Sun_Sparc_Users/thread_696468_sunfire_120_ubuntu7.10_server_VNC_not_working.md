---
title: "sunfire 120 ubuntu7.10 server VNC not working"
date: 2008-02-14
forum: Sun Sparc Users
---

### Post by bdobbel on 2008-02-14
hello there,

I have problems to make vnc work in this setup .
i have tried x11vnc , vnc4server , enz ....
nothing works for me . i think it is there isnt a grafic card in the sun .
when i startx , it says no display fond .

sorry for the bad language .

---

### Post by malibu on 2008-03-13
Hi there.. I too am having the same kinds of problems on a v120.  I just posted a thread about it..

[http://ubuntuforums.org/showthread.php?t=723220](http://ubuntuforums.org/showthread.php?t=723220)


One thing I noticed though.. You shoudlnt' have to execute startx on your server.  You probably want to start 'vncserver'.  I've been having troubles with that... Though they have gotten better since I downloaded the brand new source for tightvnc and compiled it.  The repository version of tightvnc is quite old and there has been a fix for sparc platforms since then.  Right now I'm having trouble getting the x windows fonts packages.  I'm hoping once I do that it will work.

Anyway, just thought I would tell you about my thread.

---

### Post by zgambitx on 2008-03-14
Malibu, Can I see a copy of your xorg.conf?

---

