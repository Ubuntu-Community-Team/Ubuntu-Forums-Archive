---
title: "A bundle of command line for crontab"
date: 2010-04-10
forum: Server Platforms
---

### Post by tw32029 on 2010-04-10
Hi there, I was trying to backup mySQL file in my server daily.

Is there anyway that we could generate a bundles of command in the below method?

/etc/rc.d/init.d/mysqld stop  #stoping mysql
cd /home/mybackup            #change directory...
tar -cvf <myBackupfile.tar> /var/lib/mysql/myDB/*     #create a tar file

# when it is done...
/etc/rc.d/init.d/mysqld start

And I dont think putting all these line in crontab is the proper way of doing it..

Is there any way I can write the above code in one file and execute it in the crontab:confused:

---

### Post by minaev on 2010-04-10
Write a backup script and call it from crontab.

---

### Post by sprouty on 2010-04-10
Hi,

I have the following script run every night on my database:
[PHP] 
#!/bin/sh
DAY=`/bin/date +%Y%m%d`
mysqldump DATABASE -u USERNAME -pPASSWORD > /storage/backup/mysql.$DAY.sql
[/PHP] 

Hope it helps.

Cheers,

Sprouty

---

### Post by tw32029 on 2010-04-11
minaev, sprouty

Thanks for the info...and sharing for codes....

Now it seems working fine and crontab are clean once again...

---

