---
title: "Ubuntu 8.0.4 Server Apache Overload/Crash On Restart"
date: 2010-06-06
forum: Server Platforms
---

### Post by merrydown on 2010-06-06
Hi,

I wonder if you can help.  I am a bit of a server noob having built a server to hold a php website for a client hosting at home, I have some experience, but VERY limited and don't speak fluent server.

**My problem is that overnight each day apache on my clients server stops responding.  I can still access via putty / webmin.**

The best I can see it, it seems that apache 2 opens too many child processes and chokes the system.  
[B]
My reasoning for this is:[/B]
-Though I have max child set to 20 with a keep alive of 30 there are dozens of child processes 'apache2 -k start' running, some of which were started 9.5 hours ago.

-I can stop apache, though that doesn't kill these child processes.  I can terminate the parent process which does kill the child processes, however restarting apache after killing the child processes results in a system crash.  Rebooting the server remotely after apache has stopped responding also results in a server crash. That is NO response on any port.

I would be happy to display any pertinent server config/logs etc if anyone can help me troubleshoot this?  I would be soooooooooo grateful as it has been causing us trouble for weeks now!

Jim

---

### Post by colk on 2010-06-06
ls -lvh in /var/log/apache2
Ive seen a big log file do that before

---

### Post by merrydown on 2010-06-07
Hi, I'm not familiar with that parameter, command or label.  There is nothing like that in my error/access log in that folder.  I'm thinking that isn't what you mean probably?

---

