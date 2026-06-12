---
title: "Startup problems with mysql after upgrade to Karmic"
date: 2010-11-13
forum: Server Platforms
---

### Post by theDentist on 2010-11-13
I recently upgraded to Karmic, (I know I'm a bit behind). After the upgrade I couldn't get mysql to connect, running the ps aux | grep mysql command I noticed that mysql had started twice.  When I killed one of the processes, I was then able to connect successfully with only one instance running.  Somewhere a script is being run twice on startup.  Can anyone shed some light on this and tell me which script to edit. I've already searched the forums and found nothing on this.

Thanks in advance
Peter

---

### Post by theDentist on 2010-11-13
One more thing that seems strange, when I restart the mysql server with /etc/init.d/mysql restart, it indicates the stop failed but the start succeeded. I can then still connect OK.

---

