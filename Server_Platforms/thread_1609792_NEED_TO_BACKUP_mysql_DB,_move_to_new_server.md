---
title: "NEED TO BACKUP mysql DB, move to new server"
date: 2010-10-30
forum: Server Platforms
---

### Post by carsonrose on 2010-10-30
What a pain.. Ive been trying to use phpmyadmin to backup the sql db's, but somethere in this mess I have lost privileges and cant even see my DB's anymore...

Need some help restoring root privileges and getting these DB's backed up so I can get on with the other servers....

When I start mysql, it doesnt even ask me for a password.. it just pops me into mysql, but it says MariaDB.. instead of mysql, I dont know how that MariaDB got on there, I dont know what I did to lose my priviliges and I dont know what to do to get them back....

Before all this happened, the problem was that the DB is too large to go through phpmyadmin... says there is a work around, but it has me lost.....

Any ideas?

---

### Post by carsonrose on 2010-10-30
> **carsonrose said:**
> What a pain.. Ive been trying to use phpmyadmin to backup the sql db's, but somethere in this mess I have lost privileges and cant even see my DB's anymore...

Need some help restoring root privileges and getting these DB's backed up so I can get on with the other servers....

When I start mysql, it doesnt even ask me for a password.. it just pops me into mysql, but it says MariaDB.. instead of mysql, I dont know how that MariaDB got on there, I dont know what I did to lose my priviliges and I dont know what to do to get them back....

Before all this happened, the problem was that the DB is too large to go through phpmyadmin... says there is a work around, but it has me lost.....

Any ideas?

When I try to ```
mysql --user=root mysql 

```

```
ERROR 1044 (42000): Access denied for user ''@'localhost' to database 'mysql'
```

---

### Post by carsonrose on 2010-10-31
```
[root@cra-c1 ~]# mysql --skip-grant-tables
mysql: unknown option '--skip-grant-tables'
[root@cra-c1 ~]# mysqld --skip-grant-tables
-bash: mysqld: command not found
[root@cra-c1 ~]# pidof mysqld
5813
[root@cra-c1 ~]# mysql
Welcome to the MariaDB monitor.  Commands end with ; or \g.
Your MariaDB connection id is 2933
Server version: 5.1.47-MariaDB Source distribution

Copyright (c) 2000, 2010, Oracle and/or its affiliates. All rights reserved.
This software comes with ABSOLUTELY NO WARRANTY. This is free software,
and you are welcome to modify and redistribute it under the GPL v2 license

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

MariaDB [(none)]> mysql;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'mysql' at line 1
MariaDB [(none)]> show databases
    -> ^C
    -> 
    -> 
    -> exit
    -> ^CCtrl-C -- exit!
Aborted
[root@cra-c1 ~]# ^C
[root@cra-c1 ~]# 
[root@cra-c1 ~]# 
[root@cra-c1 ~]# mysql
Welcome to the MariaDB monitor.  Commands end with ; or \g.
Your MariaDB connection id is 3135
Server version: 5.1.47-MariaDB Source distribution

Copyright (c) 2000, 2010, Oracle and/or its affiliates. All rights reserved.
This software comes with ABSOLUTELY NO WARRANTY. This is free software,
and you are welcome to modify and redistribute it under the GPL v2 license

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

MariaDB [(none)]> mysql;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'mysql' at line 1
MariaDB [(none)]> mysql
    -> 
    -> 
    -> 
    -> quit
    -> Ctrl-C -- exit!
Aborted
[root@cra-c1 ~]# mysqld_safe --skip-grant-tables &
[1] 27533
[root@cra-c1 ~]# 101030 23:39:33 mysqld_safe Logging to '/var/log/mysqld.log'.
101030 23:39:33 mysqld_safe A mysqld process already exists

[1]+  Exit 1                  mysqld_safe --skip-grant-tables
[root@cra-c1 ~]# cd /etc/my.cnf 
anaconda-ks.cfg              .gconfd/                     .lesshst                     .serverauth.6444
.bash_history                .gnome/                      .mc/                         .ssh/
.bash_logout                 .gnome2/                     .metacity/                   .tcshrc
.bash_profile                .gnome2_private/             .mysql_history               .thumbnails/
.bashrc                      .gnupg/                      .nautilus/                   .Trash/
.cshrc                       .gstreamer-0.10/             osdial-split.sql             .viminfo
Desktop/                     .gtkrc-1.2-gnome2            .redhat/                     .vnc/
.eggcups/                    .ICEauthority                restore_root_privileges.sql  .Xauthority
.elinks/                     install.log                  .rnd                         
.gconf/                      install.log.syslog           .serverauth.4167             
[root@cra-c1 ~]# cd /etc/
[root@cra-c1 etc]# ls
acpi                   dhcp6c.conf           inputrc         Muttrc              purple             shadow
adjtime                DIR_COLORS            iproute2        Muttrc.local        quotagrpadmins     shadow-
aliases                DIR_COLORS.xterm      isdn            my.cnf              quotatab           shells
aliases.db             dnsmasq.conf          issue           netplug             racoon             skel
alsa                   dumpdates             issue.net       netplug.d           rc                 slrn.rc
alternatives           environment           issue.rpmnew    NetworkManager      rc0.d              smart
anacrontab             esd.conf              java            nscd.conf           rc1.d              smartd.conf
apt                    exports               jvm             nsswitch.conf       rc2.d              smrsh
asterisk               fb.modes              jvm-commmon     ntp                 rc3.d              sound
at.deny                filesystems           jwhois.conf     ntp.conf            rc4.d              ssh
audisp                 firmware              krb5.conf       odbc.ini            rc5.d              stunnel
audit                  fonts                 ldap.conf       odbcinst.ini        rc6.d              sudoers
autofs_ldap_auth.conf  foomatic              ld.so.cache     oddjob              rc.d               sysconfig
auto.master            fstab                 ld.so.conf      oddjobd.conf        rc.local           sysctl.conf
auto.misc              gconf                 ld.so.conf.d    oddjobd.conf.d      rc.sysinit         syslog.conf
auto.net               gcrypt                lftp.conf       openldap            readahead.d        tcsd.conf
auto.smb               gdm                   libaudit.conf   openvpn             reader.conf        termcap
avahi                  ghostscript           libuser.conf    opt                 reader.conf.d      udev
bashrc                 gnome-vfs-2.0         localtime       osdial.conf         redhat-lsb         updatedb.conf
blkid                  gnome-vfs-mime-magic  login.defs      osdial.conf.rpmnew  redhat-release     usermin
bluetooth              gpm-root.conf         logrotate.conf  pam.d               request-key.conf   vimrc
bonobo-activation      gre.d                 logrotate.d     pam_pkcs11          resolv.conf        virc
capi.conf              group                 logwatch        pam_smb.conf        resolv.conf.bak    wanpipe
cdrecord.conf          group-                lsb-release.d   pango               rhgb               warnquota.conf
cipe                   grub.conf             lvm             passwd              rmt                webmin
conman.conf            gshadow               mail            passwd-             rpc                wgetrc
cron.d                 gshadow-              mailcap         pcmcia              rpm                wpa_supplicant
cron.daily             gssapi_mech.conf      mail.rc         pear.conf           rwtab              wvdial.conf
cron.deny              gtk                   makedev.d       php.d               rwtab.d            X11
cron.hourly            gtk-2.0               man.config      php.ini             samba              xdg
cron.monthly           hal                   maven           php.ini.rpmnew      sangoma_mgd.conf   xinetd.conf
crontab                host.conf             mc              pinforc             sasl2              xinetd.d
cron.weekly            HOSTNAME              mgetty+sendfax  pki                 screenrc           xml
csh.cshrc              hosts                 mime.types      pm                  scrollkeeper.conf  xrdp
csh.login              hosts.allow           minicom.users   ppp                 scsi_id.config     yp.conf
cups                   hosts.deny            mke2fs.conf     prelink.cache       securetty          yum
dahdi                  hotplug               modprobe.conf   prelink.conf        security           yum.conf
dbus-1                 httpd                 modprobe.d      prelink.conf.d      selinux            yum.repos.d
default                idmapd.conf           motd            printcap            services           zaptel.bak
depmod.d               init.d                mtab            profile             sestatus.conf
desktop-profiles       initlog.conf          mtools.conf     profile.d           setuptool.d
dev.d                  inittab               multipath.conf  protocols           sgml
[root@cra-c1 etc]# vim  mt
mtab         mtools.conf  
[root@cra-c1 etc]# vim  mt
mtab         mtools.conf  
[root@cra-c1 etc]# vim my.cnf 
[root@cra-c1 etc]# mysql -u root
Welcome to the MariaDB monitor.  Commands end with ; or \g.
Your MariaDB connection id is 3420
Server version: 5.1.47-MariaDB Source distribution

Copyright (c) 2000, 2010, Oracle and/or its affiliates. All rights reserved.
This software comes with ABSOLUTELY NO WARRANTY. This is free software,
and you are welcome to modify and redistribute it under the GPL v2 license

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

MariaDB [(none)]> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| test               |
+--------------------+
2 rows in set (0.00 sec)

MariaDB [(none)]> quit
Bye
[root@cra-c1 etc]# /etc/init.d/mysqld stop
Stopping MySQL:                                            [  OK  ]
[root@cra-c1 etc]# mysqld_safe --skip-grant-tables &
[1] 29950
[root@cra-c1 etc]# 101030 23:59:47 mysqld_safe Logging to '/var/log/mysqld.log'.
101030 23:59:47 mysqld_safe Starting mysqld daemon with databases from /var/lib/mysql

[root@cra-c1 etc]# mysql -u root mysql 
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Welcome to the MariaDB monitor.  Commands end with ; or \g.
Your MariaDB connection id is 27
Server version: 5.1.47-MariaDB Source distribution

Copyright (c) 2000, 2010, Oracle and/or its affiliates. All rights reserved.
This software comes with ABSOLUTELY NO WARRANTY. This is free software,
and you are welcome to modify and redistribute it under the GPL v2 license

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

MariaDB [mysql]> UPDATE user SET Password=PASSWORD('harvet') where USER='root'; 
Query OK, 0 rows affected (0.00 sec)
Rows matched: 3  Changed: 0  Warnings: 0

MariaDB [mysql]> FLUSH PRIVILEGES; 
Query OK, 0 rows affected (0.00 sec)

MariaDB [mysql]> quit
Bye
[root@cra-c1 etc]# /etc/init.d/mysqld stop
101031 00:02:31 mysqld_safe mysqld from pid file /var/run/mysqld/mysqld.pid ended
Stopping MySQL:                                            [  OK  ]
[1]+  Done                    mysqld_safe --skip-grant-tables
[root@cra-c1 etc]# /etc/init.d/mysqld start
Starting MySQL:                                            [  OK  ]
[root@cra-c1 etc]# mysql -u root -p 
Enter password: 
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
[root@cra-c1 etc]# mysql -u root -p 
Enter password: 
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
[root@cra-c1 etc]# mysql -u root -p 
Enter password: 
Welcome to the MariaDB monitor.  Commands end with ; or \g.
Your MariaDB connection id is 82
Server version: 5.1.47-MariaDB Source distribution

Copyright (c) 2000, 2010, Oracle and/or its affiliates. All rights reserved.
This software comes with ABSOLUTELY NO WARRANTY. This is free software,
and you are welcome to modify and redistribute it under the GPL v2 license

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

MariaDB [(none)]> quit
Bye
```

didnt work.....

---

### Post by koenn on 2010-10-31
MariaDB is a replacement for mysql. Seems to me you've been doing quite a bit more than "attemting to backup a database'. Hiding information usually doesn't make problem solving easier.
or, if this MariaDB found its way to your server without you knowing, ... who knows what else happens on that server without ypu knowing ....

Also, judging by the output you posted, you do not handle  command prompt very well, be it shell or sql.
 
so, I hope the data in those databases wasn't very important -- i don't think it's going to be easy to sort out this mess.


Ok, 
so, 
apparently, mariadb looks for its databases in /var/lib/mysql and sees only 2 : mysql and test. 
Are those the ones you want ?

If not, did your mysql keep its databases in a folder different from /var/lib/mysql  (which was also mysql's default location for db files) ?


also, run this to see if there's anything else of interest in that directory
```

ls -Ral /var/lib/mysql

```

---

### Post by carsonrose on 2010-10-31
> **koenn said:**
> MariaDB is a replacement for mysql. Seems to me you've been doing quite a bit more than "attemting to backup a database'. Hiding information usually doesn't make problem solving easier.
or, if this MariaDB found its way to your server without you knowing, ... who knows what else happens on that server without ypu knowing ....

Also, judging by the output you posted, you do not handle  command prompt very well, be it shell or sql.
 
so, I hope the data in those databases wasn't very important -- i don't think it's going to be easy to sort out this mess.


Ok, 
so, 
apparently, mariadb looks for its databases in /var/lib/mysql and sees only 2 : mysql and test. 
Are those the ones you want ?

If not, did your mysql keep its databases in a folder different from /var/lib/mysql  (which was also mysql's default location for db files) ?


also, run this to see if there's anything else of interest in that directory
```

ls -Ral /var/lib/mysql

```


Hiding informaiton? Are you serious with this ****? Why the hell would I knowingly hide information when Im asking for help? 

Yes, there is another tech that I have been using for a couple years now.... if my command line usage seems lacking, its because Im somewhat new to linux. 

And its SOOOOOOO great seeing someone like you come in and treat me like an idiot. Yes, the other tech may have put this MariaDB on without my knowledge... it was always a "go fix it" call I made to him. I got tired of paying literally THOUSANDS in tech support, so I have been learning this myself. So, excuse the hell out of me for not knowing SQL and being new to the linux shell.

Moving on......

This problem occured when I tried to use phpmyadmin to backup the DB. The root user for SQL didnt have a password.. when I set one in phpmyadmin, it killed my privileges. 

I think at this point, I just need to reestablish the privileges for root on the DB and I should be fine... the DB works fine. The Dialer uses the DB and also an archive server for recordings. Everything functions fine, I just cant administrate the DB.. lol.

---

### Post by carsonrose on 2010-10-31
> **koenn said:**
> MariaDB is a replacement for mysql. Seems to me you've been doing quite a bit more than "attemting to backup a database'. Hiding information usually doesn't make problem solving easier.
or, if this MariaDB found its way to your server without you knowing, ... who knows what else happens on that server without ypu knowing ....

Also, judging by the output you posted, you do not handle  command prompt very well, be it shell or sql.
 
so, I hope the data in those databases wasn't very important -- i don't think it's going to be easy to sort out this mess.


Ok, 
so, 
apparently, mariadb looks for its databases in /var/lib/mysql and sees only 2 : mysql and test. 
Are those the ones you want ?

If not, did your mysql keep its databases in a folder different from /var/lib/mysql  (which was also mysql's default location for db files) ?


also, run this to see if there's anything else of interest in that directory
```

ls -Ral /var/lib/mysql

```
```

[root@cra-c1 ~]# ls -Ral /var/lib/mysql
/var/lib/mysql:
total 37012
drwxr-xr-x  7 mysql mysql     4096 Oct 31 15:58 .
drwxr-xr-x 26 root  root      4096 Sep 13 12:59 ..
drwx------  2 mysql mysql     4096 Dec 21  2009 dialer
-rw-rw----  1 mysql mysql 27262976 Oct 31 15:58 ibdata1
-rw-rw----  1 mysql mysql  5242880 Oct 31 15:58 ib_logfile0
-rw-rw----  1 mysql mysql  5242880 Oct 31 15:58 ib_logfile1
-rw-rw----  1 mysql mysql    16384 Oct 31 00:02 maria_log.00000001
-rw-rw----  1 mysql mysql       52 Oct 31 00:02 maria_log_control
drwx------  2 mysql mysql     4096 Aug  6 07:07 mysql
srwxrwxrwx  1 mysql mysql        0 Oct 31 00:02 mysql.sock
-rw-r--r--  1 root  root        14 Aug  6 07:07 mysql_upgrade_info
drwx------  2 mysql mysql     4096 Jul  1 15:53 openfire
drwx------  2 mysql mysql    12288 Oct 31 15:41 osdial
drwx------  2 mysql mysql     4096 Dec 21  2009 test

/var/lib/mysql/dialer:
total 28
drwx------ 2 mysql mysql 4096 Dec 21  2009 .
drwxr-xr-x 7 mysql mysql 4096 Oct 31 15:58 ..
-rw-rw---- 1 mysql mysql 9062 Dec 21  2009 channels.frm
-rw-rw---- 1 mysql mysql   65 Dec 21  2009 db.opt

/var/lib/mysql/mysql:
total 1140
drwx------ 2 mysql mysql   4096 Aug  6 07:07 .
drwxr-xr-x 7 mysql mysql   4096 Oct 31 15:58 ..
-rw-rw---- 1 mysql mysql   8820 Aug  6 07:07 columns_priv.frm
-rw-rw---- 1 mysql mysql      0 Aug  6 07:07 columns_priv.MYD
-rw-rw---- 1 mysql mysql   4096 Aug  6 07:07 columns_priv.MYI
-rw-rw---- 1 mysql mysql   9582 Aug  6 07:07 db.frm
-rw-rw---- 1 mysql mysql   9240 Aug  7 02:31 db.MYD
-rw-rw---- 1 mysql mysql   5120 Aug  7 13:11 db.MYI
-rw-rw---- 1 mysql mysql  10223 Aug  6 07:07 event.frm
-rw-rw---- 1 mysql mysql      0 Aug  6 07:07 event.MYD
-rw-rw---- 1 mysql mysql   2048 Aug  6 07:07 event.MYI
-rw-rw---- 1 mysql mysql   8665 Aug  6 07:07 func.frm
-rw-rw---- 1 mysql mysql      0 Aug  6 07:07 func.MYD
-rw-rw---- 1 mysql mysql   1024 Aug  6 07:07 func.MYI
-rw-rw---- 1 mysql mysql     35 Oct 31 00:02 general_log.CSM
-rw-rw---- 1 mysql mysql      0 Dec 21  2009 general_log.CSV
-rw-rw---- 1 mysql mysql   8776 Aug  6 07:07 general_log.frm
-rw-rw---- 1 mysql mysql   8700 Dec 21  2009 help_category.frm
-rw-rw---- 1 mysql mysql  21497 Dec 21  2009 help_category.MYD
-rw-rw---- 1 mysql mysql   3072 Dec 21  2009 help_category.MYI
-rw-rw---- 1 mysql mysql   8612 Dec 21  2009 help_keyword.frm
-rw-rw---- 1 mysql mysql  88650 Dec 21  2009 help_keyword.MYD
-rw-rw---- 1 mysql mysql  16384 Dec 21  2009 help_keyword.MYI
-rw-rw---- 1 mysql mysql   8630 Dec 21  2009 help_relation.frm
-rw-rw---- 1 mysql mysql   8910 Dec 21  2009 help_relation.MYD
-rw-rw---- 1 mysql mysql  18432 Dec 21  2009 help_relation.MYI
-rw-rw---- 1 mysql mysql   8770 Dec 21  2009 help_topic.frm
-rw-rw---- 1 mysql mysql 417672 Dec 21  2009 help_topic.MYD
-rw-rw---- 1 mysql mysql  20480 Dec 21  2009 help_topic.MYI
-rw-rw---- 1 mysql mysql   9510 Aug  6 07:07 host.frm
-rw-rw---- 1 mysql mysql      0 Aug  6 07:07 host.MYD
-rw-rw---- 1 mysql mysql   2048 Aug  6 07:07 host.MYI
-rw-rw---- 1 mysql mysql   8778 Dec 21  2009 ndb_binlog_index.frm
-rw-rw---- 1 mysql mysql      0 Dec 21  2009 ndb_binlog_index.MYD
-rw-rw---- 1 mysql mysql   1024 Dec 21  2009 ndb_binlog_index.MYI
-rw-rw---- 1 mysql mysql   8586 Dec 21  2009 plugin.frm
-rw-rw---- 1 mysql mysql      0 Dec 21  2009 plugin.MYD
-rw-rw---- 1 mysql mysql   1024 Dec 21  2009 plugin.MYI
-rw-rw---- 1 mysql mysql   9996 Aug  6 07:07 proc.frm
-rw-rw---- 1 mysql mysql      0 Aug  6 07:07 proc.MYD
-rw-rw---- 1 mysql mysql   2048 Aug  6 07:07 proc.MYI
-rw-rw---- 1 mysql mysql   8875 Aug  6 07:07 procs_priv.frm
-rw-rw---- 1 mysql mysql      0 Aug  6 07:07 procs_priv.MYD
-rw-rw---- 1 mysql mysql   4096 Aug  6 07:07 procs_priv.MYI
-rw-rw---- 1 mysql mysql   8838 Dec 21  2009 servers.frm
-rw-rw---- 1 mysql mysql      0 Dec 21  2009 servers.MYD
-rw-rw---- 1 mysql mysql   1024 Dec 21  2009 servers.MYI
-rw-rw---- 1 mysql mysql     35 Oct 31 00:02 slow_log.CSM
-rw-rw---- 1 mysql mysql      0 Aug  6 07:07 slow_log.CSV
-rw-rw---- 1 mysql mysql   8976 Aug  6 07:07 slow_log.frm
-rw-rw---- 1 mysql mysql   8955 Aug  6 07:07 tables_priv.frm
-rw-rw---- 1 mysql mysql      0 Aug  6 07:07 tables_priv.MYD
-rw-rw---- 1 mysql mysql   4096 Aug  6 07:07 tables_priv.MYI
-rw-rw---- 1 mysql mysql   8636 Dec 21  2009 time_zone.frm
-rw-rw---- 1 mysql mysql   8624 Dec 21  2009 time_zone_leap_second.frm
-rw-rw---- 1 mysql mysql      0 Dec 21  2009 time_zone_leap_second.MYD
-rw-rw---- 1 mysql mysql   1024 Dec 21  2009 time_zone_leap_second.MYI
-rw-rw---- 1 mysql mysql      0 Dec 21  2009 time_zone.MYD
-rw-rw---- 1 mysql mysql   1024 Dec 21  2009 time_zone.MYI
-rw-rw---- 1 mysql mysql   8606 Dec 21  2009 time_zone_name.frm
-rw-rw---- 1 mysql mysql      0 Dec 21  2009 time_zone_name.MYD
-rw-rw---- 1 mysql mysql   1024 Dec 21  2009 time_zone_name.MYI
-rw-rw---- 1 mysql mysql   8686 Dec 21  2009 time_zone_transition.frm
-rw-rw---- 1 mysql mysql      0 Dec 21  2009 time_zone_transition.MYD
-rw-rw---- 1 mysql mysql   1024 Dec 21  2009 time_zone_transition.MYI
-rw-rw---- 1 mysql mysql   8748 Dec 21  2009 time_zone_transition_type.frm
-rw-rw---- 1 mysql mysql      0 Dec 21  2009 time_zone_transition_type.MYD
-rw-rw---- 1 mysql mysql   1024 Dec 21  2009 time_zone_transition_type.MYI
-rw-rw---- 1 mysql mysql  10466 Aug  6 07:07 user.frm
-rw-rw---- 1 mysql mysql   1048 Oct 30 20:26 user.MYD
-rw-rw---- 1 mysql mysql   2048 Oct 30 23:59 user.MYI

/var/lib/mysql/openfire:
total 16
drwx------ 2 mysql mysql 4096 Jul  1 15:53 .
drwxr-xr-x 7 mysql mysql 4096 Oct 31 15:58 ..
-rw-rw---- 1 mysql mysql   65 Jul  1 15:53 db.opt

/var/lib/mysql/osdial:
total 3553612
drwx------ 2 mysql mysql      12288 Oct 31 15:41 .
drwxr-xr-x 7 mysql mysql       4096 Oct 31 15:58 ..
-rw-rw---- 1 mysql mysql       9158 Dec 22  2009 call_log.frm
-rw-rw---- 1 mysql mysql 1715470336 Oct 30 15:38 call_log.ibd
-rw-rw---- 1 mysql mysql       8652 Mar 24  2010 conferences.frm
-rw-rw---- 1 mysql mysql      98304 Oct 31 01:02 conferences.ibd
-rw-rw---- 1 mysql mysql       8648 Dec 22  2009 configuration.frm
-rw-rw---- 1 mysql mysql     131072 Dec 22  2009 configuration.ibd
-rw-rw---- 1 mysql mysql         65 Dec 21  2009 db.opt
-rw-rw---- 1 mysql mysql       8742 Dec 22  2009 inbound_numbers.frm
-rw-rw---- 1 mysql mysql      98304 Dec 22  2009 inbound_numbers.ibd
-rw-rw---- 1 mysql mysql       8740 Dec 22  2009 live_channels.frm
-rw-rw---- 1 mysql mysql     163840 Oct 30 15:38 live_channels.ibd
-rw-rw---- 1 mysql mysql       9108 Dec 22  2009 live_inbound.frm
-rw-rw---- 1 mysql mysql      98304 Dec 22  2009 live_inbound.ibd
-rw-rw---- 1 mysql mysql       9108 Dec 22  2009 live_inbound_log.frm
-rw-rw---- 1 mysql mysql     147456 Dec 22  2009 live_inbound_log.ibd
-rw-rw---- 1 mysql mysql       8740 Dec 22  2009 live_sip_channels.frm
-rw-rw---- 1 mysql mysql     131072 Oct 30 15:38 live_sip_channels.ibd
-rw-rw---- 1 mysql mysql       9438 Mar 24  2010 osdial_agent_log.frm
-rw-rw---- 1 mysql mysql  121634816 Oct 29 15:11 osdial_agent_log.ibd
-rw-rw---- 1 mysql mysql       9294 Oct 31 15:41 osdial_auto_calls.frm
-rw-rw---- 1 mysql mysql     163840 Oct 31 15:41 osdial_auto_calls.ibd
-rw-rw---- 1 mysql mysql       9026 Oct 31 01:03 osdial_callbacks.frm
-rw-rw---- 1 mysql mysql     458752 Oct 31 01:04 osdial_callbacks.ibd
-rw-rw---- 1 mysql mysql       9702 Dec 22  2009 osdial_call_times.frm
-rw-rw---- 1 mysql mysql      98304 Sep 27 13:59 osdial_call_times.ibd
-rw-rw---- 1 mysql mysql       8748 Mar 24  2010 osdial_campaign_agents.frm
-rw-rw---- 1 mysql mysql     131072 Oct 31 01:04 osdial_campaign_agents.ibd
-rw-rw---- 1 mysql mysql      10048 May  1  2010 osdial_campaign_agent_stats.frm
-rw-rw---- 1 mysql mysql      98304 Oct 28 01:03 osdial_campaign_agent_stats.ibd
-rw-rw---- 1 mysql mysql       8692 Aug  4 23:37 osdial_campaign_cid_areacodes.frm
-rw-rw---- 1 mysql mysql      98304 Aug  4 23:37 osdial_campaign_cid_areacodes.ibd
-rw-rw---- 1 mysql mysql       8810 Dec 22  2009 osdial_campaign_fields.frm
-rw-rw---- 1 mysql mysql      98304 Aug  4 23:37 osdial_campaign_fields.ibd
-rw-rw---- 1 mysql mysql       8790 Dec 22  2009 osdial_campaign_forms.frm
-rw-rw---- 1 mysql mysql      98304 Oct 12 11:45 osdial_campaign_forms.ibd
-rw-rw---- 1 mysql mysql       8776 Mar 24  2010 osdial_campaign_hotkeys.frm
-rw-rw---- 1 mysql mysql      98304 Oct 12 08:42 osdial_campaign_hotkeys.ibd
-rw-rw---- 1 mysql mysql       8952 Oct 31 01:03 osdial_campaign_server_stats.frm
-rw-rw---- 1 mysql mysql      98304 Oct 31 01:04 osdial_campaign_server_stats.ibd
-rw-rw---- 1 mysql mysql      17962 Aug  6 07:08 osdial_campaigns.frm
-rw-rw---- 1 mysql mysql      98304 Oct 31 15:58 osdial_campaigns.ibd
-rw-rw---- 1 mysql mysql       8825 Mar 24  2010 osdial_campaigns_list_mix.frm
-rw-rw---- 1 mysql mysql     114688 Jul  9 11:11 osdial_campaigns_list_mix.ibd
-rw-rw---- 1 mysql mysql      11182 Oct 31 01:03 osdial_campaign_stats.frm
-rw-rw---- 1 mysql mysql      98304 Oct 31 14:59 osdial_campaign_stats.ibd
-rw-rw---- 1 mysql mysql       8788 Mar 24  2010 osdial_campaign_statuses.frm
-rw-rw---- 1 mysql mysql      98304 Sep 29 13:31 osdial_campaign_statuses.ibd
-rw-rw---- 1 mysql mysql       9385 Aug  4 23:37 osdial_carrier_dids.frm
-rw-rw---- 1 mysql mysql     114688 Aug  4 23:37 osdial_carrier_dids.ibd
-rw-rw---- 1 mysql mysql       8750 Aug  4 23:37 osdial_carrier_servers.frm
-rw-rw---- 1 mysql mysql      98304 Aug  4 23:37 osdial_carrier_servers.ibd
-rw-rw---- 1 mysql mysql       9308 Aug  4 23:37 osdial_carriers.frm
-rw-rw---- 1 mysql mysql      98304 Aug  4 23:37 osdial_carriers.ibd
-rw-rw---- 1 mysql mysql       9387 Aug  4 23:37 osdial_closer_log.frm
-rw-rw---- 1 mysql mysql   19922944 Oct 30 15:36 osdial_closer_log.ibd
-rw-rw---- 1 mysql mysql       9835 Aug  4 23:37 osdial_companies.frm
-rw-rw---- 1 mysql mysql      98304 Aug  4 23:37 osdial_companies.ibd
-rw-rw---- 1 mysql mysql       8652 Oct 31 01:03 osdial_conferences.frm
-rw-rw---- 1 mysql mysql      98304 Oct 31 01:04 osdial_conferences.ibd
-rw-rw---- 1 mysql mysql       8666 Mar 24  2010 osdial_dnc_company.frm
-rw-rw---- 1 mysql mysql      98304 Mar 24  2010 osdial_dnc_company.ibd
-rw-rw---- 1 mysql mysql       8576 Oct 31 01:03 osdial_dnc.frm
-rw-rw---- 1 mysql mysql     245760 Oct 31 01:04 osdial_dnc.ibd
-rw-rw---- 1 mysql mysql       8996 Aug  4 23:37 osdial_email_templates.frm
-rw-rw---- 1 mysql mysql      98304 Aug  4 23:37 osdial_email_templates.ibd
-rw-rw---- 1 mysql mysql       9023 Oct 31 15:41 osdial_hopper.frm
-rw-rw---- 1 mysql mysql     114688 Oct 31 15:41 osdial_hopper.ibd
-rw-rw---- 1 mysql mysql       8730 Dec 22  2009 osdial_inbound_group_agents.frm
-rw-rw---- 1 mysql mysql     229376 Oct 31 01:04 osdial_inbound_group_agents.ibd
-rw-rw---- 1 mysql mysql      14748 Aug  4 23:37 osdial_inbound_groups.frm
-rw-rw---- 1 mysql mysql      98304 Oct 27 14:26 osdial_inbound_groups.ibd
-rw-rw---- 1 mysql mysql       9118 Jun  4 04:51 osdial_ivr.frm
-rw-rw---- 1 mysql mysql     114688 Oct 25 09:36 osdial_ivr.ibd
-rw-rw---- 1 mysql mysql       8788 Dec 22  2009 osdial_ivr_options.frm
-rw-rw---- 1 mysql mysql     114688 Oct 25 09:17 osdial_ivr_options.ibd
-rw-rw---- 1 mysql mysql       8748 Mar 24  2010 osdial_lead_filters.frm
-rw-rw---- 1 mysql mysql      98304 Mar 24  2010 osdial_lead_filters.ibd
-rw-rw---- 1 mysql mysql       8790 Mar 24  2010 osdial_lead_recycle.frm
-rw-rw---- 1 mysql mysql     114688 Oct 13 10:56 osdial_lead_recycle.ibd
-rw-rw---- 1 mysql mysql       8662 Dec 22  2009 osdial_list_fields.frm
-rw-rw---- 1 mysql mysql   24117248 Oct 11 11:39 osdial_list_fields.ibd
-rw-rw---- 1 mysql mysql      14158 Dec 22  2009 osdial_list.frm
-rw-rw---- 1 mysql mysql  234881024 Oct 31 07:03 osdial_list.ibd
-rw-rw---- 1 mysql mysql       8844 Dec 22  2009 osdial_list_pins.frm
-rw-rw---- 1 mysql mysql     147456 Dec 22  2009 osdial_list_pins.ibd
-rw-rw---- 1 mysql mysql      13256 Aug  4 23:37 osdial_lists.frm
-rw-rw---- 1 mysql mysql      98304 Oct 27 16:39 osdial_lists.ibd
-rw-rw---- 1 mysql mysql      13613 Oct 31 15:41 osdial_live_agents.frm
-rw-rw---- 1 mysql mysql     327680 Oct 31 15:58 osdial_live_agents.ibd
-rw-rw---- 1 mysql mysql       8792 Dec 22  2009 osdial_live_inbound_agents.frm
-rw-rw---- 1 mysql mysql     131072 Oct 28 11:01 osdial_live_inbound_agents.ibd
-rw-rw---- 1 mysql mysql       9270 Mar 24  2010 osdial_log.frm
-rw-rw---- 1 mysql mysql  444596224 Oct 29 15:11 osdial_log.ibd
-rw-rw---- 1 mysql mysql      13416 Oct 31 15:41 osdial_manager.frm
-rw-rw---- 1 mysql mysql     212992 Oct 31 15:41 osdial_manager.ibd
-rw-rw---- 1 mysql mysql       8720 Mar 24  2010 osdial_pause_codes.frm
-rw-rw---- 1 mysql mysql      98304 Aug  3 11:39 osdial_pause_codes.ibd
-rw-rw---- 1 mysql mysql       8656 Dec 22  2009 osdial_phone_code_groups.frm
-rw-rw---- 1 mysql mysql     131072 Dec 22  2009 osdial_phone_code_groups.ibd
-rw-rw---- 1 mysql mysql       8864 Dec 22  2009 osdial_phone_codes.frm
-rw-rw---- 1 mysql mysql   27262976 Oct 30 20:16 osdial_phone_codes.ibd
-rw-rw---- 1 mysql mysql       8662 Dec 22  2009 osdial_postal_code_groups.frm
-rw-rw---- 1 mysql mysql    9437184 Dec 22  2009 osdial_postal_code_groups.ibd
-rw-rw---- 1 mysql mysql       8804 Dec 22  2009 osdial_postal_codes.frm
-rw-rw---- 1 mysql mysql  490733568 Oct 30 20:16 osdial_postal_codes.ibd
-rw-rw---- 1 mysql mysql       8908 Mar 24  2010 osdial_remote_agents.frm
-rw-rw---- 1 mysql mysql      98304 Oct 31 15:58 osdial_remote_agents.ibd
-rw-rw---- 1 mysql mysql       8660 Dec 22  2009 osdial_report_groups.frm
-rw-rw---- 1 mysql mysql    9437184 Oct 30 01:04 osdial_report_groups.ibd
-rw-rw---- 1 mysql mysql       8758 Aug  4 23:37 osdial_script_button_log.frm
-rw-rw---- 1 mysql mysql     147456 Aug  4 23:37 osdial_script_button_log.ibd
-rw-rw---- 1 mysql mysql       8814 Dec 22  2009 osdial_script_buttons.frm
-rw-rw---- 1 mysql mysql      98304 Dec 22  2009 osdial_script_buttons.ibd
-rw-rw---- 1 mysql mysql       8750 Mar 24  2010 osdial_scripts.frm
-rw-rw---- 1 mysql mysql      98304 Jun 11 10:41 osdial_scripts.ibd
-rw-rw---- 1 mysql mysql       8757 Dec 22  2009 osdial_server_trunks.frm
-rw-rw---- 1 mysql mysql     131072 Dec 22  2009 osdial_server_trunks.ibd
-rw-rw---- 1 mysql mysql       9716 Dec 22  2009 osdial_state_call_times.frm
-rw-rw---- 1 mysql mysql      98304 Sep 16 13:53 osdial_state_call_times.ibd
-rw-rw---- 1 mysql mysql       8710 Dec 22  2009 osdial_status_categories.frm
-rw-rw---- 1 mysql mysql      98304 Dec 22  2009 osdial_status_categories.ibd
-rw-rw---- 1 mysql mysql       8744 Dec 22  2009 osdial_statuses.frm
-rw-rw---- 1 mysql mysql      98304 Dec 22  2009 osdial_statuses.ibd
-rw-rw---- 1 mysql mysql      11180 Aug  4 23:37 osdial_user_groups.frm
-rw-rw---- 1 mysql mysql      98304 Oct 25 08:39 osdial_user_groups.ibd
-rw-rw---- 1 mysql mysql       8808 Mar 24  2010 osdial_user_log.frm
-rw-rw---- 1 mysql mysql   13631488 Oct 28 11:01 osdial_user_log.ibd
-rw-rw---- 1 mysql mysql      11487 Aug  4 23:37 osdial_users.frm
-rw-rw---- 1 mysql mysql     114688 Oct 31 15:58 osdial_users.ibd
-rw-rw---- 1 mysql mysql       8918 Dec 22  2009 osdial_xfer_log.frm
-rw-rw---- 1 mysql mysql   15728640 Oct 30 15:36 osdial_xfer_log.ibd
-rw-rw---- 1 mysql mysql       8778 Mar 24  2010 parked_channels.frm
-rw-rw---- 1 mysql mysql      98304 Aug  4 08:26 parked_channels.ibd
-rw-rw---- 1 mysql mysql       9008 Dec 22  2009 park_log.frm
-rw-rw---- 1 mysql mysql     114688 Dec 22  2009 park_log.ibd
-rw-rw---- 1 mysql mysql      12166 Mar 24  2010 phones.frm
-rw-rw---- 1 mysql mysql      98304 Sep 17 09:36 phones.ibd
-rw-rw---- 1 mysql mysql       8714 Dec 22  2009 qc_recordings.frm
-rw-rw---- 1 mysql mysql  264241152 Oct 30 15:40 qc_recordings.ibd
-rw-rw---- 1 mysql mysql       8634 Dec 22  2009 qc_server_rules.frm
-rw-rw---- 1 mysql mysql     114688 Dec 22  2009 qc_server_rules.ibd
-rw-rw---- 1 mysql mysql       9168 Dec 22  2009 qc_servers.frm
-rw-rw---- 1 mysql mysql     114688 Dec 22  2009 qc_servers.ibd
-rw-rw---- 1 mysql mysql       8875 Dec 22  2009 qc_transfers.frm
-rw-rw---- 1 mysql mysql     212992 Dec 22  2009 qc_transfers.ibd
-rw-rw---- 1 mysql mysql       9132 Mar 31  2010 recording_log.frm
-rw-rw---- 1 mysql mysql  234881024 Oct 30 15:40 recording_log.ibd
-rw-rw---- 1 mysql mysql       9302 May  1  2010 server_performance.frm
-rw-rw---- 1 mysql mysql      98304 May  1  2010 server_performance.ibd
-rw-rw---- 1 mysql mysql       9738 Mar 24  2010 servers.frm
-rw-rw---- 1 mysql mysql      98304 Oct 31 15:58 servers.ibd
-rw-rw---- 1 mysql mysql       8652 May  1  2010 server_updater.frm
-rw-rw---- 1 mysql mysql      98304 Oct 31 15:58 server_updater.ibd
-rw-rw---- 1 mysql mysql      10234 Aug  4 23:37 system_settings.frm
-rw-rw---- 1 mysql mysql      98304 Oct 31 13:50 system_settings.ibd
-rw-rw---- 1 mysql mysql       8761 May  1  2010 web_client_sessions.frm
-rw-rw---- 1 mysql mysql      98304 Oct 28 11:01 web_client_sessions.ibd

/var/lib/mysql/test:
total 16
drwx------ 2 mysql mysql 4096 Dec 21  2009 .
drwxr-xr-x 7 mysql mysql 4096 Oct 31 15:58 ..
```

---

### Post by koenn on 2010-10-31
> **carsonrose said:**
> Hiding informaiton? Are you serious with this ****? Why the hell would I knowingly hide information when Im asking for help? 

Yes, there is another tech that I have been using for a couple years now.... if my command line usage seems lacking, its because Im somewhat new to linux. 

And its SOOOOOOO great seeing someone like you come in and treat me like an idiot. Yes, the other tech may have put this MariaDB on without my knowledge... it was always a "go fix it" call I made to him. I got tired of paying literally THOUSANDS in tech support, so I have been learning this myself. So, excuse the hell out of me for not knowing SQL and being new to the linux shell.

Moving on......


You wouldn't be the first one to, willfully or not, omit essential information in a support request. 
Where I work, every computer problem, is described by the user, is one of "I wasn't doing anything, and suddenly ...".  

but ok, let's move on

---

### Post by carsonrose on 2010-10-31
[http://ubuntuforums.org/showthread.php?t=1609788](http://ubuntuforums.org/showthread.php?t=1609788)

This is the other thread I used..

---

### Post by koenn on 2010-10-31
so, there's quite some content in /var/lib/mysql so the databases are probably still there - so you're probably right that's a matter of getting logged on with sufficient privileges.


Did you already try to restart mysqld witn the initfile' parameter ?
I saw a   restore_root_privileges.sql file in one of your directory listings, but no mention of it being used.

the file should contain something like this
```

UPDATE mysql.user SET Password=PASSWORD('MyNewPass') WHERE User='root';
FLUSH PRIVILEGES;

```

and you should stop mysqld, then start it with
```

mysqld_safe --init-file=path/to/restore-file &

```
that's in a shell, not in mysql. 

then,
stop and start mysqld again, and try to log on.

---

### Post by carsonrose on 2010-10-31
> **koenn said:**
> so, there's quite some content in /var/lib/mysql so the databases are probably still there - so you're probably right that's a matter of getting logged on with sufficient privileges.


Did you already try to restart mysqld witn the initfile' parameter ?
I saw a   restore_root_privileges.sql file in one of your directory listings, but no mention of it being used.

the file should contain something like this
```

UPDATE mysql.user SET Password=PASSWORD('MyNewPass') WHERE User='root';
FLUSH PRIVILEGES;

```

and you should stop mysqld, then start it with
```

mysqld_safe --init-file=path/to/restore-file &

```
that's in a shell, not in mysql. 

then,
stop and start mysqld again, and try to log on.
I guess I dont understand what youre saying
 
I should edit that file or no? How would I restart sql with that parameter?

---

### Post by carsonrose on 2010-10-31
> **koenn said:**
> MariaDB is a replacement for mysql. Seems to me you've been doing quite a bit more than "attemting to backup a database'. Hiding information usually doesn't make problem solving easier.
or, if this MariaDB found its way to your server without you knowing, ... who knows what else happens on that server without ypu knowing ....

Also, judging by the output you posted, you do not handle  command prompt very well, be it shell or sql.
 
so, I hope the data in those databases wasn't very important -- i don't think it's going to be easy to sort out this mess.


Ok, 
so, 
apparently, mariadb looks for its databases in /var/lib/mysql and sees only 2 : mysql and test. 
Are those the ones you want ?

If not, did your mysql keep its databases in a folder different from /var/lib/mysql  (which was also mysql's default location for db files) ?


also, run this to see if there's anything else of interest in that directory
```

ls -Ral /var/lib/mysql

```

> **koenn said:**
> so, there's quite some content in /var/lib/mysql so the databases are probably still there - so you're probably right that's a matter of getting logged on with sufficient privileges.


Did you already try to restart mysqld witn the initfile' parameter ?
I saw a   restore_root_privileges.sql file in one of your directory listings, but no mention of it being used.

the file should contain something like this
```

UPDATE mysql.user SET Password=PASSWORD('MyNewPass') WHERE User='root';
FLUSH PRIVILEGES;

```and you should stop mysqld, then start it with
```

mysqld_safe --init-file=path/to/restore-file &

```that's in a shell, not in mysql. 

then,
stop and start mysqld again, and try to log on.


```
[root@cra-c1 ~]# UPDATE mysql.user SET Password=PASSWORD('MyNewPass') WHERE User='root';
-bash: syntax error near unexpected token `('
[root@cra-c1 ~]# mysql
Welcome to the MariaDB monitor.  Commands end with ; or \g.
Your MariaDB connection id is 16254
Server version: 5.1.47-MariaDB Source distribution

Copyright (c) 2000, 2010, Oracle and/or its affiliates. All rights reserved.
This software comes with ABSOLUTELY NO WARRANTY. This is free software,
and you are welcome to modify and redistribute it under the GPL v2 license

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

MariaDB [(none)]> UPDATE mysql.user SET Password=PASSWORD('MyNewPass') WHERE User='root';
ERROR 1142 (42000): UPDATE command denied to user ''@'localhost' for table 'user'
MariaDB [(none)]> 
```

---

### Post by carsonrose on 2010-10-31
```
MariaDB [(none)]> FLUSH PRIVILEGES;
ERROR 1227 (42000): Access denied; you need the RELOAD privilege for this operation
MariaDB [(none)]> 
```

---

### Post by koenn on 2010-10-31
again, from the beginning

create a text file, eg like so
```

(echo "UPDATE mysql.user SET Password=PASSWORD('MyNewPass') WHERE User='root';"
echo "FLUSH PRIVILEGES;"
)>> restorerootpass

```

verify the content with 
```

cat restorerootpass

```


stop mysql, start it with --init-file
```

/etc/init.d/mysql stop
mysqld_safe --init-file=restorerootpass &

```

restart, logon 
```

/etc/init.d/mysql stop
/etc/init.d/mysql start

mysql -u root -p

```
this will prompt for a password; use the new password you set in the restorerootpass file

then, at the mysql prompt, try
```

mysql> show databases;

```
always terminate sql commands with a semi-colon (+ enter)

---

### Post by carsonrose on 2010-10-31
[QUOTE=koenn;10054334]again, from the beginning

create a text file, eg like so
```

(echo "UPDATE mysql.user SET Password=PASSWORD('MyNewPass') WHERE User='root';"
echo "FLUSH PRIVILEGES;"
)>> restorerootpass

```

Couple things...

Is that "(" supposed to be at the front of the syntax? 
This is is what happened when i entered exactly as given: 
```
[root@cra-c1 ~]# (echo "UPDATE mysql.user SET Password=PASSWORD('MyNewPass') WHERE User='root';"
> 
> 
> bye
> quit
```

When I entered it without the "(", it gave me this:
```
[root@cra-c1 ~]# echo "UPDATE mysql.user SET Password=PASSWORD('MyNewPass') WHERE User='root';"
UPDATE mysql.user SET Password=PASSWORD('MyNewPass') WHERE User='root';
[root@cra-c1 ~]# echo "FLUSH PRIVILEGES;"
FLUSH PRIVILEGES;

```

I realize I set the pw to "MyNewPass", which is fine because Im reformatting this server and going with a different linux distro than centos.

Then: 
```
[root@cra-c1 ~]# cat restore_root_privileges.sql 




[root@cra-c1 ~]# /etc/init.d/mysqld stop

Stopping MySQL:                                            [  OK  ]
[root@cra-c1 ~]# 
[root@cra-c1 ~]# mysqld_safe --init-file=restorerootpass &
[1] 19438
[root@cra-c1 ~]# 101031 17:34:24 mysqld_safe Logging to '/var/log/mysqld.log'.
101031 17:34:24 mysqld_safe Starting mysqld daemon with databases from /var/lib/mysql
101031 17:34:38 mysqld_safe mysqld from pid file /var/run/mysqld/mysqld.pid ended

[1]+  Done                    mysqld_safe --init-file=restorerootpass
[root@cra-c1 ~]# 
[root@cra-c1 ~]# reboot 

Broadcast message from root (pts/6) (Sun Oct 31 17:35:24 2010):

The system is going down for reboot NOW!
[root@cra-c1 ~]# Connection to 192.168.0.6 closed by remote host.
Connection to 192.168.0.6 closed.
```

---

### Post by carsonrose on 2010-10-31
still doesnt show the DB's when i get in

I dont think it took the PW... i still had to login to sql with no password at all.... 

Just uname root and pword empty

---

### Post by carsonrose on 2010-10-31
```
[root@cra-c1 ~]# vim restore
restorerootpass              restore_root_privileges.sql  
[root@cra-c1 ~]# vim restore_root_privileges.sql 
[root@cra-c1 ~]# cat restore_root_privileges.sql 
(echo "UPDATE mysql.user SET Password=PASSWORD('********') WHERE User='root';"
echo "FLUSH PRIVILEGES;"
)>> restorerootpass
```

---

### Post by carsonrose on 2010-10-31
```
[root@cra-c1 ~]# mysql -u root -p
Enter password: 
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
[root@cra-c1 ~]# 
```

---

### Post by carsonrose on 2010-10-31
if i remove MariaDb and reinstall, would that fix this or cause more problems?

---

### Post by koenn on 2010-11-01
> **carsonrose said:**
> 

Couple things...

Is that "(" supposed to be at the front of the syntax? 
This is is what happened when i entered exactly as given: 
```
[root@cra-c1 ~]# (echo "UPDATE mysql.user SET Password=PASSWORD('MyNewPass') WHERE User='root';"
> 
> 
> bye
> quit
```

couple of things, indeed.
yes, that '(' was supposed to be there, the problem is you did **not** enter that statement exactly as given, you only did the first line. The ">" you got was a prompt to enter the rest, but you didn't; instead you hit enter a couple of times, then tried 'bye' and 'quit'. 

Look, the first step is simply  : create a text file that contains the following tekst:

UPDATE mysql.user SET Password=PASSWORD('MyNewPass') WHERE User='root';
FLUSH PRIVILEGES;


it doesn't matter how you do that, as long as the result is a text file with the given content, and nothing more than the given content.

one way of doing that would be to type **all** of the following into a shell:
```

(echo "UPDATE mysql.user SET Password=PASSWORD('MyNewPass') WHERE User='root';"
echo "FLUSH PRIVILEGES;"
)> restorerootpass
```

but if you're capable of creating such file with vim, nano, or any other text editor, thatd's fine too. 


in the procedure i proposed, the next steps (ie stopping and starteing mysql etc) are _useless_ unless you've succeeded at creating this file.

---

### Post by koenn on 2010-11-01
> **carsonrose said:**
> if i remove MariaDb and reinstall, would that fix this or cause more problems?
it *might* fix it, but you risk loosing your databases if you make a wrong decision in the uninstall process.

I wouldn't recommend it, yet.

---

