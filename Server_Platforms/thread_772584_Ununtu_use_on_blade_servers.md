---
title: "Ununtu use on blade servers"
date: 2008-04-28
forum: Server Platforms
---

### Post by oyersj on 2008-04-28
I have a customer that wants to use Ubuntu server for a blade application. This would involve about 15-20 "blades" - quad core AMD's and about 200T of storage. Single blade to run the whole show (with one "backup" or "mirrored" blade.

Has anyone any experience with setting something like this up? Is it possible?

Thanks in advance.
Scott

---

### Post by oyersj on 2008-04-28
Customer has changed from blade server to tower, but I need to "mirror" one server to the other for redundancy. Not asking for someone to do it for me, just want to know if it can be done.

Thanks.
Scott

---

### Post by cdtech on 2008-04-28
Rsync!

---

### Post by oyersj on 2008-04-28
> **cdtech said:**
> Rsync!

Thanks. Am I understanding correctly that I can setup what directories are sync'd? I could set up both servers identical and just rsync the database?

---

### Post by Brazen on 2008-04-28
It depends on if you want syncronous shared storage or asyncronous.  Rsync would be async - meaning the filesystems will not be immediately in sync, only at the moment rsync is run are your servers in sync.  You could run rsync once every day, once every hour, or more, but if you want to get up to once every 30 minutes or less, you might as well go with syncronous shared storage.

Now with syncronous storage you have a couple options, either each server keeps a copy of the storage and you use drbd to keep the two in sync (drbd makes each server commit writes at the same time, which means your effective harddrive speed will be affected by the network latency between the servers).  My choice however, would be to use a separate iscsi server for storage and connect each application server to that.  You can even have two iscsi servers being synced with drbd and have the iscsi lun (lun is the term used for what the other servers see as the harddrive) running on top of the drbd device.  The advantage of this is that you can set up your storage redundancy on the two iscsi servers, packed with harddrive space, and have all 20-ish of your other servers all connect to those.

For the failover, if you want it to be automatic, you will want to use HA and Heartbeat to monitor the servers and move the ip address and services to another machine in the event of a machine failure.

---

