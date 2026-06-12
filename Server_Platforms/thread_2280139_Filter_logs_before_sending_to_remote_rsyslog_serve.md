---
title: "Filter logs before sending to remote rsyslog server"
date: 2015-05-28
forum: Server Platforms
---

### Post by lingpanda on 2015-05-28
Hello,

How do I filter logs from being sent to a remote rsyslog server? For instance I would like to prevent cron jobs from being sent to the rsyslog server. I currently have the syntax 

```
*.* @192.168.1.10:514
```

in my rsyslog.conf file. This forwards all logs to the remote server. Now I want to start to filter out what gets sent. I'm staring with cron jobs for example. Thanks.

---

### Post by Habitual on 2015-05-28
Check /etc/rsyslog.conf 
```
for cron.*                                                  /var/log/cron
```
It may be remarked out w\an "#", if it is, unremark it and ```
service rsyslog restart
```

It can remain commented out, if that line exists and you can just add this to the bottom of the /etc/rsyslog.conf file:
```
# Log cron stuff
cron.*                                                  /var/log/cron
*.* @192.168.1.10:514
```and ```
service rsyslog restart
```
That should do it.

---

### Post by lingpanda on 2015-05-28
> **Habitual said:**
> Check /etc/rsyslog.conf 
```
for cron.*                                                  /var/log/cron
```
It may be remarked out w\an "#", if it is, unremark it and ```
service rsyslog restart
```

It can remain commented out, if that line exists and you can just add this to the bottom of the /etc/rsyslog.conf file:
```
# Log cron stuff
cron.*                                                  /var/log/cron
*.* @192.168.1.10:514
```and ```
service rsyslog restart
```
That should do it.

I tried your suggestion prior to posting. I initially did not have the 

```
cron.*                   /var/log/cron
```
line in my rsyslog.conf file. I added this in and it resulted in the logs being sent to the new cron file as well as being sent to the server. Here is my complete rsyslog.conf file. Thanks.



```
root@pf1:~# vi /etc/rsyslog.conf
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
#$ModLoad imudp
#$UDPServerRun 514

# provides TCP syslog reception
#$ModLoad imtcp
#$InputTCPServerRun 514

# Enable non-kernel facility klog messages
$KLogPermitNonKernelFacility on

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
# Log cron stuff
cron.*                                        /var/log/cron

$IncludeConfig /etc/rsyslog.d/*.conf
*.* @192.168.1.10:514


```

---

### Post by Habitual on 2015-05-28
I stripped the comments out and here is the result, including what I believe needs to happen:
```
$KLogPermitNonKernelFacility on
$ActionFileDefaultTemplate RSYSLOG_TraditionalFileFormat
$RepeatedMsgReduction on
$FileOwner syslog
$FileGroup adm
$FileCreateMode 0640
$DirCreateMode 0755
$Umask 0022
$PrivDropToUser syslog
$PrivDropToGroup syslog
$WorkDirectory /var/spool/rsyslog
$IncludeConfig /etc/rsyslog.d/*.conf

### lingpanda
cron.*                                        /var/log/cron
:msg, contains, "cron" /var/log/cron
~
*.* @192.168.1.10:514
```and of course, restart using ```
service rsyslog restart
``` after edit/save...

Also, check /etc/rsyslog.d/50-default.conf for commented cron entry, and remove the comment, save and exit. Restart rsyslog, see what's what.

---

### Post by lingpanda on 2015-05-28
> **Habitual said:**
> I stripped the comments out and here is the result, including what I believe needs to happen:
```
$KLogPermitNonKernelFacility on
$ActionFileDefaultTemplate RSYSLOG_TraditionalFileFormat
$RepeatedMsgReduction on
$FileOwner syslog
$FileGroup adm
$FileCreateMode 0640
$DirCreateMode 0755
$Umask 0022
$PrivDropToUser syslog
$PrivDropToGroup syslog
$WorkDirectory /var/spool/rsyslog
$IncludeConfig /etc/rsyslog.d/*.conf

### lingpanda
cron.*                                        /var/log/cron
:msg, contains, "cron" /var/log/cron
~
*.* @192.168.1.10:514
```and of course, restart using ```
service rsyslog restart
``` after edit/save...

Also, check /etc/rsyslog.d/50-default.conf for commented cron entry, and remove the comment, save and exit. Restart rsyslog, see what's what.


OK I might be at fault here. I decided to take a look at my syslog file and I notice the cron messages are missing. But for whatever reason they are still showing up on my server. It would seem that all was needed is 

```
cron .*          /var/log/cron
```

to prevent them from going to syslog. 

These are the cron messages I see being forwarded.

```
root@pf1:~# cat /etc/cron.d/sysstat
# The first element of the path is a directory where the debian-sa1
# script is located
PATH=/usr/lib/sysstat:/usr/sbin:/usr/sbin:/usr/bin:/sbin:/bin

# Activity reports every 10 minutes everyday
5-55/10 * * * * root command -v debian-sa1 > /dev/null && debian-sa1 1 1

# Additional run at 23:59 to rotate the statistics file
59 23 * * * root command -v debian-sa1 > /dev/null && debian-sa1 60 2
```


and executing

```
crontab -e
```

---

### Post by Habitual on 2015-05-28
Sorry, I'm stumped.

---

### Post by lingpanda on 2015-05-29
> **Habitual said:**
> Sorry, I'm stumped.

Habitual I appreciate your time. I did finally settle on a solution that worked. I added the following in my rsyslog.conf file.

```
cron.* /var/log/cron.log
:msg, contains, "cron" stop
auth,authpriv,daemon,kern,lpr,mail,mark,news,syslog,user,uucp,local0,local1,local2,local3,local4,local5,local6,local7.* @192.168.1.10:514
```

I believe I covered all the facility and priority keywords. Not exactly what I wanted to do but it works.

---

### Post by Habitual on 2015-05-29
Good Job and Well Done!
I saw that you weren't utilizing the facilities, but I didn't want to open a can-of-worms.
Props+

---

