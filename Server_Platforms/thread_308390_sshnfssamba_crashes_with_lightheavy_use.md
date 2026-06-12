---
title: "ssh/nfs/samba crashes with light/heavy use"
date: 2006-11-28
forum: Server Platforms
---

### Post by soleblaze on 2006-11-28
Hey, I just installed edgy on my system and am trying to set it up as a samba/nfs server.  The problem is, I start connect to the samba or nfs server via os x and start copying files over and it gets part way done.  Then nfs, samba, and ssh will kick me off and not accept connections (the daemons are still running on the machine).  if I restart the services I can connect again for a few minutes before it stops accepting connections again.  Has anyone seen this?

I also have apache running, but it still accepts connections when the others do not.  Also no messages relating to this show up in /var/log/messages or the /var/samba/*

System setup:

Ubuntu Edgy Eft 6.10
Athlon XP 2700+
nForce2 Motherboard
Geforce4 MX
eth0: forcedeth
eth1:  Dlink DGE-530T gigabit (sk98lin driver)

---

### Post by Permafrost91 on 2006-11-29
I'm having a similar issue with edgy. I'm trying to copy files from my laptop  running edgy to my desktop also running edgy via NFS. About 5 seconds into any transfer of information (even reading the remote directory), my laptop freezes and requires a hard-shutdown because it doesn't respond. This is frustrating. I've never used NFS before so I don't know how to troubleshoot this. Any ideas would be greatly appreciated.

---

### Post by soleblaze on 2006-11-29
Ok, I found out my problem.  Turns out one of my wireless routers had the same ip as the one I assigned to my server..whoops.

---

