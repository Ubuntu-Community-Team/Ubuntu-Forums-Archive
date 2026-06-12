---
title: "Crontab doesnt backup sql database but running manually does"
date: 2016-11-02
forum: Server Platforms
---

### Post by thomo2710 on 2016-11-02
Hi,

I want to backup my wordpress database and a couple directories

I have this script saved as backup.sh and i have made it executable. 
My server user account (useraccount in this scenario) is the user and group owner of both the backup.sh file and the /backups directory


[PHP]#!/bin/bash

cd /var/www/html/website/public

# Backup database
wp db export /var/www/html/website/backups/`date +%d%m%Y`_database.sql --add-drop-table

# Backup uploads directory
tar -zcf /var/www/html/website/backups/`date +%d%m%Y`_uploads.tar.gz wp-content/uploads

# Backup plugins directory
tar -zcf /var/www/html/website/backups/`date +%d%m%Y`_plugins.tar.gz wp-content/plugins[/PHP]


Now if i run this script from the termial manully then i get all 3 files output

If i run it with the crontab for my server user account then i dont get the sql database file, but i do get the 2 directories.

crontab -u useraccount -e

0 * * * 1 sh /var/www/html/website/backup.sh

No errors that i can see in the syslog.

Anybody any ideas?

Thanks

---

### Post by ian-weisser on 2016-11-02
Try using the full path to wp
Cron, when it runs a job under your username, does not inherit your entire environment.

---

### Post by SeijiSensei on 2016-11-02
And don't put scripts inside the web directory tree.  That's a security no-no.  I use /usr/local/bin or, more often, /usr/local/sbin for maintenance scripts.

---

### Post by thomo2710 on 2016-11-02
> **ian-weisser said:**
> Try using the full path to wp
Cron, when it runs a job under your username, does not inherit your entire environment.

Thats it.

Thankyou Ian

---

### Post by thomo2710 on 2016-11-02
> **SeijiSensei said:**
> And don't put scripts inside the web  directory tree.  That's a security no-no.  I use /usr/local/bin or, more  often, /usr/local/sbin for maintenance scripts.


noted. thanks

---

