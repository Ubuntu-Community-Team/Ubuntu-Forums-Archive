---
title: "RSyslog Default File Permissions"
date: 2011-04-07
forum: Server Platforms
---

### Post by smyk on 2011-04-07
I just build a syslog server with the current version of Ubuntu. I'm having issues with the default file permissions. I can't seem to pinpoint what is setting the permissions on the logs that are getting created. My rsyslog.conf looks like this:


[INDENT]$ModLoad imuxsock # provides support for local system logging
$ModLoad imklog   # provides kernel logging support (previously done by rklogd)
#$ModLoad imtcp
$ModLoad imudp
#$ModLoad immark  # provides --MARK-- message capability

# Templates
# log every host in its own directory
$template RemoteHost,"/var/syslog/%HOSTNAME%/%$YEAR%/%$MONTH%-%$DAY%-syslog.log

### Rulesets

# Remote Logging
$RuleSet remote
*.* ?RemoteHost

$KLogPath /proc/kmsg

### Listeners

# provides UDP syslog reception
# bind ruleset to tcp listener
$InputUDPServerBindRuleset remote
# and activate it:
$UDPServerRun 514


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
$umask 0640
$DirCreateMode 0640
$FileCreateMode 0640
$FileOwner syslog
$FileGroup syslog-group
$DirOwner syslog
$DirGroup syslog-group
$PrivDropToUser syslog
$PrivDropToGroup syslog-group

#
# Include all config files in /etc/rsyslog.d/
#
$IncludeConfig /etc/rsyslog.d/*.conf
[/INDENT]


From my understanding, umask sets the default "foundation" for the file permissions, then the DirCreateMode, FileCreateMode, etc locks the permissions down a bit further.

My permissions on the /var/syslog dir are d--x------


Any help would be greatly appreciated.

---

### Post by hearno on 2012-05-03
Did you figure this out?

---

