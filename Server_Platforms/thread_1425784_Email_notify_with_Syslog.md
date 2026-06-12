---
title: "Email notify with Syslog?"
date: 2010-03-09
forum: Server Platforms
---

### Post by sentinelace on 2010-03-09
I'm running a syslog server on ubuntu 7.04.  Can I somehow have it email me if it finds a certain thing in the log?  For example. I'm running a PRI and when the PRI goes down, it logs a "DEACTIVED" in the log.  I would like an email telling me this so I know to get on it and fix it.  Any ideas?

---

### Post by tgalati4 on 2010-03-09
Write a small script that searches your log file for the term DEACTIVATED.  If found then send an email.

Add your script to the system /etc/crontab.

Here's an example mail script from a Dapper Drake machine for when the UPS communication is down:

tgalati4@tubuntu2:/etc/apcupsd$ cat commfailure
#!/bin/sh
#
# This shell script if placed in /etc/apcupsd
# will be called by /etc/apcupsd/apccontrol when apcupsd
# loses contact with the UPS (i.e. the serial connection is not responding).
# We send an email message to root to notify him.
#
SYSADMIN=root
APCUPSD_MAIL="mail"

HOSTNAME=`hostname`
MSG="$HOSTNAME Communications with UPS lost"
#
(
   echo "Subject: $MSG"
   echo " "
   echo "$MSG"
   echo " "
   /sbin/apcaccess status
) | $APCUPSD_MAIL -s "$MSG" $SYSADMIN
exit 0

But thinking about it, I have no idea what a PRI is.  Plus, if you just search the log files, they get compressed and rotated and you have to detect the latest occurrence.  A better plan would be to find the script that actually writes DEACTIVATED to the syslog file, then put your email code right after it.

To find it, go to the directory where your PRI stuff is and:

grep DEACTIVATED *

---

### Post by sentinelace on 2010-03-10
I'll test this, do I need to install anything or will it just work?  I already know where the log is.  It's in /var/log/uc520/uc520.log and it's logged there.  I just need this script to email me when it logs deactivated.  Where do I place this script?

---

### Post by tgalati4 on 2010-03-10
You need to find the script that writes uc520.log.  Place a few lines of code (based on the example that I provided) inside of that script.

---

### Post by sentinelace on 2010-03-11
This just comes from the syslog.conf that I setup.
 
This is at the bottom of the syslog.conf 
 
local7.debug comes from the router.
 
/etc/syslog.conf
 
#Uc520 router logging
local7.debug /var/log/uc520/uc520.log
*.*;local7.none;\
auth,authpriv.none -/var/log/syslog
 
So I guess that's where I am lost to add the script?

---

### Post by tgalati4 on 2010-03-11
The syslog daemon (syslogd) can capture system messages from many devices on the same network--as long as you set up the devices with the appropriate IP address for the syslog dump.

I'm not familiar with the Uc520 router.  Perhaps the router itself as an email message facility.

So now you have to write a script that tests the uc520.log file for the presence of "DEACTIVATED" and if detected then send an email and rotate the log file.  

man logrotate

If the file isn't already autorotated.

Put your script into the system cron job (cat /etc/crontab) and set it to run every 5 minutes or however often you really need to run it.

Check the settings of the router.  There may be more elegant ways to provide notification.

---

### Post by sentinelace on 2010-03-11
I am not a big script guy.  What do I need replace in the script above for this to work?

---

### Post by Samatva on 2010-03-11
It sounds like you *could* end up with a system that would not be able to stop sending numerous e-mails under certain situations.

Consider an intelligent monitoring such as Nagios - it's not very easy to set up, but it gives great flexibility, etc.

---

### Post by sentinelace on 2010-03-11
> **Samatva said:**
> It sounds like you *could* end up with a system that would not be able to stop sending numerous e-mails under certain situations.
 
Consider an intelligent monitoring such as Nagios - it's not very easy to set up, but it gives great flexibility, etc.
 
Will that give me what I need?  That looks like monitoring.  I don't understand how that can send me an email from specifics from a log?  I don't want the entire log either.  Just pieces.

---

### Post by Samatva on 2010-03-11
Nagios can monitor all sorts of services. I have not checked to see if there is a module to detect when a PRI goes down, but think there's a good chance that there is...

Also, I know that Nagios can monitor a web page for the existence (or lack thereof) of a text string - it *might* be able to so the same for a log file.

---

### Post by sentinelace on 2010-03-11
cool.  free?  Looks like it's not?

---

### Post by Samatva on 2010-03-11
It's in the repository (nagios3) (edit: oops - don't know about 7.04...)

See also [http://www.google.com/search?q=nagios+PRI+monitor](http://www.google.com/search?q=nagios+PRI+monitor)

I don't know your field, but there may be some leads there...

---

### Post by sentinelace on 2010-03-11
Wow, got it installed.  Looks pretty good.  Is there a good area on how to configure it and make this work?

---

