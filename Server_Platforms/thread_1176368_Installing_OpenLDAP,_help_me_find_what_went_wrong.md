---
title: "Installing OpenLDAP, help me find what went wrong"
date: 2009-06-02
forum: Server Platforms
---

### Post by ghen on 2009-06-02
I was trying to follow this guide to create a basic "domain controller" setup.
[http://www.rrcomputerconsulting.com/view.php?article_id=3#4](http://www.rrcomputerconsulting.com/view.php?article_id=3#4)
but failed miserably. (error message at the end of the first code block)

Things I did differently than the article above:
Using 8.04 64 bit instead of 7.10 32 bit
username: testing
domain: pag.local
didn't install RAID (skipped step 4)
didn't install Postfix (skipped step 5)
used hdb instead of bdb database
used slapd 2.4.9 instead of whatever the tutorial used (2.2 maybe?)

This is a fresh install on a brand new partition on a hard drive containing an NTFS XP Pro partition.

**Below is the direct result from PuTTY after installing openssh-server and ntp. I bolded commands to read it easier**

```
**test@testing:~$ sudo su**
[sudo] password for test:
**root@testing:/home/test# date**
Tue Jun  2 08:15:56 EDT 2009
[B]root@testing:/home/test# mkdir /ldaphome
root@testing:/home/test# mkdir /ldap_data
root@testing:/home/test# apt-get install slapd ldap-utils migrationtools[/B]
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  libdb4.2 libltdl3 libperl5.8 libslp1 odbcinst1debian1 unixodbc
Suggested packages:
  openslp-doc slpd libct1 libmyodbc odbc-postgresql
The following NEW packages will be installed:
  ldap-utils libdb4.2 libltdl3 libperl5.8 libslp1 migrationtools
  odbcinst1debian1 slapd unixodbc
0 upgraded, 9 newly installed, 0 to remove and 27 not upgraded.
Need to get 2772kB of archives.
After this operation, 7213kB of additional disk space will be used.
Do you want to continue [Y/n]?
Get:1 http://us.archive.ubuntu.com hardy/main libdb4.2 4.2.52+dfsg-4 [415kB]
Get:2 http://us.archive.ubuntu.com hardy/main libltdl3 1.5.26-1ubuntu1 [180kB]
Get:3 http://us.archive.ubuntu.com hardy-updates/main libperl5.8 5.8.8-12ubuntu0.4 [1060B]
Get:4 http://us.archive.ubuntu.com hardy/main libslp1 1.2.1-7.1 [52.9kB]
Get:5 http://us.archive.ubuntu.com hardy/main odbcinst1debian1 2.2.11-16build1 [71.5kB]
Get:6 http://us.archive.ubuntu.com hardy/main unixodbc 2.2.11-16build1 [310kB]
Get:7 http://us.archive.ubuntu.com hardy-updates/main slapd 2.4.9-0ubuntu0.8.04.2 [1448kB]
Get:8 http://us.archive.ubuntu.com hardy-updates/main ldap-utils 2.4.9-0ubuntu0.8.04.2 [267kB]
Get:9 http://us.archive.ubuntu.com hardy/main migrationtools 47-3ubuntu2 [26.8kB]
Fetched 2772kB in 1s (1439kB/s)
Preconfiguring packages ...
Selecting previously deselected package libdb4.2.
(Reading database ... 15071 files and directories currently installed.)
Unpacking libdb4.2 (from .../libdb4.2_4.2.52+dfsg-4_amd64.deb) ...
Selecting previously deselected package libltdl3.
Unpacking libltdl3 (from .../libltdl3_1.5.26-1ubuntu1_amd64.deb) ...
Selecting previously deselected package libperl5.8.
Unpacking libperl5.8 (from .../libperl5.8_5.8.8-12ubuntu0.4_amd64.deb) ...
Selecting previously deselected package libslp1.
Unpacking libslp1 (from .../libslp1_1.2.1-7.1_amd64.deb) ...
Selecting previously deselected package odbcinst1debian1.
Unpacking odbcinst1debian1 (from .../odbcinst1debian1_2.2.11-16build1_amd64.deb) ...
Selecting previously deselected package unixodbc.
Unpacking unixodbc (from .../unixodbc_2.2.11-16build1_amd64.deb) ...
Selecting previously deselected package slapd.
Unpacking slapd (from .../slapd_2.4.9-0ubuntu0.8.04.2_amd64.deb) ...
Selecting previously deselected package ldap-utils.
Unpacking ldap-utils (from .../ldap-utils_2.4.9-0ubuntu0.8.04.2_amd64.deb) ...
Selecting previously deselected package migrationtools.
Unpacking migrationtools (from .../migrationtools_47-3ubuntu2_all.deb) ...
Setting up libdb4.2 (4.2.52+dfsg-4) ...
Setting up libltdl3 (1.5.26-1ubuntu1) ...

Setting up libperl5.8 (5.8.8-12ubuntu0.4) ...

Setting up libslp1 (1.2.1-7.1) ...

Setting up odbcinst1debian1 (2.2.11-16build1) ...

Setting up unixodbc (2.2.11-16build1) ...

Setting up slapd (2.4.9-0ubuntu0.8.04.2) ...
  Creating new user openldap... done.
  Creating initial slapd configuration... done.
  Creating initial LDAP directory... done.
Reloading AppArmor profiles : done.
Starting OpenLDAP: slapd.

Setting up ldap-utils (2.4.9-0ubuntu0.8.04.2) ...
Setting up migrationtools (47-3ubuntu2) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
root@testing:/home/test# dpkg-reconfigure slapd
Stopping OpenLDAP: slapd.
  Moving old database directory to /var/backups:
  - directory unknown... done.
  Creating initial slapd configuration... done.
  Creating initial LDAP directory... done.
Reloading AppArmor profiles : done.
Starting OpenLDAP: slapd.
**root@testing:/home/test# /etc/init.d/slapd stop**
root@testing:/home/test#
**root@testing:/home/test# nano /etc/ldap/slapd.conf**
**root@testing:/home/test# cp -R /var/lib/ldap/* /ldap_data/**
**root@testing:/home/test# chown -R openldap:openldap /ldap_data/**
**root@testing:/home/test# dpkg-reconfigure slapd**
Stopping OpenLDAP: slapd.
  Moving old database directory to /var/backups:

  Backup path /var/backups/unknown-2.4.9-0ubuntu0.8.04.2.ldapdb exists. Giving up...
**root@testing:/home/test# /etc/init.d/slapd start**
Starting OpenLDAP: slapd - failed.
The operation failed but no output was produced. For hints on what went
wrong please refer to the system's logfiles (e.g. /var/log/syslog) or
try running the daemon in Debug mode like via "slapd -d 16383" (warning:
this will create copious output).

Below, you can find the command line options used by this script to
run slapd. Do not forget to specify those options if you
want to look to debugging output:
  slapd -g openldap -u openldap -f /etc/ldap/slapd.conf

```

**directory listing of the /etc folder**

```
**root@testing:/home/test# ls -l /etc**
total 864
-rw-r--r-- 1 root root     2975 2009-06-02 08:25 adduser.conf
-rw-r--r-- 1 root root       46 2009-06-02 08:43 adjtime
-rw-r--r-- 1 root root       49 2009-06-02 08:34 aliases
drwxr-xr-x 2 root root     4096 2009-06-02 08:30 alternatives
drwxr-xr-x 3 root root     4096 2009-06-02 08:30 apm
drwxr-xr-x 2 root root     4096 2009-06-02 08:30 apparmor
drwxr-xr-x 6 root root     4096 2009-06-02 08:48 apparmor.d
drwxr-xr-x 4 root root     4096 2009-06-02 08:38 apt
-rw-r----- 1 root daemon    144 2007-02-20 09:05 at.deny
-rw-r--r-- 1 root root     1733 2008-05-12 14:36 bash.bashrc
-rw-r--r-- 1 root root   216529 2008-04-14 21:45 bash_completion
drwxr-xr-x 2 root root     4096 2009-06-02 08:30 bash_completion.d
drwxr-xr-x 2 root root     4096 2009-06-02 08:25 belocs
-rw-r--r-- 1 root root      332 2008-09-12 09:20 bindresvport.blacklist
-rw-r--r-- 1 root root      460 2009-06-02 08:34 blkid.tab
drwxr-xr-x 2 root root     4096 2009-06-02 08:30 calendar
drwxr-s--- 2 root dip      4096 2009-06-02 08:30 chatscripts
drwxr-xr-x 2 root root     4096 2009-06-02 08:25 console-setup
drwxr-xr-x 2 root root     4096 2009-06-02 08:25 console-tools
drwxr-xr-x 2 root root     4096 2009-06-02 08:30 cron.d
drwxr-xr-x 2 root root     4096 2009-06-02 08:42 cron.daily
drwxr-xr-x 2 root root     4096 2009-06-02 08:30 cron.hourly
drwxr-xr-x 2 root root     4096 2009-06-02 08:30 cron.monthly
-rw-r--r-- 1 root root      724 2008-04-08 14:13 crontab
drwxr-xr-x 2 root root     4096 2009-06-02 08:30 cron.weekly
-rw-r--r-- 1 root root     2969 2008-03-11 11:51 debconf.conf
-rw-r--r-- 1 root root       10 2007-10-20 07:51 debian_version
drwxr-xr-x 2 root root     4096 2009-06-02 08:48 default
-rw-r--r-- 1 root root      600 2007-10-23 11:01 deluser.conf
drwxr-xr-x 2 root root     4096 2009-06-02 08:25 depmod.d
drwxr-xr-x 4 root root     4096 2009-06-02 08:25 dhcp3
drwxr-xr-x 3 root root     4096 2009-06-02 08:25 dpkg
-rw-r--r-- 1 root root       34 2008-02-18 23:33 e2fsck.conf
-rw-r--r-- 1 root root       79 2009-06-02 08:25 environment
drwxr-xr-x 2 root root     4096 2009-06-02 08:25 event.d
-rw-r--r-- 1 root root      354 2007-03-05 11:23 fdmount.conf
-rw-r--r-- 1 root root      555 2009-06-02 08:24 fstab
-rw-r----- 1 root fuse      216 2008-02-26 13:25 fuse.conf
-rw-r--r-- 1 root root     2689 2008-09-12 09:20 gai.conf
drwxr-xr-x 2 root root     4096 2009-06-02 08:30 groff
-rw-r--r-- 1 root root      714 2009-06-02 08:48 group
-rw------- 1 root root      698 2009-06-02 08:42 group-
drwxr-xr-x 2 root root     4096 2009-06-02 08:30 grub.d
-rw-r----- 1 root shadow    593 2009-06-02 08:48 gshadow
-rw------- 1 root root      580 2009-06-02 08:42 gshadow-
-rw-r--r-- 1 root root     4793 2008-03-28 18:27 hdparm.conf
-rw-r--r-- 1 root root       92 2007-10-20 07:51 host.conf
-rw-r--r-- 1 root root       18 2009-06-02 08:24 hostname
-rw-r--r-- 1 root root      261 2009-06-02 08:41 hosts
-rw-r--r-- 1 root root      579 2009-06-02 08:25 hosts.allow
-rw-r--r-- 1 root root      878 2009-06-02 08:25 hosts.deny
drwxr-xr-x 2 root root     4096 2009-06-02 08:48 init.d
drwxr-xr-x 5 root root     4096 2009-06-02 08:25 initramfs-tools
-rw-r--r-- 1 root root     1723 2007-10-02 10:35 inputrc
drwxr-xr-x 2 root root     4096 2009-06-02 08:25 iproute2
-rw-r--r-- 1 root root       21 2008-12-15 13:41 issue
-rw-r--r-- 1 root root       14 2008-12-15 13:41 issue.net
-rw-r--r-- 1 root root      240 2009-06-02 08:34 kernel-img.conf
drwxr-xr-x 4 root root     4096 2009-06-02 08:58 ldap
-rw-r--r-- 1 root root     9656 2009-06-02 08:58 ld.so.cache
-rw-r--r-- 1 root root       34 2009-06-02 08:24 ld.so.conf
drwxr-xr-x 2 root root     4096 2009-06-02 08:25 ld.so.conf.d
-rw-r--r-- 1 root root     2586 2008-03-11 07:02 locale.alias
-rw-r--r-- 1 root root     3519 2009-06-02 08:25 localtime
drwxr-xr-x 3 root root     4096 2009-06-02 08:25 logcheck
-rw-r--r-- 1 root root     9681 2008-12-08 04:13 login.defs
-rw-r--r-- 1 root root      599 2008-10-09 16:06 logrotate.conf
drwxr-xr-x 2 root root     4096 2009-06-02 08:30 logrotate.d
drwxr-xr-x 2 root root     4096 2008-03-26 14:23 lsb-base
-rw-r--r-- 1 root root     3820 2008-03-10 15:00 lsb-base-logging.sh
-rw-r--r-- 1 root root       98 2008-12-15 09:17 lsb-release
-rw-r--r-- 1 root root    13144 2007-11-16 07:12 ltrace.conf
-rw-r--r-- 1 root root      111 2008-06-10 04:44 magic
-rw-r--r-- 1 root root      111 2008-06-10 04:44 magic.mime
-rw-r--r-- 1 root root     2132 2009-06-02 08:30 mailcap
-rw-r--r-- 1 root root      449 2008-04-01 14:11 mailcap.order
-rw-r--r-- 1 root root     4624 2008-03-12 09:28 manpath.config
-rw-r--r-- 1 root root    11742 2007-03-05 11:23 mediaprm
drwxr-xr-x 2 root root     4096 2009-06-02 08:48 migrationtools
-rw-r--r-- 1 root root    20891 2008-04-01 14:11 mime.types
-rw-r--r-- 1 root root      417 2008-03-27 13:25 mke2fs.conf
drwxr-xr-x 3 root root     4096 2009-06-02 08:30 modprobe.d
-rw-r--r-- 1 root root      212 2009-06-02 08:30 modules
lrwxrwxrwx 1 root root       13 2009-06-02 08:25 motd -> /var/run/motd
-rw-r--r-- 1 root root      346 2009-06-02 08:25 motd.tail
-rw-r--r-- 1 root root      414 2009-06-02 08:44 mtab
-rw-r--r-- 1 root root     7672 2008-04-08 05:15 nanorc
drwxr-xr-x 6 root root     4096 2009-06-02 08:25 network
-rw-r--r-- 1 root root       91 2007-05-15 12:07 networks
-rw-r--r-- 1 root root      475 2007-10-20 07:51 nsswitch.conf
-rw-r--r-- 1 root root     1652 2009-06-02 08:43 ntp.conf
drwxr-xr-x 2 root root     4096 2008-04-03 09:00 ODBCDataSources
-rw-r--r-- 1 root root        0 2008-04-03 09:00 odbc.ini
-rw-r--r-- 1 root root        0 2008-04-03 09:00 odbcinst.ini
drwxr-xr-x 2 root root     4096 2009-06-02 08:24 opt
-rw-r--r-- 1 root root      552 2008-05-16 11:18 pam.conf
drwxr-xr-x 2 root root     4096 2009-06-02 08:39 pam.d
-rw-r--r-- 1 root root     1089 2009-06-02 08:48 passwd
-rw------- 1 root root     1063 2009-06-02 08:48 passwd-
drwxr-xr-x 2 root root     4096 2009-06-02 08:25 pcmcia
drwxr-xr-x 4 root root     4096 2009-06-02 08:30 perl
-rw-r--r-- 1 root root      342 2009-06-02 08:30 popularity-contest.conf
drwxr-xr-x 8 root dip      4096 2009-06-02 08:30 ppp
-rw-r--r-- 1 root root      497 2009-06-02 08:25 profile
drwxr-xr-x 2 root root     4096 2008-12-15 13:41 profile.d
-rw-r--r-- 1 root root     2510 2007-12-03 17:04 protocols
drwxr-xr-x 2 root root     4096 2009-06-02 08:25 python
drwxr-xr-x 2 root root     4096 2009-06-02 08:25 python2.5
drwxr-xr-x 2 root root     4096 2009-06-02 08:48 rc0.d
drwxr-xr-x 2 root root     4096 2009-06-02 08:48 rc1.d
drwxr-xr-x 2 root root     4096 2009-06-02 08:48 rc2.d
drwxr-xr-x 2 root root     4096 2009-06-02 08:48 rc3.d
drwxr-xr-x 2 root root     4096 2009-06-02 08:48 rc4.d
drwxr-xr-x 2 root root     4096 2009-06-02 08:48 rc5.d
drwxr-xr-x 2 root root     4096 2009-06-02 08:48 rc6.d
-rwxr-xr-x 1 root root      306 2009-06-02 08:25 rc.local
drwxr-xr-x 2 root root     4096 2009-06-02 08:30 rcS.d
-rw-r--r-- 1 root root       74 2009-06-02 08:35 resolv.conf
-rwxr-xr-x 1 root root      268 2008-04-04 07:06 rmt
-rw-r--r-- 1 root root      887 2007-12-03 17:04 rpc
-rw-r--r-- 1 root root     1024 2008-12-08 04:13 securetty
drwxr-xr-x 2 root root     4096 2009-06-02 08:25 security
-rw-r--r-- 1 root root    18274 2007-12-03 17:04 services
-rw-r----- 1 root shadow    724 2009-06-02 08:48 shadow
-rw------- 1 root root      724 2009-06-02 08:48 shadow-
-rw-r--r-- 1 root root      165 2009-06-02 08:25 shells
drwxr-xr-x 2 root root     4096 2009-06-02 08:25 skel
drwxr-xr-x 2 root root     4096 2009-06-02 08:39 ssh
-r--r----- 1 root root      557 2009-06-02 08:34 sudoers
-rw-r--r-- 1 root root     2405 2008-07-10 05:29 sysctl.conf
-rw-r--r-- 1 root root     1614 2007-11-23 04:02 syslog.conf
drwxr-xr-x 2 root root     4096 2009-06-02 08:25 terminfo
-rw-r--r-- 1 root root       11 2009-06-02 08:25 timezone
-rw-r--r-- 1 root root     1260 2008-02-21 02:22 ucf.conf
drwxr-xr-x 3 root root     4096 2009-06-02 08:25 udev
drwxr-xr-x 2 root root     4096 2009-06-02 08:30 ufw
-rw-r--r-- 1 root root      214 2008-03-08 13:23 updatedb.conf
drwxr-xr-x 2 root root     4096 2009-06-02 08:30 update-manager
drwxr-xr-x 2 root root     4096 2009-06-02 08:25 vim
drwxr-xr-x 2 root root     4096 2009-06-02 08:30 w3m
-rw-r--r-- 1 root root     4221 2007-06-18 05:55 wgetrc
drwxr-xr-x 2 root root     4096 2009-06-02 08:25 wpa_supplicant
drwxr-xr-x 3 root root     4096 2009-06-02 08:25 X11
-rw-r--r-- 1 root root      461 2008-04-03 15:33 zsh_command_not_found
root@testing:/home/test#

```

**directory listing of the /etc/ldap and /ldap_data directories**

```
**root@testing:/home/test# ls -l /etc/ldap**
total 20
-rw-r--r-- 1 root root      245 2008-08-05 16:23 ldap.conf
drwxr-xr-x 2 root root     4096 2008-08-05 16:23 sasl2
drwxr-xr-x 2 root root     4096 2009-06-02 08:48 schema
-rw-r----- 1 root openldap 4748 2009-06-02 09:00 slapd.conf
**root@testing:/home/test# ls -l /ldap_data**
total 800
-rw-r--r-- 1 openldap openldap    2048 2009-06-02 09:00 alock
-rw------- 1 openldap openldap    8192 2009-06-02 09:00 __db.001
-rw------- 1 openldap openldap 2629632 2009-06-02 09:00 __db.002
-rw------- 1 openldap openldap   98304 2009-06-02 09:00 __db.003
-rw------- 1 openldap openldap  868352 2009-06-02 09:00 __db.004
-rw------- 1 openldap openldap   24576 2009-06-02 09:00 __db.005
-rw-r--r-- 1 openldap openldap      96 2009-06-02 09:00 DB_CONFIG
-rw------- 1 openldap openldap    8192 2009-06-02 09:00 dn2id.bdb
-rw------- 1 openldap openldap   32768 2009-06-02 09:00 id2entry.bdb
-rw------- 1 openldap openldap   54296 2009-06-02 09:00 log.0000000001
-rw------- 1 openldap openldap    8192 2009-06-02 09:00 objectClass.bdb
root@testing:/home/test#

```

**View of the entire slapd.conf file**

```
**root@testing:/home/test# cat /etc/ldap/slapd.conf**
# This is the main slapd configuration file. See slapd.conf(5) for more
# info on the configuration options.

#######################################################################
# Global Directives:

# Features to permit
#allow bind_v2

# Schema and objectClass definitions
include         /etc/ldap/schema/core.schema
include         /etc/ldap/schema/cosine.schema
include         /etc/ldap/schema/nis.schema
include         /etc/ldap/schema/inetorgperson.schema

# Where the pid file is put. The init.d script
# will not stop the server if you change this.
pidfile         /var/run/slapd/slapd.pid

# List of arguments that were passed to the server
argsfile        /var/run/slapd/slapd.args

# Read slapd.conf(5) for possible values
loglevel        none

# Where the dynamically loaded modules are stored
modulepath      /usr/lib/ldap
moduleload      back_hdb

# The maximum number of entries that is returned for a search operation
sizelimit 500

# The tool-threads parameter sets the actual amount of cpu's that is used
# for indexing.
tool-threads 1

#######################################################################
# Specific Backend Directives for hdb:
# Backend specific directives apply to this backend until another
# 'backend' directive occurs
backend         hdb

#######################################################################
# Specific Backend Directives for 'other':
# Backend specific directives apply to this backend until another
# 'backend' directive occurs
#backend                <other>

#######################################################################
# Specific Directives for database #1, of type hdb:
# Database specific directives apply to this databasse until another
# 'database' directive occurs
database        hdb

# The base of your directory in database #1
suffix          "dc=pag,dc=local"

# rootdn directive for specifying a superuser on the database. This is needed
# for syncrepl.
# rootdn          "cn=admin,dc=pag,dc=local"

# Where the database file are physically stored for database #1
directory       "/ldap_data"

# The dbconfig settings are used to generate a DB_CONFIG file the first
# time slapd starts.  They do NOT override existing an existing DB_CONFIG
# file.  You should therefore change these settings in DB_CONFIG directly
# or remove DB_CONFIG and restart slapd for changes to take effect.

# For the Debian package we use 2MB as default but be sure to update this
# value if you have plenty of RAM
dbconfig set_cachesize 0 2097152 0

# Sven Hartge reported that he had to set this value incredibly high
# to get slapd running at all. See http://bugs.debian.org/303057 for more
# information.

# Number of objects that can be locked at the same time.
dbconfig set_lk_max_objects 1500
# Number of locks (both requested and granted)
dbconfig set_lk_max_locks 1500
# Number of lockers
dbconfig set_lk_max_lockers 1500

# Indexing options for database #1
index           objectClass eq

# Save the time that the entry gets modified, for database #1
lastmod         on

# Checkpoint the BerkeleyDB database periodically in case of system
# failure and to speed slapd shutdown.
checkpoint      512 30

# Where to store the replica logs for database #1
# replogfile    /var/lib/ldap/replog

# The userPassword by default can be changed
# by the entry owning it if they are authenticated.
# Others should not be able to see it, except the
# admin entry below
# These access lines apply to database #1 only
access to attrs=userPassword,shadowLastChange
        by dn="cn=admin,dc=pag,dc=local" write
        by anonymous auth
        by self write
        by * none

# Ensure read access to the base for things like
# supportedSASLMechanisms.  Without this you may
# have problems with SASL not knowing what
# mechanisms are available and the like.
# Note that this is covered by the 'access to *'
# ACL below too but if you change that as people
# are wont to do you'll still need this if you
# want SASL (and possible other things) to work
# happily.
access to dn.base="" by * read

# The admin dn has full write access, everyone else
# can read everything.
access to *
        by dn="cn=admin,dc=pag,dc=local" write
        by * read

# For Netscape Roaming support, each user gets a roaming
# profile for which they have write access to
#access to dn=".*,ou=Roaming,o=morsnet"
#        by dn="cn=admin,dc=pag,dc=local" write
#        by dnattr=owner write

#######################################################################
# Specific Directives for database #2, of type 'other' (can be hdb too):
# Database specific directives apply to this databasse until another
# 'database' directive occurs
#database        <other>

# The base of your directory for database #2
#suffix         "dc=debian,dc=org"

```

---

### Post by UBSec on 2009-06-03
Hi,
 
 First, avoid to post all your directory listings (it's just an advice) for security reasons. 
 
 I need more information to help you. You can try this :
 
 1) Open two tty (terminal) . 
      > In the first enter (as root) tail -f /var/log/syslog
      > In the second enter /etc/init.d/slapd start  and post the results on the first screen.
 
 2) Have you tried this ?
    > slapd -g openldap -u openldap -f /etc/ldap/slapd.conf
    > post your output

3) You can completely remove and reinstall it 
    > apt-get remove slapd 
    > apt-get clean
    > apt-get install slapd ldap-utils

For now, u don't have to change any setup configuration. We just wanna test the default configuration. Go in your /etc/ldap/slapd.conf file and check the default domain (sometimes it's **nodmain**) . For testing enter this :
     > ladpsearch -x -b 'dc=nodmain' '(objectclass=*)'
If your the default domain is debian.org for example
     > ladpsearch -x -b 'dc=debian, dc=org' '(objectclass=*)'
Then you should have an ldif with the domain informations, the administrator ...

So far, everything looks OK.
 
Now can modify your slapd.conf ( set the domain components, the rootdn and the password ....)

UBSec

---

### Post by ghen on 2009-06-03
> **UBSec said:**
> Hi,
 
 First, avoid to post all your directory listings (it's just an advice) for security reasons. 

Its a brand new test system so it won't be production and not even the same hardware / ip. I appreciate the concern though!

 
> ...
 > In the second enter /etc/init.d/slapd start  and post the results on the first screen.

```
Jun  3 09:08:11 testing slapd[11142]: @(#) $OpenLDAP: slapd 2.4.9 (Aug  5 2008 20:20:57) $ ^Ibuildd@crested:/build/buildd/openldap2.3-2.4.9/debian/build/servers/slapd
Jun  3 09:08:11 testing kernel: [85613.058841] audit(1244034491.818:3): type=1503 operation="inode_create" requested_mask="w::" denied_mask="w::" name="/ldap_data/DUMMY" pid=11142 profile="/usr/sbin/slapd" namespace="default"
Jun  3 09:08:11 testing slapd[11142]: /etc/ldap/slapd.conf: line 63: invalid path: Permission denied
Jun  3 09:08:11 testing slapd[11142]: slapd stopped.
Jun  3 09:08:11 testing slapd[11142]: connections_destroy: nothing to destroy.

```
 
> ...
    > slapd -g openldap -u openldap -f /etc/ldap/slapd.conf
    > post your output

```
Jun  3 09:10:23 testing slapd[11146]: @(#) $OpenLDAP: slapd 2.4.9 (Aug  5 2008 20:20:57) $ ^Ibuildd@crested:/build/buildd/openldap2.3-2.4.9/debian/build/servers/slapd
Jun  3 09:10:23 testing slapd[11146]: /etc/ldap/slapd.conf: line 63: invalid path: Permission denied
Jun  3 09:10:23 testing slapd[11146]: slapd stopped.
Jun  3 09:10:23 testing slapd[11146]: connections_destroy: nothing to destroy.
Jun  3 09:10:23 testing kernel: [85744.443504] audit(1244034623.448:4): type=1503 operation="inode_create" requested_mask="w::" denied_mask="w::" name="/ldap_data/DUMMY" pid=11146 profile="/usr/sbin/slapd" namespace="default"


```
> 
3) You can completely remove and reinstall it 


This was a fresh install, so I'd make the same mistake a second time. I've reinstalled about 3 times now ;) I also posted my slapd.conf file above. You can see in there my domain, superuser, and data directory is set as:

```
# The base of your directory in database #1
suffix          "dc=pag,dc=local"

# rootdn directive for specifying a superuser on the database. This is needed
# for syncrepl.
# rootdn          "cn=admin,dc=pag,dc=local"

# Where the database file are physically stored for database #1
directory       "/ldap_data"

```

---

### Post by keithweddell on 2009-06-03
I think the log lines with "kernel: [xxxxx.xxxxxx] audit ..." are Apparmor messages telling you that Apparmor has blocked access to the files/paths that splad is trying to use.  Have a look into aa-status and aa-logprof (you will need to run them as root / via sudo)

Keith

---

### Post by ghen on 2009-06-03
[quote=wikipedia]AppArmor was first successfully ported/packaged for Ubuntu in April 2007. AppArmor comes installed by default in Ubuntu 7.10 Gutsy Gibbon, and came as a part of the release of Ubuntu 8.04. Although it only protects CUPS by default, the user can install new profiles and enforce them.[/quote]

I don't even know what apparmor is, let alone how to configure it. If all it does by default is protect CUPS I'm not sure how that would affect a service from running.

But then again, wikipedia is only as good as its editors.

---

### Post by keithweddell on 2009-06-03
Try sudo aa-status to see what processes are confined.  If slapd is confined, you can use sudo aa-logprof to decide whether to relax the restrictions.

---

### Post by ghen on 2009-06-03
```

test@testing:~$ sudo aa-status
[sudo] password for test:
apparmor module is loaded.
1 profiles are loaded.
1 profiles are in enforce mode.
   /usr/sbin/slapd
0 profiles are in complain mode.
0 processes have profiles defined.
0 processes are in enforce mode :
0 processes are in complain mode.
0 processes are unconfined but have a profile defined.
test@testing:~$ sudo aa-logprof
Reading log entries from /var/log/messages.
Updating AppArmor profiles in /etc/apparmor.d.
Use of uninitialized value in string eq at /usr/share/perl5/Immunix/SubDomain.pm line 3377.
Use of uninitialized value in string eq at /usr/share/perl5/Immunix/SubDomain.pm line 3377.

Repository: http://apparmor.test.opensuse.org/backend/api

Would you like to enable access to the
profile repository?

(E)nable Repository / (D)isable Repository / Ask Me (L)ater
Enforce-mode changes:

Profile:  /usr/sbin/slapd
Path:     /ldap_data/DUMMY
Mode:     w
Severity: unknown

 [1 - /ldap_data/DUMMY]

(A)llow / [(D)eny] / (G)lob / Glob w/(E)xt / (N)ew / Abo(r)t / (F)inish
Adding /ldap_data/DUMMY w to profile.

= Changed Local Profiles =

The following local profiles were changed.  Would you like to save them?

 [1 - /usr/sbin/slapd]

(S)ave Changes / [(V)iew Changes] / Abo(r)t
Writing updated profile for /usr/sbin/slapd.
test@testing:~$ sudo /etc/init.d/slapd start
Starting OpenLDAP: slapd.
test@testing:~$

```

I chose Ask me (L)ater for the repository (dunno what it does) and (A)llow for the slapd item.


Well that's the best I've done so far! I've screwed up tons of stuff trying to fix this though, so its another re-install from scratch for me... I'll write back in this thread after a clean install.

---

### Post by ghen on 2009-06-08
Update: apparmor was my problem the entire time. Thank you for that, I never knew that program existed and the error messages sure didn't lead to that!

What I did:

deleted the partition, reinstalled 8.04, reinstalled slapd the way I like it, ran aa-logprof and created a profile for slapd, started slapd with no problems.

---

