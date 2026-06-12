---
title: "ssh.log"
date: 2006-03-27
forum: Server Platforms
---

### Post by echo $USER on 2006-03-27
I can't find the ssh logs.

*****@ubuntu:/var/log$ whereis ssh
ssh: /usr/bin/ssh /etc/ssh /usr/bin/X11/ssh /usr/share/man/man1/ssh.1.gz

Where are they?  Thanks!  And is there a place were log files store write conversations with other users logged in?

---

### Post by claes on 2006-03-28
Does whereis show log files? If I remember correctly it only shows program-, man- and configuration files.

Check /var/log

Claes

---

### Post by echo $USER on 2006-03-29
*******@ubuntu:/var$ ls
backups  games  local  log   music  run    tmp
cache    lib    lock   mail  opt    spool  www
media@ubuntu:/var$ cd log
media@ubuntu:/var/log$ ls
acpid                   debug.2.gz         mail.err.0      samba
acpid.1.gz              debug.3.gz         mail.info       scrollkeeper.log
acpid.2.gz              dmesg              mail.info.0     scrollkeeper.log.1
acpid.3.gz              dpkg.log           mail.log        scrollkeeper.log.2
acpid.4.gz              dpkg.log.1         mail.log.0      squid
apache2                 evms-engine.1.log  mail.warn       syslog
aptitude                evms-engine.2.log  mail.warn.0     syslog.0
aptitude.1.gz           evms-engine.3.log  messages        syslog.1.gz
auth.log                evms-engine.4.log  messages.0      syslog.2.gz
auth.log.0              evms-engine.5.log  messages.1.gz   syslog.3.gz
auth.log.1.gz           evms-engine.6.log  messages.2.gz   syslog.4.gz
auth.log.2.gz           evms-engine.7.log  messages.3.gz   syslog.5.gz
auth.log.3.gz           evms-engine.8.log  mysql           syslog.6.gz
base-config.log.1       evms-engine.9.log  mysql.err       user.log
base-config-pkgsel.log  evms-engine.log    mysql.err.1.gz  user.log.0
base-config.timings.1   faillog            mysql.err.2.gz  user.log.1.gz
btmp                    fontconfig.log     mysql.err.3.gz  user.log.2.gz
btmp.1                  gdm                mysql.err.4.gz  user.log.3.gz
cups                    gnump3d            mysql.err.5.gz  uucp.log
daemon.log              installer          mysql.err.6.gz  vsftpd.log
daemon.log.0            kern.log           mysql.log       vsftpd.log.1
daemon.log.1.gz         kern.log.0         mysql.log.1.gz  wtmp
daemon.log.2.gz         kern.log.1.gz      mysql.log.2.gz  wtmp.1
daemon.log.3.gz         kern.log.2.gz      mysql.log.3.gz  Xorg.0.log
debian-installer        kern.log.3.gz      mysql.log.4.gz  Xorg.0.log.old
debug                   lastlog            mysql.log.5.gz
debug.0                 lpr.log            mysql.log.6.gz
debug.1.gz              mail.err           news
*******@ubuntu:/var/log$

---

### Post by diebels on 2006-03-29
ssh logins are in /var/log/auth.log

See ~/.bash_history for commands run. This can be altered by the user.

Maybe you want to set up something with```
/usr/bin/script
```

---

### Post by echo $USER on 2006-03-30
[QUOTE=diebels]ssh logins are in /var/log/auth.log

See ~/.bash_history for commands run. This can be altered by the user.

Maybe you want to set up something with```
/usr/bin/script
```[/QUOTE]

thanks for the info.

---

