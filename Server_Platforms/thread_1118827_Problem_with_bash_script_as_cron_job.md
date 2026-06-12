---
title: "Problem with bash script as cron job"
date: 2009-04-07
forum: Server Platforms
---

### Post by MatsB on 2009-04-07
Hi,

For some reason my cron job does not compress all my files so I’m assuming that it’s a permission issue with the cron job. When I run the tar command manually with sudo it works ok. The cron job is added with [sudo cronjob –e]

The first file is done with the cron job and the second with sudo ./backup_script.sh
-rw-r--r-- 1 root root     90800 2009-04-07 12:40 backup-2009-04-07-0815.tar.gz
-rw-r--r-- 1 root root 150313177 2009-04-03 08:15 backup-2009-04-07-0826.tar.gz

ubuntu:~$ sudo crontab -l -u root
# m h  dom mon dow   command
0 1 * * * /etc/cron.daily/backup_script.sh


I’ve created a simple bash script that looks like this:

ubuntu:~$ ls -l /etc/cron.daily/backup_script.sh
-rwxr-xr-x 1 root root 177 2009-04-07 09:42 backup_script.sh

```
#!/bin/bash

backupdir1=/etc/
backupdir2=/home/
filename="backup-$(date '+%F-%H%M').tar.gz"

echo "Creating a backup file $filename of $backupdir."

# Make a tar gzipped backup file
tar -cvzf  "$filename" "$backupdir1" "$backupdir2”
```

---

### Post by smileypaul on 2009-04-07
Generally, by just editing /etc/crontab  .. there is an option to run script as "user"

0 1 * * * root /etc/cron.daily/backup_script.sh


the script can obviousyl be kept anywhere.. not likely that it would be kept in /etc/cron.daily

just a thought.

Hopefully that helps,

---

### Post by MatsB on 2009-04-09
Sadly it did not help to add root.
```
# m h  dom mon dow   command
0 1 * * * root /home/admin/backup_script.sh
0 2 * * * root /home/admin/test.sh

```

I'm still only getting a few files and not all in /etc/ and none in /home/

I also tried a new script but with the same result:
ubuntu:~$ ls -l

-rwxr-xr-x 1 root root 421 2009-04-09 08:19 backup_script.sh
-rwxr-xr-x 1 root root  42 2009-04-09 08:26 test.sh

test.sh
```
#!/bin/bash

tar -cvzf test.tar.gz /etc

```

---

### Post by BkkBonanza on 2009-04-09
Try adding another v to the tar command to see if extra verbose mode tells you more about what it's doing, and pipe the output to a file, like,

tar -cvvzf test.tar.gz /etc >info.txt

---

### Post by MatsB on 2009-04-09
I didn't get the > info.tx to work so I used tee instead

#!/bin/bash
tar -cvvzf test.tar.gz /etc | tee info.txt

For some reason cron doesn't even create a test.tar.gz file anymore and no info.txt. Even if I remove the tee command the job doesn't create the tar file. restarting cron with /etc/init.d/cron restart didn't help either.


ubuntu:~$ sudo crontab -l
# m h  dom mon dow   command
30 16 * * * root /home/admin/test.sh

output from /var/log/syslog
Apr  9 16:30:01 spoc06 /USR/SBIN/CRON[17821]: (root) CMD (root /home/admin/test.sh)

---

