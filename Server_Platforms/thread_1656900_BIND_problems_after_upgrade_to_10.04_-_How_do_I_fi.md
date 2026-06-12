---
title: "BIND problems after upgrade to 10.04 - How do I find the problem?"
date: 2010-12-31
forum: Server Platforms
---

### Post by ivaarsen on 2010-12-31
Greetings, Ubuntu Forums!

Just this morning I decided to attempt an upgrade of my server machine.  It was running 8.04 LTS, and the upgrade was directly to 10.04 LTS.  Afterwards, I seem to be having an issue with BIND that I can't quite figure out.

Before raising the white flag and asking you guys directly what could be wrong, I'd first like to troubleshoot it on my own.  My problem, however, is I don't know where to look.  :/  The command...

sudo /etc/init.d/bind9 start

...simply results in a FAIL message.  I'd like to find out more information.

Can anybody give me some pointers on how to turn on debugging or how to log what the problem is?

I appreciate your help and time.

Eric

---

### Post by ivaarsen on 2010-12-31
Well, I found a work-around.  I found another command here on the forums that allowed me to completely smoke bind9...

sudo apt-get remove --purge bind9

I then reinstalled and it seems like I'm to a point here I can rebuild my configuration (good thing I made backups).

All the same, if anybody can chime in with a few troubleshooting tips for future reference, I would appreciate it.

Thanks again!

---

### Post by jgedeon on 2011-01-01
> **ivaarsen said:**
> Greetings, Ubuntu Forums!

Just this morning I decided to attempt an upgrade of my server machine.  It was running 8.04 LTS, and the upgrade was directly to 10.04 LTS.  Afterwards, I seem to be having an issue with BIND that I can't quite figure out.

Before raising the white flag and asking you guys directly what could be wrong, I'd first like to troubleshoot it on my own.  My problem, however, is I don't know where to look.  :/  The command...

sudo /etc/init.d/bind9 start

...simply results in a FAIL message.  I'd like to find out more information.

Can anybody give me some pointers on how to turn on debugging or how to log what the problem is?

I appreciate your help and time.

Eric

Remember rule number one: Check the logs.  When bind failed to start your answer to why if failed was in /var/logs/syslog.

tail -20 /var/log/syslog

---

### Post by woodman231 on 2011-01-03
Not sure if this helps or not, but I notice that when I do a restart for the same command it always fails.  However if I do a stop and then a start it works.  So it is possible that you were getting the error because on some level it believed that it was already started.

Thanks,
Sean W.

---

### Post by ivaarsen on 2011-01-04
> **jgedeon said:**
> Remember rule number one: Check the logs.  When bind failed to start your answer to why if failed was in /var/logs/syslog.

tail -20 /var/log/syslog

Roger that on checking the logs, but I didn't keep my head on and check all of them.  ie, I didn't make it to syslog, I was trying to make sense of /var/log/messages.  

I keep your tip mind for next time.  Thanks for the input, guys.

---

