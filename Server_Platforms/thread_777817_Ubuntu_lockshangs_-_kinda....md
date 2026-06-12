---
title: "Ubuntu locks/hangs - kinda..."
date: 2008-05-01
forum: Server Platforms
---

### Post by CarterSt on 2008-05-01
I'm runing Ubuntu Server Hardy as guest on VMWare Server with 1GB RAM.  We are testing a production website that streams videos via PHP script.  It worked flawlessly on Windows/Apache, and I've got a similar but more busy site on a non-VM server running Ubuntu Server.

Anyway, once or twice a day, on this server, Apache stops all connections.  So I can log in and stop Apache.  But if I start it again, it cannot bind to 0.0.0.0:80 - weird!  

So then if I try to sudo su, I get the prompt for password and when I enter it the server hangs.  Same if I try anything else like stopping MySQL.  My only recourse is to hard-reboot.

I examine the syslogs, but I can't find anything that happens right before the crash/hang... except the Apache access logs show a few lines with timestamps that are earlier than the previous lines, sometimes as much as 10 minutes!  The server time is never more than a couple minutes off, so this isn't a time-server adjustment issue.  Any ideas?  Thanks if you do.

---

