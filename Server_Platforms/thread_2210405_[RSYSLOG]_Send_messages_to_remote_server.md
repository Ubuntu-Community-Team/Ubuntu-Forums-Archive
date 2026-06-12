---
title: "[RSYSLOG] Send messages to remote server"
date: 2014-03-10
forum: Server Platforms
---

### Post by TheOnlyChosenOne on 2014-03-10
Hi

I followed the tutorial on [http://www.rsyslog.com/sending-messages-to-a-remote-syslog-server/](http://www.rsyslog.com/sending-messages-to-a-remote-syslog-server/) for the client and [http://www.rsyslog.com/receiving-messages-from-a-remote-system/](http://www.rsyslog.com/receiving-messages-from-a-remote-system/) for the remote server. But now I get the next error when restarting rsyslog on the remote server:
> 2014-03-10T20:37:46.010976+01:00 nsa rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="17832" x-info="http://www.rsyslog.com"] exiting on signal 15.
2014-03-10T20:37:46.046152+01:00 nsa rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="17866" x-info="http://www.rsyslog.com"] start
2014-03-10T20:37:46.045704+01:00 nsa rsyslogd-3000: unknown priority name "" [try [http://www.rsyslog.com/e/3000](http://www.rsyslog.com/e/3000) ]
2014-03-10T20:37:46.045844+01:00 nsa rsyslogd: the last error occured in /etc/rsyslog.conf, line 2:"module(load="imtcp") # needs to be done just once "
2014-03-10T20:37:46.045850+01:00 nsa rsyslogd: warning: selector line without actions will be discarded
2014-03-10T20:37:46.045863+01:00 nsa rsyslogd-3000: unknown priority name "" [try [http://www.rsyslog.com/e/3000](http://www.rsyslog.com/e/3000) ]
2014-03-10T20:37:46.045867+01:00 nsa rsyslogd: the last error occured in /etc/rsyslog.conf, line 3:"input(type="imtcp" port="514")"
2014-03-10T20:37:46.045880+01:00 nsa rsyslogd: warning: selector line without actions will be discarded
2014-03-10T20:37:46.046100+01:00 nsa rsyslogd-2124: CONFIG ERROR: could not interpret master config file '/etc/rsyslog.conf'. [try [http://www.rsyslog.com/e/2124](http://www.rsyslog.com/e/2124) ]
The tutorials don't say which config file has to be edited, or a new config file has to be made. I just replaced the /etc/rsyslog.conf on both servers with the given examples.

---

### Post by TheOnlyChosenOne on 2014-03-10
I'm a bit further now. I followed the next tutorial:
[http://www.thegeekstuff.com/2012/01/rsyslog-remote-logging/](http://www.thegeekstuff.com/2012/01/rsyslog-remote-logging/)
The log files need to show up under /var/log/*ip*/*.log, but so far this directory hasn't been created. Is there a way to test this configuration?

Thanks.

Config file remote server:
> #  /etc/rsyslog.conf    Configuration file for rsyslog.
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
# Where to place spool files
#
$WorkDirectory /var/spool/rsyslog

#
# Include all config files in /etc/rsyslog.d/
#
$IncludeConfig /etc/rsyslog.d/*.conf

# provides support for local system logging
$ModLoad imuxsock 

# provides kernel logging support (previously done by rklogd)
$ModLoad imklog

# provides UDP syslog reception. For TCP, load imtcp.
$ModLoad imudp

# For TCP, InputServerRun 514
$UDPServerRun 514

# This one is the template to generate the log filename dynamically, depending on the client's IP address.
$template FILENAME,"/var/log/%fromhost-ip%/syslog.log"

# Log all messages to the dynamically formed file. Now each clients log (192.168.1.2, 192.168.1.3,etc...), will be under a separate directory which is formed by the template FILENAME.
*.* ?FILENAME

Config file client:
> #  /etc/rsyslog.conf    Configuration file for rsyslog.
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

# Provides TCP forwarding. But the current server runs on UDP
*.* @@nsa.intern:514

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
# Where to place spool files
#
$WorkDirectory /var/spool/rsyslog

#
# Include all config files in /etc/rsyslog.d/
#
$IncludeConfig /etc/rsyslog.d/*.conf

---

### Post by TheOnlyChosenOne on 2014-03-10
It almost seems to work. But I get the next error on the remote server:
> Mar 10 22:07:15 nsa rsyslogd-3000: Could not open dynamic file '/var/log/192.168.0.182/syslog.log' [state -3000] - discarding message [try [http://www.rsyslog.com/e/3000](http://www.rsyslog.com/e/3000) ]
192.168.0.182 is the ip of the client. So the client can send messages, but somehow it cannot create the file. I already tried [this]("http://ubuntuforums.org/showthread.php?t=1686061").

Edit: I manually added the directory (192.168.0.182) and chmod it to 777. Now it works.
Edit2: This is a bit noobish. chown syslog:adm 192.168.0.* is more secure :)

---

