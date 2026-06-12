---
title: "Daily cron jobs running at a different time in 18.04 vs. 16.04"
date: 2018-11-06
forum: Server Platforms
---

### Post by jfaberna on 2018-11-06
On my server I have 2 cron jobs I put into /etc/cron.daily for database backup and optimization. The scripts email when done with the date and time.

On Ubuntu 16.04 it ran around 7:35 am. After the 'do-release-upgrade' it runs at 12:10 am.

I always wondered why 7:35am with a /etc/crontab entry like the one below, but I really can't figure out 12:10 am based on it.

Any ideas?

25 6    * * *    root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )

Jim A

---

### Post by TheFu on 2018-11-06
Anacron controls are only within a 24 hr period.  If you want things to happen at specific times, then you need to use cron, not anacron.

The manpages for anacron and cron have more details.

---

### Post by jfaberna on 2018-11-06
What I found out elsewhere will solve my problem:

Create an override, the easy way is to
do this command:

sudo systemctl edit anacron.timer

[Unit]
Description=Trigger anacron at 07:30, as happened before the Ubuntu
18.04 upgrade.

[Timer]
OnCalendar=
OnCalendar=07:30
RandomizedDelaySec=0s
Persistent=true

---

### Post by TheFu on 2018-11-06
That doesn't alter anacron's behavior of only supporting 24 hour resolution in jobs.
I hope it works, at least for a little bit. 

If you need control to the minute, use cron.

---

### Post by jfaberna on 2018-11-07
The override didn't work as you suspected it wouldn't.  So I need some help on how to do this.  I thought cron used crontab. So I thought I had it set to run daily jobs at the right time. It seems that because anacron exist, cron will not run daily jobs.

Could you point me to some examples that would work in 18.04.  I can't have the server running my backend stuff at midnight.  Too much stuff happening at that time. I need to push it out to 6-7am.

Jim A

would a solution be to move my daily at 6am cron jobs from the /etc/cron.daily directory to $HOME and then setup a new entry in /etc/crontab to run that job at 6am?

---

### Post by howefield on 2018-11-07
Thread moved to the "*Server Platforms*" forum.

---

### Post by jfaberna on 2018-11-07
What I'm testing is the following:
1. Remove the override.conf from /etc/systemd/system that I created since it didn't work
2. Remove my commands from /etc/cron.daily and move them to $HOME
3. Add an entry into /etc/crontab of:
    25 6	* * *	root	/home/jim/optimize_mythdb ; /home/jim/mythtv-backup

Does this seem like it would run the optimize_mythdb and mythtv-backup commands at 6:25 AM every morning??

Jim A

---

### Post by TheFu on 2018-11-07
cron.daily/ scripts are run by anacron.
If you use any of the other crontab methods .... **/etc/crontab**, **crontab -e** or **sudo crontab -e**.  Cron has slightly different file formats - /etc/crontab is different from the others.  In general, running backups under a non-root account looses important information necessary to restore a working system.  Owership, groups, and permissions are 50% of the restore. It isn't just about having the data.

Things that run as root need to be held in a root-only location.  Don't let a normal userid have write control over those scripts/files.
I put this into all my crontab files as a reminder for the file fields:
```
# .---------------- minute (0 - 59) 
# |  .------------- hour (0 - 23)
# |  |  .---------- day of month (1 - 31)
# |  |  |  .------- month (1 - 12) OR jan,feb,mar,apr ... 
# |  |  |  |  .---- day of week (0 - 6) (Sunday=0 or 7)
# |  |  |  |  |
# *  *  *  *  *  command to be executed
15 1  *  *  * /root/bin/backup-to-rom.sh
```

For example. This is in the crontab for root - sudo crontab -e

I don't touch /etc/crontab. I have a few reasons for that, learned over the decades doing admin work.

---

### Post by jfaberna on 2018-11-07
I understand your concerns about running as root. My scripts regardless of where located will fail if not run as root.  I think I have setup the entry in /etc/crontab to do that:

25 6	* * *	root	/home/jim/optimize_mythdb ; /home/jim/mythtv-backup

to me this means have root run /home/jim/optimize_mythdb followed by /home/jim/mythtv-backup at 6:25am everyday.

Will this work?

Jim A

---

### Post by TheFu on 2018-11-07
Some things, like backups, need to run as root.  That wasn't my point.  

You can check the manpage for crontab to see the required fields for an entry.  
```
$ man -s 5 crontab
``` will get you to the crontab file format manpage for YOUR system. I don't have any 18.04 here, so I can't look up the answer. The file format probably hasn't changed, but IDK.

I've never seen a compound statement, like you are using above, in any crontab.  Put those 2 commands into a file in /root/bin/ ... and move both of those other scripts into there too, then call that new script from the crontab.  Don't have root scripts in a normal userid's HOME. Poor security choice.

Already showed how I do backups above.

---

### Post by jfaberna on 2018-11-07
Thanks for your help.  This server is behind 2 firewalls and only has VPN access from the internet.  I'm this only user and all other computers in the house connect to a media streaming app. Based on this I'm satisfied with the security I have setup. 

My previous methods of running my daily optimizing and backups worked at the correct time.  The problem is Ubuntu 18.04 changed from Ubuntu 16.04.  Could be a bug, or it could be they changed it to screw with me.

I've setup a test case using the methods you suggested. I'll see what happens overnight.

Jim A

---

### Post by jfaberna on 2018-11-08
> **jfaberna said:**
> I understand your concerns about running as root. My scripts regardless of where located will fail if not run as root.  I think I have setup the entry in /etc/crontab to do that:

25 6	* * *	root	/home/jim/optimize_mythdb ; /home/jim/mythtv-backup

to me this means have root run /home/jim/optimize_mythdb followed by /home/jim/mythtv-backup at 6:25am everyday.

Will this work?

Jim A

This worked, but I'm concerned about having it continue to work through upgrades. I'm going to test using systemd override files which seems to be more main stream than modifying critical system files.

Thanks for the help, I'm going to mark this as solved.

Jim A

---

### Post by TheFu on 2018-11-08
Happy you found a solution that works.  But if you used the root crontab as suggested above, those issues and others go away.  Just be certain to add the different crontabs to any backups.  Use **crontab -l **to get them.

Systemd is still new and still changing.  Eventually, it will be proven bug free enough, but IMHO it isn't yet.

---

