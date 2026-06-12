---
title: "exim4 won't forward email"
date: 2009-05-15
forum: Server Platforms
---

### Post by rstackhouse on 2009-05-15
I have recently set up and configured exim4.  I tried sending a test message to see if it would forward to my gmail, but it didn't work.

Checking the exim log this is what I found:

> 2009-05-15 11:01:21 1M4vAH-0003qN-Uu == [Email Protected] R=userforward defer (-1): bad owner for /home/user/.forward

Anyone got any ideas what I might be doing wrong?

---

### Post by rstackhouse on 2009-05-15
Nevermind, total noob mistake.

I created an alias to run vim as sudo, and without thinking used that to create the .forward file in my home directory.

---

