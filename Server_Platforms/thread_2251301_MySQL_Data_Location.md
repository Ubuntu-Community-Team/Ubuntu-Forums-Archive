---
title: "MySQL Data Location"
date: 2014-11-03
forum: Server Platforms
---

### Post by Andrew_Perry on 2014-11-03
I am using Ubuntu Server 14.04 and trying to change the data directory location for MySQL. I have looked on various web sites and forums (probably including this forum) and they all basically give the same set of instructions, namely:-

1. Stop the MySQL service.
2. Copy directory /var/lib/mysql to the new location, ensuring that file/directory ownerships and permissions are transferred.
3. Edit references to /var/lib/mysql in my.cnf and also the AppArmor profile.
4. Reload the AppArmor service.
5. Restart the MySQL service.

I have followed these instructions carefully and the MySQL service restarts without errors. If however I try and load a web page that accesses one of the databases, it comes up with errors as if it has not connected properly to the database. Undoing the above operations causes normal behaviour to be restored.

Tried an alternative method of using a bind mount to make /var/lib/mysql to point to the alternative location and exactly the same problem occurs.

I am missing something?

Thanks,

Andrew.

---

### Post by nerdtron on 2014-11-03
Post here the files you edited and the lines you edited on them.
This could be an error on the apparmor. Did you try to reboot?
Any errors on the mysql error logs? (although it won't say app armor error, it cna be helpful sometimes)

---

### Post by Andrew_Perry on 2014-11-03
Thanks for the reply. Please see attachment containing the two config files. A reboot made no difference. I'll check the logs later but at least here is something to go with.

---

