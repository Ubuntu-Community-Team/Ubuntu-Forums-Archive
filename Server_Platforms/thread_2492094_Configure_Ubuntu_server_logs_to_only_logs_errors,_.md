---
title: "Configure Ubuntu server logs to only logs errors, and nothing else"
date: 2023-10-30
forum: Server Platforms
---

### Post by leonbrag on 2023-10-30
Hello,

Objective: configure ALL Ubuntu server logs to only log errors, and nothing else.

```
pi@beachpi:/etc/rsyslog.d$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 22.04.3 LTS
Release:        22.04
Codename:       jammy

```
My understanding is that I need to modify /etc/rsyslog.d/50-default.conf 

This is how file looks now:

```
pi@beachpi:/etc/rsyslog.d$ cat 50-default.conf
#  Default rules for rsyslog.
#
#                       For more information see rsyslog.conf(5) and /etc/rsyslog.conf


#
# First some standard log files.  Log by facility.
#
auth,authpriv.*                 /var/log/auth.log
*.*;auth,authpriv.none          -/var/log/syslog
#cron.*                         /var/log/cron.log
#daemon.*                       -/var/log/daemon.log
kern.*                          -/var/log/kern.log
#lpr.*                          -/var/log/lpr.log
mail.*                          -/var/log/mail.log
#user.*                         -/var/log/user.log


#
# Logging for the mail system.  Split it up so that
# it is easy to write scripts to parse these files.
#
#mail.info                      -/var/log/mail.info
#mail.warn                      -/var/log/mail.warn
mail.err                        /var/log/mail.err


#
# Some "catch-all" log files.
#
#*.=debug;\
#       auth,authpriv.none;\
#       news.none;mail.none     -/var/log/debug
#*.=info;*.=notice;*.=warn;\
#       auth,authpriv.none;\
#       cron,daemon.none;\
#       mail,news.none          -/var/log/messages


#
# Emergencies are sent to everybody logged in.
#
*.emerg                         :omusrmsg:*


#
# I like to have messages displayed on the console, but only on a virtual
# console I usually leave idle.
#
#daemon,mail.*;\
#       news.=crit;news.=err;news.=notice;\
#       *.=debug;*.=info;\
#       *.=notice;*.=warn       /dev/tty8

```
Question: what specific changes should I make to disable all messages other than errors ?

thanks !

---

### Post by coffeecat on 2023-10-30
Support, not chat.

*Thread moved to **Server Platforms**.*

---

### Post by TheFu on 2023-10-30
I don't know the answer, but syslog has been deprecated for 5+ yrs.  Logs have been managed by journald and the journalctl since 2016. Settings for it are in /etc/systemd/journald.conf and the documentation for it is in the manpage for journald.conf.  You can look up the answer there, just like anyone else can.

A taste from the manpage:
```
       MaxLevelStore=, MaxLevelSyslog=, MaxLevelKMsg=,
       MaxLevelConsole=, MaxLevelWall=
           Controls the maximum log level of messages that are
           stored in the journal, forwarded to syslog, kmsg,
           the console or wall (if that is enabled, see above).
           As argument, takes one of "emerg", "alert", "crit",
           "err", "warning", "notice", "info", "debug", or
           integer values in the range of 0–7 (corresponding to
           the same levels).
```

BTW, Debian 12 doesn't bother with any text logs, at least not in the install I played with a few months ago.  no more syslog, messages, auth.log ... everything was only accessible through **journalctl**.  The migration from text logs to a binary log format used by journald is nearly complete. Also, of all the things I dislike about systemd, there is 1 extremely awesome spot - journald.  It is amazing and provides fantastic controls over logs and transmission to a centralized log server along with easy filtering of the logs by user, error level, process.  It is amazing and can be really easy to use for non-experts as well.   There are many 1 page cheat sheets that show the power of journalctl.

---

### Post by MAFoElffen on 2023-10-30
+1 -- 

"journald and journctl"

When it first arrived I balked at using it just because it was new and different. I'm old, and used to doing things a certain way with some things. I have my comfort zones. But I forced myself to learn and use it. It took me a while. 

But now that I know "how to use it", it makes things so much easier. It is now understood by me as a very welcome change.

I like that you can do queries, and retrieve the format in json, to use with other management tools. It really opened up a lot of possibilities.

---

### Post by leonbrag on 2023-10-30
In my box (set w/out any customization) rsyslog is running just fine, by default:

pi@beachpi:~$ systemctl status rsyslog
&#9679; rsyslog.service - System Logging Service
     Loaded: loaded (/lib/systemd/system/rsyslog.service; enabled; vendor preset: enabled)
     Active: active (running) since Thu 2023-10-26 16:35:26 PDT; 3 days ago
TriggeredBy: &#9679; syslog.socket
       Docs: man:rsyslogd(8)
             man:rsyslog.conf(5)
             [https://www.rsyslog.com/doc/](https://www.rsyslog.com/doc/)
   Main PID: 670 (rsyslogd)
      Tasks: 4 (limit: 366)
     Memory: 1.9M
        CPU: 1.690s
     CGroup: /system.slice/rsyslog.service
             &#9492;&#9472;670 /usr/sbin/rsyslogd -n -iNONE

Note, in my original posts all the directories and conf files are from rsyslog, not syslog.

I have changed journald setting to set max to "err". 

Can someone un-confuse me with relationship between these two facilities that are both running: rsyslogd and journald

I am not using any remote log capturing, forwarding.

---

### Post by MAFoElffen on 2023-10-30
> 
The systemd-journald service does not keep separate files, as rsyslog does. The idea is to avoid checking different files for issues. Systemd-journald saves the events and messages in a binary format that cannot be read with a text editor. You can query the journal with the journalctl command.

If I want to know something, I'll often refer to my RedHat Doc's. I do RedHat also, and they just have better SysAdmin documentation. From RedHat:
> 
Syslog and rsyslog have long been used to provide logging on Linux servers. Systemd became the default service manager with Red Hat Enterprise Linux (RHEL) 7, and it introduced its own logging system called systemd-journald. systemd-journald continues to be the logging mechanism on RHEL 8 and 9 while keeping rsyslog for backward compatibility.
...
The systemd-journald service does not keep separate files, as rsyslog does. The idea is to avoid checking different files for issues. Systemd-journald saves the events and messages in a binary format that cannot be read with a text editor. You can query the journal with the journalctl command.
...
RHEL 8 and 9 servers use both rsyslog and systemd-journald, and they complement each other to perform logging. Systemd-journald does not have a mechanism to forward logs to external systems and monitoring applications. A configuration modifies this in the /etc/systemd/journald.conf. The ForwardToSyslog parameter defines whether entries in the journal should be forwarded to syslog. When enabled, syslog then captures the entries as they come through systemd-journald and forwards them accordingly.

So a lot of people feel that rsyslogd generates duplication's of log files, where the information is already stored on the system... But rsyslogd is still needed to forward logs remotely. I don't know if that is a feature they will add to systemd-journald, but in my logic, if they added that, that would then make rsyslogd unneeded. Right?

[s]I don't know if that is in the future plans.[/s] Or am I missing something with that?

EDIT:
Dang. LOL. Found it: 'systemd-journal-remote' & 'systemd-journal-upload' <-- I guess I need to test these in DEV Noble Server to see if these are worked out for us yet. I see some issues filed on these in systemd.

---

