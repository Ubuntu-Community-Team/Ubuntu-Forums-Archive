---
title: "/etc/cron.daily/logrotate: Re-opening all log files"
date: 2008-06-09
forum: Server Platforms
---

### Post by robinbillings on 2008-06-09
I am running a server using Hardy and had both gnome and kde desktops installed.  Since I didn't know about tasksel, I used synaptics to remove KDE and all applications related to KDE.  The system boots fine into gnome, but each day I get a message from anacron 'cron.daily' as follows:

/etc/cron.daily/logrotate:
Re-opening all log files

What could be causing this?  Any suggestions on which log file I should inspect to trace this error down?

Thank you!

Robin Billings

---

### Post by RealPSL on 2008-06-11
logrotate is used to rotate log files so they do not grow to ridiculous sizes and fill up drives. Yours best bet to might be to run ```
logrotate -dv 
``` to try to find out if you have a real problem.

---

### Post by robinbillings on 2008-06-12
This is what sudo logrotate -d -v does:

:~$ sudo sudo logrotate -d -v

logrotate 3.7.1 - Copyright (C) 1995-2001 Red Hat, Inc.
This may be freely redistributed under the terms of the GNU Public License

Usage: logrotate [-dfv?] [-d|--debug] [-f|--force] [-m|--mail command]
        [-s|--state statefile] [-v|--verbose] [-?|--help] [--usage]
        [OPTION...] <configfile>

Is there a configfile I should be specifying?

Robin

---

### Post by robinbillings on 2008-06-12
sudo logrotate -vf /etc/logrotate.conf

---------------------
reading config file /etc/logrotate.conf
including /etc/logrotate.d
reading config file acpid
reading config info for /var/log/acpid
reading config file apache2
reading config info for /var/log/apache2/*.log
reading config file apport
reading config info for /var/log/apport.log
reading config file apt
reading config info for /var/log/apt/term.log
reading config file aptitude
reading config info for /var/log/aptitude
reading config file clamav-daemon
reading config info for /var/log/clamav/clamav.log
reading config file clamav-freshclam
reading config info for /var/log/clamav/freshclam.log
reading config file cupsys
reading config info for /var/log/cups/*log
reading config file dirmngr
reading config info for /var/log/dirmngr.log
reading config file dpkg
reading config info for /var/log/dpkg.log
reading config file mailman
reading config info for /var/log/mailman/vette /var/log/mailman/error /var/log/mailman/bounce
reading config info for /var/log/mailman/digest
reading config info for /var/log/mailman/subscribe /var/log/mailman/post
reading config info for /var/log/mailman/qrunner /var/log/mailman/fromusenet /var/log/mailman/locks /var/log/mailman/smtp /var/log/mailman/smtp-failure
reading config file mysql-server
reading config info for /var/log/mysql.log /var/log/mysql/mysql.log /var/log/mysql/mysql-slow.log
reading config file ppp
reading config info for /var/log/ppp-connect-errors
reading config file razor
reading config info for /var/log/razor-agent.log
reading config file samba
reading config info for /var/log/samba/log.smbd
reading config info for /var/log/samba/log.nmbd
reading config file scrollkeeper
reading config info for /var/log/scrollkeeper.log
reading config file unattended-upgrades
reading config info for /var/log/unattended-upgrades/unattended-upgrades.log
reading config file vsftpd
reading config info for /var/log/vsftpd.log
reading config file winbind
reading config info for /var/log/samba/log.winbindd
reading config file wpa_action
reading config info for /var/log/wpa_action.log
reading config info for /var/log/wtmp
reading config info for /var/log/btmp

Handling 26 logs

rotating pattern: /var/log/acpid  weekly (4 rotations)
empty log files are rotated, old logs are removed
considering log /var/log/acpid
  log /var/log/acpid does not exist -- skipping

rotating pattern: /var/log/apache2/*.log  weekly (52 rotations)
empty log files are not rotated, old logs are removed
considering log /var/log/apache2/access.log
  log does not need rotating
considering log /var/log/apache2/error.log
  log does not need rotating
not running shared postrotate script, since no logs were rotated

rotating pattern: /var/log/apport.log  after 1 days (7 rotations)
empty log files are not rotated, old logs are removed
considering log /var/log/apport.log
  log does not need rotating

rotating pattern: /var/log/apt/term.log  monthly (6 rotations)
empty log files are not rotated, old logs are removed
considering log /var/log/apt/term.log
  log does not need rotating

rotating pattern: /var/log/aptitude  monthly (6 rotations)
empty log files are not rotated, old logs are removed
considering log /var/log/aptitude
  log does not need rotating

rotating pattern: /var/log/clamav/clamav.log  weekly (12 rotations)
empty log files are rotated, old logs are removed
considering log /var/log/clamav/clamav.log
  log does not need rotating

rotating pattern: /var/log/clamav/freshclam.log  weekly (12 rotations)
empty log files are rotated, old logs are removed
considering log /var/log/clamav/freshclam.log
  log does not need rotating

rotating pattern: /var/log/cups/*log  after 1 days (7 rotations)
empty log files are not rotated, old logs are removed
considering log /var/log/cups/access_log
  log does not need rotating
considering log /var/log/cups/cups-pdf_log
  log does not need rotating
considering log /var/log/cups/error_log
  log does not need rotating
considering log /var/log/cups/page_log
  log does not need rotating
not running shared postrotate script, since no logs were rotated

rotating pattern: /var/log/dirmngr.log  weekly (4 rotations)
empty log files are not rotated, old logs are removed
considering log /var/log/dirmngr.log
  log does not need rotating

rotating pattern: /var/log/dpkg.log  monthly (12 rotations)
empty log files are not rotated, old logs are removed
considering log /var/log/dpkg.log
  log does not need rotating

rotating pattern: /var/log/mailman/vette /var/log/mailman/error /var/log/mailman/bounce  weekly (4 rotations)
empty log files are rotated, old logs are removed
considering log /var/log/mailman/vette
  log /var/log/mailman/vette does not exist -- skipping
considering log /var/log/mailman/error
  log does not need rotating
considering log /var/log/mailman/bounce
  log /var/log/mailman/bounce does not exist -- skipping
not running shared postrotate script, since no logs were rotated

rotating pattern: /var/log/mailman/digest  monthly (4 rotations)
empty log files are rotated, old logs are removed
considering log /var/log/mailman/digest
  log /var/log/mailman/digest does not exist -- skipping
not running shared postrotate script, since no logs were rotated

rotating pattern: /var/log/mailman/subscribe /var/log/mailman/post  monthly (12 rotations)
empty log files are rotated, old logs are removed
considering log /var/log/mailman/subscribe
  log does not need rotating
considering log /var/log/mailman/post
  log /var/log/mailman/post does not exist -- skipping
not running shared postrotate script, since no logs were rotated

rotating pattern: /var/log/mailman/qrunner /var/log/mailman/fromusenet /var/log/mailman/locks /var/log/mailman/smtp /var/log/mailman/smtp-failure  after 1 days (7 rotations)
empty log files are rotated, old logs are removed
considering log /var/log/mailman/qrunner
  log does not need rotating
considering log /var/log/mailman/fromusenet
  log /var/log/mailman/fromusenet does not exist -- skipping
considering log /var/log/mailman/locks
  log /var/log/mailman/locks does not exist -- skipping
considering log /var/log/mailman/smtp
  log does not need rotating
considering log /var/log/mailman/smtp-failure
  log /var/log/mailman/smtp-failure does not exist -- skipping
not running shared postrotate script, since no logs were rotated

rotating pattern: /var/log/mysql.log /var/log/mysql/mysql.log /var/log/mysql/mysql-slow.log  after 1 days (7 rotations)
empty log files are rotated, old logs are removed
considering log /var/log/mysql.log
  log does not need rotating
considering log /var/log/mysql/mysql.log
  log /var/log/mysql/mysql.log does not exist -- skipping
considering log /var/log/mysql/mysql-slow.log
  log /var/log/mysql/mysql-slow.log does not exist -- skipping
not running shared postrotate script, since no logs were rotated

rotating pattern: /var/log/ppp-connect-errors  weekly (4 rotations)
empty log files are not rotated, old logs are removed
considering log /var/log/ppp-connect-errors
  log /var/log/ppp-connect-errors does not exist -- skipping

rotating pattern: /var/log/razor-agent.log  weekly (3 rotations)
empty log files are not rotated, old logs are removed
considering log /var/log/razor-agent.log
  log does not need rotating

rotating pattern: /var/log/samba/log.smbd  weekly (7 rotations)
empty log files are not rotated, old logs are removed
considering log /var/log/samba/log.smbd
  log does not need rotating

rotating pattern: /var/log/samba/log.nmbd  weekly (7 rotations)
empty log files are not rotated, old logs are removed
considering log /var/log/samba/log.nmbd
  log does not need rotating

rotating pattern: /var/log/scrollkeeper.log  weekly (2 rotations)
empty log files are rotated, old logs are removed
considering log /var/log/scrollkeeper.log
  log does not need rotating

rotating pattern: /var/log/unattended-upgrades/unattended-upgrades.log  monthly (6 rotations)
empty log files are not rotated, old logs are removed
considering log /var/log/unattended-upgrades/unattended-upgrades.log
  log /var/log/unattended-upgrades/unattended-upgrades.log does not exist -- skipping

rotating pattern: /var/log/vsftpd.log  weekly (4 rotations)
empty log files are not rotated, old logs are removed
considering log /var/log/vsftpd.log
  log does not need rotating

rotating pattern: /var/log/samba/log.winbindd  weekly (7 rotations)
empty log files are not rotated, old logs are removed
considering log /var/log/samba/log.winbindd
  log does not need rotating

rotating pattern: /var/log/wpa_action.log  after 1 days (5 rotations)
empty log files are rotated, old logs are removed
considering log /var/log/wpa_action.log
  log /var/log/wpa_action.log does not exist -- skipping

rotating pattern: /var/log/wtmp  monthly (1 rotations)
empty log files are rotated, old logs are removed
considering log /var/log/wtmp
  log does not need rotating

rotating pattern: /var/log/btmp  monthly (1 rotations)
empty log files are rotated, old logs are removed
considering log /var/log/btmp
  log does not need rotating
--------------------------------------

Not sure what here would be causing cron.daily to send the message.  Is there a way to turn off the message?

Robin

---

### Post by MJN on 2008-06-13
Are you using (have installed) mailman? This used to exhibit the same problem following a successfull log rotation however it was fixed in v2.1.9-10. Try an upgrade if this applies to you.
 
Mathew

---

### Post by robinbillings on 2008-06-13
I am using mailman.  Version 1.2.1.9-9u appears to be installed.  I will upgrade and see if that solves the problem.

Thank you.

Robin

---

### Post by robinbillings on 2008-06-16
Actually,

I have 2.1.9 installed, so I doubt that's it.  Is there a way to just turn off this notification?


Robin

---

### Post by MJN on 2008-06-16
> **robinbillings said:**
> Actually,

I have 2.1.9 installed, so I doubt that's it.

I'm not sure I follow your logic - it is fixed in v2.1.9-10 - this is greater than v2.1.9 (or v2.1.9-9u that you said you had). This version however has yet to reach Hardy (and may well not do given it is non-urgent).

> Is there a way to just turn off this notification?Do you have a /etc/logrotate.d/mailman config file that controls the rotation?

Mathew

---

### Post by pearcec on 2008-06-30
> **robinbillings said:**
> I am running a server using Hardy and had both gnome and kde desktops installed.  Since I didn't know about tasksel, I used synaptics to remove KDE and all applications related to KDE.  The system boots fine into gnome, but each day I get a message from anacron 'cron.daily' as follows:

/etc/cron.daily/logrotate:
Re-opening all log files

What could be causing this?  Any suggestions on which log file I should inspect to trace this error down?

Thank you!

Robin Billings

Try the patch I posted here.

[https://bugs.launchpad.net/ubuntu/+source/mailman/+bug/244233](https://bugs.launchpad.net/ubuntu/+source/mailman/+bug/244233)

---

