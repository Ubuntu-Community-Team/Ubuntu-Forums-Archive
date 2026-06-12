---
title: "logs smell old sometimes"
date: 2007-03-27
forum: Server Platforms
---

### Post by erasmo.da.rotterdam on 2007-03-27
Hi!!
I have to set up a LAMP server.
the first question is: the logrotate activity has to be activated or is it effective after the server installation?
the second is more trivial: how long do I have to preserve logs?
I am managing a server which has more than three years and I have never needed to look into **compressed logrotated** logs...
:confused:

---

### Post by conjur3r on 2007-03-27
1. Yeah.  Logrotate should work after server installation.
2. What do your archiving policies say?  If you don't have any, talk with the business owners and talk to them to see what a reasonable period is.

---

### Post by erasmo.da.rotterdam on 2007-03-27
Fortunately(:confused:) I am the one who can decide how long mantain log files
If there isn't any particular rule to follow I'll probably keep them as long as there is no need for space on the partition.
:popcorn:

---

