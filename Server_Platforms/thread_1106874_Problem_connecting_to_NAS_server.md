---
title: "Problem connecting to NAS server"
date: 2009-03-26
forum: Server Platforms
---

### Post by caverDK on 2009-03-26
I have installed Ubuntu 8.10 server on a pc, and using it as a NAS server.

I'm using webmin and and putty for administration of the server. Besides that the server is running samba, torrentflux and mediatomb.

It's been running for several weeks without problems. But now it's beginning to act strangely.

When connecting remotely to webmin via Firefox I'll get a "Failed to connect" at first try. If I try again after one minute or so I get in. I can then start working in webmin, but after some time (sometimes only a couple of minutes) I get a "Connection interrupted". After some time I can get in again.... Same connection problem for samba and putty.

Any ideas to what the problem can be?

/Casper

---

### Post by BkkBonanza on 2009-03-26
Maybe flakey cable or mis-configured ip address conflict? Have you changed anything at all on the network recently, even if it seems unrelated?

---

### Post by caverDK on 2009-03-26
> **BkkBonaza said:**
> Maybe flakey cable or mis-configured ip address conflict? Have you changed anything at all on the network recently, even if it seems unrelated?

Come to thing about it we actually had a power outrage not long ago. So I just soft rebooted the router. And it seems to help, remote access connection has now been open for more than 20 minutes. That was not possible before.

I was so sure it was a software problem. Thanks for leading me in the right direction :)

---

### Post by BkkBonanza on 2009-03-26
Cool. :)

---

