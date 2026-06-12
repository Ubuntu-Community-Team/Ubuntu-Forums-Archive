---
title: "How to backup a server with wordpress"
date: 2015-11-13
forum: Server Platforms
---

### Post by fernandoch on 2015-11-13
Hello,

How would you backup a server running multiple wordpress sites?

Would you simple use this script?

[https://help.ubuntu.com/lts/serverguide/backup-shellscripts.html](https://help.ubuntu.com/lts/serverguide/backup-shellscripts.html)

Thanks

---

### Post by Habitual on 2015-11-13
I use
```
mysqldump -u<user> -p<password> <identifier> /path/to/file.sql
tar -pczf /path/to/archive.tar.gz /path/to/file.sql /var/www/vhost0/ /var/www/vhost1/ /etc/apache2/sites-enabled/vhost0 /etc/apache2/sites-enabled/vhost1
rm /path/to/file.sql
#EOF
```

and then move the file off the host.

---

### Post by fernandoch on 2015-11-13
Nice one, with mysqldump I imagine you backup all the databases.

You don't do physical backup of your mysql, just logical?

---

### Post by Habitual on 2015-11-13
> **fernandoch said:**
> Nice one, with mysqldump I imagine you backup all the databases.

You don't do physical backup of your mysql, just logical?
Well, I only have the one db that we care about in the event of an emergency.

The host is backed in its entirety using Amazon tools.

---

### Post by SeijiSensei on 2015-11-13
Creating portable "dump" files has always been my preferred way to backup MySQL and PostgreSQL databases.  That said, I've found that backing up /var/lib/mysql can work as well.  I once had a project to restore a MySQL database.  I upgraded to the newest version and then replaced the /var/lib/mysql tree that was created during the installation with the existing one.  MySQL started right up.  PostgreSQL has more differences between versions so I haven't been able to make that trick work reliably.  That's why I rely on dump files.

I'm not sure what you mean by "physical" versus "logical" backups. Is dumping the database and writing the file to another machine or to a removable storage device "physical" or "logical?"

You also need to back up the "wordpress" directory tree for each site as well, of course.  Uploaded objects, add-ons, themes, and the like are all stored there, not in the database.

---

### Post by fernandoch on 2015-11-13
Thanks for the input.

A logical backup is with mysqldump.

A physical one is with OS tools (copying the files).

In the ubuntu doc I posted above they just do a physical backup of files.

I might give it a try and see how it restores a mysql db as this is what worries me the most.

---

### Post by volkswagner on 2015-11-14
[Updraft Plus]("http://updraftplus.com/") is a backup plugin for WordPress. The free version offers enough to get the job done.  It will backup the DB and site directory, then compress into
a single file.  You can then use a script to copy off site.

---

### Post by fernandoch on 2015-11-14
Thanks a lot.

---

