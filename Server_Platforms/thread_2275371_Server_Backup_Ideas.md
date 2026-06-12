---
title: "Server Backup Ideas"
date: 2015-04-25
forum: Server Platforms
---

### Post by Mike_Hughes on 2015-04-25
Does anyone have any ideas schemes for backing up a Web Server? Also how do you get a Server to come on and boot  by itself when the power goes out and comes back?

Mike

---

### Post by ian-weisser on 2015-04-26
> **Mike_Hughes said:**
> [H]ow do you get a Server to come on and boot  by itself when the power goes out and comes back?

That's usually a BIOS setting. Not related to any OS.

> **Mike_Hughes said:**
> Does anyone have any ideas schemes for  backing up a Web Server?

Depends on the purpose of the backup, the software running the webserver, the content it serves, and how immediate you need a restore to be.

---

### Post by Mike_Hughes on 2015-04-26
That is all true. I was just wanting to see what others are doing for their headless Servers.

---

### Post by SeijiSensei on 2015-04-26
Each night I run a script on my cloud web server that uses pg_dumpall and "mysqldump --all-databases" to back up the system's databases. The script then uses rsync to transfer those database dumps along with the contents of the website tree and various other things like logs to a server in my house.

I also pay my service provider, [Linode]("http://www.linode.com/"), a few dollars each month to keep [snapshots]("https://www.linode.com/backups") of my virtual machines.  

I use WordPress for some sites.  The content is largely stored in each site's MySQL database, but uploaded objects like images are stored in the filesystem (as they should be).  So to back up an entire WP site, I need both the database and the files in the website tree.  I use PostgreSQL for the applications I write myself, so I have to back that up as well.

---

