---
title: "Can I create a user who can read any file?"
date: 2008-08-12
forum: Security
---

### Post by Greg-&gt;G on 2008-08-12
I am trying to setup a system for offsite backups.  Both the backup and the original are behind firewalls.  I control the firewall in front of the original, but not the one in front of the backup.

I want to have the backup automatically copy files via rsync-over-ssh from the original.  I can't have the original send the files to the backup because it can't connect to the backup through it's firewall, so I have to go in this direction (backup connects to original).  

My question is what user should the rsync/ssh log in as?  The backup should be able to read anything on the system.  But I don't want to allow remote root logins, and the backup user doesn't need to have write access to anything.  So is there a way to create a user who can read anything on the filesystem, regardless of permissions, but respect write permissions of the filesystem?  

Or alternately, is there a different and/or better way to solve my problem?

thanks,
greg

---

### Post by benign on 2008-08-12
Nevermind.

---

