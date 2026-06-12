---
title: "How to clear Apache logs?"
date: 2009-03-13
forum: Server Platforms
---

### Post by botfish on 2009-03-13
How do I clear my Apache logs?

My log/permissions/owner/group:
-rw-r--r-- 1 root root 126619976 2009-03-13 17:28 apache_access.log
-rw-r--r-- 1 root root    526194 2009-03-13 17:26 apache_error.log
-rw-rw-rw- 1 me   me           1 2009-03-13 17:49 phperror.log

I've tried:

$ sudo cat /dev/null > ./apache_access.log
-bash: apache_access.log: Permission denied

$ sudo echo " "> ./apache_access.log
-bash: ./apache_access.log: Permission denied

$ sudo echo > ./apache_access.log
-bash: ./apache_access.log: Permission denied

---

### Post by BkkBonanza on 2009-03-13
There are a few ways to rotate your logs. The way I always used was to mv the files and then do a graceful restart of apache. This seems to be recommended. To do this you move the files to some other directory like this,

mkdir old
mv apache*.log php*.log old
apachectl graceful
sleep 60
# do what you want here, like tar up the old files and send them to backup
# I send mine to Amazon S3, cheap and infinite

The graceful restart causes apache to close and re-open it's logs. The old logs will still catch some slow entries (that's why the sleep command) but new logging goes into the new files created in the current directory and the old files are left in the old directory. If you don't want them then just delete them. I use tar to archive them and then send them to S3 for backup.

---

