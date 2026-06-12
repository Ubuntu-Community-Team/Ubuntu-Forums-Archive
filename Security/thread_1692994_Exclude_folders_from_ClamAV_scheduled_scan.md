---
title: "Exclude folders from ClamAV scheduled scan"
date: 2011-02-22
forum: Security
---

### Post by kevpatts on 2011-02-22
Hey all,

I have network shares automounted in /media and I want to exclude them from my automatic scheduled ClamAV scan in Maverick. How do I do this? I can't find any CRON link or script that actually starts the scan. Is it the Daemon that does this?

Kevpatts

---

### Post by SeijiSensei on 2011-02-24
Are you saying there is an automated scan running but you can't find it?  First, run "sudo grep CRON /var/log/syslog" to see all the log entries from the cron daemon.  You should also check all the possible locations where a cron job might be run:  /etc/crontab, /etc/cron.*, and /var/spool/cron.

If, as I suspect, there is no scheduled job, you can script your own like this:

```
#!/bin/bash

DIRS="/home /stuff [etc.]"

for d in $DIRS
do
    clamscan $d | grep -v OK >> /var/log/clamscan 2>&1
done

exit 0

```

Put the directories you want to scan in the DIRS list.  Only files that don't pass muster will be reported to /var/log/clamscan.

Create the script with an editor like nano using sudo.  Save it to a directory like /usr/local/sbin and make it executable with "chmod a+x /path/to/the/script".  Then create a symbolic link to the file in /etc/cron.daily like this:

```

cd /etc/cron.daily
sudo ln -s /path/to/the/script

```

 It will run every night.

---

