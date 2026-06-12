---
title: "Backuppc: connection refused"
date: 2009-06-27
forum: Server Platforms
---

### Post by platonio on 2009-06-27
Hey guys,

I need your help. I´ve got absolutely no idea of this problem.

On my server is running backuppc to backup all the clients.

But from one day to another the backups doesn´t work anymore.

So I started to find out what´s the problem.

If I type "rsync hostname::C" I get an connection refused,
when I use "rsync ip-address::C" the connection works!

Anyone have a idea?

Thank oyu

Chris

---

### Post by TwiceOver on 2009-06-27
Can you ping by hostname?

---

### Post by platonio on 2009-06-27
Ping by hostname works.

:confused:

---

### Post by TwiceOver on 2009-06-27
Sorry, no help for ya.  I use backuppc to backup 30 windows clients but that is all with Samba, haven't even tried rsync yet.

---

### Post by Bushwack on 2009-06-27
Not really a solution, but I've run into similar issues with backuppc finding my clients and I just gave up and adding entries into /etc/hosts for the clients.  That may not be a good option for you though if you have lots of machines with changing ips.

---

