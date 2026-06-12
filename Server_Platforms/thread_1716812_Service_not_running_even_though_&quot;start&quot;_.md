---
title: "Service not running even though &quot;start&quot; command outputs [OK]"
date: 2011-03-29
forum: Server Platforms
---

### Post by fuzzywuggle on 2011-03-29
Hello Ubuntu Guru's,

I am running an application called SGW and when I run the ps command the output shows a question mark next to the PID.

After installing the application it said the service was running with an [OK] at the end of the command line.

If I issue a "start" command (sudo or not) it also returns [OK] as well. However, if I issue a "status" command I receive the following:

[COLOR=Red]*[/COLOR] sgw is not running

Any pointers as to how to verify what is killing the sgw service?

Below is the ouput of the ps command I run:

UID  PID    PPID  C  STIME    TTY   TIME            CMD
root  4755     1    0   21:56     ?      00:00:00     /usr/bin/sgw -f /etc/sgw.ini

Any feedback would be greatly appreciated! :)

---

