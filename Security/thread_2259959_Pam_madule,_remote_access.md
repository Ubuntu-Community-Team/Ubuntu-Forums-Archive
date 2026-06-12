---
title: "Pam madule, remote access?"
date: 2015-01-08
forum: Security
---

### Post by welefort on 2015-01-08
I'm part of a group of about 15 servers running a distributed system.  We use pam authentication for our users.  I've been told that running a binary pam module will allow someone remote access to my system.    Unfortunately I don't know enough to respond.   Can anyone explain this?  Is is possible for one of the other people on the network to get access to my server?


Running. Ubuntu 14.04 server.

---

### Post by bashiergui on 2015-01-08
Your question is too vague to get a yes/no answer. 

Research pam authentication and whatever distributed system you're running. There will be hardening you can do to secure your operating system, distributed system app, and the pam auth. Things like patching routinely, backups, not allowing remote root logins. Without knowing your setup it's hard to get any more specific than that.

---

