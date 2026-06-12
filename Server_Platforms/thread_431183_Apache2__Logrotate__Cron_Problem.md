---
title: "Apache2 / Logrotate / Cron Problem"
date: 2007-05-02
forum: Server Platforms
---

### Post by mikestefff on 2007-05-02
Hey,

I noticed logrotate was only rotating dmesg and nothing else. I cannot seem to figure out why though. My desktop has the same configuration and it rotates everything without a problem. I started checking everything and I know that cron runs logrotate every morning, and apache is included in logrotate.d. So..is there something I am missing?

Also, I came across a thread that says that logrotate causes apache2 in Ubuntu to disconnect all existing connections while the logs are rotated. Is this true? Whats the best method?

Thanks alot,
Mike

---

### Post by mikestefff on 2007-05-03
No one can help out with this one? Thought it would be an easy one..

---

### Post by MJN on 2007-05-03
By default Apache is set to have its logs rotated weekly, not daily. Or are you not getting any rotations at all?

The 'best' way of rotating the logs depends on your requirements. The Apache development team have provided the logrotate.d config for Apache hence the default is what they consider 'best'. Does this not meet your needs?

If you would prefer Apache to leave current connections active (although this can fail in some circumstances leaving you with no service at all) then simply change **/etc/init.d/apache2 restart > /dev/null** to **/etc/init.d/apache2 reload > /dev/null** in /etc/logrotate.d/apache2.

See [http://httpd.apache.org/docs/2.0/stopping.html](http://httpd.apache.org/docs/2.0/stopping.html) for further details on stopping/starting Apache.

Mathew

P.S. You could always add a -v flag to your daily logrotate cron entry to see exactly what's happening...

---

### Post by mikestefff on 2007-05-03
I know it is set up by default - but nothing is happening.

The strangest thing is that it is setup the same way on my local machine as it is on my vps, and the local machine works fine..

What am I missing?

---

### Post by MJN on 2007-05-03
Have you tried the -v flag? What does it say?

---

### Post by mikestefff on 2007-05-03
Oh I missed that message. I don't need it to rotate everyday. I seems like cron runs everyday and logrotate checks to see if it is a week old. I could be wrong though. I haven't changed anything - everything is still the way it is set up automatically. -v is for verbose? I won't be able to see because it runs at 6am every day.

---

### Post by MJN on 2007-05-03
You'll just have to get up earlier!

Just kidding... any output that occurs because of the -v flag will be e-mailed to you (root) by cron when the script is run.

Has it been a week since Apache was logging?

You can also check logrotate's view on the things with **sudo logrotate -d /etc/logrotate.conf** - this won't change anything but should tell you whether Apache is set to be rotated and when. For reference my output is (I rotate weekly and keep them for a year):

```

rotating pattern: /var/log/apache2/*.log  weekly (52 rotations)
empty log files are not rotated, old logs are removed
considering log /var/log/apache2/access.log
  log does not need rotating
```Mathew

---

### Post by mikestefff on 2007-05-03
rotating pattern: /var/log/apache2/*.log  weekly (52 rotations)
empty log files are not rotated, old logs are removed
considering log /var/log/apache2/access.log
  log does not need rotating
considering log /var/log/apache2/error.log
  log does not need rotating
not running shared postrotate script, since no logs were rotated

===

Apache has been running for about 3 months. My access.log is gigantic and growing a ton every day. I don't get why it isn't rotating though..

What can I do..? Anything else you'd like to see?

---

### Post by MJN on 2007-05-03
Hmm...

Contents of /var/lib/logrotate/status ?

Mathew

---

### Post by mikestefff on 2007-05-03
Local Machine: All of the times for every log file

VPS: "logrotate state -- version 2"

---

### Post by MJN on 2007-05-03
I know that - that's why I asked! Help me out here - I need the *contents*! (specifically, the time/date of the apache log file status)

Mathew

---

### Post by mikestefff on 2007-05-04
Well why would the local machine's data matter - it works fine..but here you go

LOCAL MACHINE:

logrotate state -- version 2
"/var/log/acpid" 2007-4-29
"/var/log/apport.log" 2007-5-2
"/var/log/aptitude" 2006-11-10
"/var/log/cups/access_log" 2007-5-2
"/var/log/cups/error_log" 2007-5-2
"/var/log/cups/page_log" 2006-11-7
"/var/log/dpkg.log" 2007-5-1
"/var/log/ppp-connect-errors" 2006-11-7
"/var/log/scrollkeeper.log" 2007-4-29
"/var/log/unattended-upgrades/unattended-upgrades.log" 2006-11-7
"/var/log/wpa_action.log" 2006-11-7
"/var/log/wtmp" 2007-5-1
"/var/log/btmp" 2007-5-1
"/var/log/pure-ftpd/transfer.log" 2007-1-16
"/var/log/apache2/access.log" 2007-4-29
"/var/log/apache2/error.log" 2007-4-29
"/var/log/mysql.log" 2007-5-4
"/var/log/mysql/mysql.log" 2006-11-27
"/var/log/mysql/mysql-slow.log" 2006-11-27
"/var/log/suphp/suphp.log" 2007-3-21

VPS:

logrotate state -- version 2

Thanks..

(PS - I'm a real idiot..I kept checking the first page for a response..I just realized there were two pages..)

---

### Post by MJN on 2007-05-04
No... not yet!

I asked you for the *contents* of the file i.e. what exactly were the times/dates etc? Or was what you pasted exactly what was in the file?

Mathew

---

### Post by MJN on 2007-05-04
If you also post the output of **ls -l /var/log/apache2/** that might give some clues.

Mathew

---

### Post by MJN on 2007-05-04
(Please don't edit previous posts after a reply - it can easily cause confusion for future readers following the thread... not to mention myself!)

Would I be right in thinking 'VPS' is your server? (it might've helped if you'd mentioned that - I thought it was part of the contents of your status file)

It's clear that for some reason your status file is not being written to - as you can see from the one on your 'local machine' it is this file that records when logs were last rotated and hence can then determine if they need rotating this time around....

In the absence of any status data I assume the fallback must be to not do anything... What are the permissions (ls -l) on the status file?

Mathew

---

### Post by mikestefff on 2007-05-04
Sorry about the edit - I thought I did it before anyone even had a chance to read.

Yes VPS = server. I thought I did mention that.

(Local Machine) ls -l /var/log/apache2/:
-rw-r----- 1 root adm 361929 2007-05-04 03:30 access.log
-rw-r----- 1 root adm 198170 2007-04-28 14:40 access.log.1
-rw-r----- 1 root adm  12915 2007-02-23 17:17 access.log.10.gz
-rw-r----- 1 root adm  43739 2007-02-17 13:16 access.log.11.gz
-rw-r----- 1 root adm  44899 2007-02-09 13:22 access.log.12.gz
-rw-r----- 1 root adm  48805 2007-02-04 00:30 access.log.13.gz
-rw-r----- 1 root adm  16442 2007-01-27 18:19 access.log.14.gz
-rw-r----- 1 root adm  83541 2007-04-22 07:35 access.log.2.gz
-rw-r----- 1 root adm  15414 2007-04-15 02:13 access.log.3.gz
-rw-r----- 1 root adm  50481 2007-04-08 01:43 access.log.4.gz
-rw-r----- 1 root adm  14290 2007-04-01 00:14 access.log.5.gz
-rw-r----- 1 root adm  70903 2007-03-25 04:12 access.log.6.gz
-rw-r----- 1 root adm  38243 2007-03-18 05:13 access.log.7.gz
-rw-r----- 1 root adm  30254 2007-03-12 01:55 access.log.8.gz
-rw-r----- 1 root adm   5845 2007-02-26 17:31 access.log.9.gz
-rw-r----- 1 root adm    577 2007-05-03 10:45 error.log
-rw-r----- 1 root adm    746 2007-04-29 07:35 error.log.1
-rw-r----- 1 root adm    652 2007-02-25 15:23 error.log.10.gz
-rw-r----- 1 root adm   1637 2007-02-18 14:08 error.log.11.gz
-rw-r----- 1 root adm    480 2007-02-11 10:08 error.log.12.gz
-rw-r----- 1 root adm   1420 2007-02-04 12:04 error.log.13.gz
-rw-r----- 1 root adm   2330 2007-01-28 13:26 error.log.14.gz
-rw-r----- 1 root adm   1313 2007-04-22 07:35 error.log.2.gz
-rw-r----- 1 root adm    216 2007-04-15 07:35 error.log.3.gz
-rw-r----- 1 root adm   1031 2007-04-08 07:35 error.log.4.gz
-rw-r----- 1 root adm    391 2007-04-01 07:35 error.log.5.gz
-rw-r----- 1 root adm   6329 2007-03-25 07:35 error.log.6.gz
-rw-r----- 1 root adm   5882 2007-03-18 16:51 error.log.7.gz
-rw-r----- 1 root adm    622 2007-03-12 12:07 error.log.8.gz
-rw-r----- 1 root adm    314 2007-03-04 13:54 error.log.9.gz

(VPS):

-rw-r----- 1 www-data adm 724779801 May  4 13:13 access.log
-rw-r----- 1 root     adm    279583 May  3 21:18 error.log

Hmm..why the hell is it www-data..I guess that should be changed. It just changed it to root. I don't recall ever seeing that though. Do you think that is the problem??

The status file is root:root on both.

Thanks

---

### Post by MJN on 2007-05-04
Shouldn't matter - www-data is simply the user Apache runs as. Furthermore your error.log owner:group is root:adm and that's not getting rotated either.

It was the permissions of the status file I was after - not the owner. No matter - try deleting the status file and re-running **sudo logrotate -v /etc/logrotate.conf** . Finger's crossed it should create a new status file populated with datestamps.

Mathew

---

### Post by mikestefff on 2007-05-04
Ok - I just did that. This was the output from the VPS after logrotate -v /etc/logrotate.conf:

reading config file /etc/logrotate.conf
including /etc/logrotate.d
reading config file apache2
reading config info for /var/log/apache2/*.log 
reading config file clamav-daemon
reading config info for /var/log/clamav/clamav.log 
reading config file clamav-freshclam
reading config info for /var/log/clamav/freshclam.log 
reading config file dpkg
reading config info for /var/log/dpkg.log 
reading config file mysql-server
reading config info for /var/log/mysql.log /var/log/mysql/mysql.log /var/log/mysql/mysql-slow.log 
reading config file sendmail
reading config file wu-ftpd
reading config info for /var/log/wu-ftpd/xferreport 
reading config info for /var/log/wtmp 

Handling 7 logs

rotating pattern: /var/log/apache2/*.log  weekly (52 rotations)
empty log files are not rotated, old logs are removed
considering log /var/log/apache2/access.log
  log does not need rotating
considering log /var/log/apache2/error.log
  log does not need rotating
not running shared postrotate script, since no logs were rotated

rotating pattern: /var/log/clamav/clamav.log  weekly (12 rotations)
empty log files are rotated, old logs are removed
considering log /var/log/clamav/clamav.log
  log does not need rotating

rotating pattern: /var/log/clamav/freshclam.log  weekly (12 rotations)
empty log files are rotated, old logs are removed
considering log /var/log/clamav/freshclam.log
  log does not need rotating

rotating pattern: /var/log/dpkg.log  monthly (12 rotations)
empty log files are not rotated, old logs are removed
considering log /var/log/dpkg.log
  log does not need rotating

rotating pattern: /var/log/mysql.log /var/log/mysql/mysql.log /var/log/mysql/mysql-slow.log  after 1 days (7 rotations)
empty log files are rotated, old logs are removed
considering log /var/log/mysql.log
  log does not need rotating
considering log /var/log/mysql/mysql.log
  log /var/log/mysql/mysql.log does not exist -- skipping
considering log /var/log/mysql/mysql-slow.log
  log /var/log/mysql/mysql-slow.log does not exist -- skipping
not running shared postrotate script, since no logs were rotated

rotating pattern: /var/log/wu-ftpd/xferreport  monthly (15 rotations)
empty log files are rotated, old logs are removed
considering log /var/log/wu-ftpd/xferreport
  log /var/log/wu-ftpd/xferreport does not exist -- skipping

rotating pattern: /var/log/wtmp  monthly (1 rotations)
empty log files are rotated, old logs are removed
considering log /var/log/wtmp
  log does not need rotating
=======================
AND this is the status:

logrotate state -- version 2
"/var/log/apache2/access.log" 2007-5-4
"/var/log/apache2/error.log" 2007-5-4
"/var/log/clamav/clamav.log" 2007-5-4
"/var/log/clamav/freshclam.log" 2007-5-4
"/var/log/dpkg.log" 2007-5-4
"/var/log/mysql.log" 2007-5-4
"/var/log/mysql/mysql.log" 2007-5-4
"/var/log/mysql/mysql-slow.log" 2007-5-4
"/var/log/wu-ftpd/xferreport" 2007-5-4
"/var/log/wtmp" 2007-5-4

===========

So does that mean it should work from now on?

---

### Post by MJN on 2007-05-04
I reckon it does indeed...

You could always check by editing the status file such that the datestamp for the Apache logs are, say, last week then rerun logrotate and it'll think the logs are in need of rotation..

Mathew

---

### Post by mikestefff on 2007-05-04
Thank you very much. Hope it work outs. I'll post back after a week if it doesn't.

Thanks again.

---

### Post by MJN on 2007-05-04
You're welcome.

I'm off for a lie down! ;-)

Mathew

---

