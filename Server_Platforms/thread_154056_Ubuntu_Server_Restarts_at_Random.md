---
title: "Ubuntu Server Restarts at Random"
date: 2006-04-02
forum: Server Platforms
---

### Post by happyponcho42 on 2006-04-02
For the past 2 weeks now, my Ubuntu server has undergone some self-reboots, meaning no human intervention, it just reboots on its own.  I am weary to suspect a hardware failure, since the server has only been in production for a couple of weeks, but then again, hardware failures are really not that uncommon.

Before jumping on the wagon and attempting to weed out the hardware, I'd like to try to find the source of these reboots if they have something to do with a kernel panic or something related to software rather then hardware.

I have been working on Linux/Unix servers for quite some time, from CentOS, to RedHat/Fedora to FreeBSD and finally Ubuntu.  However, I've never had to deal with system logs before so I am unsure as to what logs to check to determine the cause of these self-reboots.

Can anyone point out a certain log that I should examine to find the cause of the reboots as well as certain lines of text I should keep an eye out for?


Thank You

---

### Post by Glut on 2006-04-03
/var/log/kern.log contains kernel logs.
Certain lines of text are more difficult.
Kernel logs will have a time on the left hand side often something along the lines of [1234], find the lowest time and check the entries before that. Also, check the last few lines of kern.log.0 after a reboot.

---

