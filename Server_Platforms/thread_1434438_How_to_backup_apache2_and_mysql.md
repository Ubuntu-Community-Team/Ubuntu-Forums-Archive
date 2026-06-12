---
title: "How to backup apache2 and mysql?"
date: 2010-03-20
forum: Server Platforms
---

### Post by hockey97 on 2010-03-20
Hi, I would like to know how to back up mysql and apache2 manually.

Meaning just click and drag files to a external hard drive.

any ideas?  would like to know how to make a backup so all I have to do is if the hard drives fail and I need to reinstall or put my websites on to another server I can easily just transfer the files and it will work. No need to ever play with the configurations ever again.

---

### Post by Vegan on 2010-03-20
I use /home/username for each site, so I can use tar to backup everything.

You can do the same for MySQL databases as well.

---

### Post by jrssystemsnet on 2010-03-20
> **Vegan said:**
> You can do the same for MySQL databases as well.Just because you *can* ... on a lightly-loaded server ... usually ... doesn't mean you *should*.

```
you@box:~$ mysqldump -u root --all-databases | gzip > /backups/mysqldbs.gz
``` is the proper way to back up your MySQL databases.

If you wanna get a little fancier...

```
#!/bin/sh

DATE=`date "+%Y-%m-%d____%H.%M"`

/usr/bin/mysqldump -u root --all-databases | gzip > /backups/mysqldbs.$DATE.gz
```

Save that to mysqlbackup.sh, chmod 755 mysqlbackup.sh, and now you've got a script that will back up your mysql dbs, compress them, and put the date in the filename for you.

If you have a root password on your MySQL, add the option -pmyrootpassword (note: no space between -p and the password) to the command, chown the script root, and chmod it 500 (so nobody but root can read the script, and thus see your MySQL root password).  After you do that, you'll need to use sudo to run the script (or just run it from root's crontab, in which case sudo isn't necessary because it's already being run as root).

---

### Post by jrssystemsnet on 2010-03-20
Oh, and to restore from your backed up databases:

```
zcat mysqldbs.gz | mysql -u root -pmyrootpassword
```

If you don't have a root mysql password, of course, you don't need the -p option.

---

### Post by kgatan on 2010-03-21
Check the link below for a nice mysql dump script. I use it together with Cron to make daily backups.
 
 
[http://sourceforge.net/projects/automysqlbackup/](http://sourceforge.net/projects/automysqlbackup/)

---

