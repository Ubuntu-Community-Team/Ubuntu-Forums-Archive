---
title: "389 Directory Server"
date: 2009-10-26
forum: Server Platforms
---

### Post by druhboruch on 2009-10-26
I just learned that former Fedora Directory Server (now 389 Directory Server) has been packaged for Karmic.

There is ppa available:
[https://launchpad.net/~ubuntu-389-directory-server/+archive/ppa](https://launchpad.net/~ubuntu-389-directory-server/+archive/ppa)

I would very much like to try it.

I am very interested in your opinions:

Is it good?, is it bad? Is it worth the trouble?

Any feedback appreciated.

---

### Post by tenmoi on 2009-10-28
currently it is useless because you cannt install it without a lot of headaches. I have tried to overcome the first hurdle of installation but found that it would take me lots of time to get round to starting the dirsrv-admin-server so I gave up and WAIT.

---

### Post by druhboruch on 2009-10-28
> **tenmoi said:**
> currently it is useless because you cannt install it without a lot of headaches. I have tried to overcome the first hurdle of installation but found that it would take me lots of time to get round to starting the dirsrv-admin-server so I gave up and WAIT.

Could you be a little more specific?
I know that there was some problem due to this bug:
[https://bugs.launchpad.net/ubuntu/+source/ca-certificates/+bug/392104](https://bugs.launchpad.net/ubuntu/+source/ca-certificates/+bug/392104)

I think it is resolved by now.

There is also a recent tread in Karmic forum about problems with the installation of slapd package...

---

### Post by tenmoi on 2009-10-31
No, it is not that bug. And I suggest you install the software and feel a little pain installing it on karmic.

Anyway, I have installed it on fedora 11 and to my surprise there's no part in the official Redhat document on how you can join a client to the server. Perhaps the server was and is meant for tinkling around and not for production (kidding!). 

afterall. $AD rules, but DR is COOL (figuratively and plainly)

---

