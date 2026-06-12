---
title: "Ubuntu 16.04 -who is john in /etc/cron.d"
date: 2016-07-02
forum: Security
---

### Post by expatver on 2016-07-02
Still learning about Ubuntu security. I run Tiger, Eset NOD32 for linux and rkhunter. This morning around 2 Am watching htop and both Tiger and Eset taking some cpu time although I have put neither in cron for any specific system task at that hour or day. Out of curiosity I started looking at the various cron entries in /etc.  Thats when I bumped into john

/etc/cron.d/john



#
# Start john everyday at the same to try to crack the passwords. The
# second line will then later stop the process so that it doesn't
# consume system resources that are needed otherwise. You are
# encouraged to change the times.
#
# Also notice that John is 'nice'd, if you don't like this (you 
# believe that your system can run fine with john doing its work)
# just remove the 'nice' call
#
# JOHN_OPTIONS = foo bar (man 5 crontab)
#
#00 1    * * *    root    [ -x /usr/share/john/cronjob ] && nice /usr/share/john/cronjob start
#00 7    * * *    root    [ -x /usr/share/john/cronjob ] && /usr/share/john/cronjob stop

Realize that everything is commented out  but what is this used for specifically  as a cron'ed application. I searched this and found reference to John the Ripper .  What would be the purpose of something like this running in the background, check passwords to see if they are robust?

If this is a really dumb question please accept my apologies. 

Thanks 
Expat

---

### Post by TheFu on 2016-07-02
Yes. That is the purpose.

However, nothing replaces the thing on your shoulder as an aid to security.
The 2nd best thing is versioned backups.

---

### Post by expatver on 2016-07-02
TheFu

Thanks for the info. There are a lot of great tools included in Ubuntu to help lock down a system.

I run an automated back up weekly with the backup tool included in the distro.  I am going to guess  by versioned backups, this would be  a backup any time a change is made to the system i.e. when Synaptic wants to do an OS update, when a user is added or removed,  a program, or any changes made......but with some time frame as a maximum limit for intervals, yes? 

Many thanks for the interest and reply

Expat

---

### Post by mikodo on 2016-07-03
Hi,

I think TheFu may have been alluding to versioned backups as, backups that retain the earlier information before backups each time. I know he likes rdiff-backup.

                        [URL="http://rdiff-backup.nongnu.org/"]ttp://rdiff-backup.nongnu.org/

                        [/URL][https://rc.fas.harvard.edu/resources/documentation/linux/rdiff-backup/](https://rc.fas.harvard.edu/resources/documentation/linux/rdiff-backup/)

---

### Post by TheFu on 2016-07-03
I do daily, automatic, backups and retain at least 60 days of those for low-risk systems.  The amount of storage needed for this is 1.20x the original size (on average). Relatively cheap insurance.

The backups are created without "mounting" storage on the system being backed up. The backups made are validated by restoring to a system from time to time.  Since most of my systems are virtual machines, that really isn't hard to test, but the first few attempts at recovery of a new system almost always fail. Need to ensure everything needed for the restore is included in the backup process. We see restore failures in these forums all the time - please **practice a restore at least a few times with whatever tool you use.**

Don't know what the "built-in" backup tool is or how good/bad it might be. The tool that works for you, is the right tool to use. It just needs to actually restore.  Backups are 10% of the task. Restoring is the other 90% - the main point of all this effort.

---

### Post by expatver on 2016-07-07
Mikodo and TheFu

Thanks for the great information and links on backups. 

Sorry to have been so long in replying.
The  application included in the distro for backups is Deja-dup FYI.  I have tried backing up an individual file with this and it seems to work. 

Regards

---

### Post by TheFu on 2016-07-08
Before picking deja-dup, check these forums for issues with that tool. Think you want to go into it with eyes open.  Plus, deja-dup is more like the 1970s backup tools, so you'll need a schedule for weekly fulls and daily incrementals.

And while backing up 1 file is a start, it isn't anything like backing up a system that can be restored.

Just sayin'.

---

### Post by Habitual on 2016-07-08
who installed John the Ripper?
what shell does john have?

---

### Post by expatver on 2016-07-08
Seems it came  default on 16.04.

---

### Post by Habitual on 2016-07-08
Oh.

---

