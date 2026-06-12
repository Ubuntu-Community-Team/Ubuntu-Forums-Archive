---
title: "How to set up  /etc/systemd/journald.conf ? Feedback!"
date: 2024-04-12
forum: Server Platforms
---

### Post by civilpolisen on 2024-04-12
/etc/systemd/journald.conf  

I'm about to go through all servers to reduce space. Mainly because our back-up if full and I see no point in saving log files for future generations...!
I've discovered that the journal log takes up some 3.9 to 4 GB on every server and for the past 5+ years at this company we've never used that log... Not that I know of!
Backing up some 35-40 servers, that's quite much data!

As for now, I've edited the journald-conf-file on every computer to the following... and I've looked for advice on Internet about these things.
I want some logging, but only a smaller part! (The file is written as default, no spacing,  and without the five EDIT -marks as I just added for this forum posting!)

```

#  systemd is free software; you can redistribute it and/or modify it
#  under the terms of the GNU Lesser General Public License as published by
#  the Free Software Foundation; either version 2.1 of the License, or
#  (at your option) any later version.
#
# Entries in this file show the compile time defaults.
# You can change settings by editing this file.
# Defaults can be restored by simply deleting this file.
#
# See journald.conf(5) for details.

[Journal]
#Storage=auto
#Compress=yes
#Seal=yes
#SplitMode=uid
#SyncIntervalSec=5m

RateLimitIntervalSec=0s     <<-- EDIT
RateLimitBurst=0 <<-- EDIT
SystemMaxUse=500MB <<-- EDIT

#SystemKeepFree=
#SystemMaxFileSize=

SystemMaxFiles=60 <<-- EDIT

#RuntimeMaxUse=
#RuntimeKeepFree=
#RuntimeMaxFileSize=
#RuntimeMaxFiles=100
#MaxRetentionSec=

MaxFileSec=1month <<-- EDIT

#ForwardToSyslog=yes
#ForwardToKMsg=no
#ForwardToConsole=no
#ForwardToWall=yes
#TTYPath=/dev/console
#MaxLevelStore=debug
#MaxLevelSyslog=debug
#MaxLevelKMsg=notice
#MaxLevelConsole=info
#MaxLevelWall=emerg
#LineMax=48K
#ReadKMsg=yes


```

---

### Post by TheFu on 2024-04-12
Is there a reason you don't have all logs sent to a central logging server for important analytics and security reviews?  If you are the admin and not reviewing logs daily, ouch!  I can't imagine that.  Every week or two, I see new attacks against my systems and need to modify what types of traffic are allowed in.  

Their is a manpage for the journald.conf file.  That's where I'd look to make my decisions. It is well documented.
```
JOURNALD.CONF(5)                          journald.conf                          JOURNALD.CONF(5)

NAME
       journald.conf, journald.conf.d, journald@.conf - Journal service configuration files
...

```
You probably know this already.  Posted for lurkers to see over the next 10 yrs.

---

### Post by civilpolisen on 2024-04-15
Thank you for your valuable posting!
We don't really have a "well thought of log strategy" as of to this date. Not in the sense you refers to.
The reason I'm diving in to the log files are that the dirvish back-up is not working since there's "no space left on device".
So... instead of expanding the virtual server that acts like a back-up server, wish is possible, I thought of reducing the back-up volumes.

We have some huge data volumes as I see no reason to have! The LDAP server is 173 GB in the back-up, while the server itself is allocate to more reasonable 20 GB!
I enclose the back-up view below.

My first priority now is to reduce the storage of logs we never need or look at.
We had a discussion about these things last Friday, (April 12), and at this time we don't have a routine to look at the logs.
1. What's in the log.
2. As you suggest, who's visiting us.

I'm not that skilled yet that I can do all these things all by myself and all alone! My boss, however, is one of the most skilled Unix / Linux / Ubuntu hackers that is!
Last Friday we spoke about getting more detailed attention to the logs...

Below is the LDAP server. The files varies a lot! We turned on the extra logging at the end of last year. We recently turned it off.
I still think 900 MB a day is too much... but I can live with that. 

```
root@dirvish:/srv/backup/ldap-server# du -sh *
6,9G    20221007
3,0G    20230101
3,0G    20230402
2,0G    20230507
2,7G    20230604
2,1G    20230702
7,6G    20230806
2,1G    20230903
11G    20231001
1,6G    20231105
723M    20231203
2,7G    20240107
14G    20240121
14G    20240128
15G    20240204
14G    20240211
14G    20240218
15G    20240225
15G    20240303
3,1G    20240310
2,0G    20240317
2,3G    20240324
3,0G    20240331
2,9G    20240401
2,6G    20240402
2,8G    20240403
2,3G    20240404
1,4G    20240405
1,2G    20240406
1,1G    20240407
1,1G    20240408
1002M    20240409
1,1G    20240410
1007M    20240411
885M    20240412
871M    20240413
890M    20240414
76K    dirvish
```

---

### Post by TheFu on 2024-04-15
Why backup logs at all, especially if you don't look at them?  Backups don't need to be all or nothing.  Be selective. Get the stuff you need only.
For example, my email gateway server doesn't really have any data. It is just the in/out gateway for SMTP traffic to be filtered/dropped.  The backups for it are only that is needed to recreate the server quickly.

```
# /usr/bin/rdiff-backup --list-increment-sizes spam2
        Time                       Size        Cumulative size
-----------------------------------------------------------------------------
Mon Apr 15 00:03:28 2024         3.89 MB           3.89 MB   (current mirror)
Sun Apr 14 00:03:24 2024         1.27 KB           3.90 MB
Sat Apr 13 00:03:24 2024         1.15 KB           3.90 MB
Fri Apr 12 00:03:23 2024         1.46 KB           3.90 MB
Thu Apr 11 00:03:24 2024         1.27 KB           3.90 MB
Wed Apr 10 00:03:24 2024         1.32 KB           3.90 MB
....
Thu Apr 20 00:03:20 2023         1.39 KB           4.42 MB
Wed Apr 19 00:03:18 2023         1.25 KB           4.42 MB
Tue Apr 18 00:03:29 2023         1.81 KB           4.42 MB
Mon Apr 17 00:03:19 2023         1.68 KB           4.42 MB
Sun Apr 16 00:03:19 2023         1.27 KB           4.42 MB
```

You get the idea.  That gateway is a high-risk server since it is directly on the internet.  I have 366 days of versioned backups.  All that needs only 4.5MB of space because I'm selective.  To recreate it, including the OS install, is about 20 minutes of my time.

Of course, the real email server is much larger and will take longer to restore - probably 45 minutes. That email server used by the end users isn't on the internet and it is only available through a VPN connection.

You do now how to limit the size of all logs, right?  There is seldom any reason for a log to be over 100MB in size, unless you are specifically researching some issue.

---

### Post by civilpolisen on 2024-04-16
Thank  you for the reply!
I have two alternatives. Ask for more space or limit the need of space. There is much more space available but that's not much of a challenge!
That's why I write here instead! To try to limit the need of space instead!

I don't check the logs but I would love to, if I knew how to do it and what to look for!

I'm not sure how many servers we have online, with static IP, but it must be some 30 servers... 

So... one way to reduce the logging is to edit the journald.conf -file, as described in the first post.
I believe we'll be heading for two alternatives. Greater logging with servers on Internet and next to none logging with internal servers aimed at development.
I shall study the documentation as you described as helpful in the second post!

Here's one. [https://www.freedesktop.org/software/systemd/man/latest/journald.conf.html](https://www.freedesktop.org/software/systemd/man/latest/journald.conf.html)

---

### Post by civilpolisen on 2024-04-16
[https://ubuntu.com/training](https://ubuntu.com/training)

> 
Ubuntu Server Administration
Basic on-site Ubuntu Server training

A three-day hands-on course at your premises for up to 15 students, that teaches you how to install and administer Ubuntu Server.

I think i can handle that part fairly well! At least to cover our main needs. Not all needs, it's true!
We recently had a server black-out and it ended up being a raid-issue...! Or a disk issue. 
That's heavy for me!

I need a course or training in how to read logs!
I believe there are information out there... I just need to find it!

---

### Post by TheFu on 2024-04-16
> **civilpolisen said:**
> Thank  you for the reply!
I have two alternatives. Ask for more space or limit the need of space. There is much more space available but that's not much of a challenge!
That's why I write here instead! To try to limit the need of space instead!
Four alternatives.  
3. Limit the space needed  AND add a little more.
4. Limit the space needed significantly AND reduce the storage provided.

> **civilpolisen said:**
> I don't check the logs but I would love to, if I knew how to do it and what to look for!

Did you google "ubuntu log files"   There are how-to guides all over the place.  Any you don't need to limit it to ubuntu, since all Linux versions use similar logging methods and locations.

> **civilpolisen said:**
> 
I shall study the documentation as you described as helpful in the second post!

Here's one. [https://www.freedesktop.org/software/systemd/man/latest/journald.conf.html](https://www.freedesktop.org/software/systemd/man/latest/journald.conf.html)
You should always use the local manpage for documentation first.  That's because it is written for the exact versions of the software ON-THE-SERVER TODAY, not what might be there in 2 yrs, which is what that link has.

Also, besides journald.conf, many distros still convert those to regular text log files, so you'll want to configure logrotate.  That's in /etc/logrotate.d/ with plenty of examples.

Nobody is great at log files until they start reading them, getting used to reading them and learn what is unusual, errors, warnings, and normal stuff.  Practice and experience.  Additionally, I use **logwatch** to get a daily report of the most important system log entries through a daily email about each system.  I've customized parts of the output for my needs.  Customization is built-into logwatch configs, if you choose to use it.

---

