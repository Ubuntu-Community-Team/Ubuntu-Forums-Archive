---
title: "Cron job error"
date: 2010-08-13
forum: Server Platforms
---

### Post by duceduc on 2010-08-13
I am receiving cron job error via email for amavis-new program.
```

*Cron <amavis@web-server> test -e /usr/sbin/amavisd-new-cronjob && /usr/sbin/amavisd-new-cronjob sa-syn*

bayes: cannot open bayes databases /etc/spamassassin/bayes_* R/O: tie failed: Permission denied
bayes: expire_old_tokens: locker: safe_lock: cannot create tmp lockfile /etc/spamassassin/bayes.lock.web-server.20927 for /etc/spamassassin/bayes.lock: Permission denied
```

I don't know exactly what I did to cause this error. It maybe from using this script taken from [this blog](http://hash-pipe.com/2008/09/im-teaching-spam-assassin-about-the-spam-in-my-maildirs/). It is a script to run sa-learn for spamassassin using a cron job. 

I can't imagine the script is at fault but I am no expert. Which is why I am consulting the real experts here. :P

---

### Post by uptime365 on 2010-08-14
Hi,

Can you try to set the particular cron as root user . It seems the user  that runs the cron doesn't have permission to access the said  files/dirs.

Uptime

---

### Post by duceduc on 2010-08-14
Thanks for the reply. How would I do that. Here is the cron job script.
> #
#  SpamAssassin maintenance for amavisd-new
#
# m h dom mon dow user  command
18 */3	* * *	amavis	test -e /usr/sbin/amavisd-new-cronjob && /usr/sbin/amavisd-new-cronjob sa-sync


---

### Post by mw4jet on 2011-01-15
I have same error message.
 
This file is in /root
 
File name: rsync-shell.sh
 
[PHP] 
#!bin/bash
sudo rsync -az --delete /home/mark/music/ /mymounts/d2p1/home_backup
[/PHP]
 
If I "sudo crontab -l" I get:
 
[PHP] 
# m h dom mon dow
0 * * * * /root/rsync-shell.sh
[/PHP]
 
 
I continually receive this message on my servers mail from cron daemon:
[PHP] 
/bin/sh: /root/rsync-shell.sh: Permission denied
 
[/PHP]
 
I thought that by putting the rsync-shell.sh in root that permissions would be no problem, but I guess I am wrong. 
 
There is a difference if I "sudo crontab -e" or "crontab -e" if I do not use sudo it says "there is no crontab for mark" (I am only user on server as mark).
 
I am new this year to Ubuntu headless server, am learning loads but I surely have to work at it!
 
Help anyone?
 
Edit to add: I created a crontab -e without "sudo", entered the 0 * * * * /root/rsync-shell.sh file and it failed with same reason.

---

### Post by mw4jet on 2011-01-15
Is it possible the "--delete" is causing the permission error?
 
( I try to learn and read on the forum and web before posting because most times there is no response, I hope to hear from someone this time)

---

### Post by mw4jet on 2011-01-16
Needed to be "su" and create crontab -e. 
 
Thanks anyway, kept searching an got it figured out [here]("http://ubuntuforums.org/showthread.php?t=102626&highlight=cron+job+error")

---

