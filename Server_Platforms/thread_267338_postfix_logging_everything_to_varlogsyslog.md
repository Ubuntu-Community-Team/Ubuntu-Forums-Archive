---
title: "postfix logging everything to /var/log/syslog"
date: 2006-09-28
forum: Server Platforms
---

### Post by ultralame on 2006-09-28
My postfix messages are *ALL* getting logged to /var/log/syslog, including the ones that are getting logged to the mail.* log files.

How can I stop the mail messages from getting logged there?

1) There is no mention of logging in my main.cf file.
/etc/syslog.conf:
> #  /etc/syslog.conf     Configuration file for syslogd.
#
#                       For more information see syslog.conf(5)
#                       manpage.

#
# First some standard logfiles.  Log by facility.
#

auth,authpriv.*                 /var/log/auth.log
*.*;auth,authpriv.none          -/var/log/syslog
#cron.*                         /var/log/cron.log
daemon.*                        -/var/log/daemon.log
kern.*                          -/var/log/kern.log
lpr.*                           -/var/log/lpr.log
mail.*                          -/var/log/mail.log
user.*                          -/var/log/user.log
uucp.*                          /var/log/uucp.log

#
# Logging for the mail system.  Split it up so that
# it is easy to write scripts to parse these files.
#
mail.info                       -/var/log/mail.info
mail.warn                       -/var/log/mail.warn
mail.err                        /var/log/mail.err

# Logging for INN news system
#
news.crit                       /var/log/news/news.crit
news.err                        /var/log/news/news.err
news.notice                     -/var/log/news/news.notice

#
# Some `catch-all' logfiles.
#
*.=debug;\
        auth,authpriv.none;\
        news.none;mail.none     -/var/log/debug
*.=info;*.=notice;*.=warn;\
        auth,authpriv.none;\
        cron,daemon.none;\
        mail,news.none          -/var/log/messages

#
# Emergencies are sent to everybody logged in.
#
*.emerg                         *

#
# I like to have messages displayed on the console, but only on a virtual
# console I usually leave idle.
#
#daemon,mail.*;\
#       news.=crit;news.=err;news.=notice;\
#       *.=debug;*.=info;\
#       *.=notice;*.=warn       /dev/tty8

# The named pipe /dev/xconsole is for the `xconsole' utility.  To use it,
# you must invoke `xconsole' with the `-file' option:
#
#    $ xconsole -file /dev/xconsole [...]
#
# NOTE: adjust the list below, or you'll go crazy if you have a reasonably
#      busy site..
#
daemon.*;mail.*;\
        news.crit;news.err;news.notice;\
        *.=debug;*.=info;\
        *.=notice;*.=warn       |/dev/xconsole

---

### Post by foxylad on 2006-09-29
Change the line:

*.*;auth,authpriv.none        -/var/log/syslog

to:

*.*;auth,authpriv.none;mail.none        -/var/log/syslog

Cheers!
Greg.

---

### Post by wislon on 2007-03-23
> **foxylad said:**
> Change the line:

*.*;auth,authpriv.none        -/var/log/syslog

to:

*.*;auth,authpriv.none;mail.none        -/var/log/syslog

Cheers!
Greg.
Foxylad, thanks man! 

Mine was working perfectly and then I installed webmin to have a poke around, and next thing I know the postfix had stopped logging to mail.log.

_How_ do you know how to do this? I'd even had a look in the syslog.conf file and was trying to wrap my brain around it, and then given up in disgust! :)

wislon.

---

### Post by whawes on 2007-05-10
I think you also need to restart syslogd to make the changes take effect:

```
sudo /etc/init.d/sysklogd restart
```

---

