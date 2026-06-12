---
title: "Permission Denied problem when trying to create new screen sessions"
date: 2010-08-19
forum: Server Platforms
---

### Post by richardgaywood on 2010-08-19
Hi all. Run across a problem on a fresh install of 10.04 on a server I haven't seen before.

Out of the box, screen wouldn't work as a normal user, only as root. Checking permissions on /dev/tty* I figured that adding my user account to the tty group would help, and it did. I can now get a screen session running. But when I hit ctrl-A C to spawn a new screen, I get the message:

```
Cannot open /dev/ttyp5: Permission denied
```

Checking permissions:

```
rich@server:~$ ls -alt /dev/ttyp*
crw--w---- 1 rich tty 3,  4 2010-08-19 22:13 /dev/ttyp4
crw--w---- 1 rich tty 3,  0 2010-08-19 22:13 /dev/ttyp0
crw-rw---- 1 rich tty 3,  1 2010-08-19 22:12 /dev/ttyp1
crw--w---- 1 root tty 3,  5 2010-08-19 17:45 /dev/ttyp5
crw--w---- 1 root tty 3,  6 2010-08-19 17:45 /dev/ttyp6
crw--w---- 1 root tty 3,  7 2010-08-19 17:45 /dev/ttyp7
crw--w---- 1 root tty 3,  8 2010-08-19 17:45 /dev/ttyp8
crw-rw---- 1 root tty 3,  9 2010-08-19 17:45 /dev/ttyp9
crw-rw---- 1 root tty 3, 10 2010-08-19 17:45 /dev/ttypa
crw-rw---- 1 root tty 3, 11 2010-08-19 17:45 /dev/ttypb
crw-rw---- 1 root tty 3, 12 2010-08-19 17:45 /dev/ttypc
crw-rw---- 1 root tty 3, 13 2010-08-19 17:45 /dev/ttypd
crw-rw---- 1 root tty 3, 14 2010-08-19 17:45 /dev/ttype
crw-rw---- 1 root tty 3, 15 2010-08-19 17:45 /dev/ttypf
crw--w---- 1 rich tty 3,  3 2010-08-19 16:07 /dev/ttyp3
crw-rw---- 1 root tty 3,  2 2010-08-19 16:05 /dev/ttyp2

```

I'm not sure why some of those tty ports have ended up owned by my user account, rather than root. If I fiddle with the permissions, e.g. I tried chmod g+rw, then I see the same error message and the permission change resets itself a few seconds later.

I've never seen screen not Just Work (TM) before. What am I doing wrong?

---

