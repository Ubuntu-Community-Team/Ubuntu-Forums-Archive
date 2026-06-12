---
title: "CronTab not executing script,  works fine manually"
date: 2011-05-09
forum: Server Platforms
---

### Post by jaes84 on 2011-05-09
I have written a simple backup script, and added it to CronTab, but it doesnt execute at all.
Here is my script: [http://pastebin.com/NiPfd4UL](http://pastebin.com/NiPfd4UL)
And my CronTab entry:

0 */2 * * * root /home/server/Scripts/backup.sh

Anyone got any ideas?

---

### Post by DaithiF on 2011-05-09
Hi, some things to check:
1. is cron running:
sudo status cron
2. is the script executable
chmod +x /path/to/script
3. you have a space between the shebang and /bin/bash in the script you posted, i don't *think* this will cause a failure, but there shouldn't be a space so you may as well remove it.
4. does the script run ok from the command line?
5. which crontab have you put this in ... /etc/crontab, or root's crontab as edited by sudo crontab -e, or another ... there are particular pitfalls associated with each.
6. capture stdout/stderr output of the job to see what errors may be reported. ie. append 
**> /path/to/some/logfile 2>&1** to your job definition

---

### Post by jaes84 on 2011-05-09
> **DaithiF said:**
> Hi, some things to check:
1. is cron running:
sudo status cron
2. is the script executable
chmod +x /path/to/script
3. you have a space between the shebang and /bin/bash in the script you posted, i don't *think* this will cause a failure, but there shouldn't be a space so you may as well remove it.
4. does the script run ok from the command line?
5. which crontab have you put this in ... /etc/crontab, or root's crontab as edited by sudo crontab -e, or another ... there are particular pitfalls associated with each.
6. capture stdout/stderr output of the job to see what errors may be reported. ie. append 
**> /path/to/some/logfile 2>&1** to your job definition

1. it is running
2. it is
3. fixed
4. yes
5.crontab -e
6. i have done *crontab entry* >> /backuplog, that file doesn't exist

---

### Post by DaithiF on 2011-05-09
the format of the cron entries in individual users crontabs (ie. those edited via crontab -e) **do not **include the name of the user (since that is already clear from the ownership of the crontab).  so take out the root field from your crontab entry.

also, in case its not obvious, if you want this to run as root then you need to **sudo crontab -e**, rather than crontab -e.  the former will edit root's crontab, the latter your own users.

---

### Post by jaes84 on 2011-05-09
THANKS SO MUCH!
adding the entry in sudo crontab -e worked!

---

### Post by jaes84 on 2011-05-09
But while i am at it, how do you remove backups older than 2 days within a script?

---

### Post by DaithiF on 2011-05-09
> **jaes84 said:**
> But while i am at it, how do you remove backups older than 2 days within a script?
using the 'ol find / -exec combo
```
 find /some/path -mtime +2 -exec rm -f "{}" \;
```

---

