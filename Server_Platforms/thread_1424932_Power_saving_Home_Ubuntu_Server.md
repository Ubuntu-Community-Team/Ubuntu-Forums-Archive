---
title: "Power saving Home Ubuntu Server"
date: 2010-03-08
forum: Server Platforms
---

### Post by Unrequited on 2010-03-08
I've been tinkering with creating a home file server more for fun than anything else. However I'd rather that it wasn't running 24/7 as this is unnecessary. Is there anyway to determine whether the server is being used or accessed? Specifically can I test if samba is being used.
Waking the machine will be done using wake on lan.
Thanks in advance

---

### Post by jonabyte on 2010-03-10
Log files will tell you.

---

### Post by tgalati4 on 2010-03-10
It's tough to use smbd usage as a shutdown criteria.  Perhaps just shut it down at a certain time each night.

There are some tools that you can use:

man smbcontrol

tgalati4@tpad-Gloria7 ~ $ sudo smbcontrol smbd ping
PONG from pid 2467

Take the Process ID (pid) from above and feed it to:

tgalati4@tpad-Gloria7 ~ $ ps u -p 2467
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root      2467  0.0  0.0  13064  1528 ?        Ss   Feb24   0:00 /usr/sbin/smbd -D

Since I don't have any Windows machines, my smbd is pretty quiet.

You could use gawk (man gawk) to grab the CPU% (in the third field above) and do a test.  If greater than 0.0% than smbd is doing something, put off sleep for 10 minutes, etc.

---

