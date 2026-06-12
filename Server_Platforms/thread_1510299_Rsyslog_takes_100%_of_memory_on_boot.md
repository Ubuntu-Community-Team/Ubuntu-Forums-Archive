---
title: "Rsyslog takes 100% of memory on boot"
date: 2010-06-15
forum: Server Platforms
---

### Post by noex869 on 2010-06-15
I'm trying to run a logging server with encryption but rsyslog takes 100% of the memory on boot.  This only happens when these two sets of lines are both in the rsyslog.conf

```
$ModLoad imtcp
$InputTCPServerRun 10514

```
and
```
$DefaultNetstreamDriver gtls
$ActionSendStreamDriverAuthMode x509/name
$ActionSendStreamDriverMode 1
```

I can run it non-encrypted with no problems.  This is running on a ubuntu 10.4 vm on a ESXv4.  It has also been tested on a vmware workstation 7.  It still has the memory issue when no clients are talking to it.

rsyslog 4.2.0-2ubuntu8
gnutls-bin 2.8.5-2

Any Ideas as to what might be causing this?

rsyslog.conf - rsyslog owns and can read the ca, key, and cert
```
#  /etc/rsyslog.conf    Configuration file for rsyslog.
#
#            For more information see
#            /usr/share/doc/rsyslog-doc/html/rsyslog_conf.html
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
$ModLoad imtcp
$InputTCPServerRun 10514

# TLS
$DefaultNetstreamDriver gtls

$DefaultNetstreamDriverCAFile /etc/ssl/rsyslog/ca.crt
$DefaultNetstreamDriverCertFile /etc/ssl/rsyslog/server.crt
$DefaultNetstreamDriverKeyFile /etc/ssl/rsyslog/server.key

$ActionSendStreamDriverAuthMode x509/name
$ActionSendStreamDriverPermittedPeer client.example.com
$ActionSendStreamDriverMode 1

###########################
#### GLOBAL DIRECTIVES ####
###########################

#
# Use traditional timestamp format.
# To enable high precision timestamps, comment out the following line.
#
# $ActionFileDefaultTemplate RSYSLOG_TraditionalFileFormat

# Filter duplicated messages
# $RepeatedMsgReduction on

# Uniprocessor optimization
$OptimizeForUniprocessor on

# For handling windows events
$EscapeControlCharactersOnReceive off

#
# Set the default permissions for all log files.
#
$FileOwner syslog
$FileGroup adm
$FileCreateMode 0640
$DirOwner syslog
$DirGroup adm
$DirCreateMode 0755
$Umask 0022
$PrivDropToUser syslog
#$PrivDropToGroup syslog
$privDropToGroup adm

#
# Include all config files in /etc/rsyslog.d/
#
$IncludeConfig /etc/rsyslog.d/*.conf

```

---

### Post by noex869 on 2010-07-14
I still have no idea what was causing this problem, but building rsyslog 5.4.0 from source seems to have fixed the problem.

---

### Post by noex869 on 2010-08-27
Rsyslog 5.4.0 handles bad input better which is why my problem went away but rsyslog was still not working.  There was an error in generating the certs that I saw as warning. doh. Its all working now with proper certs and stock rsyslog; however, I can't find a free windows client that can send to rsyslog with native tls.

---

