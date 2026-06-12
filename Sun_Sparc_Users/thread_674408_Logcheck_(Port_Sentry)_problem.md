---
title: "Logcheck (Port Sentry) problem"
date: 2008-01-21
forum: Sun Sparc Users
---

### Post by RobSand on 2008-01-21
Greetings!

Logcheck is installed on a Solaris sparc machine running Solaris 10.  It (Logcheck) is being driven by a scheduled cron job and it works as it is supposed to.

However,  I am having a problem getting it to work whenever I try to add a rule to the  /usr/local/etc/logcheck.violations file in order to cause the Logcheck application to send an alert whenever an ssh login attempt failure occurs.

As of this writing, I have done the following:

(1)  Made necessary entries in the /etc/syslog.conf to insure that ssh logging is occuring.  This has been verified.

(2)  The cron job which instigates the Logcheck application is running normally. This has been verified.

(3)  I edited the /usr/local/etc/logcheck.sh script to look like this:

# SunOS, Sun Solaris 2.5
$LOGTAIL /var/log/syslog > $TMPDIR/check.$$
$LOGTAIL /var/adm/messages >> $TMPDIR/check.$$
#$LOGTAIL /var/adm/auth >> $TMPDIR/check.$$
$LOGTAIL /var/log/ssh.log >> $TMPDIR/check.$$

(4)  I have installed the following line in the /usr/local/etc/logcheck.violations file:
       "authentication failed"  (minus the quotes, of course!)

The "authentication failed" line was added to cause the logcheck script to alert on any failed ssh login attempts because the ssh.log file reports, in part "Authentication failed".

(5) When I try to test Logcheck to send an alert by purposefully failing an ssh login attempt,  the failed login attempt is reported in
/var/log/ssh.log but the Logcheck application fails to send an e-mail message alert to the sysadmin.

Any ideas as to what I need to do to correct this problem so that Logcheck will report the failed ssh login attempt?

Andy and all responses are very much appreciated!  Thanks ahead of time!

Rob Sandifer

---

### Post by netztier on 2008-01-22
Rob, please!

At the risk of repeating myself: [http://ubuntuforums.org/showpost.php?p=3539375&postcount=3](http://ubuntuforums.org/showpost.php?p=3539375&postcount=3)

Ever heard of [BigAdmin]("http://www.sun.com/bigadmin/home/index.html")? It's a good ressource for questions regarding **Solaris**, way better than a forum related to running *Ubuntu* on a SPARC machine.

At least, if you just can't resist posting Solaris related questions to ubuntuforums.org, please do so in [Other OS Talk]("http://ubuntuforums.org/forumdisplay.php?f=147")

regards

Marc

---

