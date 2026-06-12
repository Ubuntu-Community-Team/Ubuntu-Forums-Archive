---
title: "Problem with defining userrights"
date: 2013-01-08
forum: Server Platforms
---

### Post by frebae on 2013-01-08
Hi,
In the directory /var/www I made 2 subdirectory's.
By means of a FTP connection I want to place files in those directories to give other people the possibility to download this files.
The problem is that this files get the rights of the ftp user and it is not possible for other people to download.
How can I solve this problem ?
Some help please to solve this problem.

Kind regards,

Freddy

---

### Post by bab1 on 2013-01-08
> **frebae said:**
> Hi,
In the directory /var/www I made 2 subdirectory's.
By means of a FTP connection I want to place files in those directories to give other people the possibility to download this files.
The problem is that this files get the rights of the ftp user and it is not possible for other people to download.
How can I solve this problem ?
Some help please to solve this problem.

Kind regards,

Freddy
Manage the directories with the group permissions (GID) rather than the UID.  By that I mean create a group with all the users in it and set the group to have rw permissions.  You then have to set the GID bit on the root directory for the directory branch (/var/www).  To set the GID (sgid) see [**_[COLOR="Blue"]here[/COLOR]_**]("http://www.zzee.com/solutions/unix-permissions.shtml#setuid") (hint: I set the perms to 2775).  The sgid bit (the 2) gives group  inheritance to all directories and files in the subdirectories.

---

