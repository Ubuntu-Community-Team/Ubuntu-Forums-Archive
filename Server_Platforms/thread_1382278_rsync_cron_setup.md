---
title: "rsync cron setup"
date: 2010-01-15
forum: Server Platforms
---

### Post by kwickcut on 2010-01-15
Hello all i want to run rsync with a cron do i do not have to do it each night manually.

i have the script i use now through command line


```
cd /backups
files=$(find /backups -maxdepth 1 -mtime +14)

for x in $files

do
        echo "deleting ${x} ... "
        rm -rf ${x}
        echo
done

``` 


how would i make this a cron that would run every night say at midnight


thanks


kwick

---

### Post by Ilalmi on 2010-01-16
[http://help.ubuntu.com/community/CronHowto](http://help.ubuntu.com/community/CronHowto) should show you how to do it.

---

### Post by DaithiF on 2010-01-19
also, you could simplify your script by performing the delete via the find command itself, so:
```
find /backups -maxdepth 1 -mtime +14 -exec rm -rf {} \;
```

---

