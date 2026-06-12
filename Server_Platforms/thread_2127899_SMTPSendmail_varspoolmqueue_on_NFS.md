---
title: "SMTP/Sendmail /var/spool/mqueue on NFS"
date: 2013-03-21
forum: Server Platforms
---

### Post by hash4all on 2013-03-21
Expert,

I am newbie on smtp/sendmail and on Ubuntu.
I have two servers, Server A and Server B and configured smtp/sendmail on it.
These two are configured in HA mode or active/standby mode.

Could you please let me know what is the best way to use mail queue on NFS mount?
Also can I use single NFS mount to be use on both the Server A and B (mount point /var/spool/queue) or is there any impact on performance?

If NFS mount is not possible could you please let me know what is the best way for mail queue.

Thanks

---

### Post by hash4all on 2013-03-22
Expert,

any suggestion?

Waiting for the reply.

---

### Post by howefield on 2013-03-22
Thread moved to the "Server Platforms" forum.

---

### Post by hash4all on 2013-03-22
expert,

any feedback on this?

---

### Post by hash4all on 2013-03-29
Expert,

any one to suggest or help here?

Thanks
Hash

---

### Post by Zill on 2013-03-29
hash4all:  Firstly, I am not an "expert", nor do I run a SMTP or Sendmail server but I *do* use NFS.

I do not fully understand your question but my understanding is that any NFS mount just becomes a part of the root file system for a particular machine.  I would guess that this means you can, if you wish, keep your mail queue on such a mount as it will appear to be on the "local" file system.  IMHO, the only significant performance hit will be the delay in transferring data over your LAN to the NFS server.

I suggest you create a test system (populated with some dummy data) to test this on and then, if you hit any problems, post back with actual terminal output to show exactly what is happening.

HTH.

---

### Post by SeijiSensei on 2013-03-29
As long as "no_root_squash" is used on the server, so that root can mount /var/spool/mqueue without losing privileges, then yes, you can have an NFS-mounted queue.  However I would discourage you from having both machines despool the messages because of possible contention over file locks.  Let one machine handle the sending, with the other waiting in reserve.

If sendmail starts with "-bd -q15m" or something similar, remove the "-q15m" from one of the servers.

---

### Post by hash4all on 2013-04-01
Thanks for reply.

Thanks
Hash

---

