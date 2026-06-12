---
title: "Can't compile postfix on 8.04"
date: 2008-07-25
forum: Server Platforms
---

### Post by Phulerock on 2008-07-25
I use Ubuntu 8.04 server, and want to install Postfix from source. Server is already installed build-essential, db4.

```
root@ubuntuserver:~/source# dpkg -l | grep db4
ii  libdb4.6                              4.6.21-6ubuntu1             Berkeley v4.6 Database Libraries [runtime]
ii  libdb4.6-dev                          4.6.21-6ubuntu1             Berkeley v4.6 Database Libraries [developmen

```
But I can't compile it:
```
root@ubuntuserver:~/source/postfix-2.5.2# make
make -f Makefile.in MAKELEVEL= Makefiles
(echo "# Do not edit -- this file documents how Postfix was built for your machine."; /bin/sh makedefs) >makedefs.tmp
makedefs.test.c:1:23: error: sys/types.h: No such file or directory
makedefs.test.c:2:23: error: sys/epoll.h: No such file or directory
makedefs.test.c:3:19: error: errno.h: No such file or directory
makedefs.test.c:4:19: error: stdio.h: No such file or directory
makedefs.test.c:5:20: error: stdlib.h: No such file or directory
makedefs.test.c: In function ‘main’:
makedefs.test.c:13: warning: incompatible implicit declaration of built-in function ‘exit’
makedefs.test.c:15: warning: incompatible implicit declaration of built-in function ‘exit’
make: *** [Makefiles] Error 1
make: *** [Makefiles] Error 2

```

Anyone help me ? I really don't know this idea (compile from source) will improve performance rather than install binaries from "apt-get". If you know this, pls show me your recomment.
Thanks

---

### Post by songshu on 2008-07-26
to make a long story short.

just use the .deb from the repos


if there is any speed advantage by compiling from source at all, it would be so minimal you would never notice it.

---

### Post by Bachstelze on 2008-07-26
build-essential is not installed.

---

### Post by Phulerock on 2008-07-27
OK, I will check my packages again, I don't remember that I installed build-essential properly. May be I use apt-get insall -d, so it s only download and don't install anything. thanks for suggest.

---

### Post by Phulerock on 2008-07-28
Thanks HymnToLife, after install build-essential properly, compile postfix very easy and smooth, this my mistake, I only download these packages by issue command:

apt-get install -d build-essential

2 days hard work ! :(

---

