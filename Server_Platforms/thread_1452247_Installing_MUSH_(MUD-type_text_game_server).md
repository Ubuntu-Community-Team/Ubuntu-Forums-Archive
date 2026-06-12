---
title: "Installing MUSH (MUD-type text game server)"
date: 2010-04-11
forum: Server Platforms
---

### Post by Th3Professor on 2010-04-11
I've tried installing PennMUSH but it came up with an error when I ran the configure and make install commands. I'm not sure what's going on, am wondering - could someone help?

The only change I made in the config for the actual mush was I added '=' as an option for chat channels in the mush. Everything else is default.

I don't know if it'll need just a fresh delete and complete redo on install. That's fine if it does. I haven't done anything with it since I received the error messages.

Here are the last few lines after typing "make install" that show errors:

chunk.c: In function `chunk_init':
chunk.c:2364: warning: implicit declaration of function `posix_fallocate'
chunk.c: In function `chunk_fork_file':
chunk.c:2508: warning: implicit declaration of function `posix_fadvise'
chunk.c:2508: error: `POSIX_FADV_SEQUENTIAL' undeclared (first use in this function)
chunk.c:2508: error: (Each undeclared identifier is reported only once
chunk.c:2508: error: for each function it appears in.)
chunk.c:2526: error: `POSIX_FADV_RANDOM' undeclared (first use in this function)
chunk.c: In function `chunk_fork_child':
chunk.c:2555: error: `POSIX_FADV_RANDOM' undeclared (first use in this function)
make[1]: *** [chunk.o] Error 1
make[1]: Leaving directory `/home/[omitted]/pennmush-1.8.3p13/src'
make: *** [all] Error 2

---

### Post by fang0654 on 2010-04-11
I just downloaded the source and tried compiling it on 10.04 without any issues.  I did the following:

make update
make
sudo checkinstall

You'll need to apt-get install checkinstall first.

Try removing your change and compiling to at least narrow down the trouble.

---

### Post by Th3Professor on 2010-04-12
Installing the mush server app on a server running centos linux system. I don't appear to be in the sudoers file. Any work arounds?

---

### Post by fang0654 on 2010-04-12
CentOS doesn't use sudo in the way Ubuntu does.

You have to install it as root.

su -
checkinstall

---

### Post by Th3Professor on 2010-04-12
su - 
...doesn't work. :/

---

### Post by fang0654 on 2010-04-12
su - root
?

---

### Post by Th3Professor on 2010-04-13
I don't have root privileges. su - root doesn't work. I have installed apps before, even ones that would "supposedly require" root access. I'm not sure why this one isn't working. :( EDit: Correction: I have installed server apps without requiring root type access (installed "locally" within a given account). That doesn't seem to be working in this case.

---

### Post by Th3Professor on 2010-04-14
<bump>
...is there a way to install the text-game server without root-type of access?

---

### Post by Th3Professor on 2010-04-16
bump
anybody?

---

### Post by Th3Professor on 2010-04-18
I've tried installing PennMUSH but it came up with an error when I ran the configure and make install commands. I'm not sure what's going on, am wondering - could someone help?

The only change I made in the config for the actual mush was I added '=' as an option for chat channels in the mush. Everything else is default.

I don't know if it'll need just a fresh delete and complete redo on install. That's fine if it does. I haven't done anything with it since I received the error messages.

---

### Post by Th3Professor on 2010-04-19
nevermind

---

