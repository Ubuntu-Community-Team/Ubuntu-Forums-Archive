---
title: "crontab"
date: 2010-12-13
forum: Server Platforms
---

### Post by jovemac on 2010-12-13
Dear all!

I am using ubuntu server 10.10 to run a php mysql application. Tried to create a cronjob for automatic backup of mysql database. Tried creating the script as below:

> 

#!/bin/bash
mysqldump -u root -ppassword databasename > /path/database.sql
mount /dev/sdb1 /mnt/usb
mysqldump -u root -ppassword databasename > /path/database.sql
umount /dev/sdb1



chmod 777 filename.

Its a multipurpose that the database file is saved in both external drive and also in the hdd.

I saved it and executed from the command prompt. It worked fine.

Added to the crontab by typing crontab -e

> 

30 * * * * /bin/sh /path/filename

in such a way to take backup every 30th minute of each hour round the clock all days.

crontab successfully added.

After that there is no result. No backup is happening. 

Please advise.

Regards - Jo

---

### Post by chrislynch8 on 2010-12-14
Did you set the cron up under root? crontab -e -u root.

Is the Cron running? can you see it in syslog or cron.log

You don't need the /bin/sh statement as the paths are defined for crontab. 

Try adding 
30 * * * * /path/to/file >> /var/log/cronbackup.log 2>&1

This logfile will contain any output from you script, these might have the reason it is not working.

Rgds
Chris

---

### Post by CharlesA on 2010-12-14
Don't use sh if you are telling it to use bash.

Make sure the script has execute permissions.

You might also need to include the full path to mount and mysqldump, but I'm not sure on that.

---

### Post by karlson on 2010-12-14
> **jovemac said:**
> 
chmod 777 filename.


Given that this is going to run as root you don't want to set permissions to 777.

You want to do something like:

chmod 711 filename 

or

chmod 755 filename

Also don't put a /bin/sh into crontab, making the script executable will do the trick.

Also you want to call the crontab script:

30 * * * * /path/filename > /logpath/filename.log 2>&1

Also,

Use full paths to mysqldump and mount and umount.

---

### Post by arrrghhh on 2010-12-14
I would ensure the script does its job before putting it in cron as well... once you know you can sudo /path/script and it functions as you expect, then try to shoehorn it into cron ;)

---

