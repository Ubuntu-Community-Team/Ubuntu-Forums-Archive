---
title: "freshclam --config-file=FreshClam.conf ERROR: Can't open/parse the config file FreshC"
date: 2017-02-28
forum: Security
---

### Post by lance bermudez on 2017-02-28
freshclam --config-file=FreshClam.conf
ERROR: Can't open/parse the config file FreshClam.conf

I have it working at home but not at school. I copied the file over that is working. To get freshclam to work I have to 
:/etc/clamav# service clamav-freshclam stop
for home I have freshclam -vvv
for school freshclam --config-file=FreshClam.conf

permissions
```

:/etc/clamav# ls -l
total 16
-r--r--r-- 1 clamav adm   921 Feb  7 21:11 freshclam.conf
-r--r--r-- 1 clamav adm   921 Feb 27 22:29 FreshClam.conf

```

works at home with
```

:/etc/clamav# cat freshclam.conf 
# Automatically created by the clamav-freshclam postinst
# Comments will get lost when you reconfigure the clamav-freshclam package

DatabaseOwner clamav
UpdateLogFile /var/log/clamav/freshclam.log
LogVerbose true
LogSyslog false
LogFacility LOG_LOCAL6
LogFileMaxSize 0
LogRotate true
LogTime true
Foreground false
Debug false
MaxAttempts 10
DatabaseDirectory /var/lib/clamav
DNSDatabaseInfo current.cvd.clamav.net
AllowSupplementaryGroups false
ConnectTimeout 30
ReceiveTimeout 30
TestDatabases yes
ScriptedUpdates yes
CompressLocalDatabase no
SafeBrowsing true
Bytecode true
NotifyClamd /etc/clamav/clamd.conf
# Check for new database 24 times a day
Checks 24
# Proxy settings
#HTTPProxyServer myproxy.com
HTTPProxyServer 192.168.1.2
HTTPProxyPort 3128
DatabaseMirror db.local.clamav.net
DatabaseMirror database.clamav.net

```

configuration for school
```

:/etc/clamav# cat freshclam.conf 
# Automatically created by the clamav-freshclam postinst
# Comments will get lost when you reconfigure the clamav-freshclam package

DatabaseOwner clamav
UpdateLogFile /var/log/clamav/freshclam.log
LogVerbose true
LogSyslog false
LogFacility LOG_LOCAL6
LogFileMaxSize 0
LogRotate true
LogTime true
Foreground false
Debug false
MaxAttempts 10
DatabaseDirectory /var/lib/clamav
DNSDatabaseInfo current.cvd.clamav.net
AllowSupplementaryGroups false
ConnectTimeout 30
ReceiveTimeout 30
TestDatabases yes
ScriptedUpdates yes
CompressLocalDatabase no
SafeBrowsing true
Bytecode true
NotifyClamd /etc/clamav/clamd.conf
# Check for new database 24 times a day
Checks 24
# Proxy settings
#HTTPProxyServer myproxy.com
HTTPProxyServer 12.168.1.5
HTTPProxyPort 3128
DatabaseMirror db.local.clamav.net
DatabaseMirror database.clamav.net

```

---

