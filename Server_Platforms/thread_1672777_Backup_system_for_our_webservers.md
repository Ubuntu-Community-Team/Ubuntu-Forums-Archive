---
title: "Backup system for our webservers"
date: 2011-01-21
forum: Server Platforms
---

### Post by garethsimpsonuk on 2011-01-21
Hi,

I’m on the lookout for a backup system for our web servers and was wondering if anyone could advise me on a good linux based system:

Server Details:

- CentOS
- MySQL
- PHP
- Apache
- It hosts mainly CMS driven sites
- I have shell access but no root privs

Requirements:

- Backup all web / vhosts files 
- Backup databases
- Automatic / Cron
- Backups downloaded to our office server via ftp etc.
- Preferably web gui driven
- An email / notification of some sort would be useful
- Backup of other critical data such as email would also be good

My host recommended a Linux box in the office that downloads all site files via ftp, dumps the database using a MySQL connection and tars the 2 up together.

Here are a few tools that I know of that could do this:
[http://www.bacula.org/en/](http://www.bacula.org/en/)
[http://backuppc.sourceforge.net/](http://backuppc.sourceforge.net/)
[http://www.diffingo.com/oss/fwbackups/faq](http://www.diffingo.com/oss/fwbackups/faq)

Bacula seems to be the best. The server comes with the Plesk control panel and the native backup system is rubbish. 

Does anyone know of a good solution for doing the above?

Many thanks

---

### Post by HermanAB on 2011-01-21
Howdy,

There is no easy way to do it.

You need to Export the MySQL database, then make a backup of the exported copy.  Go to the MySQL web site and start reading on mysqldump and other methods to export.

Once you got the database problem sorted out, then you can make the backup using rsync or a Bacula tape system or whatever.

---

### Post by garethsimpsonuk on 2011-01-25
Thanks for the reply. I was initially looking at bacula but that requires some software to install on the server which I can't do.

Backuppc now seems the best option as I can backup using rsync over ssh. As you say I need a script to dump the databases but I've read that this is possible with backuppc.

Can anyone point me in the direction of getting / writing a script that can be inegrated into backuppc?

Many thanks

---

