---
title: "Script output copied to a central server??"
date: 2013-04-18
forum: Server Platforms
---

### Post by rbishop on 2013-04-18
Here is my setup:

I have roughly 50 servers that I have written a backup script for.  Each of these servers will rsync information to a spot on the server then upload that backup to a central server.  Within this script each of the servers adds information to a log file on that particular server.  What I would like to do is have a central log file on the backup target that is updated by each server with the information from the individual servers.

Is there a way to do this?  I have looked at setting up a Syslog server but I am not sure this will do what I want since the log file is just one I have have created, not like /var/log/messages etc.

Any help or guidance would be greatly appreciated.

Thanks in advance.

---

### Post by papibe on 2013-04-18
Hi  rbishop.

Here are my thoughts:

Syslog server would help you with that. It is highly configurable, and It has a facility to deal with user generated logs. The only possible con could be that at first glance may look like a tank killing a fly.

Another approach could be just to run another rsync after the main one exclusively for the logs.

BTW, I would recommend taking a look at an enterprise backup solution like [BackupPC]("http://backuppc.sourceforge.net/") (in the repositories).

Regards.

---

