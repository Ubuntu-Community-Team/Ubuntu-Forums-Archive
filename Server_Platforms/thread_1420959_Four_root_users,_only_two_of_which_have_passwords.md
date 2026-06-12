---
title: "Four root users, only two of which have passwords"
date: 2010-03-03
forum: Server Platforms
---

### Post by Vunutus on 2010-03-03
I'm just wondering if this is a security issue or not. I have four MySQL root users, each for different hosts. Three machine specific: localhost, cobalt (my hostname), and 127.0.0.1. The other one is one I added for remote access from a local machine. Of the four, only root@localhost and the remote root have a password hash assigned.

Is this a security risk? If I run "mysqladmin -u root -p password <x>", it only sets root@localhost.

---

### Post by Iowan on 2010-03-03
You should probably brace for the incoming "Why do you have [root]("http://ubuntuforums.org/showthread.php?&t=283131") at all"? ;)

---

### Post by Vunutus on 2010-03-04
> **Iowan said:**
> You should probably brace for the incoming "Why do you have [root]("http://ubuntuforums.org/showthread.php?&t=283131") at all"? ;)

I just realised that I forgot to specify it's MySQL root users I'm talking about :oops:

---

