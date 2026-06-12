---
title: "Ubuntu Filesystem backup and upload to Mega script"
date: 2016-09-28
forum: Server Platforms
---

### Post by rhandy2 on 2016-09-28
Hello

I´m beginner and I try to create on shell script to backup my filesystem and upload to Mega

```

#!/bin/sh##### path to cron work
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/root/filesysbackup.sh

tar -cvpzf /FileSysBackup/backup.tar.gz --exclude=/path/backup.tar.gz --exclude=/path --one-file-system /
rm -f /path/backupsplit/*
split -d -b 200m /path/backup.tar.gz /path/backupsplit/backup.tar.gz
rm -f /FileSysBackup/backup.tar.gz
LOCALDIR="/path/backupsplit"
REMOTEDIR="/Root/path"
LOG="/var/log/mega.log"
hostname=`hostname`

# UPLOAD TO MEGA
MEGACOPY='megacopy'
MEGARM='megarm'
BACKUP_TIME=`date +%c`
# delete files on remote server
for i in $REMOTEDIR; do
$MEGARM  $i
done
# Run the synchronization to Mega
megamkdir /Root/path
SYNC=`$MEGACOPY --no-progress --local $LOCALDIR --remote $REMOTEDIR`
exit 0

```


My problem is when it finish create files and split do not upload to Mega.

If run only this script after files created it uploads!!
```
LOCALDIR="/path/backupsplit"REMOTEDIR="/Root/path"
LOG="/var/log/mega.log"
hostname=`hostname`
MEGACOPY='megacopy'
MEGARM='megarm'
BACKUP_TIME=`date +%c`

# delete files on remote server
for i in $REMOTEDIR; do
$MEGARM  $i
done
# Run the synchronization to Mega
megamkdir /Root/path

SYNC=`$MEGACOPY --no-progress --local $LOCALDIR --remote $REMOTEDIR`

exit 0
```

---

### Post by TheFu on 2016-09-28
**tar** is not an appropriate whole-system backup tool. It is very inefficient without lots of custom stuff. There are 50 better options.

Use a modern backup tool.

Since you plan to upload the backup to the cloud, you **must** encrypt it.  That means something like **duplicity** should be used.

It is generally considered a best practice to have a local backup AND a remote backup.  So ... have duplicity make the local backup, then use mega to copy that up to the cloud.

---

### Post by rhandy2 on 2016-09-29
Hi TheFu. thank you for your reply I never try other backup system. What is the best I can use remotely by ssh or web.

---

### Post by TheFu on 2016-09-29
> **rhandy2 said:**
> Hi TheFu. thank you for your reply I never try other backup system. What is the best I can use remotely by ssh or web.

Already answered that question (duplicity), but there are 50 options. "ubuntu backup" is the search I'd use.  There are ubuntu pages about backup options.
I don't use a tool that meets your needs - I will NOT use public cloud storage.

---

### Post by rhandy2 on 2016-09-29
Ok. Thank you!!! :-)

---

