---
title: "sending logs from servers to workstation..."
date: 2007-09-05
forum: Server Platforms
---

### Post by Mia_tech on 2007-09-05
I have an ubuntu server and a windows 2k3 server and I'm trying to centrilize the logs to single workstation, instead of going to every server checking for logs, I don't mind if the logs are send by mail, or configure to send to a specific workstation...........if someone could point me in the right direction!

---

### Post by Mr. C. on 2007-09-06
Which logs ?

Where do you want your logs to go?

syslog-based logs can log to a central, networked log server.

```
man syslog
```

MrC

---

### Post by Mia_tech on 2007-09-06
from my ubuntu box I want to copy the auth.lgo.....I was thinking like use the cp command to copy the log to a centrilize location something like

cp /var/log/auth.lgo //x.x.x.x/share/

don't know if this is the best way to do it, and as far as my w2k3 box I was thinking the same process but for the event viewer files.

---

### Post by Mr. C. on 2007-09-06
You can copy the logs if you desire; nothing wrong with that, but it certainly is a more manual process.  Use scp, rdist, rsync, ftp, or whatever you desire.  Copy them after they are no longer in use (i.e. after logrotate has rotated them).

Syslog was designed to be network logging aware.  Why not use it as it was intended.

For WinX, you can use something like Snare:

[http://www.intersectalliance.com/projects/SnareWindows/index.html](http://www.intersectalliance.com/projects/SnareWindows/index.html)

to convert Windows Eventlog messages into syslog format.  Kiwi syslog and its like provide syslog capabilities on Windows.

MrC

---

### Post by Mia_tech on 2007-09-06
> **Mr. C. said:**
> You can copy the logs if you desire; nothing wrong with that, but it certainly is a more manual process.  Use scp, rdist, rsync, ftp, or whatever you desire.  Copy them after they are no longer in use (i.e. after logrotate has rotated them).

Syslog was designed to be network logging aware.  Why not use it as it was intended.

For WinX, you can use something like Snare:

[http://www.intersectalliance.com/projects/SnareWindows/index.html](http://www.intersectalliance.com/projects/SnareWindows/index.html)

to convert Windows Eventlog messages into syslog format.  Kiwi syslog and its like provide syslog capabilities on Windows.

MrC

could you elaborate more on what scp, and rdist are I know wht rsync and ftp can do...

---

### Post by Mr. C. on 2007-09-08
This should explain:

[http://en.wikipedia.org/wiki/Secure_copy](http://en.wikipedia.org/wiki/Secure_copy)
[http://www.benedikt-stockebrand.de/rdist-intro_d.html](http://www.benedikt-stockebrand.de/rdist-intro_d.html)

MrC

---

