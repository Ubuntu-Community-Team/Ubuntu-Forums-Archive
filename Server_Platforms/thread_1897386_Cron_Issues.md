---
title: "Cron Issues"
date: 2011-12-19
forum: Server Platforms
---

### Post by albertramsbottom on 2011-12-19
Hi

I seem to be having a few issues with some permissions with my cron jobs.

I am logged in as root but keep getting emails about a permission denied error

Anyway, i now have the following cron jobs running but I keep getting emails with errors in them:


Line in cron:
42 0 * * * find /mnt/storevault/backup/daily/* -ctime +32 -exec rm -f {} \;

Error:
find: /mnt/storevault/backup/daily/*: No such file or directory

This directory exists but not sure about the "*" at the end, i thought this was a wildcard. This works on another server without these errors.
Also I can CD to mnt/storevault/backup/monthly no problems at all so my fstab mount is working nicely.

The other error is similar

Line in cron:
50 * * * * /usr/local/sbin/server-check.sh

Error:
/bin/sh: /usr/local/sbin/server-check.sh: Permission denied

I do not know why this would happen as i am logged in as root

Cheers for any assitance

---

### Post by SeijiSensei on 2011-12-19
> **albertramsbottom said:**
> Line in cron:
50 * * * * /usr/local/sbin/server-check.sh

Error:
/bin/sh: /usr/local/sbin/server-check.sh: Permission denied

I do not know why this would happen as i am logged in as root

Whose crontab is this?  Did you put this in root's crontab with "sudo crontab -e"?

Is server-check.sh marked executable?  If the script is owned by root, use "sudo chmod u+x /usr/local/sbin/server-check.sh" to make it executable.

---

### Post by albertramsbottom on 2011-12-19
Ok that seems to work now thanks to your advice

I dont suppose you know how to restart a cif s mount.  I have created another in my fstab file but cannot restart the server

Cheers for all your help

Paul

---

### Post by SeijiSensei on 2011-12-20
> **albertramsbottom said:**
> Ok that seems to work now thanks to your advice

I dont suppose you know how to restart a cif s mount.  I have created another in my fstab file but cannot restart the server

Cheers for all your help

Paul

```
sudo mount -t cifs -a
```

should do the trick.  If the OS complains that the share is already mounted, rerun the command adding "-o remount" at the end.

"mount -t fstype -a" tells the mount program to consult /etc/fstab and mount all (-a) filesystems of type "fstype".  Without the -t parameter, "mount -a" will attempt to mount all filesystems referenced in /etc/fstab.

What was the problem with the cron job?  Was the script not executable?

---

