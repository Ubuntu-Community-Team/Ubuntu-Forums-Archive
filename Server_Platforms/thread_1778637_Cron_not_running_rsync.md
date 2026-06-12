---
title: "Cron not running rsync?"
date: 2011-06-09
forum: Server Platforms
---

### Post by skrimpy on 2011-06-09
I've written a script to pull backup files from my remote server to my local machine.  I entered the script into the crontab - I know that the cron is running the script because it has two parts.  First it pulls the remote files in, then it checks for files older than 10 days and removes those.  The cron is removing old files.

But the cron is not pulling the remote files in via the rsync command.  When I run the script manually from the terminal it works just fine, but for some reason the cronjob isn't working.  How can I get my cron daemon to run the rsync?  Am I missing a permissions issue?  I do not need to execute the script as root so it doesn't seem like that's the problem.  My local machine has the remote machine's key paired so I don't need to input a password to log into it.

Is there a log file I can/should check for an error message?

Here's my script:

```

#!/bin/sh

THEDATE=`date +%d%m%y%H%M`

rsync -a root@my.remote.ip.here:/backups/files/* offsitebackups/

find Sites/offsitebackups/milk* -mtime +10 -exec rm {} \;
find Sites/offsitebackups/nbbc* -mtime +10 -exec rm {} \;
find Sites/offsitebackups/tiger* -mtime +10 -exec rm {} \;
find Sites/offsitebackups/vahq* -mtime +10 -exec rm {} \;
find Sites/offsitebackups/db* -mtime +10 -exec rm {} \;
find Sites/offsitebackups/first* -mtime +10 -exec rm {} \;

```

---

### Post by blind2314 on 2011-06-09
> **skrimpy said:**
> I've written a script to pull backup files from my remote server to my local machine. I entered the script into the crontab - I know that the cron is running the script because it has two parts. First it pulls the remote files in, then it checks for files older than 10 days and removes those. The cron is removing old files.
 
But the cron is not pulling the remote files in via the rsync command. When I run the script manually from the terminal it works just fine, but for some reason the cronjob isn't working. How can I get my cron daemon to run the rsync? Am I missing a permissions issue? I do not need to execute the script as root so it doesn't seem like that's the problem. My local machine has the remote machine's key paired so I don't need to input a password to log into it.
 
Is there a log file I can/should check for an error message?
 
Here's my script:
 
```

#!/bin/sh
 
THEDATE=`date +%d%m%y%H%M`
 
rsync -a root@my.remote.ip.here:/backups/files/* offsitebackups/
 
find Sites/offsitebackups/milk* -mtime +10 -exec rm {} \;
find Sites/offsitebackups/nbbc* -mtime +10 -exec rm {} \;
find Sites/offsitebackups/tiger* -mtime +10 -exec rm {} \;
find Sites/offsitebackups/vahq* -mtime +10 -exec rm {} \;
find Sites/offsitebackups/db* -mtime +10 -exec rm {} \;
find Sites/offsitebackups/first* -mtime +10 -exec rm {} \;

```
 
I don't know if you've tried this yet, but put the full path to rsync in your crontab/script.

---

### Post by DaithiF on 2011-06-09
Hi,
capture stdout & stderr output from the job to a log file and inspect it afterwards for errors.
ie. amend you cron definition like so:
* * * * * /path/to/yourjob** >> ****/path/to/logfile 2>&1**

---

### Post by skrimpy on 2011-06-13
> **blind2314 said:**
> I don't know if you've tried this yet, but put the full path to rsync in your crontab/script.

Thanks blind, this appears to have been the issue - backups are running and being placed in my local directory now :)  

Sorry it took a couple of days to thank you, had out of town guests come in.  I was very pleased to check a few days after making this fix and see that the backups are downloading!

---

