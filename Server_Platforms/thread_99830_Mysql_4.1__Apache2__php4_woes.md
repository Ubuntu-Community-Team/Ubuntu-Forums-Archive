---
title: "Mysql 4.1 / Apache2 / php4 woes"
date: 2005-12-06
forum: Server Platforms
---

### Post by Syirrus on 2005-12-06
I recently upgraded my ubuntu server to breezy from hoary. The upgrade went well for the expection of mysql not working properly.  I combed the forums and found what I though to be the solution (apt-get install mysql-server-4.1 instead) but things still don't work.  I get the following error message when I try to start mysqld:

```

sudo mysqld
InnoDB: Error: auto-extending data file ./ibdata1 is of a different size
InnoDB: 0 pages (rounded down to MB) than specified in the .cnf file:
InnoDB: initial 640 pages, max 0 (relevant if non-zero) pages!
InnoDB: Could not open or create data files.
InnoDB: If you tried to add new data files, and it failed here,
InnoDB: you should now edit innodb_data_file_path in my.cnf back
InnoDB: to what it was, and remove the new ibdata files InnoDB created
InnoDB: in this failed attempt. InnoDB only wrote those files full of
InnoDB: zeros, but did not yet use them in any way. But be careful: do not
InnoDB: remove old data files which contain your precious data!
051206  9:02:19 [ERROR] Can't init databases
051206  9:02:19 [ERROR] Aborting
051206  9:02:20 [Note] mysqld: Shutdown complete

```

If I try to bring up my website (that is what I'm using mysql for) I get the following error message:

```

MySQL extension not loaded in PHP.
Recompile PHP, edit php.ini or choose a different SQL layer.

```

I'm a fairly familar with Linux, but I'm still green behind the ears. I've uninstalled and reinstalled all relevent packages for mysql/php/apache2 but to no avail.  Does anyone have any suggestions?

---

### Post by ugus on 2005-12-06
uninstall reinstall mysql, worked for me and other guys

---

### Post by Novastorm on 2005-12-06
This page should help you,

[https://wiki.ubuntu.com/ApacheMySQLPHP?highlight=%28php%29%7C%28apache%29%7C%28mysql%29](https://wiki.ubuntu.com/ApacheMySQLPHP?highlight=%28php%29%7C%28apache%29%7C%28mysql%29)

I suspect you haven't done what is outlined in the step, "Edit PHP Configuration to Work With MYSQL"

Also it looks like your existing databases are corrupt, try moving them elsewhere temporarily so that Mysql doesn't abort. Can't remember the exact directory for the databases at the moment, and don't have a ubuntu machine with mysql available, but i think they're in /var/spool/mysql or something around there.

---

### Post by LordHunter317 on 2005-12-06
Post your my.cnf.  It's misconfigured in someway.

What MySQL is basically saying is it tried to start an InnoDB database file, but it was bigger than the allowed size for it.  You didn't accidently copy a MySQL configuration from somewhere else over the default one, did you?  That would cause this behavior.

---

### Post by Syirrus on 2005-12-08
ahh I see what the problem is.  There was a problem with my mysql database as mentioned above.  I just ended up reinstall everything and everything is working now.  Thank you very much for all of your input.  

Ubuntu is a wonderful product, but the community really makes it the best!

Syirrus

---

