---
title: "Deleted log files taking up huge disk space"
date: 2010-09-07
forum: Server Platforms
---

### Post by Hypnoz on 2010-09-07
My /var/ partition continues to fill up on all my servers, and it is because the logs in /var/log/apache2 or /var/log/mysql are being deleted during log rotate, but their file handles are being held open. Thus, a "du -sh /var/log" shows the correct values, but "df | grep /var" shows something much different. 

It seems that the log files rotate, however if I run "lsof | grep deleted" it returns lots of files that are no longer visible in the directory, however refuse to clear themselves off the disk.

The only way I have found to make these log files go away (and thus clear up the disk space on the partition I should have) is to restart either apache or mysql, depending on which process has huge sized log files being held open.

Is it just me, or is this a big flaw in the way linux works, that it can't figure out how to release file handle for a log so the disk space can be reclaimed? Am I doing something terribly wrong here? This is happening to me a lot lately.


Here is some output from one of my web servers so you can see what I am seeing...

root@web49:~# df -h | grep /var$
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda8             9.2G  6.1G  2.7G  70% /var


root@web49:~# du -sh /var
2.3G	/var


root@web49:~# lsof | grep deleted
init          1     root    0u      CHR        5,1                  573 /dev/console (deleted)
init          1     root    1u      CHR        5,1                  573 /dev/console (deleted)
init          1     root    2u      CHR        5,1                  573 /dev/console (deleted)
apache2    1947 www-data    2w      REG        8,8      1764     961064 /var/log/apache2/error.log.1 (deleted)
apache2    1947 www-data   10w      REG        8,8         0     961151 /var/log/apache2/ssl-error.log (deleted)
apache2    1947 www-data   12w      REG        8,8 128539106     961113 /var/log/apache2/ssl-access.log.1 (deleted)
apache2    1947 www-data   13w      REG       0,18         0      11579 /var/run/apache2/ssl_mutex (deleted)
apache2    1947 www-data   14w      REG        8,8 543490200     961080 /var/log/apache2/access.log.1 (deleted)
apache2    1947 www-data   15w      REG        8,8   1985010     961068 /var/log/apache2/rewrite.log.1 (deleted)
apache2    4048 www-data    2w      REG        8,8       252     961109 /var/log/apache2/error.log.1 (deleted)
apache2    4048 www-data   10w      REG        8,8         0     961165 /var/log/apache2/ssl-error.log (deleted)
apache2    4048 www-data   12w      REG        8,8         0     961160 /var/log/apache2/ssl-access.log (deleted)
apache2    4048 www-data   13w      REG       0,18         0      11579 /var/run/apache2/ssl_mutex (deleted)
apache2    4048 www-data   14w      REG        8,8 389837843     961103 /var/log/apache2/access.log.1 (deleted)
(continues for a long time)

root@web49:~# lsof | grep deleted | wc -l
360

---

### Post by dtfinch on 2010-09-07
What does your "/etc/logrotate.d/apache2" look like? Normally logrotate's postrotate for apache2 calls "/etc/init.d/apache2 reload" after rotating, which performs a graceful restart so that apache will close and reopen its logs. But it sounds like that's not happening.

---

### Post by Hypnoz on 2010-09-07
> **dtfinch said:**
> What does your "/etc/logrotate.d/apache2" look like? Normally logrotate's postrotate for apache2 calls "/etc/init.d/apache2 reload" after rotating, which performs a graceful restart so that apache will close and reopen its logs. But it sounds like that's not happening.

root@web49:/etc/logrotate.d# cat apache2 
```
/var/log/apache2/*.log {
	weekly
	missingok
	rotate 52
	compress
	delaycompress
	notifempty
	create 640 root logview
	sharedscripts
	postrotate
		if [ -f "`. /etc/apache2/envvars ; echo ${APACHE_PID_FILE:-/var/run/apache2.pid}`" ]; then
			/etc/init.d/apache2 reload > /dev/null
		fi
	endscript
}
```

I tried to run this command manually to see if it helped, but it seems an apache reload doesn't release the file handle, only restart does.

root@web49:/etc/logrotate.d# /etc/init.d/apache2 reload
 * Reloading web server config apache2                                                                                                                                 [ OK ] 
root@web49:/etc/logrotate.d# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda8             9.2G  6.1G  2.7G  70% /var

---

### Post by dtfinch on 2010-09-07
/etc/init.d/apache2 reload calls "apache2ctl graceful" (at least on the versions I checked, intrepid and lucid) which is documented as closing and reopening the log files. [http://httpd.apache.org/docs/2.2/stopping.html](http://httpd.apache.org/docs/2.2/stopping.html) 

I haven't found any bug reports of graceful restarts silently failing like this. Which version of Ubuntu Server are you running and is there anything unusual about your configuration that comes to mind?

---

### Post by Hypnoz on 2010-09-07
> **dtfinch said:**
> /etc/init.d/apache2 reload calls "apache2ctl graceful" (at least on the versions I checked, intrepid and lucid) which is documented as closing and reopening the log files. [http://httpd.apache.org/docs/2.2/stopping.html](http://httpd.apache.org/docs/2.2/stopping.html) 

I haven't found any bug reports of graceful restarts silently failing like this. Which version of Ubuntu Server are you running and is there anything unusual about your configuration that comes to mind?

Running Server 8.04 LTS.

It seems this happens more frequently on servers that are being hit pretty heavily on apache. I'm wondering if the increased amount of apache calls affects its ability to release logs on a graceful/reload.

---

### Post by BkkBonanza on 2010-09-08
I used to use Apache up til version 2.2. The log rotation for me always behaved gracefully. I handled my logs a bit differently and I'm just mentioning it here because it may help you figure out what's happening.

I always had a daily backup cron setup. And part of that was backing up the logs independently of logrotate. In my backup script I would move the logs to a new directory created and named by date, and then call apachectl graceful. Then sleep briefly, so the logs could release, and do a tar archive and offsite transfer (to s3).

The thing about this is when you move then logs they **keep** their open file descriptors in the new directory. And as soon as apachectl graceful has released each file, the new logs are created again in the original log directory. So you can see clearly see that new logs are opened, and the old logs are closed.

Hope this helps debug, as you can mv your logs just before logrotate and then watch how it behaves.

BTW I haven't used Apache now for a couple years. I'm super happy with Nginx now.

---

### Post by Hypnoz on 2010-09-08
BkkBonaza: Thanks for the tips I'll look into this.

I currently have this issue on one of my databases, maybe someone has an idea of how to resolve this without restarting mysql (which I really don't want to do just to clear a log file...)

root@db08:/var/lib/mysql# lsof | grep deleted
mysqld    28506    mysql    3w      REG                8,8  6183611907   20578399 /var/log/mysql/mysql-slow.log.1 (deleted)

This *deleted* log file is now 6gb and the file handle is being held open. What can I do to make this log file go away?

---

### Post by BkkBonanza on 2010-09-08
What happens when you try the FLUSH LOGS statement. It's supposed to start new logs, close the old ones.

mysqladmin flush-logs

According to the Mysql docs if you rename the log files before flushing them then the new ones will have the original name, leaving the old logs with the new names.

See below for ideas. Also max-bin-log cfg directive to start new logs when they reach some size (if using binary logs)
[http://dev.mysql.com/doc/refman/5.0/en/log-file-maintenance.html](http://dev.mysql.com/doc/refman/5.0/en/log-file-maintenance.html)

---

### Post by Hypnoz on 2010-09-16
For mysql, the mysqladmin flushlogs statement worked great!

If only there were a similar command for apache, I could sit here like a babysitter and blow all these servers noses and wipe their asses constantly a little easier.

---

### Post by jkildea on 2011-01-05
Hi,

I am having the same problem of apache2 log files (error.log) filling up my disk. I naively did a "rm error.log" and recreated the log file manually but the disk space is still not free.

Is there a bug in apache2 or is there something I should do in my configuration?

Thanks

---

