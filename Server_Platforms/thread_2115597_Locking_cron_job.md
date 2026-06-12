---
title: "Locking cron job?"
date: 2013-02-13
forum: Server Platforms
---

### Post by GodAtum on 2013-02-13
I have the cron job which runs every 20 mins:

```
0,20,40 * * * * find /data/mysql -name "mysql-bin.*" -mmin -20 -exec cp -fp {} /data/working/mysql_backups \; >> /data/working/mysql_backups/daily_flush.cronlog 2>&1

```How do i lock the job while it is running to prevent it running itself again if it is still running after 20 mins?

Do i need to put the command in s script and use the setlock parameter like so?

[HTML]0,20,40 * * * * /usr/local/bin/setlock -n /tmp/cronlock.1234567.12345 sh -c $'/housekeeping/binlogs.sh'[/HTML]

Binlogs.sh script:
```
find /data/mysql -name "mysql-bin.*" -mmin -20 -exec cp -fp {}  /data/working/mysql_backups \; >>  /data/working/mysql_backups/daily_flush.cronlog 2>&1
```

---

### Post by hawkmage on 2013-02-13
There is nothing in cron its self to do this.  You can put the logic into the script to detect if is is running and exit before doing any processing.

---

### Post by GodAtum on 2013-02-14
> **hawkmage said:**
> There is nothing in cron its self to do this.  You can put the logic into the script to detect if is is running and exit before doing any processing.

What code could I use to do this please?

---

### Post by spynappels on 2013-02-14
You could put in a test at the start of the script along the following lines:

if output (ps -ef | grep name_of_script) != 0|NULL;
then exit 1

Exact syntax will depend on language of choice. 

Output from ps -ef command will probably be NULL if the script is not running, but check that.

---

### Post by GodAtum on 2013-02-14
> **spynappels said:**
> You could put in a test at the start of the script along the following lines:

if output (ps -ef | grep name_of_script) != 0|NULL;
then exit 1

Exact syntax will depend on language of choice. 

Output from ps -ef command will probably be NULL if the script is not running, but check that.

Thanks. So my final shell script would be:

```
#!/bin/sh
if output (ps -ef | grep binlogs) != 0|NULL;
then exit 1

find /data/mysql -name "mysql-bin.*" -mmin -20 -exec cp -fp {} /data/working/mysql_backups \; >> /data/working/mysql_backups;/daily_flush.cronlog 2>&1
```

---

### Post by schragge on 2013-02-14
In shell script this
```

if output (ps -ef | grep binlogs) != 0|NULL;
then exit 1

```
should be
```

ps -ef|grep binlogs >/dev/null 2>&1 && exit 1

```

or
```

pgrep binlogs >/dev/null 2>&1 && exit 1

```

---

### Post by SeijiSensei on 2013-02-14
I usually just have the script write a lock file somewhere like /tmp and check for its existence when the script runs.  When the script completes it deletes the file.  You can include some code to send you an email if the script fails because it encounters the lock file.  Something like:

```

#!/bin/sh
LOCKFILE=/tmp/scriptlock

if [ -s $LOCKFILE ]
then
   mail -s 'script cannot run' you@example.com
   exit 1

else
   touch $LOCKFILE 
   do stuff
   rm -f $LOCKFILE
   exit 0

fi

```

---

### Post by spynappels on 2013-02-14
> **spynappels said:**
> 
Exact syntax will depend on language of choice. 


So you need to look at the manpages for test or even Google "if then Bash" and format the test statement to give you the result you want.

---

