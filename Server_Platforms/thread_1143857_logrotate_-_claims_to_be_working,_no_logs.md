---
title: "logrotate - claims to be working, no logs"
date: 2009-04-30
forum: Server Platforms
---

### Post by edpatterson on 2009-04-30
In an attempt to get a larger audience I have removed squid from the picture and am using files that anyone who is interested can duplicate.

I created a log file in an existing directory
  [FONT="Courier New"]**ls /bin > /tmp/log/bin.log**[/FONT]
Then I created a logrotate config file name rotate in the same directory
[FONT="Courier New"][B]/tmp/log/*.log {
  rotate 10
  missingok
  sharedscripts
}[/B][/FONT]

Next I attempted to rotate the log
[FONT="Courier New"]**logrotate -d -f rotate**[/FONT]
The following was displayed on the screen
[FONT="Courier New"][B]
reading config file rotate
reading config info for /tmp/log/*.log

Handling 1 logs

rotating pattern: /tmp/log/*.log  forced from command line (10 rotations)
empty log files are rotated, old logs are removed
considering log /tmp/log/bin.log
  log needs rotating
rotating log /tmp/log/bin.log, log->rotateCount is 10
renaming /tmp/log/bin.log.10 to /tmp/log/bin.log.11 (rotatecount 10, logstart 1, i 10),
renaming /tmp/log/bin.log.9 to /tmp/log/bin.log.10 (rotatecount 10, logstart 1, i 9),
renaming /tmp/log/bin.log.8 to /tmp/log/bin.log.9 (rotatecount 10, logstart 1, i 8),
renaming /tmp/log/bin.log.7 to /tmp/log/bin.log.8 (rotatecount 10, logstart 1, i 7),
renaming /tmp/log/bin.log.6 to /tmp/log/bin.log.7 (rotatecount 10, logstart 1, i 6),
renaming /tmp/log/bin.log.5 to /tmp/log/bin.log.6 (rotatecount 10, logstart 1, i 5),
renaming /tmp/log/bin.log.4 to /tmp/log/bin.log.5 (rotatecount 10, logstart 1, i 4),
renaming /tmp/log/bin.log.3 to /tmp/log/bin.log.4 (rotatecount 10, logstart 1, i 3),
renaming /tmp/log/bin.log.2 to /tmp/log/bin.log.3 (rotatecount 10, logstart 1, i 2),
renaming /tmp/log/bin.log.1 to /tmp/log/bin.log.2 (rotatecount 10, logstart 1, i 1),
renaming /tmp/log/bin.log.0 to /tmp/log/bin.log.1 (rotatecount 10, logstart 1, i 0),
renaming /tmp/log/bin.log to /tmp/log/bin.log.1
removing old log /tmp/log/bin.log.11
[/B][/FONT]

At this point I expected to see 10. All I saw was the original 2 files, rotate and bin.log.

I am massively confused...
Ed

---

### Post by Corin-EU on 2009-04-30
From the man page for logrotate

> 
-d     Turns  on  debug  mode  and  implies -v. 

In debug mode, no changes will be made to the  logs  or  to the logrotate state file.



It would appear that there is a bug in the -d mode in that it claims bin.log.1, bin.log.2 etc exist even though they do not.

Drop the -d, ie logrotate -f rotate, and you will see bin.log rotated to bin.log.1

---

### Post by edpatterson on 2009-04-30
Arrrrg! I even printed out the man page and highlighted the various switches as I tried them. The squid file in logrotate.d had the -d switch and it was working and I feel like an idiot. An idiot with a rotating log, but an idiot none the less.

Thanks a million.
Ed

---

### Post by John Cheng on 2009-05-01
> **edpatterson said:**
> Arrrrg! I even printed out the man page and highlighted the various switches as I tried them. The squid file in logrotate.d had the -d switch and it was working and I feel like an idiot. An idiot with a rotating log, but an idiot none the less.

Thanks a million.
Ed

We need a "best of Ubuntu forums" thread for this comment. :P

---

