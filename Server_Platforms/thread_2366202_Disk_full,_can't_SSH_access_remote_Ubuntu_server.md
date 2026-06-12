---
title: "Disk full, can't SSH access remote Ubuntu server"
date: 2017-07-14
forum: Server Platforms
---

### Post by thefullestusername on 2017-07-14
I have a cheap remote VPS running ubuntu 14.04-x86_64-minimal

Unfortunately I accidentally let the disk fill up 100%, and now I can no longer access it through SSH. 

Pinging the IP fails but server is reported to be running fine.

Thanks for any help.

---

### Post by deadflowr on 2017-07-15
Moved to *Server Platforms*

---

### Post by darkod on 2017-07-15
Do you have console access through the provider control panel? That could allow you to log in and clean up some files.

Just be careful what you clean up, for example if you start deleting kernels manually be careful how you do it.

---

### Post by TheFu on 2017-07-15
+1 on the console access.

Don't let /var fill up.  Ever.  Often, /tmp/ is really /var/tmp/.  It has changed over the years, so I can't say exactly which Linux versions that happens on.

Anything that was installed by APT needs to be cleaned up by APT too.  APT means any package manager front-end. That goes for programs and stuff /etc/.  Things in your HOME don't count. Delete those directly.

---

### Post by thefullestusername on 2017-07-15
only option i see is "noVNC console" but it does not seem to work. It just says Loading at the top and never changes. I believe I tried it before but it didn't work.

Should I open a ticket and ask if they can enter console?



rm -rf /var/tmp/


rm -rf /tmp/

should be safe yeah?



Thanks.

---

### Post by TheFu on 2017-07-15
Sounds like they don't provide console access.
Removing files blindly is never a good idea.  We never know what might be there.

---

### Post by thefullestusername on 2017-07-20
> **TheFu said:**
> Sounds like they don't provide console access.
Removing files blindly is never a good idea.  We never know what might be there.

yeah turns out they don't so i had to reinstall lol. lesson learned.


in the future, what can I do to prevent this from happening? is there some kind of idiot-proofing I can install that will make sure I always have a few MB of free space?

---

### Post by TheFu on 2017-07-20
Sure - it is called system monitoring.  Running a server requires hands on administration.  There isn't any install and forget server ... except an AS400.  Unix servers require daily monitoring by a human.  And a few MB simply isn't sufficient.  You need 500MB-1G free for a happy server.

NEVER let /var fill up.

And backups are this neat thing too.  If anything bad happens, 15-30 minutes later you should be back to the point from the last backup.

---

