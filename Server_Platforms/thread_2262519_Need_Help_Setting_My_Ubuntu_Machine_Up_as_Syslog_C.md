---
title: "Need Help Setting My Ubuntu Machine Up as Syslog Client"
date: 2015-01-25
forum: Server Platforms
---

### Post by uRock on 2015-01-25
I recently placed a Cisco 2651XM as my gateway router and I'd like to set up rsyslog on my ubuntu machine to receive syslog messages. I'd like to have the messages going to a separate file to make for easy viewing. 

Could someone walk me through setting this up in Ubuntu 14.04?

Cheers, Beers & Thanks,
uRock

---

### Post by Habitual on 2015-01-25
[http://ubuntuforums.org/showthread.php?t=2261829&p=13213945#post13213945](http://ubuntuforums.org/showthread.php?t=2261829&p=13213945#post13213945) are some tips I posted.

Have fun.

Subscribed with interest...

---

### Post by uRock on 2015-01-25
> **Habitual said:**
> Here's how I send named logs to my remote syslog server...

I created a /etc/rsyslog.d/10-watchfile.conf file and stuck these contents in it.
```
### /etc/rsyslog.d/10-watchfile.conf
### rsyslogd 7.6.6 on Ubuntu 12.04.5 LTS
# apache error.log
$InputFileName /var/log/apache2/error.log
$InputFileTag apache-errors:
$InputFileStateFile state_file_error_apache
$InputFileFacility local6
$InputFileSeverity info
$InputRunFileMonitor
$InputFilePollInterval 10

# apache access.log
$InputFileName /var/log/apache2/access.log
$InputFileTag apache-access:
$InputFileStateFile state_file_access_apache
$InputFileFacility local6
$InputFileSeverity info
$InputRunFileMonitor
$InputFilePollInterval 10

if $programname == 'apache-access' then @rem.ote.hos.tip:514 
& stop
if $programname == 'apache-errors' then @rem.ote.hos.tip:514
& stop


``` and bounced the rsyslog service daemon using 
```
service rsyslog restart
```

Then on the remote syslog server (@rem.ote.hos.tip) I edited /etc/rsyslog.conf and used this $template
```
$template RemoteHost, "/mnt/kibana/remotes/%HOSTNAME%/%HOSTNAME%.log"
*.* -?RemoteHost
...
# Remote Logging
$RuleSet remote
*.info;mail.none;authpriv.none;cron.none                ?RemoteHost

```

I check either host sending and/or receiving using
```
tcpdump -nn -i eth0 port 514
```

Hope that helps.In the [s]second[/s] third code block is that a file you created or an entry in the rsyslog.conf file?

I was thinking I would be editting this part of the rsyslog.conf, but I am not sure what to type into it to get it to create the log files when the data starts coming in.```
# provides UDP syslog reception
#$ModLoad imudp
#$UDPServerRun 514
```

---

### Post by Habitual on 2015-01-26
Rock:
On the receiving end (your workstation)
You need to **UNcomment **
$UDPServerRun 514
and
$ModLoad imudp 
in /etc/rsyslog.conf

Here's my sanitized /etc/rsyslog.conf on my rsyslog 'server' adjusted for your environment.
```
## Modules
module(load="imuxsock") 
module(load="imklog")   
module(load="imudp") 
###module(load="imtcp")

# Debug options from http://www.rsyslog.com/doc/debug.html
#syslog.* /kibana/syslog.debug;RSYSLOG_DebugFormat
#$DebugFile /path/to/save/syslog.debug 
#$DebugLevel 2

$template RemoteHost, "/path/to/save/cisco.log"
*.* -?RemoteHost

$ActionFileDefaultTemplate RSYSLOG_TraditionalFileFormat


### I touched NONE of this
## Rulesets
# Local Logging
$RuleSet local
kern.*                                                  /var/log/messages
*.info;mail.none;authpriv.none;cron.none                /var/log/messages
authpriv.*                                              /var/log/secure
mail.*                                                  -/var/log/maillog
cron.*                                                  /var/log/cron
*.emerg                                                 :omusrmsg:*
uucp,news.crit                                          /var/log/spooler
local7.*                                                /var/log/boot.log
### ^^^ Should be what's already there, or "default"

$DefaultRuleset local

# Remote Logging
$RuleSet remote
*.info;mail.none;authpriv.none;cron.none                ?RemoteHost

### Input fron UPD applied here from $RuleSet remote
$InputUDPServerBindRuleset remote
### Run UDP Listener
$UDPServerRun 514


### Security
$AllowedSender UDP, ip.of_cisco_gateway_host 
```

I am downloading and installing [http://mirrors.advancedhosters.com/ubuntu-releases/14.04.1/ubuntu-14.04.1-desktop-amd64.iso](http://mirrors.advancedhosters.com/ubuntu-releases/14.04.1/ubuntu-14.04.1-desktop-amd64.iso) in a VM now so I can mirror your requirement.

Edit: Mon Jan 26, 2015 -  9:50:02 AM EST
Installed
```
lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty
```

the /etc/rsyslog.conf I have (sans the comments and blank lines) is
```
cat /etc/rsyslog.conf | grep -v "#" | sed '/^$/d'
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

```

So I'd make a backup of this first and then edit 
```
#$ModLoad imudp
#$UDPServerRun 514
``` to uncomment those.

and at the bottom of /etc/rsyslog.conf I'd add
```
$template RemoteHost, "/path/to/save/cisco.log"
*.* -?RemoteHost
# Remote Logging
$RuleSet remote
*.info;mail.none;authpriv.none;cron.none                ?RemoteHost
### Security
$AllowedSender UDP, ip.of_cisco_gateway_host 
```
and bounce with 
```
sudo service rsyslog restart
```

Adjust "/path/to/save/cisco.log" accordingly.
once that is done, then we'd need to manipulate the cisco host's rsyslog.conf or possibly one of the files in /etc/syslog.d/ on it to start sending stuff over.

This assumes you have udp:514 port open on your workstation.

Let me know!

---

### Post by uRock on 2015-01-28
Awesome, thanx! I will give this a try this weekend.

---

### Post by Habitual on 2015-01-28
You are very welcome.

---

### Post by uRock on 2015-02-01
It created the log file, but now the system is sending the local machine's log messages to the file. Not just the Cisco messages.


rsyslog.conf 
```
ronnie@*:~$ cat /etc/rsyslog.conf | grep -v "#" | sed '/^$/d'
$ModLoad imudp
$UDPServerRun 514
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
$template RemoteHost, "/home/ronnie/CiscoLogs/cisco.log"
*.* -?RemoteHost
$RuleSet remote
*.info;mail.none;authpriv.none;cron.none                ?RemoteHost
$AllowedSender UDP, 10.10.10.1
```

---

### Post by Habitual on 2015-02-01
> **uRock said:**
> It created the log file, but now the system is sending the local machine's log messages to the file. Not just the Cisco messages.

Well, that's a start.
Use the watchfile example in post #[3]("http://ubuntuforums.org/showthread.php?t=2262519&p=13215683#post13215683") for the cisco log file(s) only?

---

### Post by uRock on 2015-02-01
Will do, thanks!

---

### Post by Habitual on 2015-02-02
> **uRock said:**
> Will do, thanks!

I should have explicitly stated that this watchfile (or something similar) is utilized on the cisco device.

---

