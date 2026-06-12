---
title: "debmirror problem"
date: 2015-01-30
forum: Server Platforms
---

### Post by Nigel_Pain on 2015-01-30
I've started supporting a mirror server from someone who has moved on to other things. I've not got much Linux experience, although I did spend a lot of time supporting Solaris a few years ago, and have just attended a Linux Sysadmin training course.
The server updates its local distributions daily using debmirror but this is failing with the following message:

```
Arches: amd64,i386
Dists: precise,precise-security,precise-updates,precise-proposed,precise-backports,lucid,lucid-security,lucid-updates,lucid-proposed,lucid-backports
Sections: main,restricted,universe,multiverse
Pdiff mode: use
Will clean up after mirroring.
Attempting to get lock ...
Loading debmirror state cache.
Magic number checking on storable file failed at /usr/lib/perl/5.14/Storable.pm line 379, at /usr/bin/debmirror line 2669
WARNING: releasing 1 pending lock...
```

Has anyone any ideas what is causing this?

---

### Post by howefield on 2015-01-30
Thread moved to the "*Server Platforms*" forum.

---

