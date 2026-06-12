---
title: "Remote Disc Mirroring"
date: 2010-11-05
forum: Server Platforms
---

### Post by The Foz on 2010-11-05
Does anyone know if there is any software that will do full mirroring between a local and a remote file system.

I have a server (9.04) and a laptop (9.10). Each user has shared a shared directory on the server, and on the laptop. Updates to files may be done on either system. I want to keep both copies syncronised.

Currently I use a script based on rsync (scheduled by cron) to keep the local and remote copies in sync. The problem with this approach is that rsync only seems to be able to handle deletion of files if one file system is the master, which is not the case in my set-up. If I move a file to a different directory, rsync will reinstate the old file as well as copying the new one.

I was hoping there was some software that could do proper mirroring between the 2 systems, but6 so far I cannot find anything.

---

### Post by finni on 2010-11-05
Maybe mdraid might be able to do this, I am not sure though.

---

### Post by Cosma on 2010-11-05
i haven't used any of them but maybe it helps you get into the right direction:

[http://oss.linbit.com/csync2/](http://oss.linbit.com/csync2/)
[http://www.cis.upenn.edu/~bcpierce/unison/]("http://www.cis.upenn.edu/%7Ebcpierce/unison/")

---

### Post by The Foz on 2010-11-10
I decided to give DRBD ([http://www.drbd.org/home/what-is-drbd/]("http://www.drbd.org/home/what-is-drbd/")) a try.

First I tested it out for mirroring between 2 test Virtual Machines. Once I was happy with it, I configured it on my real live systems.

It seems very good: fast, and easy to configure and administer.

---

