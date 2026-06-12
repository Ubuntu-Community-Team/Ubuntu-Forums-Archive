---
title: "Need to redirect a log from rsyslog."
date: 2014-07-14
forum: Server Platforms
---

### Post by welefort on 2014-07-14
I have a server ngircd running fine on a 14.04 system.  The currently logging for ngircd dumps the logs to syslog.  What I'd like to do is create its own log file.  I was told the best way would be to use rsyslog facility.    After some googling, i found that creating a conf file in /etc/rsyslog.d/  would be what I need.    So I created on there called ngircd.log.   It contains
```

# Log messages generated ngircd log messages to file
:msg,contains,"[ngircd " /var/log/ngircd/ngircd.log

```

Restarted both rsyslog and ngircd..to no effect.   Could anyone help with this.?

---

### Post by Lars Noodén on 2014-07-14
Check which [SyslogFacility](http://ngircd.barton.de/doc/sample-ngircd.conf) you are using and then use rsyslog to shunt those messages to their own file.  In a new file in /etc/rsyslog.d/ add

```

local5.* /var/log/ngircd/ngircd.log

```

Or something like that.  Then reload rsyslog's configuration.

---

### Post by welefort on 2014-07-14
Gave it a try with no luck.  

My Ngircd.conf

```
# Syslog "facility" to which ngIRCd should send log messages.
    # Possible values are system dependent, but most probably auth, daemon,
    # user and local1 through local7 are possible values; see syslog(3).
    # Default is "local5" for historical reasons, you probably want to
    # change this to "daemon", for example.
    SyslogFacility = local7
```


and from /etc/rsyslog.d/ngircd.conf
```
local7.* /var/log/ngircd/ngircd.log
```


Still getting log outputs to syslog

---

### Post by Lars Noodén on 2014-07-14
And you restarted / reloaded rsyslogd after making the changes to the config file, I presume?

What is the whole rsyslog config file showing?

---

### Post by welefort on 2014-07-14
I stopped ngircd and rsyslog before making the changes.    Adjusted them as suggested,  and restarted rsyslog first, then ngircd.

/etc/rsyslog.d/ngircd.conf
```
local7.* /var/log/ngircd/ngircd.log
```


/etc/rsyslog.d/50-default.conf
```
#  Default rules for rsyslog.
#
#            For more information see rsyslog.conf(5) and /etc/rsyslog.conf

#
# First some standard log files.  Log by facility.
#
auth,authpriv.*            /var/log/auth.log
*.*;auth,authpriv.none        -/var/log/syslog
#cron.*                /var/log/cron.log
#daemon.*            -/var/log/daemon.log
kern.*                -/var/log/kern.log
#lpr.*                -/var/log/lpr.log
mail.*                -/var/log/mail.log
#user.*                -/var/log/user.log

#
# Logging for the mail system.  Split it up so that
# it is easy to write scripts to parse these files.
#
#mail.info            -/var/log/mail.info
#mail.warn            -/var/log/mail.warn
mail.err            /var/log/mail.err

#
# Logging for INN news system.
#
news.crit            /var/log/news/news.crit
news.err            /var/log/news/news.err
news.notice            -/var/log/news/news.notice

#
# Some "catch-all" log files.
#
#*.=debug;\
#    auth,authpriv.none;\
#    news.none;mail.none    -/var/log/debug
#*.=info;*.=notice;*.=warn;\
#    auth,authpriv.none;\
#    cron,daemon.none;\
#    mail,news.none        -/var/log/messages

#
# Emergencies are sent to everybody logged in.
#
*.emerg                                :omusrmsg:*

#
# I like to have messages displayed on the console, but only on a virtual
# console I usually leave idle.
#
#daemon,mail.*;\
#    news.=crit;news.=err;news.=notice;\
#    *.=debug;*.=info;\
#    *.=notice;*.=warn    /dev/tty8

# The named pipe /dev/xconsole is for the `xconsole' utility.  To use it,
# you must invoke `xconsole' with the `-file' option:
# 
#    $ xconsole -file /dev/xconsole [...]
#
# NOTE: adjust the list below, or you'll go crazy if you have a reasonably
#      busy site..
#
daemon.*;mail.*;\
    news.err;\
    *.=debug;*.=info;\
    *.=notice;*.=warn    |/dev/xconsole
```

---

### Post by Lars Noodén on 2014-07-14
I'm not sure what to try.  I'm guessing the syntax for the configuration file is ok:

```

/usr/sbin/rsyslogd -N 1

```

and that /var/log/ngircd/ exists.

---

### Post by welefort on 2014-07-14
$/usr/sbin/rsyslogd -N 1
```
rsyslogd: version 7.4.4, config validation run (level 1), master config /etc/rsyslog.conf
rsyslogd: End of config validation run. Bye.
```

$ ls -la /var/log/ngircd/
```
total 8
drwxr-xr-x  2 root   root   4096 Jul 14 10:36 .
drwxrwxr-x 21 syslog syslog 4096 Jul 14 10:35 ..
-rw-r--r--  1 root   root      0 Jul 14 10:36 ngircd.log
```

---

