---
title: "Migrate hosted virtual Ubuntu server 8.04 to 10.04 [within 7 days]"
date: 2011-10-29
forum: Server Platforms
---

### Post by jesuspresley on 2011-10-29
I need to migrate my healthy 8.04 install to a new machine provided by my hosting company Hosteurope (due to harddisk capacities and better performance on the new product)

Hosteurope provides a parallel installation for 7 days, so within this timespan I need to migrate the following packages and data (among others) to the new machine:

[LIST]
[*]Apache,
[*]PHP5,
[*]MySQL (including several TYPO3 and Wordpress installations)
[*]ProFTP
[*]OpenSSL (no signed certificate)
[*]Ruby on Rails + Passenger (Redmine installation) 
[*]Sendmail (No Mailboxes, only for sending mails) 
[/LIST]

Ho would you approach this task? 

[LIST=1]
[*]My idea was to upgrade my 8.04 distro to 10.04 first. 
[*]Then install all packages that i need on the new machine (using the package list exported by *dpkg --get-selection *)
[*]Then send all configurations to the new machine with rsync.
[*]Then fiddle around (I am a little bit afraid of messing things up here....)
[/LIST]

Any other strategies, experiences?

---

### Post by collisionystm on 2011-10-29
> **jesuspresley said:**
> I need to migrate my healthy 8.04 install to a new machine provided by my hosting company Hosteurope (due to harddisk capacities and better performance on the new product)

Hosteurope provides me with a parallel install for 7 days, so within this timespan I need to migrate the following packages and data (among others) to the new machine:

[LIST]
[*]Apache,
[*]PHP5,
[*]MySQL (including several TYPO3 and Wordpress installations)
[*]ProFTP
[*]OpenSSL (no signed certificate)
[*]Ruby on Rails + Passenger (Redmine installation) 
[*]Sendmail (No Mailboxes, only for sending mails) 
[/LIST]

Ho would you approach this task? 

[LIST=1]
[*]My idea was to upgrade my 8.04 distro to 10.04 first. 
[*]Then install all packages that i need on the new machine (using the package list exported by *dpkg --get-selection *)
[*]Then send all configurations to the new machine with rsync.
[*]Then fiddle around (I am a little bit afraid of messing things up here....)
[/LIST]

Any other strategies, experiences?

Obviously if you are asking you are feeling a time crunch. Lets get you more time first.

Do you have any newer machines laying around? 

I would do this on day one.

Get VMware ESXi. It is free for 60 days. use the converter program to pull the image of your 8.04 onto the vmware server local in your shop. NOW you have it for more than 7 days to find things you will probably miss along the way and help rebuild them.

---

### Post by collisionystm on 2011-10-29
I would NOT upgrade your 8.04 to 10.04. Waste of time. To dangerous with a Hosted system.

---

### Post by SeijiSensei on 2011-10-29
Start with a fresh 10.04 server.  Install "LAMP" for Apache, PHP, and MySQL, and install the 10.04 packages for the remaining items like proftpd and Ruby on Rails.  If you specifically want sendmail and not Postfix, then remove Postfix and install sendmail.

Now you just need to migrate the settings from the old server to this one.  For most applications, that means simply copying over the relevant configurations in /etc, e.g., /etc/apache2 for the Apache server.  You'll also need to migrate data directories like /var/www.

For MySQL, you're probably best off running mysqldump (as the MySQL root user) on the 8.04 machine to dump all the databases to a portable text file.  Then import that file into the database on the new machine.

Seven days isn't an unreasonable amount of time to accomplish this.  Most of what I described can be done in a solid couple of days work.

---

### Post by e79 on 2011-10-29
EDIT
 SeijiSensei's advices ar far more precise and valuable...but nontheless...
--------------------------
I would not upgrade as well, there is always a good chance somehting 'just won't work' after your upgrade.

I would start by testing my new environment (Ubuntu 10.04 LTS) on a virtual machine at home and see if I can backup all the data (MySQL DB, Apache2 config, WordPress install etc) from the old machine and then try to restore it into this virtual machine.

If everything is working correctly, you can then redo same steps in your real hosted environnment.

I would have a look here:
[http://codex.wordpress.org/Moving_WordPress](http://codex.wordpress.org/Moving_WordPress)
[http://www.cyberciti.biz/tips/move-mysql-users-privileges-grants-from-one-host-to-new-host.html](http://www.cyberciti.biz/tips/move-mysql-users-privileges-grants-from-one-host-to-new-host.html)
[http://tomcat.apache.org/migration.html](http://tomcat.apache.org/migration.html)

My $0.02

---

### Post by jesuspresley on 2011-10-29
Thanks so far, highly appreciated. Some detail questions:

**MySQL:**
How about copying the MySQL data directory /var/lib/mysql instead of dumping the databases? 

**System users:**
I guess they can also be copied from a directory?

**File permissions:**
How to make sure that the permissions stay the same on critical files (like my.cnf)?

---

### Post by SeijiSensei on 2011-10-30
> **jesuspresley said:**
> How about copying the MySQL data directory /var/lib/mysql instead of dumping the databases?

You can try that.  While it has worked for me in the past, dumping and reloading the database may be more reliable. 

> System users:
I guess they can also be copied from a directory?

I'm not sure what you're referring to here.  All the critical user information is stored in just three files -- /etc/passwd, /etc/group, and /etc/shadow.  If you copy these files you'll have the user information as before.  Obviously if you have real users with home directories you'll need to copy /home as well.

> File permissions:
How to make sure that the permissions stay the same on critical files (like my.cnf)?

The files will have the same permissions on 10.04 as they did on 8.04, particularly files associated with system users.  The uid and gid of the mysql user doesn't change across releases.  If it did, chaos would ensue.

This isn't as hard as you seem to think it will be.  Plus if something goes wrong, you can just blow away the new VM and start over.

---

### Post by jesuspresley on 2011-11-04
Thanks for al the hints. The migration worked fine. Here is a very rough walkthough:

[LIST]
[*]Set up a clean 10.04 system on new host
[*]Installed all needed packages (handpicked, not exported from old server)
[*]Imported system users and groups with Webmin user export/import function
[*]Transferred important config directories (to a temp. directory first) with rsync (option -aE preserved file permissions based on uid / gid)
[*]Transferred apache htdocs directory (/var/www/) and subversion root with rsync
[*]Transferred mysql data directory directory (/var/lib/mysql) with rsync to temp directory on new server. Then copied handpicked innoDB files from temp to /var/lib/mysql (except system-db like mysql)
[*]Backed up old server (6.5 GB) to a backup directory with rsync
[/LIST]

I had difficulties with Redmine (Ruby on Rails) but everything else was quite easy to manage.

---

