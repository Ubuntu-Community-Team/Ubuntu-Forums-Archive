---
title: "Proftpd: Failed to retrieve directory listing"
date: 2009-06-09
forum: Server Platforms
---

### Post by thrones on 2009-06-09
Using Ubuntu server Jaunty. I have proftpd installed and configured but am getting this error when I try to connect via filezilla:

[PHP]Status:	Resolving address of <mydomain.com>
Status:	Connecting to <myipaddress>:21...
Status:	Connection established, waiting for welcome message...
Response:	220 <myserver>
Command:	USER <userftp>
Response:	331 Password required for <userftp>
Command:	PASS *******
Response:	230-Welcome, archive user user@::ffff:<randomip> !
Response:	 
Response:	 The local time is: Tue Jun  9 09:08:11 2009
Response:	 
Response:	 This is an experimental FTP server.  If you have any unusual problems,
Response:	 please report them via e-mail to <root@cpe-myipaddress.com>.
Response:	 
Response:	230 Anonymous access granted, restrictions apply
Command:	OPTS UTF8 ON
Response:	200 UTF8 set to on
Status:	Connected
Status:	Retrieving directory listing...
Command:	PWD
Response:	257 "/" is the current directory
Command:	TYPE I
Response:	200 Type set to I
Command:	PASV
Response:	227 Entering Passive Mode (<myipaddress>,195,95)
Command:	LIST
Error:	Connection timed out
Error:	Failed to retrieve directory listing[/PHP]

When using android's ftp client it just hangs on the PASV command as well.

My proftpd.conf is as follows

[PHP]ServerType standalone
DefaultServer on
Umask 022
ServerName "192.168.1.3"
ServerIdent on "<myserver>"
ServerAdmin email@example.org
IdentLookups off
UseReverseDNS off
Port 21
PassivePorts 60000 60100
MasqueradeAddress <my dyndns address>
TimesGMT off
MaxInstances 30
MaxLoginAttempts 3
TimeoutLogin 300
TimeoutNoTransfer 120
TimeoutIdle 120
DisplayLogin welcome.msg
DisplayChdir .message
User nobody
Group nobody
DirFakeUser off nobody
DirFakeGroup off nobody
DefaultTransferMode binary
AllowForeignAddress off
AllowRetrieveRestart on
AllowStoreRestart on
DeleteAbortedStores off
TransferRate RETR 220
TransferRate STOR 250
TransferRate STOU 250
TransferRate APPE 250
SystemLog /var/log/secure
RequireValidShell off
<IfModule mod_tls.c>
TLSEngine off
TLSRequired off
TLSVerifyClient off
TLSProtocol SSLv23
TLSLog /var/log/proftpd_tls.log
TLSRSACertificateFile /etc/gadmin-proftpd/certs/cert.pem
TLSRSACertificateKeyFile /etc/gadmin-proftpd/certs/key.pem
TLSCACertificateFile /etc/gadmin-proftpd/certs/cacert.pem
TLSRenegotiate required off
</IfModule>
<IfModule mod_ratio.c>
Ratios off
SaveRatios off
RatioFile "/restricted/proftpd_ratios"
RatioTempFile "/restricted/proftpd_ratios_temp"
CwdRatioMsg "Please upload first!"
FileRatioErrMsg "FileRatio limit exceeded, upload something first..."
ByteRatioErrMsg "ByteRatio limit exceeded, upload something first..."
LeechRatioMsg "Your ratio is unlimited."
</IfModule>
<Limit LOGIN>
  AllowUser <userftp>
  DenyALL
</Limit>

<Anonymous /home/ftp>
User <userftp>
Group nobody
AnonRequirePassword on
MaxClients 5 "The server is full, hosting %m users"
DisplayLogin welcome.msg
<Limit LOGIN>
Allow from all
Deny from all
</Limit>
<Limit LIST NLST  RETR  PWD XPWD  SIZE  STAT  CWD XCWD  CDUP XCUP >
 AllowAll
</Limit>
<Limit STOR STOU  APPE  RNFR RNTO  DELE  MKD XMKD SITE_MKDIR  RMD XRMD SITE_RMDIR  SITE  SITE_CHMOD  SITE_CHGRP  MTDM >
 DenyAll
</Limit>
</Anonymous>
[/PHP]

I'm pretty sure I've forwarded my ports correctly. Attached is a screenshot:
[IMG]http://imgur.com/FQFKb.png[/IMG]

What could be the problem?

---

### Post by loudog23 on 2009-07-14
It took me a while because all seems fine, so the only things that comes to my mind would be your permision.
if proftpd (or the user using the ftp) dosen't have proper permision, the system kick him without listing.

[http://ubuntuforums.org/showthread.php?t=79588](http://ubuntuforums.org/showthread.php?t=79588) <- Excelent thread on proftpd

I would also try to change the part inside <anonymous>
```
<Limit LOGIN>
Allow from all
Deny from all
</Limit> 
```
to the same you have above
```
<Limit LOGIN>
  AllowUser <userftp>
  DenyALL
</Limit> 
```

---

### Post by loudog23 on 2009-07-14
> 
  AllowUser <userftp>


BOOM!!! remove the < and >

btw, if you add more user, simply put a , bewteen

```
AllowUser loudog23, thrones, userftp
```

---

