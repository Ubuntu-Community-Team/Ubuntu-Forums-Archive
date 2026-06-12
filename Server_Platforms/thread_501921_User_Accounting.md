---
title: "User Accounting"
date: 2007-07-15
forum: Server Platforms
---

### Post by delphiguy on 2007-07-15
Cheers,

I am running FTP and Samba on my Feisty system.  And I usually manage this machine from a windows machine
using Putty and SSH.

However I am wondering, is there a way for me to know what time a User Log in and Log out, as well as how many bytes a user has put in the system and how many bytes a user has downloaded.  Also I want to know 
which files they uploaded or downloaded.  Also I want to get the list of all users and groups in my system.  I 
know that there is a groups command that lists all the groups a user is a member of.  Is there an equivalent of
that where I get a list of all users a group is a member of?

Thanks.

---

### Post by Mr. C. on 2007-07-15
Consider the following commands and log files

**Commands**
[LIST]
[*]last
[*]du -s /home/*
[/LIST]

**Log Files**
[LIST]
[*]/var/log/vsftpd.log
[*]/var/log/smb*  (i don't recall exactly the naming scheme for Ubuntu's samba logs).
[/LIST]

The /etc/passwd file lists your users.  I'm not sure I understand your last question - you mean for each group, a list of which users are in that group ?  If so, that would just be the /etc/group file.

MrC

---

### Post by delphiguy on 2007-07-16
thanks for the quick reply.  I'll check that out.

---

