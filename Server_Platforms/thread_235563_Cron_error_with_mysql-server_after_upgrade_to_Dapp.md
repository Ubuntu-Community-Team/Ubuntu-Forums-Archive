---
title: "Cron error with mysql-server after upgrade to Dapper"
date: 2006-08-13
forum: Server Platforms
---

### Post by cpbl on 2006-08-13
I just upgraded a Breezy Server to Dapper.
Now I get emails from root every day saying:

```

Subject: Cron <root@sr-219> test -x /usr/sbin/anacron || run-parts --report
    /etc/cron.daily

/etc/cron.daily/mysql-server:
ERROR 1373 (HY000) at line 1: Target log not found in binlog index
run-parts: /etc/cron.daily/mysql-server exited with return code 1

```

Can anyone interpret this for me?

There is no explanation from Google, although the mysql forum says, cryptically:
> 
If you change this line in /etc/cron.daily/mysql-server
filename=`tail -n $KEEP_BINARY_LOGS $tmp | head -n 1`
change it to
filename=`tail -n $KEEP_BINARY_LOGS $tmp | head -n 1 | awk '{print $1}'`

This is due to the SHOW MASTER LOGS; command now printing out file size as well as the file name for the log files.


Thanks!

---

### Post by sjpwong on 2006-08-15
> **cpbl said:**
> 
```

Subject: Cron <root@sr-219> test -x /usr/sbin/anacron || run-parts --report
    /etc/cron.daily

/etc/cron.daily/mysql-server:
ERROR 1373 (HY000) at line 1: Target log not found in binlog index
run-parts: /etc/cron.daily/mysql-server exited with return code 1

```




Thank-you, your cryptic change fixed the problem for me :-)  If you insert an 'echo ${filename}' after the line in the shell script that assigns filename then you will see that the filename has a number after it, not just the filename.  This breaks the next command to remove all logs prior to that.

I'll file this as a bug if it isn't already there.

Strange that this bug is still there...

---

### Post by sjpwong on 2006-08-15
Here's the relevant launchpad entry, note that there are some obseleted files that should have been removed by the upgrade.

[https://launchpad.net/distros/ubuntu/+source/mysql-dfsg-5.0/+bug/40705](https://launchpad.net/distros/ubuntu/+source/mysql-dfsg-5.0/+bug/40705)

---

