---
title: "Timeshift Schedule"
date: 2018-01-19
forum: Ubuntu/Debian BASED
---

### Post by TechnoJunky on 2018-01-19
I have an older computer and when Timeshift runs, it is pretty useless until it finishes. I see how to change it from daily to weekly, etc, but doesn't allow you to change the time of day that it runs. It always wants to run at about 6 AM, which is a time that I am always on my computer. I'd much prefer it to run in the middle of the night instead. Can anyone tell me how to change that?

---

### Post by TheFu on 2018-01-19
I don't use timeshift, but suspect it is using anacron to control execution time. anacron tries to run daily jobs around 7:30a here.
/etc/cron.d/anacron has a setting that controls the daily start time.  Change that.

Doing this will alter when **all** daily, weekly, monthly jobs controlled by anacron run, so beware.

If you want more control, use cron or use a different backup tool.  Back-In-Time uses a similar idea and supports taking hourly snapshots, which would be quicker since fewer files would change every hour.  Or you can use a shell backup tool which is much more flexible.

OTOH, if this is already working and meets your needs, excellent.

---

### Post by TechnoJunky on 2018-01-21
I just switched to Bodhi Linux, reinstalled and Timeshift.  It's run once since the install.  I went to the cron.d directory but don't see a file anacron.  There is a file called timeshift-hourly, but nothing about the start time.  I'll see what I can find using cron and keep Back-In-Time in mind if I can't get this to work the way I want.

---

### Post by TheFu on 2018-01-21
Don't know anything about Bodhi Linux. Sorry.  Maybe it doesn't use anacron?

---

### Post by TechnoJunky on 2018-01-23
Bodhi is a distribution that uses Ubuntu 16.04 for the base and it's own version of Enlightenment for the desktop.  I believe that it would still use Anacron, if I had anything setup in it.  I am starting to believe that Timeshift uses something else for scheduling, but don't know what yet.

---

### Post by TheFu on 2018-01-23
cron?

---

### Post by vasa1 on 2018-01-23
From [https://github.com/teejee2008/timeshift](https://github.com/teejee2008/timeshift)> Timeshift requires very little setup. Just install it, run it for the first time and take the first snapshot. Cron job can be enabled for taking automatic snapshots of the system at regular intervals. The backup levels can be selected from the Settings window.
Also:> Unlike similar tools that are scheduled to take backups at a fixed time of the day, Timeshift is designed to run once every hour and take snapshots only when a snapshot is due. This is more suitable for desktop users who keep their laptops and desktops switched on for few hours daily. Scheduling snapshots at a fixed time on such users will result in missed backups since the system may not be running when the snapshot is scheduled to run. By running once every hour and creating snapshots when due, Timeshift ensures that backups are not missed.
What does ```
grep -r timeshift /etc/cron*
```show?

---

### Post by TheFu on 2018-01-23
Could also be in the root crontab ...  **sudo crontab -l** will show that.  Cron has about 8 different locations for jobs to be configured. Usually they end up in /etc/crontab or cron.d/ or cron.hourly/ or cron.daily/ or ... , but not always.

---

### Post by TechnoJunky on 2018-01-27
```
grep -r timeshift /etc/cron* produces /etc/cron.d/timeshift-hourly:0 * * * * root timeshift --check --scripted
```
```
sudo crontab -l
```produces ```
no crontab for root
```

---

### Post by TheFu on 2018-01-27
The cron.d/ directory is where scripts are placed that "might" be used for crontabs as desired.
The name of the file "timeshift-hourly" means nothing.  Put that line into /etc/crontab and send the -HUP signal to the crontab process to force it to re-read the crontab file.

If you do that, it will  run at the top of every hour. You might want it to run at a different minute during the hour. A time when the system isn't as busy, say 23 min after the hour?  ```
$ man -s 5  crontab
``` explains the format of that file so you can modify it safely.  It also explains how to run once a day at a time you specify.

If you need more details, [https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

---

### Post by sid5432 on 2018-05-19
The cron entry in /etc/cron.d/timeshift-hourly sets up the system to  check the timeshift setting every hour; the action it takes is  determined by the setting in /etc/timeshift.json.

My timeshift  setting does a daily backup. What seems to happen is that timeshift  decides to do a backup every 24 hours, at the hour of the day when you  created your first backup. Thus if you created your first backup at 10am  in the morning, your system runs a daily backup everyday at 10am, which  is probably not the most convenient time for the system to be busy. I  assume that for other schedules (weekly or monthly, etc.), the time of  day when the backup occurs will also be at 10am.

I haven't looked  into the code to figure out if there is any way to change this behavior  (or specify/change the hour of the day the backup occurs). The obvious  solution is to create your first backup at the time of day when you  least want to be working. A better way is to create a one-time crontab  entry to do this (with the command line "timeshift --create -scripted").  But turn off the timeshift scheduling while you are waiting for the  first timeshift backup to be created (presumably in the middle of the  night). The next day, once the timeshift backup is created, remove the  crontab entry, and then turn on the timeshift scheduling.

If you  already have backups created, creating a backup in, say 3am in the  morning, doesn't change the normal backup schedule. So if your regular  backup is at 10am, even though you created a backup at 3am, the next  time 10am rolls around, timeshift will still run a backup. The only to  change this seems to be to first delete all existing backups.

There's  one more wrinkle to this: if you turn off your computer for an extended  period of time and miss a couple of hourly checks, the next time you  turn on the computer, it seems that timeshift will create a backup as  soon as the hour rolls around (so your computer gets really busy almost  as soon as you turn it back on).

---

### Post by TheFu on 2018-05-19
When any cron script runs is 100% predictable.
It just depends on which cron  method is used. All of them can be modified.

Anacron is actually run by cron and it sets up when all "daily" or weekly or monthly or yearly tasks will be run.   On 90% of my systems, daily anacron runs at 6:25am, but on 1 system, it is 7:26am. That is controlled in the /etc/crontab file.  No magic.

Running a task on any time that is a mod 5 minutes is probably not optimal, since  :00, :05, :10,:15 .... you get the idea ... is when most installed programs will setup their cron entries. Really don't want multiple, I/O heavy tasks, running concurrently, if avoiding that is possible.

---

