---
title: "iscsid process count"
date: 2011-01-05
forum: Server Platforms
---

### Post by mrcriminy on 2011-01-05
I'm running an old ubuntu 8.10 server with a mounted filesystem over iscsi. For some reason iscsid is running over 200 processes.

Here is some stats:
uname -r : 2.6.27-7-server
09:00:19 up 455 days, 12:33,  1 user,  load average: 0.00, 0.00, 0.00
iscsid version 2.0-865
396 processes, 279 /sbin/iscsid processes.

I'm mostly concerned because it's constantly tripping up the nagios notifications attached to this machine, but I want to verify my iscsi setup isn't wonky.

As far as the iscsi device is setup, it's out of my knowledge. I do know the iscsi device has 36G displayed to the linux host on it, 35G of which is filled up. Reading and writing on this device is common, as it's the location for a user-provided content database.

Any help? Thank you.

---

### Post by psusi on 2011-01-05
8.10 reached end of life and stopped being supported nearly a year ago now.  It is buggy and insecure, and you need to upgrade.

---

### Post by mrcriminy on 2011-01-13
Meh. I'm not an any position to upgrade the machine at the moment (can't afford the downtown and I can't get a replacement machine in there in time).

FWIW, those words have come out of my mouth into deaf ears already, so you haven't said anything I don't already know.

---

