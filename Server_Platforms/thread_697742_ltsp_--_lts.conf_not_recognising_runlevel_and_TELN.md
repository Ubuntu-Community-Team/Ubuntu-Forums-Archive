---
title: "ltsp -- lts.conf not recognising runlevel and TELNET_HOST"
date: 2008-02-15
forum: Server Platforms
---

### Post by mxc on 2008-02-15
Hi there,

We would like our thin clients to boot into a telnet session on another machine. According to our understanding editing lts.conf should allow this with the options such as:

TELNET_HOST=ip addy of server

This appears not to work. Also trying to get the thin client to boot to the command line is also a challenge. We have tried adding

RUNLEVEL=3 and
SCREEN_1=shell

After editing /opt/ltsp/i386/etc/lts.conf we run ltsp-update-image, but none of these seem to work.

Any help appreciated.

---

