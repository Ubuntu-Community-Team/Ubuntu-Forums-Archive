---
title: "syslog filter"
date: 2013-09-16
forum: Server Platforms
---

### Post by luciano_rinetti on 2013-09-16
I'm running Ubuntu Server 11.04 with an Courier IMAP server ver. 4.8.0. The IMAP relate log messages are now populating the /var/log/syslog and /var/log/mail.log
files.
What i can do to avoid the IMAP logs in the syslog file ?
Regards,

---

### Post by nerdtron on 2013-09-16
Ubuntu 11.04 server? not 12.04? Then you should upgrade.
Anyway I just checked the /var/log/syslog of our mail server and there are indeed IMAP/postfix logs in there. Why to do want to remove the imap logs in syslog?

---

### Post by luciano_rinetti on 2013-09-16
Yes i need to upgrade to 12.04 LTS but the mail server is always online, so ...
The system rsyslog configuration, already logs "mail logs" in /var/log/mail.log:
mail.*                         -/var/log/mail.log
so it seems a waste of space and time duplicate in the syslog file. So i'mlooking to "redirect" mail logs only in mail.log file.

Regards

---

### Post by SeijiSensei on 2013-09-16
I don't use Courier, so this is just a guess, but perhaps it is using a different syslog "facility" rather than the "mail" facility.  /etc/rsyslog.d/50-default shows mail.* routed to /var/log/mail.log except for mail.err which is routed to /var/log/mail.err.  Are there any files in /etc/rsyslog.d/ that relate to Courier?  Is there a log facility specified in a configuration file for Courier itself?  

You could try editing /etc/rsyslog.d/50-default.conf and adding "mail.none" to the default routing to /var/log/syslog like this:
```

# First some standard log files.  Log by facility.
#
auth,authpriv.*                 /var/log/auth.log
*.*;**mail.none;**auth,authpriv.none          -/var/log/syslog

```

Run "sudo service rsyslog restart" after making the change.

---

### Post by luciano_rinetti on 2013-09-16
The problem was solved when i add the "mail.none" in the file /etc/rsyslog.d/50-default.conf as follows.
No log files are specified in the courier configuration file, but i added a "DEBUG_LOGIN=1" in the /etc/courier/imapd
in the past to better investigate an old problem, and this led to populate the mail.debug file.
Now the /var/log/syslog reports only "system" logs and all mail related logs are confined in the mail.*level* file.
I am only surprised that tha mail.log is still populated, i suppose that defining all *level *file for the mail service,
no logs should go in the mail.log file.
Many thanks to all you that take time to answer me.

auth,authpriv.*                 /var/log/auth.log
*.*;[COLOR=#ff0000]mail.none;[/COLOR]auth,authpriv.none                -/var/log/syslog       <<<<<--------------------
#cron.*                         /var/log/cron.log
#daemon.*                       -/var/log/daemon.log
kern.*                          -/var/log/kern.log
#lpr.*                          -/var/log/lpr.log
#mail.*                         -/var/log/mail.log
#user.*                         -/var/log/user.log

#
# Logging for the mail system.  Split it up so that
# it is easy to write scripts to parse these files.
#
mail.=emerg             /var/log/mail.emerg
mail.=alert             /var/log/mail.alert
mail.=crit              /var/log/mail.crit
mail.=err                       /var/log/mail.err
mail.=warn                      -/var/log/mail.warn
mail.=notice                    -/var/log/mail.notice
mail.=info                      -/var/log/mail.info
mail.=debug                     -/var/log/mail.debug
mail.*                          -/var/log/mail.log

*.emerg                         *

daemon.*;mail.*;\
        news.err;\
        *.=debug;*.=info;\
        *.=notice;*.=warn       |/dev/xconsole

---

