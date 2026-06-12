---
title: "iptables and logging"
date: 2011-07-13
forum: Security
---

### Post by Cyked on 2011-07-13
I haven't touched IP tables in a while other than adding new rules for INPUT. and I usually just look at apache errors for people digging for things that don't exist on my server.

What I am having an issue with is what logging level I should be using in logging chains and what, if anything, should I be adding to syslog.conf

Right now I can ONLY getting warning level (4) logs with iptables to work.  Here is my syslog.

If I add chains for logging at either info or debug level NOTHING gets logged in /var/log/firewall/firewall.log (bolded the line I'm working with).

```
#  /etc/syslog.conf     Configuration file for syslogd.
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


#
# Logging for the mail system.  Split it up so that
# it is easy to write scripts to parse these files.
#
mail.info                       -/var/log/mail.info
mail.warning                    -/var/log/mail.warn
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
*.=info;*.=notice;*.=warning;\
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
#       *.=notice;*.=warning    /dev/tty8

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
        *.=notice;*.=warning    |/dev/xconsole


**kern.warning /var/log/firewall/firewall.log**

```


example iptables:
```
LOG        all  --  111.111.111.111       anywhere            limit: avg 5/min burst 5 LOG level warning prefix `Block 111: '
```

can I not simply do something like this?
kern.info /var/log/firewall/firewall.log
or kern.debug?  I also update the ifconfig chain for info/debug as well..

What am I doing wrong.

---

### Post by Cyked on 2011-07-13
Secondary thought.... I want my the logs from iptables only in the firewall.log files, NOT also in kern, messages, and syslog, etc

---

### Post by Cyked on 2011-07-19
Anyone?

---

