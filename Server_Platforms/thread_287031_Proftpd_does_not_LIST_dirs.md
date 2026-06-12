---
title: "Proftpd does not LIST dirs"
date: 2006-10-28
forum: Server Platforms
---

### Post by linux_newbie_1888 on 2006-10-28
I'm trying to log into my proftpd server for the first time.

My webserver is behind a router, hence the masqueradeaddress setting and passiveports setting in the following config file. 

My problem is that I can connect to the machine - but when trying to LIST the directory, WS_FTP times out with a **"retrieve folder listing failed"** error.

Having read around the problem, I figured it's something to do with my router setup - however, I have port forwarding set up on my router seemingly well (port 21 of external ip >> internal ip of webserver, port 60000 etc of external ip >> internal ip of webserver).

Any ideas on how I could give this thing a kick up the bum into allowing me a folder listing?

:-k 

```
ServerType standalone
DefaultServer on
Umask 022
ServerName "my.external.ip.address"
ServerIdent on "The FTP Server"
Bind "my.external.ip.address"
ServerAdmin webmaster@adomain.com

IdentLookups off
UseReverseDNS off
Port 21
PassivePorts 60000 60001
MasqueradeAddress ftp.adomain.com
TimesGMT off

MaxInstances 30
MaxLoginAttempts 3
TimeoutLogin 300
TimeoutNoTransfer 120
TimeoutIdle 120

User userftp
Group userftp
DirFakeUser off nobody
DirFakeGroup off nobody

DefaultTransferMode ascii
AllowForeignAddress on
AllowRetrieveRestart on
AllowStoreRestart on
DeleteAbortedStores off

TransferRate RETR 30
TransferRate STOR 40
TransferRate STOU 40
TransferRate APPE 40

SystemLog /var/log/secure

<VirtualHost my.internal.ip.address>
DefaultRoot ~
ServerName "Virtual Server"

<Limit LOGIN>
AllowUser au
DenyALL
</Limit>

<Anonymous /var/www/domain>
User au
Group au
AnonRequirePassword on
AllowOverwrite on

<Limit LOGIN>
Allow from all
Deny from all
</Limit>

<Limit ROOT_DIR_ALLOW RETR LIST NLST MDTM SIZE STAT CWD XCWD PWD XPWD CDUP XCUP>
AllowAll
</Limit>

<Limit ROOT_DIR_DENY DELE APPE STOR STOU SITE_CHMOD SITE_CHGRP RNFR RNTO MKD XMKD RMD XRMD>
AllowAll
</Limit>

</Anonymous>
</VirtualHost>
```

---

