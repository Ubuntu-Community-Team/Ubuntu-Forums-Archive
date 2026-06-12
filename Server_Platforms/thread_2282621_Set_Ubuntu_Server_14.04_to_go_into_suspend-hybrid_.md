---
title: "Set Ubuntu Server 14.04 to go into suspend-hybrid when idle?"
date: 2015-06-15
forum: Server Platforms
---

### Post by PartisanEntity on 2015-06-15
I have a headless server running Ubuntu Server Edition 14.04.

I have tested pm-suspend-hybrid and it works. I am able to manually put the server into suspend-hybrid through command line.

I am also successfully able to resume the server through WoL from another machine.

What I would like to do is get the server to automatically go into suspend-hybrid when not in use for at least 30 mins.

By *use* I mean:

[LIST]
[*]remote machines are accessing NFS shares on the server over the network
[*]my TV is accessing DLNA content over the network
[/LIST]

If it is too complicated to determine when a machine is idle, alternatively I would like to set the server to go into suspend-hybrid from 01:00 AM every day.

Is there any tutorial or step by step process I can use to get this working?

---

### Post by TheFu on 2015-06-15
I don't know.

However, [http://www.cyberciti.biz/faq/appleosx-bsd-find-clients-connecting-to-a-nfsserver/](http://www.cyberciti.biz/faq/appleosx-bsd-find-clients-connecting-to-a-nfsserver/) does provide some ideas, but you'll probably need to use autofs for NFS mounts, not fstab mounting. Plus if any program or even a shell has a PWD on the NFS storage, then it will remain active and will not disconnect. Removing an NFS server from under an active "hard" NFS mount is bad - lock up the client - bad.

Interesting idea.  I weanied out and put my nfs server on the same box as my media server since it uses 20W of power and the "server" with powerful CPUs and lots-o-RAM uses 100W+. Easier to leave it on.

I can't just check the CPU load - since my systems all wake up every minute to provide monitoring data back to a central server.

pm-suspend is the command, BTW.

---

### Post by nerdtron on 2015-06-17
Not sure, but probably some way to measure server load? maybe nfsiostat that can determine if the nfs is in use. Then write a script that will check if system is idle for 30. For example, check if nfs is idle, then save a file (checker file), then after 10 minutes check the nfs again, if idle update the file (checker file) so on up to 30 minutes. Then suspend the server if it's idle.

> suspend-hybrid from 01:00 AM every day.
crontab entry? 
```
0 1 * * * /command/to/suspend/here
```

---

