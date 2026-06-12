---
title: "Prevent logrotate from rotating certain logs"
date: 2006-12-22
forum: Server Platforms
---

### Post by dualusbibook on 2006-12-22
I am reposting this in the server section as I'm not getting any help in the general form.  I have been doing on/off searches over the past week since my original post and have not been able to solve my problem.  Hopefully someone in this forum will be able to shed some light on my problem.

Thx.

Original post:
I'm having trouble preventing logrotate from rotating my mail logs. I have a daily cron script that runs at midnight that takes care of my mail logs.

What I have tried so far is to add an entry into /etc/logrotate.conf that would rotate the log if it reached a certain size. The size of course is large enough that it will never reach it. The problem is the log is still being rotated.

What I have tried currently is:
/var/log/mail.log {
missingok
daily
rotate 5
nocompress
size 100M
}

Is this the right approach? I have been unable to find any information on the net regarding an omit command.

My mail program is postfix, and currently the logs are rotating once a week which corresponds to the top part of my /etc/logrotate.conf file.

Any thoughts or ideas would be appreciated. Also I can provided more info if needed.

---

### Post by MJN on 2006-12-23
> **dualusbibook said:**
> I am reposting this in the server section as I'm not getting any help in the general form. I have been doing on/off searches over the past week since my original post and have not been able to solve my problem. Hopefully someone in this forum will be able to shed some light on my problem.
 
Thx.
 
Original post:
I'm having trouble preventing logrotate from rotating my mail logs. I have a daily cron script that runs at midnight that takes care of my mail logs.
<cut>

 
Hold it right there...
 
Mail logs are regarded as a system log file and hence it's not Logrotate that manages them... but rather syslog via the daily and weekly sysklogd cron jobs.
 
Hence no matter what you do/add to the logrotate config your mail logs will still be 'interfered' with by syslog.
 
Check out [http://www.ducea.com/2006/06/06/rotating-linux-log-files-part-1-syslog/](http://www.ducea.com/2006/06/06/rotating-linux-log-files-part-1-syslog/) for a nice overview of what's going on and pointers to how to modify its behaviour.
 
Mathew

---

### Post by dualusbibook on 2006-12-23
That was perfect.  Thanks a million.  I was able to get my mail.* logs to be ignored.  It is so much easier when I'm looking in the right direction.

Also, your URL has additional articles that are interesting and helpful.

thx again.

---

### Post by dualusbibook on 2006-12-24
Hmm I spoke to soon. :( 

I used the -s flag to ignore a set pattern via command line and the output was what I wanted.  A list of my logs but excluding my mail.* logs.  However, when I made the change to the /etc/cron.weekly/sysklogd file I got an email this morning from the cron deamon.

The output of syslogd-listfiles --weekly is:
/var/log/mail.warn
/var/log/uucp.log
/var/log/user.log
/var/log/daemon.log
/var/log/messages
/var/log/debug
/var/log/auth.log
/var/log/mail.err
/var/log/mail.log
/var/log/kern.log
/var/log/lpr.log
/var/log/mail.info

Now using syslogd-listfiles --weekly -s mail.* to exclude my mail logs I get:
/var/log/uucp.log
/var/log/user.log
/var/log/daemon.log
/var/log/messages
/var/log/debug
/var/log/auth.log
/var/log/kern.log
/var/log/lpr.log

Whis is the list I thought i wanted so I made my edit on line 39 to read:
for LOG in `syslogd-listfiles --weekly -s mail.*`

No dice.  Am I missing something simple here?

Thx for any ideas.

---

