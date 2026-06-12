---
title: "RAID drives fails shutdown"
date: 2007-07-26
forum: Server Platforms
---

### Post by GTHvidsten on 2007-07-26
When I shut down my newly installed 7.04 server, I get this message:

Stopping MD array md1: [Failed]

However, I also get these messages:

Stopping MD array md0: [OK]
Stopping MD array md2: [OK]

Why can't some of the MD arrays shut down properly?

---

### Post by brent113 on 2007-07-26
Usually that error is caused by the device being mounted or used in some way.  I might make sure the device is not mounted and nothing is using it, then try again.

I assume you're using mdadm?

---

### Post by GTHvidsten on 2007-07-26
I used the Software RAID setup that came during the installation of Ubuntu Server. I think that uses mdadm, but I have no experience in using it myself.
It's okay that the drives may be mounted, but this is during the shutdown sequence. Shouldn't they be unmounted by then?
The shutdown sequence does continue nonetheless. It's just annoying having "Failed" messages on the screen.

---

### Post by brent113 on 2007-07-26
Yea I know it's SUPPOSED to unmount them, but that doesn't necessarily mean they are unmounted during shutdown.  I have had the opposite problem where during startup it says it's failed, by but the time the computer is turned on, it works fine (I have only 1, md0).

My guess is that something is using it at the time it polls for status, but if you're not having any problems with data loss, I'd ignore it.

---

### Post by bandara772001 on 2007-07-28
u try with this urls,it will help to u

[http://users.piuha.net/martti/comp/ubuntu/raid.html](http://users.piuha.net/martti/comp/ubuntu/raid.html)

[https://help.ubuntu.com/community/FileServerOnLVMOnRAID1?highlight=%28raid%29](https://help.ubuntu.com/community/FileServerOnLVMOnRAID1?highlight=%28raid%29)

thanks
ananda-srilanka

---

