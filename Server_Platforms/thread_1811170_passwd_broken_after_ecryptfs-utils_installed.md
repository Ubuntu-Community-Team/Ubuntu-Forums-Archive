---
title: "passwd broken after ecryptfs-utils installed"
date: 2011-07-24
forum: Server Platforms
---

### Post by taraquedo on 2011-07-24
Hi there,

I'm getting a strange problem with passwd after I have installed ecryptfs-utils (with dependencies) on my Ubuntu 10.04.3 LTS Server. Every time I want to change a user's password as root I get a "passwd: Permission denied" message. This happens as root and it also happens as normal user with sudo. After removing the ecryptfs-utils everything works fine.

The packages are ecryptfs-utils, keyutils, lib(ecryptfs0, nspr4-0d, 
nss3-1d). I've done a "root@myserver$ strace passwd paul 2>err.txt" where paul is an ordinary user. err.txt is attached to this message. Does someone know what is going on? I can't use ecryptfs because of this problem and I don't understand the trace completely.

Greetings from germany!

---

