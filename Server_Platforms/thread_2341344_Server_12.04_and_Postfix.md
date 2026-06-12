---
title: "Server 12.04 and Postfix"
date: 2016-10-27
forum: Server Platforms
---

### Post by christopher_scheper on 2016-10-27
Apologies in advance, I'm no sysadmin.  Barely a user here and I need Unity to do that.  My server 12.04 is running postfix and they are HAMMERING my syslog server.  I want to quit sending informational syslog.  The Admin that built the server (no longer available) put the line 
*.*                 @our.syslogserver.com
at the end of rsyslog.conf

I have tried every thing I can find in the google machine to no avail.  I have even commented out(I used 3 ###) the line in rsyslog.conf  as well as a line from the standard log files category:

# First some standard log files.  Log by facility.
#
auth,authpriv.*                 /var/log/auth.log
###*.*;auth,authpriv.none               -/var/log/syslog
#cron.*                         /var/log/cron.log
#daemon.*                       -/var/log/daemon.log
kern.*                          -/var/log/kern.log
#lpr.*                          -/var/log/lpr.log
mail.*                          -/var/log/mail.log
#user.*                         -/var/log/user.log

.
.
.

###*.*                                 @our.syslogserver.com


Last but not least, **sudo service rsyslog** **stop** did not ebb the flow of mail.info syslogging.  I'm at a loss.  postfix points to rsyslog, right?  Where are these logs coming from?

Thank You,
/shep

---

### Post by SeijiSensei on 2016-10-27
Postfix uses the "mail" facility, so the entry
```
mail.* -/var/log/mail.log
```
is the likely source of the traffic.

You might also check the level of verbosity in the configuration files as well: [http://www.postfix.org/DEBUG_README.html#debug_peer](http://www.postfix.org/DEBUG_README.html#debug_peer)

---

### Post by christopher_scheper on 2016-10-27
solved

---

### Post by lisati on 2016-10-27
> **christopher_scheper said:**
> solved

You can mark a thread solved by clicking on the "Thread tools" drop-down menu near the top of the page, and then click on "Mark thread solved."

---

