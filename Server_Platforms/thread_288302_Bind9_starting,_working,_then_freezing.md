---
title: "Bind9 starting, working, then freezing?"
date: 2006-10-29
forum: Server Platforms
---

### Post by SecurityMonkey on 2006-10-29
This is really strange.  I upgraded my dapper box to Edgy, and now when I start bind9 here's what happens:

1) Bind starts up okay (checked logs - loads all zones, 'server running').
2) I can do nslookups locally and remotely - no problemo.
3) After X minutes (10 or 20) bind refuses to answer any queries.  
4) rndc hangs on any command.

Anybody?

---

### Post by SecurityMonkey on 2006-10-29
[[Followup]]

It would appear that this may have something to do with multithreading in the new edgy-eft kernel.  I added '-n 1' to /etc/default/bind and restarted bind.  

It hasn't frozen up yet.  

*fingers crossed*

I was going to test this by booting into my dapper kernel since the edgy installer was nice enough to leave it there for me to boot into as "LinuxOLD".  However, it locks up right after it grabs init.

---

