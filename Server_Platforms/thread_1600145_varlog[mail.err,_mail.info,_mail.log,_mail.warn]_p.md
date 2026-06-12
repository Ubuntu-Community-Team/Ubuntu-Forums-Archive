---
title: "/var/log/[mail.err, mail.info, mail.log, mail.warn] problems"
date: 2010-10-18
forum: Server Platforms
---

### Post by williamburn on 2010-10-18
I setup my first x64 Ubutnu 10.04 server, dedicated for Nessus scanning.  My problem is that the /var/log/mail* logs are filling up at an alarming rate.  I'm certain I don't have something configured properly and I would appreciate any help that can be given. Obviously anywhere that is > 1G is alarming to me.  Are there any suggestions where to to turn off mail logging, I don't think I need it.  I would like to see Syslog, but perhaps not so verbose.  Is it possible, I need to turn off the Nessus logging to the maillog?

Thank you in advance.

Enclosed is a quick look at my /var/log:

-rw-rw-r--  1 root      utmp 287K 2010-10-18 15:08 lastlog
-rw-r-----  1 syslog    adm     0 2010-08-25 07:42 lpr.log
-rw-r-----  1 syslog    adm  4.6G 2010-10-18 15:18 mail.err
-rw-r-----  1 syslog    adm  8.4G 2010-10-18 15:18 mail.info
-rw-r-----  1 syslog    adm  8.4G 2010-10-18 15:18 mail.log
-rw-r-----  1 syslog    adm  4.6G 2010-10-18 15:18 mail.warn
-rw-r-----  1 syslog    adm  664K 2010-10-18 14:09 messages
-rw-r-----  1 syslog    adm  242K 2010-08-29 06:25 messages.1
drwxr-s---  2 mysql     adm  4.0K 2010-09-03 06:43 mysql
-rw-r-----  1 mysql     adm     0 2010-08-25 07:38 mysql.err
-rw-r-----  1 mysql     adm     0 2010-09-03 06:43 mysql.log
-rw-r-----  1 mysql     adm    20 2010-09-02 06:46 mysql.log.1.gz
-rw-r-----  1 mysql     adm    20 2010-09-01 06:37 mysql.log.2.gz
-rw-r-----  1 mysql     adm    20 2010-08-31 06:45 mysql.log.3.gz
-rw-r-----  1 mysql     adm    20 2010-08-30 06:49 mysql.log.4.gz
-rw-r-----  1 mysql     adm    20 2010-08-29 06:25 mysql.log.5.gz
-rw-r-----  1 mysql     adm    20 2010-08-28 06:43 mysql.log.6.gz
-rw-r-----  1 mysql     adm    20 2010-08-27 06:39 mysql.log.7.gz
drwxr-xr-x  2 root      root 4.0K 2010-08-25 07:42 news
-rw-r--r--  1 root      root    0 2010-08-25 07:28 pycentral.log
-rw-r-----  1 syslog    adm  8.4G 2010-10-18 15:18 syslog
-rw-r-----  1 syslog    adm  182K 2010-09-03 06:39 syslog.1
-rw-r-----  1 syslog    adm   932 2010-09-02 06:39 syslog.2.gz
-rw-r-----  1 syslog    adm   16K 2010-09-01 06:25 syslog.3.gz
-rw-r-----  1 syslog    adm   912 2010-08-31 06:39 syslog.4.gz
-rw-r-----  1 syslog    adm   921 2010-08-30 06:39 syslog.5.gz
-rw-r-----  1 syslog    adm   901 2010-08-29 06:25 syslog.6.gz
-rw-r-----  1 syslog    adm   907 2010-08-28 06:39 syslog.7.gz
-rw-r--r--  1 root      root 208K 2010-10-18 14:09 udev
-rw-r-----  1 syslog    adm     0 2010-08-25 07:42 ufw.log
-rw-r-----  1 syslog    adm  9.0K 2010-09-27 15:03 user.log
-rw-r-----  1 syslog    adm  4.5K 2010-08-25 07:52 user.log.1
-rw-rw-r--  1 root      utmp 100K 2010-10-18 15:08 wtmp
-rw-rw-r--  1 root      utmp  39K 2010-08-31 15:41 wtmp.1

I have found a few articles that mention /etc/rsyslog.conf and /etc/logrotate.conf.  Here is my rsyslog.conf file:

# system-specific logs may be configured here
root@usnsh-s-ss5:/opt# more /etc/rsyslog.conf
#  /etc/rsyslog.conf    Configuration file for rsyslog.
#
#                       For more information see
#                       /usr/share/doc/rsyslog-doc/html/rsyslog_conf.html
#
#  Default logging rules can be found in /etc/rsyslog.d/50-default.conf


#################
#### MODULES ####
#################

$ModLoad imuxsock # provides support for local system logging
$ModLoad imklog   # provides kernel logging support (previously done by rklogd)
#$ModLoad immark  # provides --MARK-- message capability

$KLogPath /proc/kmsg

# provides UDP syslog reception
#$ModLoad imudp
#$UDPServerRun 514

# provides TCP syslog reception
#$ModLoad imtcp
#$InputTCPServerRun 514


###########################
#### GLOBAL DIRECTIVES ####
###########################

#
# Use traditional timestamp format.
# To enable high precision timestamps, comment out the following line.
#
$ActionFileDefaultTemplate RSYSLOG_TraditionalFileFormat

# Filter duplicated messages
$RepeatedMsgReduction on

#
# Set the default permissions for all log files.
#
$FileOwner syslog
$FileGroup adm
$FileCreateMode 0640
$DirCreateMode 0755
$Umask 0022
$PrivDropToUser syslog
$PrivDropToGroup syslog

#
# Include all config files in /etc/rsyslog.d/
#
$IncludeConfig /etc/rsyslog.d/*.conf

---

### Post by SeijiSensei on 2010-10-18
I'd start by disabling Postfix and see what it's complaining about in the mail logs.

---

