---
title: "ip logging issues - ubuntu 12.10"
date: 2013-08-08
forum: Server Platforms
---

### Post by J4nbhp4 on 2013-08-08
This was posted in another thread and that thread has been closed so I can not reply to that thread. But I am having the same issue as the guy in that thread. 

The problem, none of my iptables dropped packets are being logged. I can not find them in /var/log/*
But, if I run the command "dmesg" I can view the dropped packets.

I thought all dropped packets should be logged to /var/log/syslog, but I am not showing anything. According to the /etc/syslogd.conf file all kern.* messages should be logged to /var/log/kern.log but that file is just empty. Why?

```
$ sudo iptables -L -vChain INPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination
   32  2688 ACCEPT     all  --  lo     any     anywhere             anywhere
 3580  266K ACCEPT     all  --  any    any     anywhere             anywhere             state RELATED,ESTABLISHED
    1    48 ACCEPT     tcp  --  any    any     anywhere             anywhere             tcp dpt:ssh
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere             tcp dpt:http
   26  1488 LOG        all  --  any    any     anywhere             anywhere             limit: avg 5/min burst 5 LOG level debug prefix "iptables denied: "
   32  1848 DROP       all  --  any    any     anywhere             anywhere


Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination


Chain OUTPUT (policy ACCEPT 2038 packets, 325K bytes)
 pkts bytes target     prot opt in     out     source               destination



```
```
$ sudo cat /etc/syslog.conf#  /etc/syslog.conf     Configuration file for syslogd.
#
#                       For more information see syslog.conf(5)
#                       manpage.


#
# First some standard logfiles.  Log by facility.
#


auth,authpriv.*          -/var/log/auth.log
*.*;auth,authpriv.none          -/var/log/syslog
#cron.*                  -/var/log/cron.log
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
mail.err                 -/var/log/mail.err


# Logging for INN news system
#
news.crit                -/var/log/news/news.crit
news.err                 -/var/log/news/news.err
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
#daemon.*;mail.*;\
#       news.err;\
#       *.=debug;*.=info;\
#       *.=notice;*.=warning    |/dev/xconsole



```

---

### Post by SeijiSensei on 2013-08-08
Packets are only logged if you have an appropriate iptables rule.  Add this to the bottom of the INPUT ruleset:

```
/sbin/iptables -A INPUT -j LOG
```

Now any packets that do not match a rule will be logged to /var/log/syslog.  If you want to log packets matching a particular rule, add an identical rule before it that uses "-j LOG".  For instance, if I wanted to log every SSH connection, I could use:

```
/sbin/iptables -A INPUT -p tcp --dport 22 -j LOG
/sbin/iptables -A INPUT -p tcp --dport 22 -j ACCEPT

```

The first rule logs the connection; the second accepts it.

---

### Post by J4nbhp4 on 2013-08-08
> **SeijiSensei said:**
> Packets are only logged if you have an appropriate iptables rule.  Add this to the bottom of the INPUT ruleset:

```
/sbin/iptables -A INPUT -j LOG
```



Is this not what I already have?

```
26  1488 LOG        all  --  any    any     anywhere             anywhere             limit: avg 5/min burst 5 LOG level debug prefix "iptables denied: "
```

I copied this rule from the ubuntu iptables wiki. I still don't understand why I am not receiving these messages in syslog. They are only available in dmesg. It seems to me that syslog must be broken. No?

---

### Post by SeijiSensei on 2013-08-08
I see where the issue lies.  Iptables errors are logged by the kernel, so it uses the kern.* facility.  You have that directed to /var/log/kern.log in your syslog configuration. Try looking in that file.

---

### Post by J4nbhp4 on 2013-08-08
> **SeijiSensei said:**
> I see where the issue lies.  Iptables errors are logged by the kernel, so it uses the kern.* facility.  You have that directed to /var/log/kern.log in your syslog configuration. Try looking in that file.


I agree completely with you. But therein lies the problem. That file is completely empty. The /var/log/dmesg log file is completely empty to and yet all my iptable logs show up when I run the command $ dmesg

I am dumb founded, I do not understand why it is not working. You say that your logs are showing up in syslog. Can you copy and paste your /etc/syslog.conf so we can compare?

I have also tried kern.warning and kern.=debug /var/log/syslog and still nothing. Something is broken and I am not used to syslog, I am more used to syslog-ng

---

### Post by J4nbhp4 on 2013-08-08
ok. I seemed to have solved it. 

I think the issue lies in restarting the kernel log service after updating iptables.

$ sudo service klogd restart 

seemed to now give me a copy of the logs in everyone one of the log files I tried in syslog.conf :) so it works, should probably update the wiki

---

