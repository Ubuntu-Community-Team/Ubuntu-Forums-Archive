---
title: "Running rsync from crontab"
date: 2009-11-10
forum: Server Platforms
---

### Post by rshol on 2009-11-10
I'm running 9.10 server and trying to automate backup to a USB drive attached to the server.  My crontab line is this:

```
00 4    * * *   root    rsync -rout --modify-window=1 /home/ /media/"My Book"/backup/
```

My expectation is that this will run every day at 4 AM and copy the contents of /home to /backup on the USB drive. The rsync part of the line runs from a command prompt but with errors because it can't change groups on the USB drive which is formatted FAT32. But that does not keep anything from being copied over.  It appears not to run at all as a cron job.  What am I doing wrong/

---

### Post by drdos2006 on 2009-11-10
I cannot get crontab to work either, works from the console though.
Using 9.10 64bit. I am testing at the moment with less switches in my script to see if the switches are the problem.

---

### Post by drdos2006 on 2009-11-10
My test script.
 #!/bin/bash
sudo rsync --verbose --recursive  --archive --modify-window=1 --times --update --delete   --progress --itemize-changes --log-file=/media/sda/backup-log.txt    /media/sda/test/  /media/sdd/test

My /etc/crontab
# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user	command
17 *	* * *	root    cd / && run-parts --report /etc/cron.hourly
25 6	* * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6	* * 7	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6	1 * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
#

23   7    *    *    *   root	/bin/bash  /home/c2d-geoff/test.sh
 
My log file is not being generated and am checking on that now, however my file is being copied.

---

### Post by rshol on 2009-11-10
I am also running the 64 bit version, should have mentioned that in the OP.

---

### Post by drdos2006 on 2009-11-10
I have changed the position of the log file to first switch, removed hyphen, removed".txt" all to no avail. Still cannot get cron to generate log file but terminal  with bash there is no problem. ??
Will take time to sort out, I guess. I hope my scripts are of some benefit to you.

---

