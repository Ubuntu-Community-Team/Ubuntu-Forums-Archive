---
title: "Networking shares help!!! please..."
date: 2010-03-21
forum: Server Platforms
---

### Post by jflcooper on 2010-03-21
Hi all,

Ok this is what i have setup

**Server 1 - Ubuntu 8.10**
172.16.0.50
/var/rails/server2/site_media

**Server 2 - Ubuntu 8.10**
172.16.0.51
/var/rails/site_media

As you can see both servers are on the same network. I want to server 2's 'site_media' directory to link to the server 1's 'server2/site_media' directory.

Can anyone please help me with the BEST and EASIEST way to do this??

If you can please link to some material or Tutorials that would help me with this that would be much appreciated.

Cheers

---

### Post by Sef on 2010-03-21
Moved to Server Platforms.

---

### Post by TitanusEramius on 2010-03-21
You have to use NFS for this, it's Network File Sharing, and is Linux' way of using a network. Samba is what you need if you got Windows-machines on the network that needs access, but in my experience NFS works far better, so even if got both on your network, I would recommend setting both up. Some reading:

[http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)

Even though it might look like a lot material to cover, it's actually not that bad once you get started :)

---

### Post by jflcooper on 2010-03-21
TitanusEramius,

I COULD KISS YOU RIGHT NOW MATE!!!!!!

That was absolutely PERFECT! I wish there were more people like you on this forum to help new people like me... much much thanks...

Worked Perfectly

Cheers
Coops

> **TitanusEramius said:**
> You have to use NFS for this, it's Network File Sharing, and is Linux' way of using a network. Samba is what you need if you got Windows-machines on the network that needs access, but in my experience NFS works far better, so even if got both on your network, I would recommend setting both up. Some reading:

[http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)

Even though it might look like a lot material to cover, it's actually not that bad once you get started :)

---

### Post by TitanusEramius on 2010-03-21
You are so very welcome, nice to hear it helps :D

Btw, if this solves your issue, will you please mark the thread solved?

---

