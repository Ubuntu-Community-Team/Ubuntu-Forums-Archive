---
title: "Dirvish, why is one of the rows in the script not triggered!?"
date: 2023-04-11
forum: Server Platforms
---

### Post by civilpolisen on 2023-04-11
I look at my daily log file and I notice that one of the servers are not backed up.


[IMG]https://syscare.se/files/dirvish_daily-1.png[/IMG]


Maybe there is an error with the connection? It happens. So... I look in the backup folder that Dirvish supports.

[IMG]https://syscare.se/files/dirvish_daily-2.png[/IMG]

I see! Dates are missing! There are no logfiles to look at because the script for this server wasn't even triggered!

I look in the config-file.

[IMG]https://syscare.se/files/dirvish_daily-3.png[/IMG]

That's odd! Only this server is failing to execute! Why could that be!? 
My river of ideas just run dry,,,!
How could it be!?

---

### Post by TheFu on 2023-04-11
The size is huge.  Perhaps the program has a timeout period or a monitoring tool sees it running for too long and kills it?

---

### Post by civilpolisen on 2023-04-12
The backup begins att 22:00 and is usually complete by 2 am. Sometimes at 3 am and from time to time even as late as 9:30 am the next morning.
There is much data but it should't be an obsicle and a reason for the back-up not to complete. Occationally, possible, but not on a daily basis!

Why is one row in the script missing and not executed!?

```

root@dirvishtull1:/srv/backup/odooutv12/20230411# grep -r "Backup-complete:" /srv/backup/*/20230411/summary
/srv/backup/abe/20230411/summary:Backup-complete: 2023-04-11 23:20:39
/srv/backup/amber/20230411/summary:Backup-complete: 2023-04-11 23:20:39
/srv/backup/barney/20230411/summary:Backup-complete: 2023-04-11 23:21:11
/srv/backup/bart/20230411/summary:Backup-complete: 2023-04-11 23:34:26
/srv/backup/burns/20230411/summary:Backup-complete: 2023-04-11 23:51:00
/srv/backup/cyrus/20230411/summary:Backup-complete: 2023-04-11 23:58:18
/srv/backup/edna/20230411/summary:Backup-complete: 2023-04-12 00:01:56
/srv/backup/eliza/20230411/summary:Backup-complete: 2023-04-12 00:06:58
/srv/backup/homer/20230411/summary:Backup-complete: 2023-04-12 00:14:25
/srv/backup/hugo/20230411/summary:Backup-complete: 2023-04-12 00:15:55
/srv/backup/lisa/20230411/summary:Backup-complete: 2023-04-12 00:32:03
/srv/backup/maggie/20230411/summary:Backup-complete: 2023-04-12 00:46:54
/srv/backup/marge/20230411/summary:Backup-complete: 2023-04-12 00:57:06
/srv/backup/odooutv10/20230411/summary:Backup-complete: 2023-04-12 01:08:42
/srv/backup/odooutv12/20230411/summary:Backup-complete: 2023-04-12 01:14:14
/srv/backup/odooutv13/20230411/summary:Backup-complete: 2023-04-12 01:20:16
/srv/backup/odooutv15/20230411/summary:Backup-complete: 2023-04-12 01:24:02 -- note! UTV14 is missing!
/srv/backup/odooutv16/20230411/summary:Backup-complete: 2023-04-12 01:30:22
/srv/backup/odooutv9/20230411/summary:Backup-complete: 2023-04-12 01:04:39
/srv/backup/rita/20230411/summary:Backup-complete: 2023-04-12 01:31:46
/srv/backup/stanley/20230411/summary:Backup-complete: 2023-04-12 01:38:08
root@dirvishtull1:/srv/backup/odooutv12/20230411# grep -r "Backup-complete:" /srv/backup/*/20230410/summary
/srv/backup/abe/20230410/summary:Backup-complete: 2023-04-10 22:04:16
/srv/backup/amber/20230410/summary:Backup-complete: 2023-04-10 22:04:16
/srv/backup/barney/20230410/summary:Backup-complete: 2023-04-10 22:05:13
/srv/backup/bart/20230410/summary:Backup-complete: 2023-04-10 22:15:39
/srv/backup/burns/20230410/summary:Backup-complete: 2023-04-10 22:29:49
/srv/backup/cyrus/20230410/summary:Backup-complete: 2023-04-10 22:36:02
/srv/backup/edna/20230410/summary:Backup-complete: 2023-04-10 22:39:13
/srv/backup/eliza/20230410/summary:Backup-complete: 2023-04-10 22:44:50
/srv/backup/homer/20230410/summary:Backup-complete: 2023-04-10 22:50:16
/srv/backup/hugo/20230410/summary:Backup-complete: 2023-04-10 22:50:33
/srv/backup/lisa/20230410/summary:Backup-complete: 2023-04-10 23:05:32
/srv/backup/maggie/20230410/summary:Backup-complete: 2023-04-10 23:27:54
/srv/backup/marge/20230410/summary:Backup-complete: 2023-04-10 23:38:31
/srv/backup/odooutv10/20230410/summary:Backup-complete: 2023-04-10 23:48:53
/srv/backup/odooutv12/20230410/summary:Backup-complete: 2023-04-10 23:53:46
/srv/backup/odooutv13/20230410/summary:Backup-complete: 2023-04-11 00:00:17
/srv/backup/odooutv15/20230410/summary:Backup-complete: 2023-04-11 00:04:47 -- note! UTV14 is missing!
/srv/backup/odooutv16/20230410/summary:Backup-complete: 2023-04-11 00:08:15
/srv/backup/odooutv9/20230410/summary:Backup-complete: 2023-04-10 23:45:33
/srv/backup/rita/20230410/summary:Backup-complete: 2023-04-11 00:09:44
/srv/backup/stanley/20230410/summary:Backup-complete: 2023-04-11 00:14:36
root@dirvishtull1:/srv/backup/odooutv12/20230411# grep -r "Backup-complete:" /srv/backup/*/20230409/summary
/srv/backup/abe/20230409/summary:Backup-complete: 2023-04-09 22:49:15
/srv/backup/amber/20230409/summary:Backup-complete: 2023-04-09 22:49:15
/srv/backup/barney/20230409/summary:Backup-complete: 2023-04-09 22:50:23
/srv/backup/bart/20230409/summary:Backup-complete: 2023-04-09 23:00:22
/srv/backup/burns/20230409/summary:Backup-complete: 2023-04-09 23:12:53
/srv/backup/cyrus/20230409/summary:Backup-complete: 2023-04-09 23:19:38
/srv/backup/edna/20230409/summary:Backup-complete: 2023-04-09 23:23:09
/srv/backup/eliza/20230409/summary:Backup-complete: 2023-04-09 23:27:33
/srv/backup/homer/20230409/summary:Backup-complete: 2023-04-09 23:36:00
/srv/backup/hugo/20230409/summary:Backup-complete: 2023-04-09 23:37:16
/srv/backup/lisa/20230409/summary:Backup-complete: 2023-04-09 23:49:56
/srv/backup/maggie/20230409/summary:Backup-complete: 2023-04-10 00:05:39
/srv/backup/marge/20230409/summary:Backup-complete: 2023-04-10 00:14:37
/srv/backup/odooutv10/20230409/summary:Backup-complete: 2023-04-10 00:23:26
/srv/backup/odooutv12/20230409/summary:Backup-complete: 2023-04-10 00:28:05
/srv/backup/odooutv13/20230409/summary:Backup-complete: 2023-04-10 00:32:52
/srv/backup/odooutv15/20230409/summary:Backup-complete: 2023-04-10 00:35:55 -- note! UTV14 is missing!
/srv/backup/odooutv16/20230409/summary:Backup-complete: 2023-04-10 00:38:35
/srv/backup/odooutv9/20230409/summary:Backup-complete: 2023-04-10 00:20:34
/srv/backup/rita/20230409/summary:Backup-complete: 2023-04-10 00:39:38
/srv/backup/stanley/20230409/summary:Backup-complete: 2023-04-10 00:42:43
root@dirvishtull1:/srv/backup/odooutv12/20230411# grep -r "Backup-complete:" /srv/backup/*/20230408/summary
/srv/backup/abe/20230408/summary:Backup-complete: 2023-04-09 01:28:52
/srv/backup/amber/20230408/summary:Backup-complete: 2023-04-09 01:28:52
/srv/backup/barney/20230408/summary:Backup-complete: 2023-04-09 01:30:06
/srv/backup/bart/20230408/summary:Backup-complete: 2023-04-09 02:04:54
/srv/backup/burns/20230408/summary:Backup-complete: 2023-04-09 02:48:56
/srv/backup/cyrus/20230408/summary:Backup-complete: 2023-04-09 02:55:11
/srv/backup/edna/20230408/summary:Backup-complete: 2023-04-09 02:59:33
/srv/backup/eliza/20230408/summary:Backup-complete: 2023-04-09 03:04:37
/srv/backup/homer/20230408/summary:Backup-complete: 2023-04-09 03:13:29
/srv/backup/hugo/20230408/summary:Backup-complete: 2023-04-09 03:14:46
/srv/backup/lisa/20230408/summary:Backup-complete: 2023-04-09 03:32:30
/srv/backup/maggie/20230408/summary:Backup-complete: 2023-04-09 03:49:32
/srv/backup/marge/20230408/summary:Backup-complete: 2023-04-09 04:01:12
/srv/backup/odooutv10/20230408/summary:Backup-complete: 2023-04-09 04:11:15
/srv/backup/odooutv12/20230408/summary:Backup-complete: 2023-04-09 04:17:01
/srv/backup/odooutv13/20230408/summary:Backup-complete: 2023-04-09 04:25:51
/srv/backup/odooutv15/20230408/summary:Backup-complete: 2023-04-09 04:29:38 -- note! UTV14 is missing!
/srv/backup/odooutv16/20230408/summary:Backup-complete: 2023-04-09 04:34:19
/srv/backup/odooutv9/20230408/summary:Backup-complete: 2023-04-09 04:08:12
/srv/backup/rita/20230408/summary:Backup-complete: 2023-04-09 04:35:22
/srv/backup/stanley/20230408/summary:Backup-complete: 2023-04-09 04:38:22
root@dirvishtull1:/srv/backup/odooutv12/20230411# grep -r "Backup-complete:" /srv/backup/*/20230407/summary
/srv/backup/abe/20230407/summary:Backup-complete: 2023-04-08 00:37:35
/srv/backup/amber/20230407/summary:Backup-complete: 2023-04-08 00:37:36
/srv/backup/barney/20230407/summary:Backup-complete: 2023-04-08 00:39:07
/srv/backup/bart/20230407/summary:Backup-complete: 2023-04-08 00:51:24
/srv/backup/burns/20230407/summary:Backup-complete: 2023-04-08 01:07:01
/srv/backup/cyrus/20230407/summary:Backup-complete: 2023-04-08 01:13:26
/srv/backup/edna/20230407/summary:Backup-complete: 2023-04-08 01:16:50
/srv/backup/eliza/20230407/summary:Backup-complete: 2023-04-08 01:21:21
/srv/backup/homer/20230407/summary:Backup-complete: 2023-04-08 01:28:45
/srv/backup/hugo/20230407/summary:Backup-complete: 2023-04-08 01:30:04
/srv/backup/lisa/20230407/summary:Backup-complete: 2023-04-08 01:43:35
/srv/backup/maggie/20230407/summary:Backup-complete: 2023-04-08 01:56:55
/srv/backup/marge/20230407/summary:Backup-complete: 2023-04-08 02:06:26
/srv/backup/odooutv10/20230407/summary:Backup-complete: 2023-04-08 02:15:46
/srv/backup/odooutv12/20230407/summary:Backup-complete: 2023-04-08 02:20:07
/srv/backup/odooutv13/20230407/summary:Backup-complete: 2023-04-08 02:25:35
/srv/backup/odooutv15/20230407/summary:Backup-complete: 2023-04-08 02:29:42-- note! UTV14 is missing!
/srv/backup/odooutv16/20230407/summary:Backup-complete: 2023-04-08 02:32:36
/srv/backup/odooutv9/20230407/summary:Backup-complete: 2023-04-08 02:12:25
/srv/backup/rita/20230407/summary:Backup-complete: 2023-04-08 02:33:55
/srv/backup/stanley/20230407/summary:Backup-complete: 2023-04-08 02:36:23
root@dirvishtull1:/srv/backup/odooutv12/20230411# grep -r "Backup-complete:" /srv/backup/*/20230406/summary
/srv/backup/abe/20230406/summary:Backup-complete: 2023-04-06 23:43:58
/srv/backup/amber/20230406/summary:Backup-complete: 2023-04-06 23:43:59
/srv/backup/barney/20230406/summary:Backup-complete: 2023-04-06 23:45:52
/srv/backup/bart/20230406/summary:Backup-complete: 2023-04-07 00:03:22
/srv/backup/burns/20230406/summary:Backup-complete: 2023-04-07 00:30:01
/srv/backup/cyrus/20230406/summary:Backup-complete: 2023-04-07 00:44:49
/srv/backup/edna/20230406/summary:Backup-complete: 2023-04-07 00:49:54
/srv/backup/eliza/20230406/summary:Backup-complete: 2023-04-07 01:00:43
/srv/backup/homer/20230406/summary:Backup-complete: 2023-04-07 01:18:55
/srv/backup/hugo/20230406/summary:Backup-complete: 2023-04-07 01:23:40
/srv/backup/lisa/20230406/summary:Backup-complete: 2023-04-07 01:40:02
/srv/backup/maggie/20230406/summary:Backup-complete: 2023-04-07 02:07:04
/srv/backup/marge/20230406/summary:Backup-complete: 2023-04-07 02:20:57
/srv/backup/odooutv10/20230406/summary:Backup-complete: 2023-04-07 02:45:27
/srv/backup/odooutv12/20230406/summary:Backup-complete: 2023-04-07 03:11:01
/srv/backup/odooutv13/20230406/summary:Backup-complete: 2023-04-07 03:57:53
/srv/backup/odooutv15/20230406/summary:Backup-complete: 2023-04-07 04:25:34 -- note! UTV14 is missing!
/srv/backup/odooutv16/20230406/summary:Backup-complete: 2023-04-07 04:48:37
/srv/backup/odooutv9/20230406/summary:Backup-complete: 2023-04-07 02:32:03
/srv/backup/rita/20230406/summary:Backup-complete: 2023-04-07 04:54:44
/srv/backup/stanley/20230406/summary:Backup-complete: 2023-04-07 05:06:05
root@dirvishtull1:/srv/backup/odooutv12/20230411# 

```

---

### Post by civilpolisen on 2023-04-12
It seems like this is the issue!


**dirvish does not delete lock file on some failures**

[https://bugs.launchpad.net/ubuntu/+source/dirvish/+bug/1779702](https://bugs.launchpad.net/ubuntu/+source/dirvish/+bug/1779702)

So... just to remove the lock_file inside the dirvish folder and problem solved! However, I made a new backup... but I believe kust removing the lock_file solves it all!


```
root@dirvishtull1:/srv/backup/odooutv14/dirvish# ls
default.conf  default.hist  du  lock_file
root@dirvishtull1:/srv/backup/odooutv14/dirvish# cat lock_file 
405807
root@dirvishtull1:/srv/backup/odooutv14/dirvish# rm lock_file 
```

---

### Post by TheFu on 2023-04-12
If backups take hours, I think you need a better backup tool.  I'm serious.  I used to use rsync and it was taking 10 hrs to backup all my systems.  That was unacceptable.  Switched to rdiff-backup and now backups are finished for all the systems in less than 1 hour.  

HOW a backup is accomplished matters.  Find a smarter tool.  Most daily system backups take 1-2 minutes, but it is dependent on the number of files that need to be checked.  From last night, 
```
ElapsedTime 8.38 (8.38 seconds)
ElapsedTime 7.91 (7.91 seconds)
ElapsedTime 6.16 (6.16 seconds)
ElapsedTime 2.50 (2.50 seconds)
ElapsedTime 29.48 (29.48 seconds)
ElapsedTime 49.24 (49.24 seconds)
ElapsedTime 22.13 (22.13 seconds)
ElapsedTime 7.10 (7.10 seconds)
ElapsedTime 45.36 (45.36 seconds)
ElapsedTime 167.48 (2 minutes 47.48 seconds)
ElapsedTime 79.84 (1 minute 19.84 seconds)
ElapsedTime 1349.43 (22 minutes 29.43 seconds)
```
Lots of systems here don't hold any data, so the backups are just configs to put things back.  The last system has millions of files. The actually changed data in the backup last night was less than 1 GB. Only changed data gets xferred to the backup server storage.  rdiff-backup is faster than rsync of the same data, after the first backup.

---

