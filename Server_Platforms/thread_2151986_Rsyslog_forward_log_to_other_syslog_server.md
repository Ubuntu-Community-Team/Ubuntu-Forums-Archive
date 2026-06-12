---
title: "Rsyslog forward log to other syslog server"
date: 2013-06-06
forum: Server Platforms
---

### Post by termvrl on 2013-06-06
Hi All,

I want to ask. How we can forward text file from rsyslog server to another syslog server using syslog.

---

### Post by slickymaster on 2013-06-06
[Reliable Forwarding of syslog Messages with Rsyslog]("http://www.rsyslog.com/doc/rsyslog_reliable_forwarding.html")

---

### Post by termvrl on 2013-06-07
Hi slickymaster,

i still cannot fwd the syslog, 
What i try to do, i setup 2 rsyslog server, rsyslog1 and rsyslog2.
My firewall logs forward to rsyslog1 using syslog udp514, i manage to receive the log ar rsyslog1.
At rsyslog1, i do some log correlation. the result is output to file "output.txt".
I want to forward the result to the rsyslog2. 

Here my rsyslog.conf file.

```
root@ubuntu:/etc# more rsyslog.conf

$ModLoad imuxsock # provides support for local system logging
$WorkDirectory /home/rsyslog/sec-2.7.2/output.txt
$ModLoad imklog   # provides kernel logging support (previously done by rklogd)
#$ModLoad immark  # provides --MARK-- message capability

# provides UDP syslog reception
$ModLoad imudp
$UDPServerRun 514

# provides TCP syslog reception
#$ModLoad imtcp
#$InputTCPServerRun 514

##########################
#### GLOBAL DIRECTIVES ####
###########################

#
# Use traditional timestamp format.
# To enable high precision timestamps, comment out the following line.
#
$ActionFileDefaultTemplate RSYSLOG_TraditionalFileFormat

# Filter duplicated messages
#$RepeatedMsgReduction on

#
# Set the default permissions for all log files.
#
$FileOwner adm
$FileGroup adm
$FileCreateMode 0640
$DirCreateMode 0755
$Umask 0022
$PrivDropToUser adm
$PrivDropToGroup adm

#
# Where to place spool files
#
$ActionQueueType LinkedList   # use asynchronous processing
$ActionQueueFileName srvrfwd  # set file name, also enables disk mode
$ActionResumeRetryCount -1    # infinite retries on insert failure
$ActionQueueSaveOnShutdown on # save in-memory data if rsyslog shuts down
*.*       @@192.168.0.124:514
#
# Include all config files in /etc/rsyslog.d/
#
$IncludeConfig /etc/rsyslog.d/*.conf

```


Thanks for your help.

---

### Post by slickymaster on 2013-06-07
[How do I configure rsyslog to send logs from a specific program to a remote syslog server?]("http://askubuntu.com/questions/186592/how-do-i-configure-rsyslog-to-send-logs-from-a-specific-program-to-a-remote-sysl")[URL="http://kb.monitorware.com/forwarding-other-syslog-t1581.html"]
Forwarding to other syslog[/URL]
[How to Setup Rsyslog Remote Logging on Linux]("http://www.thegeekstuff.com/2012/01/rsyslog-remote-logging/")
[Sending messages to a remote syslog server]("http://www.rsyslog.com/sending-messages-to-a-remote-syslog-server/")

---

### Post by termvrl on 2013-06-07
Hi 

Thanks
Now i can receive the logs.
the problem with this line,

*.*       @@192.168.0.124:514


@@ == send using TCP.

My syslog server listening on UDP.

So, i change to 

*.*       @192.168.0.124:514

Thanks!:D

---

### Post by slickymaster on 2013-06-07
You're welcome. Glad you got it fixed.

---

