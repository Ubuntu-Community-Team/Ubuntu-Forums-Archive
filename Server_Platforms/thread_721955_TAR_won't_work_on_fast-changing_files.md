---
title: "TAR won't work on fast-changing files"
date: 2008-03-11
forum: Server Platforms
---

### Post by lodp on 2008-03-11
I'd like to have certain folders on my server tar-gzipped and FTP'ed to a remote location, as a cronjob. There's a Webmin module that does just that (it's called plainly "File System Backup").

My Problem is that Apache Access logs are changing so fast that in the process TAR always issues the following error:

> tar: /[...]/logs/access_log: file changed as we read it

The backup utility can execute commands before and after the backup starts. So it would probably work if I just had it turn off apache before the backup, and back on after that. But as that would piss off a cpl of hundred users every day, I would rather not do that.

Is there a way to re-load apache and make it stop logging or logging somewhere else for that brief period? It's only a cpl of minutes..

---

### Post by lodp on 2008-03-11
OK, I've found this messy workaround -- just restarting apache specifying a different config file (that doesn't include the CustomLog directive and therefore doesn't write stuff to the directory I'm trying to tar). It's messy because I have to include duplicates of all my virtual hosts.

But I think I ran into a bug in apache here. I use the following command to restart:

> apache2 -f /etc/apache2/apache2-nolog.conf -k restart

Apache restarts alright, and evidently it parses the alternative config file (because it complains about syntax errors if there are any in apache2-nolog.conf). But it doesn't stop writing to that custom logfile. It only stops doing that when I run

> apache2 -k stop

apache2 -f /etc/apache2/apache2-nolog.conf -k start

Isn't that crazy? Should I file a bug for this?

---

