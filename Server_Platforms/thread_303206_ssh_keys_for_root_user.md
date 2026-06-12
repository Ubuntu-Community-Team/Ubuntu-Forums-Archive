---
title: "ssh keys for root user"
date: 2006-11-19
forum: Server Platforms
---

### Post by aparsons on 2006-11-19
Hi:

I have two servers that I need to rsync via ssh.  I have ssh up and running, and I've disabled the root user from logging in via ssh.  I had a few questions:

1) Is it possible to disable root logins using the keyboard (prompt for password) but authenticate root users using ssh keys?  I have a key on each server in ~/.ssh/authenticated_keys

2) If it isn't possible to disallow keyboard root users and allow root logins with key pairs, is there a way to create a user (username= rysnc) with root privleges so that my rsyc scripts don't encounter any permission issues?

Thanks!

---

### Post by JLTB on 2006-11-20
Hi aparsons,

For obvious reasons I would suggest that rsyncing with root access is a bad idea...

What I have done to rsync my servers (I do it for backup purposes) is create a user on my backup box (the box the backups will be on) called 'backup' or something similar.  I give it little or no permissions besides being able to write to my backup folder

ie:

```

chown -R backup:backup /media/backups
chmod -R 644 /media/backups

```

Then I share the RSA keys for that account.  This limits the ability for a malicious user to damage the system if the backup account was compromised.  Of course, it's also a good idea to duplicate your backup data as well, since a compromised backup account could still ruin your backups (probably the worst thing to happen).

Also, if you REALLY need to do something as root you can always use the old **+S** hack with chmod.  This will give any script you chmod the ability to run as superuser (aka root).  In general this is a bad idea, I would avoid it.

Good luck,

James.

---

### Post by JLTB on 2006-11-20
Sorry, that's **+s** (lower case s) for the set-uid switch!

---

### Post by aparsons on 2006-11-20
Fixed!  Thanks for the advice.

-Allan

---

### Post by MJN on 2006-11-21
> **JLTB said:**
> Hi aparsons,

For obvious reasons I would suggest that rsyncing with root access is a bad idea...

Undesirable perhaps, but often unavoidable - sometimes it's essential for rsync to be running as root at both ends - e.g. an entire system backup/restore where full permissions to read/write (and preserve ownership) are required.

The security concerns of allowing root SSH access, even with key authentication (and no passwords), can be mitigated to a certain extent by ensuring that only the rsync command can be executed (i.e. no other command or shell access) for root.

Plenty of guides available covering sshd's *PermitRootLogin forced-commands-only* directive - I recommend [www.jdmz.net/ssh/]("http://www.jdmz.net/ssh/").

Mathew

---

