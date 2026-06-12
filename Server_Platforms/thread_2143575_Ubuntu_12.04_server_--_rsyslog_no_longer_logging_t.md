---
title: "Ubuntu 12.04 server -- rsyslog no longer logging to default /var/log/syslog"
date: 2013-05-09
forum: Server Platforms
---

### Post by jimmah6786 on 2013-05-09
Hi All,

I've been trying to get rsyslog working to accept remote logs. I've read many articles that argue how easy it is, implementing steps on both the server side and client/forward side.

In messing around with my rsyslog.conf I believe I have render rsyslog broken. As when I tail my /var/log/syslog log, there are no entries in the past hour and I have started, stop, restarted services.

Here is my rsyslog.conf file:
```
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

# provides UDP syslog reception
$ModLoad imudp
$UDPServerRun 514

# provides TCP syslog reception
$ModLoad imtcp
$InputTCPServerRun 514


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
# Where to place spool files
#
$WorkDirectory /var/spool/rsyslog

#
# Include all config files in /etc/rsyslog.d/
$IncludeConfig /etc/rsyslog.d/*.conf
```

As you can see the only difference from the default rsyslog.conf is I've enabled UDP module.

I do a sudo service rsyslog restart
```
sudo service rsyslog restart
```

Check the process is running,
```
ps gaux|grep rsyslog
root     27921  0.0  0.0  17280  1200 ?        Ss   11:29   0:00 rsyslogd -c5
root     27922  0.0  0.0      0     0 ?        Z    11:29   0:00 [rsyslogd] <defunct>
1000     28023  0.0  0.0   9384   912 pts/0    S+   11:30   0:00 grep --color=auto rsyslog
```

tailing my **/var/log/syslog** file hasn't show anything within an hour. Even though I've restart the rsyslog service like 30 times.

Am I missing a step somewhere?

Thank you for taking a look, I appreciate it.

---

### Post by jimmah6786 on 2013-05-09
Ok, I figured it out. I checked out another ubuntu server I had running. Specifically the **permissions** that are set on the** /var/log/syslog** file.

Changed ownership of **/var/log/syslog from root.adm to syslog.adm** and now it works.

---

