---
title: "slapd.conf error after install (openldap)"
date: 2009-05-27
forum: Server Platforms
---

### Post by ghen on 2009-05-27
Running 8.04 server
following this guide: [http://www.rrcomputerconsulting.com/view.php?article_id=3#11](http://www.rrcomputerconsulting.com/view.php?article_id=3#11)


after running sudo dpkg-reconfigure slapd and choosing the options in the guide with minor differences I get the following error message when I try to start slapd:

```
No Configuration file was found for slapd at /etc/ldap/slapd.conf.
If you have moved the slapd configuration file please modify
/etc/default/slapd to reflect this. If you choose not to configure slapd 
during installation then you need to do so prior to attempting to start slapd.
```

I rebooted the system and tried to start slapd (sudo /etc/init.d/slapd start) and got this:

```
Starting OpenLDAP: (slapd running, no recovery), slapd - failed.
The operation failed but no output was produced. For hints on what went
wrong please refer to the system's logfiles (e.g. /var/log/syslog) or
try running the daemon in Debug mode like via "slapd -d 16383" (warning:
this will create copious output).

Below you can find the command line options used by this script to run slapd. 
Do not forget to specify those options if you want to look to debugging output:
   slapd -g openldap -u openldap -f /etc/ldap/slapd.conf
```

/var/log/syslog says:
```
slapd[4567]: /etc/ldap/slapd.conf: line 63: invalid path: Permission denied
```

ls -l /etc/ldap says (only showing the slapd.conf line)

```

-rw-r----- 1 openldap openldap 4748 2009-5-27 11:17 slapd.conf

```
I checked /etc/default/slapd, the file exists and states the default has not changed.

I checked /etc/ldap/slapd.conf and it also exists with no strange settings.

---

### Post by samosamo on 2009-05-27
we can't help you if you don't post the contents of both /etc/default and /etc files.

the ubuntu community documentation is pretty good. i suggest you use that next time.

---

### Post by ghen on 2009-05-28
I've been RTFMing the entire internet for a week now. If I missed your one perfect document that explains the issue then I'm sorry.


is this what you requested?

```

ls -l /etc/default
total 64
-rw-r--r-- 1 root root   47 2008-04-18 12:02 bootlogd
-rw-r--r-- 1 root root  475 2009-05-27 10:12 console-setup
-rw-r--r-- 1 root root   92 2008-04-18 12:02 devpts
-rw-r--r-- 1 root root   86 2008-04-18 12:02 halt
-rw-r--r-- 1 root root  313 2007-11-23 04:02 klogd
-rw-r--r-- 1 root root   19 2009-05-27 10:12 locale
-rw-r--r-- 1 root root   15 2009-05-13 17:05 ntp
-rw-r--r-- 1 root root  456 2009-01-06 10:49 ntpdate
-rw-r--r-- 1 root root  260 2009-05-27 10:28 rcS
-rw-r--r-- 1 root root 1352 2008-04-10 20:11 rsync
-rw-r--r-- 1 root root 1800 2009-05-27 11:42 slapd
-rw-r--r-- 1 root root  301 2008-05-14 10:39 ssh
-rw-r--r-- 1 root root  186 2007-11-23 04:02 syslogd
-rw-r--r-- 1 root root  289 2008-04-18 12:02 tmpfs
-rw-r--r-- 1 root root  922 2009-01-20 07:51 ufw
-rw-r--r-- 1 root root 1118 2008-12-08 04:13 useradd

```

```
ls -l /etc
total 900
-rw-r--r-- 1 root     root       2975 2009-05-27 10:12 adduser.conf
-rw-r--r-- 1 root     root         46 2009-05-27 11:32 adjtime
-rw-r--r-- 1 root     root         54 2009-05-27 10:28 aliases
-rw-r--r-- 1 root     root      12288 2009-05-27 11:12 aliases.db
drwxr-xr-x 2 root     root       4096 2009-05-27 10:26 alternatives
drwxr-xr-x 3 root     root       4096 2009-05-27 10:26 apm
drwxr-xr-x 2 root     root       4096 2009-05-27 10:39 apparmor
drwxr-xr-x 6 root     root       4096 2009-05-27 11:14 apparmor.d
drwxr-xr-x 4 root     root       4096 2009-05-27 10:28 apt
-rw-r----- 1 root     daemon      144 2007-02-20 09:05 at.deny
-rw-r--r-- 1 root     root       1733 2008-05-12 14:36 bash.bashrc
-rw-r--r-- 1 root     root     216529 2008-04-14 21:45 bash_completion
drwxr-xr-x 2 root     root       4096 2009-05-27 10:26 bash_completion.d
drwxr-xr-x 2 root     root       4096 2009-05-27 10:12 belocs
-rw-r--r-- 1 root     root        332 2008-09-12 09:20 bindresvport.blacklist
-rw-r--r-- 1 root     root        460 2009-05-27 10:39 blkid.tab
-rw-r--r-- 1 root     root        460 2009-05-27 10:38 blkid.tab.old
drwxr-xr-x 2 root     root       4096 2009-05-27 10:26 calendar
drwxr-s--- 2 root     dip        4096 2009-05-27 10:26 chatscripts
drwxr-xr-x 2 root     root       4096 2009-05-27 10:12 console-setup
drwxr-xr-x 2 root     root       4096 2009-05-27 10:12 console-tools
drwxr-xr-x 2 root     root       4096 2009-05-27 10:26 cron.d
drwxr-xr-x 2 root     root       4096 2009-05-27 11:01 cron.daily
drwxr-xr-x 2 root     root       4096 2009-05-27 10:26 cron.hourly
drwxr-xr-x 2 root     root       4096 2009-05-27 10:26 cron.monthly
-rw-r--r-- 1 root     root        724 2008-04-08 14:13 crontab
drwxr-xr-x 2 root     root       4096 2009-05-27 10:26 cron.weekly
-rw-r--r-- 1 root     root       2969 2008-03-11 11:51 debconf.conf
-rw-r--r-- 1 root     root         10 2007-10-20 07:51 debian_version
drwxr-xr-x 2 root     root       4096 2009-05-27 11:31 default
-rw-r--r-- 1 root     root        600 2007-10-23 11:01 deluser.conf
drwxr-xr-x 2 root     root       4096 2009-05-27 10:12 depmod.d
drwxr-xr-x 4 root     root       4096 2009-05-27 10:12 dhcp3
drwxr-xr-x 3 root     root       4096 2009-05-27 10:12 dpkg
-rw-r--r-- 1 root     root         34 2008-02-18 23:33 e2fsck.conf
-rw-r--r-- 1 root     root         79 2009-05-27 10:12 environment
drwxr-xr-x 2 root     root       4096 2009-05-27 10:12 event.d
-rw-r--r-- 1 root     root        354 2007-03-05 11:23 fdmount.conf
-rw-r--r-- 1 root     root        555 2009-05-27 10:11 fstab
-rw-r----- 1 root     fuse        216 2008-02-26 13:25 fuse.conf
-rw-r--r-- 1 root     root       2689 2008-09-12 09:20 gai.conf
drwxr-xr-x 2 root     root       4096 2009-05-27 10:26 groff
-rw-r--r-- 1 root     root        826 2009-05-27 11:14 group
-rw------- 1 root     root        810 2009-05-27 11:12 group-
drwxr-xr-x 2 root     root       4096 2009-05-27 10:26 grub.d
-rw-r----- 1 root     shadow      696 2009-05-27 11:14 gshadow
-rw------- 1 root     root        683 2009-05-27 11:12 gshadow-
-rw-r--r-- 1 root     root       4793 2008-03-28 18:27 hdparm.conf
-rw-r--r-- 1 root     root         92 2007-10-20 07:51 host.conf
-rw-r--r-- 1 root     root         15 2009-05-27 10:11 hostname
-rw-r--r-- 1 root     root        255 2009-05-27 10:58 hosts
-rw-r--r-- 1 root     root        579 2009-05-27 10:12 hosts.allow
-rw-r--r-- 1 root     root        878 2009-05-27 10:12 hosts.deny
-rw-r--r-- 1 root     root          0 2009-05-27 11:12 inetd.conf
drwxr-xr-x 2 root     root       4096 2009-05-27 11:31 init.d
drwxr-xr-x 5 root     root       4096 2009-05-27 10:12 initramfs-tools
-rw-r--r-- 1 root     root       1723 2007-10-02 10:35 inputrc
drwxr-xr-x 2 root     root       4096 2009-05-27 10:12 iproute2
-rw-r--r-- 1 root     root         21 2008-12-15 13:41 issue
-rw-r--r-- 1 root     root         14 2008-12-15 13:41 issue.net
-rw-r--r-- 1 root     root        240 2009-05-27 10:28 kernel-img.conf
drwxr-xr-x 4 openldap openldap   4096 2009-05-27 11:15 ldap
-rw-r--r-- 1 root     root      10174 2009-05-27 11:31 ld.so.cache
-rw-r--r-- 1 root     root         34 2009-05-27 10:11 ld.so.conf
drwxr-xr-x 2 root     root       4096 2009-05-27 10:11 ld.so.conf.d
-rw-r--r-- 1 root     root       2586 2008-03-11 07:02 locale.alias
-rw-r--r-- 1 root     root       3519 2009-05-27 10:39 localtime
drwxr-xr-x 3 root     root       4096 2009-05-27 10:12 logcheck
-rw-r--r-- 1 root     root       9681 2008-12-08 04:13 login.defs
-rw-r--r-- 1 root     root        599 2008-10-09 16:06 logrotate.conf
drwxr-xr-x 2 root     root       4096 2009-05-27 10:38 logrotate.d
drwxr-xr-x 2 root     root       4096 2008-03-26 14:23 lsb-base
-rw-r--r-- 1 root     root       3820 2008-03-10 15:00 lsb-base-logging.sh
-rw-r--r-- 1 root     root         98 2008-12-15 09:17 lsb-release
-rw-r--r-- 1 root     root      13144 2007-11-16 07:12 ltrace.conf
-rw-r--r-- 1 root     root        111 2008-06-10 04:44 magic
-rw-r--r-- 1 root     root        111 2008-06-10 04:44 magic.mime
-rw-r--r-- 1 root     root       2132 2009-05-27 10:26 mailcap
-rw-r--r-- 1 root     root        449 2008-04-01 14:11 mailcap.order
-rw-r--r-- 1 root     root         15 2009-05-27 11:12 mailname
-rw-r--r-- 1 root     root        125 2007-10-24 08:27 mail.rc
-rw-r--r-- 1 root     root       4624 2008-03-12 09:28 manpath.config
-rw-r--r-- 1 root     root      11742 2007-03-05 11:23 mediaprm
drwxr-xr-x 2 root     root       4096 2009-05-27 11:14 migrationtools
-rw-r--r-- 1 root     root      20891 2008-04-01 14:11 mime.types
-rw-r--r-- 1 root     root        417 2008-03-27 13:25 mke2fs.conf
drwxr-xr-x 3 root     root       4096 2009-05-27 10:26 modprobe.d
-rw-r--r-- 1 root     root        212 2009-05-27 10:26 modules
lrwxrwxrwx 1 root     root         13 2009-05-27 10:12 motd -> /var/run/motd
-rw-r--r-- 1 root     root        346 2009-05-27 10:12 motd.tail
-rw-r--r-- 1 root     root        414 2009-05-27 11:33 mtab
-rw-r--r-- 1 root     root       7672 2008-04-08 05:15 nanorc
drwxr-xr-x 6 root     root       4096 2009-05-27 10:12 network
-rw-r--r-- 1 root     root         91 2007-05-15 12:07 networks
-rw-r--r-- 1 root     root        475 2007-10-20 07:51 nsswitch.conf
-rw-r--r-- 1 root     root       1652 2009-05-27 11:03 ntp.conf
drwxr-xr-x 2 root     root       4096 2008-04-03 09:00 ODBCDataSources
-rw-r--r-- 1 root     root          0 2008-04-03 09:00 odbc.ini
-rw-r--r-- 1 root     root          0 2008-04-03 09:00 odbcinst.ini
drwxr-xr-x 2 root     root       4096 2009-05-27 10:11 opt
-rw-r--r-- 1 root     root        552 2008-05-16 11:18 pam.conf
drwxr-xr-x 2 root     root       4096 2009-05-27 11:31 pam.d
-rw-r--r-- 1 root     root       1153 2009-05-27 11:31 passwd
-rw------- 1 root     root       1153 2009-05-27 11:31 passwd-
drwxr-xr-x 2 root     root       4096 2009-05-27 10:12 pcmcia
drwxr-xr-x 4 root     root       4096 2009-05-27 10:26 perl
-rw-r--r-- 1 root     root        342 2009-05-27 10:26 popularity-contest.conf
drwxr-xr-x 3 root     root       4096 2009-05-27 11:12 postfix
drwxr-xr-x 8 root     dip        4096 2009-05-27 10:26 ppp
-rw-r--r-- 1 root     root        497 2009-05-27 10:12 profile
drwxr-xr-x 2 root     root       4096 2008-12-15 13:41 profile.d
-rw-r--r-- 1 root     root       2510 2007-12-03 17:04 protocols
drwxr-xr-x 2 root     root       4096 2009-05-27 10:12 python
drwxr-xr-x 2 root     root       4096 2009-05-27 10:12 python2.5
drwxr-xr-x 2 root     root       4096 2009-05-27 11:14 rc0.d
drwxr-xr-x 2 root     root       4096 2009-05-27 11:31 rc1.d
drwxr-xr-x 2 root     root       4096 2009-05-27 11:31 rc2.d
drwxr-xr-x 2 root     root       4096 2009-05-27 11:31 rc3.d
drwxr-xr-x 2 root     root       4096 2009-05-27 11:31 rc4.d
drwxr-xr-x 2 root     root       4096 2009-05-27 11:31 rc5.d
drwxr-xr-x 2 root     root       4096 2009-05-27 11:14 rc6.d
-rwxr-xr-x 1 root     root        306 2009-05-27 10:12 rc.local
drwxr-xr-x 2 root     root       4096 2009-05-27 10:38 rcS.d
drwxr-xr-x 3 root     root       4096 2009-05-27 11:12 resolvconf
-rw-r--r-- 1 root     root         74 2009-05-27 10:29 resolv.conf
-rwxr-xr-x 1 root     root        268 2008-04-04 07:06 rmt
-rw-r--r-- 1 root     root        887 2007-12-03 17:04 rpc
-rw-r--r-- 1 root     root       1024 2008-12-08 04:13 securetty
drwxr-xr-x 2 root     root       4096 2009-05-27 10:12 security
-rw-r--r-- 1 root     root      18274 2007-12-03 17:04 services
-rw-r----- 1 root     shadow      758 2009-05-27 11:31 shadow
-rw------- 1 root     root        758 2009-05-27 11:31 shadow-
-rw-r--r-- 1 root     root        165 2009-05-27 10:12 shells
drwxr-xr-x 2 root     root       4096 2009-05-27 10:12 skel
drwxr-xr-x 2 root     root       4096 2009-05-27 11:31 ssh
drwxr-xr-x 4 root     root       4096 2009-05-27 11:12 ssl
-r--r----- 1 root     root        557 2009-05-27 10:28 sudoers
-rw-r--r-- 1 root     root       2405 2008-07-10 05:29 sysctl.conf
-rw-r--r-- 1 root     root       1614 2007-11-23 04:02 syslog.conf
drwxr-xr-x 2 root     root       4096 2009-05-27 10:12 terminfo
-rw-r--r-- 1 root     root         17 2009-05-27 10:39 timezone
-rw-r--r-- 1 root     root       1260 2008-02-21 02:22 ucf.conf
drwxr-xr-x 3 root     root       4096 2009-05-27 10:39 udev
drwxr-xr-x 2 root     root       4096 2009-05-27 10:26 ufw
-rw-r--r-- 1 root     root        214 2008-03-08 13:23 updatedb.conf
drwxr-xr-x 2 root     root       4096 2009-05-27 10:39 update-manager
drwxr-xr-x 2 root     root       4096 2009-05-27 10:12 vim
drwxr-xr-x 2 root     root       4096 2009-05-27 10:26 w3m
-rw-r--r-- 1 root     root       4221 2007-06-18 05:55 wgetrc
drwxr-xr-x 2 root     root       4096 2009-05-27 10:12 wpa_supplicant
drwxr-xr-x 3 root     root       4096 2009-05-27 10:12 X11
-rw-r--r-- 1 root     root        461 2008-04-03 15:33 zsh_command_not_found

```

---

