---
title: "Log files not working"
date: 2012-08-13
forum: Server Platforms
---

### Post by Catalyph on 2012-08-13
I have Ubuntu server 11.10 installed and it has been running great for 10 8 months or so.
at one point i kept getting ssh attacks to i put a firewall on the system and then would periodically check the auth.log file to see how many attacks i was getting.

however this week i noticed that the auth.log file have not changed for 3 weeks.
and NONE of my ssh login atempts good or bad have been logged.

this was working fine up untill 3 weeks ago.

I looked around online and could not find much.
one person suggested it might be logrotate 
so i ran  

```
sudo logrotate --force --verbose /etc/logrotate.conf
```

Im wondering if the logging not working has anything to do with the  first couple lines saying Ignoring syslog-ng.disabled, because of  .disabled ending




the out put was :


```
reading config file /etc/logrotate.conf
including /etc/logrotate.d
Ignoring syslog-ng.disabled, because of .disabled ending
Ignoring rsyslog.disabled, because of .disabled ending
reading config file apport
reading config info for /var/log/apport.log
reading config file apt
reading config info for /var/log/apt/term.log
reading config info for /var/log/apt/history.log
reading config file aptitude
reading config info for /var/log/aptitude
reading config file atop
reading config info for /var/log/atop.log
reading config file dpkg
reading config info for /var/log/dpkg.log
reading config info for /var/log/alternatives.log
reading config file ppp
reading config info for /var/log/ppp-connect-errors
reading config file proftpd-basic
reading config info for /var/log/proftpd/proftpd.log
/var/log/proftpd/controls.log

reading config info for /var/log/proftpd/xferlog
/var/log/proftpd/xferreport

reading config file psaccs_atop
reading config info for /var/log/atop/dummy_before
reading config file psaccu_atop
reading config info for /var/log/atop/dummy_after
reading config file samba
reading config info for /var/log/samba/log.smbd
reading config info for /var/log/samba/log.nmbd
reading config file ufw
reading config info for /var/log/ufw.log

reading config file unattended-upgrades
reading config info for /var/log/unattended-upgrades/unattended-upgrades.log
reading config file winbind
reading config info for /var/log/samba/log.winbindd
reading config info for /var/log/wtmp
reading config info for /var/log/btmp

Handling 19 logs

rotating pattern: /var/log/apport.log  forced from command line (7 rotations)
empty log files are not rotated, old logs are removed
considering log /var/log/apport.log
  log /var/log/apport.log does not exist -- skipping

rotating pattern: /var/log/apt/term.log  forced from command line (12 rotations)
empty log files are not rotated, old logs are removed
considering log /var/log/apt/term.log
  log does not need rotating

rotating pattern: /var/log/apt/history.log  forced from command line (12 rotations)
empty log files are not rotated, old logs are removed
considering log /var/log/apt/history.log
  log does not need rotating

rotating pattern: /var/log/aptitude  forced from command line (6 rotations)
empty log files are not rotated, old logs are removed
considering log /var/log/aptitude
  log /var/log/aptitude does not exist -- skipping

rotating pattern: /var/log/atop.log  forced from command line (14 rotations)
empty log files are rotated, old logs are removed
considering log /var/log/atop.log
  log needs rotating
rotating log /var/log/atop.log, log->rotateCount is 14
dateext suffix '-20120813'
glob pattern '-[0-9][0-9][0-9][0-9][0-9][0-9][0-9][0-9]'
renaming /var/log/atop.log.14 to /var/log/atop.log.15 (rotatecount 14, logstart 1, i 14),
renaming /var/log/atop.log.13 to /var/log/atop.log.14 (rotatecount 14, logstart 1, i 13),
renaming /var/log/atop.log.12 to /var/log/atop.log.13 (rotatecount 14, logstart 1, i 12),
renaming /var/log/atop.log.11 to /var/log/atop.log.12 (rotatecount 14, logstart 1, i 11),
renaming /var/log/atop.log.10 to /var/log/atop.log.11 (rotatecount 14, logstart 1, i 10),
renaming /var/log/atop.log.9 to /var/log/atop.log.10 (rotatecount 14, logstart 1, i 9),
renaming /var/log/atop.log.8 to /var/log/atop.log.9 (rotatecount 14, logstart 1, i 8),
renaming /var/log/atop.log.7 to /var/log/atop.log.8 (rotatecount 14, logstart 1, i 7),
renaming /var/log/atop.log.6 to /var/log/atop.log.7 (rotatecount 14, logstart 1, i 6),
renaming /var/log/atop.log.5 to /var/log/atop.log.6 (rotatecount 14, logstart 1, i 5),
renaming /var/log/atop.log.4 to /var/log/atop.log.5 (rotatecount 14, logstart 1, i 4),
renaming /var/log/atop.log.3 to /var/log/atop.log.4 (rotatecount 14, logstart 1, i 3),
renaming /var/log/atop.log.2 to /var/log/atop.log.3 (rotatecount 14, logstart 1, i 2),
renaming /var/log/atop.log.1 to /var/log/atop.log.2 (rotatecount 14, logstart 1, i 1),
renaming /var/log/atop.log.0 to /var/log/atop.log.1 (rotatecount 14, logstart 1, i 0),
old log /var/log/atop.log.0 does not exist
running prerotate script
renaming /var/log/atop.log to /var/log/atop.log.1
running postrotate script
removing old log /var/log/atop.log.15

rotating pattern: /var/log/dpkg.log  forced from command line (12 rotations)
empty log files are not rotated, old logs are removed
considering log /var/log/dpkg.log
  log does not need rotating

rotating pattern: /var/log/alternatives.log  forced from command line (12 rotations)
empty log files are not rotated, old logs are removed
considering log /var/log/alternatives.log
  log does not need rotating

rotating pattern: /var/log/ppp-connect-errors  forced from command line (4 rotations)
empty log files are not rotated, old logs are removed
considering log /var/log/ppp-connect-errors
  log /var/log/ppp-connect-errors does not exist -- skipping

rotating pattern: /var/log/proftpd/proftpd.log
/var/log/proftpd/controls.log
 forced from command line (7 rotations)
empty log files are not rotated, old logs are removed
considering log /var/log/proftpd/proftpd.log
  log needs rotating
considering log /var/log/proftpd/controls.log
  log does not need rotating
rotating log /var/log/proftpd/proftpd.log, log->rotateCount is 7
dateext suffix '-20120813'
glob pattern '-[0-9][0-9][0-9][0-9][0-9][0-9][0-9][0-9]'
compressing log with: /bin/gzip
renaming /var/log/proftpd/proftpd.log.7.gz to /var/log/proftpd/proftpd.log.8.gz (rotatecount 7, logstart 1, i 7),
renaming /var/log/proftpd/proftpd.log.6.gz to /var/log/proftpd/proftpd.log.7.gz (rotatecount 7, logstart 1, i 6),
renaming /var/log/proftpd/proftpd.log.5.gz to /var/log/proftpd/proftpd.log.6.gz (rotatecount 7, logstart 1, i 5),
renaming /var/log/proftpd/proftpd.log.4.gz to /var/log/proftpd/proftpd.log.5.gz (rotatecount 7, logstart 1, i 4),
renaming /var/log/proftpd/proftpd.log.3.gz to /var/log/proftpd/proftpd.log.4.gz (rotatecount 7, logstart 1, i 3),
renaming /var/log/proftpd/proftpd.log.2.gz to /var/log/proftpd/proftpd.log.3.gz (rotatecount 7, logstart 1, i 2),
renaming /var/log/proftpd/proftpd.log.1.gz to /var/log/proftpd/proftpd.log.2.gz (rotatecount 7, logstart 1, i 1),
renaming /var/log/proftpd/proftpd.log.0.gz to /var/log/proftpd/proftpd.log.1.gz (rotatecount 7, logstart 1, i 0),
old log /var/log/proftpd/proftpd.log.0.gz does not exist
renaming /var/log/proftpd/proftpd.log to /var/log/proftpd/proftpd.log.1
creating new /var/log/proftpd/proftpd.log mode = 0640 uid = 0 gid = 4
running postrotate script
removing old log /var/log/proftpd/proftpd.log.8.gz

rotating pattern: /var/log/proftpd/xferlog
/var/log/proftpd/xferreport
 forced from command line (7 rotations)
empty log files are not rotated, old logs are removed
considering log /var/log/proftpd/xferlog
  log does not need rotating
considering log /var/log/proftpd/xferreport
  log does not need rotating
not running prerotate script, since no logs will be rotated
not running postrotate script, since no logs were rotated

rotating pattern: /var/log/atop/dummy_before  forced from command line (1 rotations)
empty log files are rotated, old logs are removed
considering log /var/log/atop/dummy_before
  log /var/log/atop/dummy_before does not exist -- skipping
not running postrotate script, since no logs were rotated

rotating pattern: /var/log/atop/dummy_after  forced from command line (1 rotations)
empty log files are rotated, old logs are removed
considering log /var/log/atop/dummy_after
  log /var/log/atop/dummy_after does not exist -- skipping
not running postrotate script, since no logs were rotated

rotating pattern: /var/log/samba/log.smbd  forced from command line (7 rotations)
empty log files are not rotated, old logs are removed
considering log /var/log/samba/log.smbd
  log needs rotating
rotating log /var/log/samba/log.smbd, log->rotateCount is 7
dateext suffix '-20120813'
glob pattern '-[0-9][0-9][0-9][0-9][0-9][0-9][0-9][0-9]'
renaming /var/log/samba/log.smbd.7.gz to /var/log/samba/log.smbd.8.gz (rotatecount 7, logstart 1, i 7),
renaming /var/log/samba/log.smbd.6.gz to /var/log/samba/log.smbd.7.gz (rotatecount 7, logstart 1, i 6),
renaming /var/log/samba/log.smbd.5.gz to /var/log/samba/log.smbd.6.gz (rotatecount 7, logstart 1, i 5),
renaming /var/log/samba/log.smbd.4.gz to /var/log/samba/log.smbd.5.gz (rotatecount 7, logstart 1, i 4),
renaming /var/log/samba/log.smbd.3.gz to /var/log/samba/log.smbd.4.gz (rotatecount 7, logstart 1, i 3),
renaming /var/log/samba/log.smbd.2.gz to /var/log/samba/log.smbd.3.gz (rotatecount 7, logstart 1, i 2),
renaming /var/log/samba/log.smbd.1.gz to /var/log/samba/log.smbd.2.gz (rotatecount 7, logstart 1, i 1),
renaming /var/log/samba/log.smbd.0.gz to /var/log/samba/log.smbd.1.gz (rotatecount 7, logstart 1, i 0),
old log /var/log/samba/log.smbd.0.gz does not exist
renaming /var/log/samba/log.smbd to /var/log/samba/log.smbd.1
creating new /var/log/samba/log.smbd mode = 0644 uid = 0 gid = 0
running postrotate script
compressing log with: /bin/gzip
removing old log /var/log/samba/log.smbd.8.gz

rotating pattern: /var/log/samba/log.nmbd  forced from command line (7 rotations)
empty log files are not rotated, old logs are removed
considering log /var/log/samba/log.nmbd
  log does not need rotating
not running postrotate script, since no logs were rotated

rotating pattern: /var/log/ufw.log
 forced from command line (4 rotations)
empty log files are not rotated, old logs are removed
considering log /var/log/ufw.log
  log does not need rotating
not running postrotate script, since no logs were rotated

rotating pattern: /var/log/unattended-upgrades/unattended-upgrades.log  forced from command line (6 rotations)
empty log files are not rotated, old logs are removed
considering log /var/log/unattended-upgrades/unattended-upgrades.log
  log /var/log/unattended-upgrades/unattended-upgrades.log does not exist -- skipping

rotating pattern: /var/log/samba/log.winbindd  forced from command line (7 rotations)
empty log files are not rotated, old logs are removed
considering log /var/log/samba/log.winbindd
  log does not need rotating
not running postrotate script, since no logs were rotated

rotating pattern: /var/log/wtmp  forced from command line (1 rotations)
empty log files are rotated, old logs are removed
considering log /var/log/wtmp
  log needs rotating
rotating log /var/log/wtmp, log->rotateCount is 1
dateext suffix '-20120813'
glob pattern '-[0-9][0-9][0-9][0-9][0-9][0-9][0-9][0-9]'
renaming /var/log/wtmp.1 to /var/log/wtmp.2 (rotatecount 1, logstart 1, i 1),
renaming /var/log/wtmp.0 to /var/log/wtmp.1 (rotatecount 1, logstart 1, i 0),
old log /var/log/wtmp.0 does not exist
renaming /var/log/wtmp to /var/log/wtmp.1
creating new /var/log/wtmp mode = 0664 uid = 0 gid = 43
removing old log /var/log/wtmp.2

rotating pattern: /var/log/btmp  forced from command line (1 rotations)
empty log files are rotated, old logs are removed
considering log /var/log/btmp
  log needs rotating
rotating log /var/log/btmp, log->rotateCount is 1
dateext suffix '-20120813'
glob pattern '-[0-9][0-9][0-9][0-9][0-9][0-9][0-9][0-9]'
renaming /var/log/btmp.1 to /var/log/btmp.2 (rotatecount 1, logstart 1, i 1),
renaming /var/log/btmp.0 to /var/log/btmp.1 (rotatecount 1, logstart 1, i 0),
old log /var/log/btmp.0 does not exist
renaming /var/log/btmp to /var/log/btmp.1
creating new /var/log/btmp mode = 0660 uid = 0 gid = 43
removing old log /var/log/btmp.2
UBserver@Vault:/etc/logrotate.d$


```

---

### Post by Catalyph on 2012-08-13
I had recently installed syslog-ng on the system, but the uninstalled (apt-get remove syslog-ng) thinking that my default logging with continue, im not sure if this is what caused the issue.

---

### Post by koenn on 2012-08-13
> **Catalyph said:**
> ...  thinking that my default logging would continue, ... 
that is very unlikely - I'd expect the syslog-ng package would have a "Conflict" with other similar loggers (sysklogd, rsyslog, ...) so when you install syslog-ng, the others get removed. So there's no fall-back when you uninstall syslog-ng.

You probably need to reinstall a logging daemon. rsyslog works very well.

---

### Post by Catalyph on 2012-08-13
is rsyslog the default for ubuntu 11.10 ?

---

### Post by koenn on 2012-08-13
> **Catalyph said:**
> is rsyslog the default for ubuntu 11.10 ?

don't know. It's the default in 12.04 but it is relatively new (to Debian standards) so I'm not sure when it started appearing in Ubuntu.

you could check the repo's eg
```

  :~$ apt-cache search rsyslog

...

rsyslog - enhanced multi-threaded syslogd
rsyslog-doc - documentation for rsyslog
rsyslog-gnutls - TLS protocol support for rsyslog
rsyslog-gssapi - GSSAPI authentication and encryption support for rsyslog
rsyslog-mysql - MySQL output plugin for rsyslog
rsyslog-pgsql - PostgreSQL output plugin for rsyslog
rsyslog-relp - RELP protocol support for rsyslog


```

---

### Post by koenn on 2012-08-13
scratch that

I'm still on 10.04 and it has rsyslog, so
yeah.

---

### Post by Catalyph on 2012-08-13
Should just reinstalling it work then ?
apt-get install rsyslog

or would i need to do anything else?

---

### Post by koenn on 2012-08-13
you need a config file, but normally one is installed by default.

Just try it already. What's the worst that can happen ?

---

### Post by Catalyph on 2012-08-15
OK I installed rsyslog.

apt-get install rsyslog

the auth.log file was created new with the current date, but there is nothing in it..

it is 0 bytes and has not gotten and bigger or any logging for 2 days?

and help on how to get my logging back to Ubuntu default would be awesome.

---

### Post by koenn on 2012-08-15
check if rsyslog is running. 

also check that there is a /etc/rsyslog.conf file and/or .conf files in /etc/rsyslog.d

---

### Post by smartboyhw on 2012-08-16
I'm a bit mystified...Why is the tag [Lubuntu]? This is about server, isn't it?

---

### Post by nothingspecial on 2012-08-16
Prefix changed from lubuntu to ubuntu.

---

### Post by Catalyph on 2012-08-17
```
user@Vault:~$ sudo service rsyslog status
[sudo] password for user:
rsyslog start/running, process 758
user@Vault:~$ lss /etc/ | grep rsys
-rw-r--r--   1 root root                1.2K 2011-06-17 13:13 rsyslog.conf
drwxr-xr-x   2 root root                4.0K 2012-04-15 19:26 rsyslog.d

user@Vault:~$ lss /etc/rsyslog.d
total 16K
drwxr-xr-x  2 root root 4.0K 2012-04-15 19:26 .
drwxr-xr-x 93 root root 4.0K 2012-08-16 14:25 ..
-rw-r--r--  1 root root  311 2011-07-18 18:30 20-ufw.conf
-rw-r--r--  1 root root 1.6K 2012-04-15 19:26 50-default.conf

```

---

### Post by Catalyph on 2012-08-17
Server is still not logging anything. still have a 0 size auth.log file.

although the rsyslog service is running and it does have .config files....

---

### Post by Catalyph on 2012-08-18
bump

---

### Post by koenn on 2012-08-20
suggestion :


temporarily replace your config file with one that only contains something like

```

*.*   /var/log/test.log

```
this should send any logging to the filer mentioned. 

don't forget to restart rsyslog, so it'll read the modified config

then, force a logging event by running something like
```

logger -p daemon.info "test"

```
this should put an entry in the logfile.


see what you get, take it from there.

---

### Post by koenn on 2012-08-20
see also:
[http://ubuntuforums.org/showthread.php?p=12177629](http://ubuntuforums.org/showthread.php?p=12177629)

---

### Post by cholericfun on 2012-08-24
Just having the same problem, hope its a bug and not a feature from the producer of the last entry

neither getting ssh logins nor anacron job or other sudo uses

sshd_config has 
```
# Logging
SyslogFacility AUTH
LogLevel INFO
```

last entry:
> Aug 24 00:57:58 PC_NAME sshd[23336]: Did not receive identification string from 123.189.4.148i set up sshd to only allow myself to login, maybe the username was too easy to guess. Also the port wasnt standard - at least to the outside.

taken the sshd off the port-forwading for now but somehow my X11 got screwed up...


Thinking back i uninstalles some of the unity stuff on this 12.04 machine, using gnome now.
Logs seem to have been working until shutdown, Not afterwards.

---

### Post by cholericfun on 2012-08-25
Hi, 
i didnt have any entries in auth.log and realized the permission have changed somehow (how is rather mysterious to me)
```
ll auth.log
```
was:
```
-rw-r----- 1 root root 0 Aug 25 11:26 auth.log
```
changed to
```
-rw-r----- 1 syslog root 619 Aug 25 11:26 auth.log
```
and immediatly fills up.
Anyone any ideas if this is indeed the right ownership of the file and why it could have changed (i installed and removed DesktopEnv related things, shouldnt be interfering with rsyslog)

---

### Post by LHammonds on 2012-08-25
> **cholericfun said:**
> Anyone any ideas if this is indeed the right ownership of the file and why it could have changed (i installed and removed DesktopEnv related things, shouldnt be interfering with rsyslog)

I have Ubuntu Server 12.04 LTS (64-bit) installed and this is the permission settings on my file:

```
-rw-r----- 1 syslog adm 61804 Aug 25 10:34 auth.log
```I verified it is the same on 5 other 12.04 servers I have running as well as 2 servers running 10.04.

As for ideas on how it changed, my initial thought would be that somebody issued a chown command using the recursive -R incorrectly.

Take a look by typing **ls -l /var/log** and see if everything was set to root:root.  There should be many files set to syslog:adm and some set to root:utmp and root:root

LHammonds

---

### Post by cholericfun on 2012-08-27
Hi

i mainly got root:root
some have other groups, but only the one syslog:adm that i manually changed for auth.conf

from a glance, the other logs that mean something to me seem to be filling.

@Catalyph, Have you had any luck with your install?

---

### Post by gemmajid on 2012-09-05
guys i having the same problem , my audit.log file doesn't making log it's empty kindly suggest me what to do ..

---

### Post by vwal on 2012-11-23
I just lost about an hour with this same problem until I came across this thread. The [post]("http://ubuntuforums.org/showpost.php?p=12194657&postcount=19") by **cholericfun** was the solution for me: the ownership of auth.log had changed! Like **Catalyph**, I also had installed, and then removed syslog-ng, but I did not change the ownership of auth.log, so my guess is that syslog-ng installation changes the file's ownership, and when I backed out to rsyslog (i.e. reinstalled it and ubuntu-minimal), the  ownership of auth.log wasn't reset to the original "syslog.adm".

---

