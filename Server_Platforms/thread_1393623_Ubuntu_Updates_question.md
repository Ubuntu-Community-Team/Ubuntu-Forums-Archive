---
title: "Ubuntu Updates question"
date: 2010-01-29
forum: Server Platforms
---

### Post by unix4linux on 2010-01-29
Every time I login to my system via ssh(ubuntu 9.04 server), I get an update message saying I have:

30 packages can be updated.
72 updates are security updates.

When I run "apt-get upgrade" it doesn't find anything to update/upgrade.  So, why does it keep saying I have 30 packages can be updated and 72 updates are security updates?

Thanks,
G

---

### Post by KnottyMars on 2010-01-29
Im kinda new to Ubuntu, but I thought that you had to use

```

sudo aptitude update

sudo aptitude dist-upgrade

```

That has always worked for me, hope that helps

---

### Post by Iowan on 2010-01-29
If you prefer **apt-get**, try **sudo apt-get update** (to get a fresh list of what's available) before running **apt-get upgrade**.

---

### Post by unix4linux on 2010-01-31
Ok, I guess I didn't make myself clear...that's my fault.

I always run apt-get update before upgrade.  After I run upgrade, I continue to see the system telling me that there are packages to update and or upgrade.

---

### Post by martien on 2010-01-31
> **unix4linux said:**
> Ok, I guess I didn't make myself clear...that's my fault.

I always run apt-get update before upgrade.  After I run upgrade, I continue to see the system telling me that there are packages to update and or upgrade.

The login msg is just showing the content of /etc/motd, so I guess /etc/motd is generated on startup or is reloading on some period of time, so that may be the reason you still have updates to do.

---

### Post by unix4linux on 2010-02-01
Martien,

I used aptitude instead and it cleared that updates from the login.  I guess apt-get probably doesn't refresh the motd where aptitude does?...oh well, aptitude did it for me.

Thanks a bunch all :-)

---

