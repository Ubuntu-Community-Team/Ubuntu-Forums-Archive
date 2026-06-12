---
title: "Backup Script Log File (rsync help)"
date: 2011-03-07
forum: Server Platforms
---

### Post by idny on 2011-03-07
Hello,

I am running Ubuntu Server 10.10 and i currently have a script that backs up my samba share each day at 1AM.
The scripts looks like:

> #!/bin/bash
#
# Simple Backup Script
#
# This tells the script to grab the date from the system.
DATE=$TODAY(date)
echo Backup started...'date'
rsync -av /mnt/ARRAY/tech/* /sbackup/
echo "Backup finished at " `date` >> $/sbackup/backup.log
exit 0
# End of script

My problem here is i want the script to print the files that were copied/backup up into the backup.log
Im guessing you need to pipe the data from rsync somehow? How would I go about getting this information into the log?
Thanks

---

### Post by BkkBonanza on 2011-03-07
You could add a pipe on the rsync command or better yet to capture the whole script output add it in the cronjob line, eg.

* 1 * * * /path/to/script >>/path/to/backup.log

The >> pipe symbol will append output to that file each time it runs.

If you want error info also logged then add **2>&1** on the end. This pipes stderr (file 2) also to stdout (file 1).

---

### Post by idny on 2011-03-09
Thanks BkkBonanza
Worked well, Got the crontab passing the whole output from the script to the log.

---

