---
title: "Backup tools over ftp/sftp"
date: 2008-08-24
forum: Server Platforms
---

### Post by mansonthomas on 2008-08-24
Hi,

  I need to backup some data and export it over ftp or ssh.

  I'd like to make a full backup once a week, differential backup every night.

  I want to be able to list directories that should be backup and define some exclusion rule (directory with certain name, do not follow symlink).

  I also like to be able to export the backup to multiple destination.

  If it can be simple to use, would be great, I'm not masochist ;)

  Does anyone knows an open source tool that will do that ?


Thanks,
Thomas.

---

### Post by mansonthomas on 2008-08-24
up

---

### Post by mansonthomas on 2008-08-24
no one ?

---

### Post by mansonthomas on 2008-08-24
up

---

### Post by tamoneya on 2008-08-24
sbackup: [http://sbackup.wiki.sourceforge.net/](http://sbackup.wiki.sourceforge.net/)

Please do not bump a post for 24 hours.

---

### Post by loboc on 2008-08-24
rsync and daemon mode

---

### Post by inphektion on 2008-08-24
> **tamoneya said:**
> sbackup: [http://sbackup.wiki.sourceforge.net/](http://sbackup.wiki.sourceforge.net/)

Please do not bump a post for 24 hours.

huh, looks pretty nice.  I think it can replace my hacked up cron tar backups pretty easily.

---

### Post by mansonthomas on 2008-08-25
Hi,

I've found this :

[http://migas-sbackup.sourceforge.net/](http://migas-sbackup.sourceforge.net/)

I'll try both and will give some feedback.

Thomas

---

### Post by mansonthomas on 2008-08-25
One more : [http://www.bacula.org](http://www.bacula.org)

---

### Post by mansonthomas on 2008-08-31
I've reviewed the 3 links : 

I do not choose this one because : 

* sbackup : no documentation, is quite young, depends on Python
* migas-sbackup : seems to be dead, no activity since January 2007

I choose bacula, because it's documented, seems mature, meets my requirements.

---

### Post by Vegan on 2008-08-31
the old school tar works.

---

### Post by cariboo on 2008-08-31
Since nobody else has mentioned it rsync using ssh have a look at this howto here:

[http://troy.jdmz.net/rsync/index.html](http://troy.jdmz.net/rsync/index.html)

Jim

---

