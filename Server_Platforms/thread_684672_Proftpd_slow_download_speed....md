---
title: "Proftpd slow download speed..."
date: 2008-02-01
forum: Server Platforms
---

### Post by chris23 on 2008-02-01
Here's my proftpd.conf file..on windows i used to get higher speed when downloading..i pretty sure that is a settings problem...pls 
get a look at it..thanks

when i start the server i get
- IPv6 getaddrinfo 'home' error: No address associated with hostname
maybe there;s something wrong with that...

p.s the server is behind a router but I think that I've configured that..

```

DefaultRoot ~
ServerType standalone
DefaultServer on
Umask 022
ServerName "****.myftp.org"
ServerIdent on "****"
ServerAdmin Admin@this.domain.topdomain
<Global>
DefaultRoot ~
ServerIdent on "FTP Server ready."
IdentLookups off
</Global>
IdentLookups off
UseReverseDNS off
Port 21
PassivePorts 49152 65534
#MasqueradeAddress *****.myftp.org
TimesGMT off
MaxInstances 30
MaxLoginAttempts 3
TimeoutLogin 300
TimeoutNoTransfer 120
TimeoutIdle 120
DisplayLogin welcome.msg
User nobody
Group nobody
DirFakeUser off nobody
DirFakeGroup off nobody
DefaultTransferMode binary
AllowForeignAddress off
AllowRetrieveRestart on
AllowStoreRestart on
DeleteAbortedStores off
#SystemLog /var/log/secure
RequireValidShell off
#gp_random_username_length 6
#gp_random_password_length 6
#gp_randomize_case lower
#gp_useradd_homedir_path /var/ftp
#gp_html_path /var/www/html/ftp.htm
#gp_welcome_name welcome.msg
<IfModule mod_tls.c>
TLSEngine off
TLSRequired off
TLSVerifyClient off
TLSProtocol TLSv1
TLSLog /var/log/proftpd_tls.log
TLSRSACertificateFile /etc/gproftpd/gproftpd.pem
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
  AllowUser user
  DenyALL
</Limit>
<Anonymous /home/ftp-shared/>
User user
Group ftp-users
AnonRequirePassword on
MaxClients 40 "The server is full, hosting %m users"
DisplayLogin welcome.msg
<Limit LOGIN>
Allow from all
Deny from all
</Limit>
<Limit LIST NLST  APPE  RETR  PWD XPWD  SIZE  STAT  CWD XCWD  CDUP XCUP >
 AllowAll
</Limit>
<Limit STOR STOU  RNFR RNTO  DELE  MKD XMKD SITE_MKDIR  RMD XRMD SITE_RMDIR  SITE  SITE_CHMOD  SITE_CHGRP  MTDM >
 DenyAll
</Limit>
<Directory /home/ftp-shared/Download/Movies/>
<Limit LIST NLST  APPE  RETR  SITE  PWD XPWD  SIZE  STAT  CWD XCWD  CDUP XCUP >
 AllowAll
</Limit>
<Limit STOR STOU  RNFR RNTO  DELE  MKD XMKD SITE_MKDIR  RMD XRMD SITE_RMDIR  SITE_CHMOD  SITE_CHGRP  MTDM >
 DenyAll
</Limit>
</Directory>
<Directory /home/ftp-shared/Upload/>
AllowOverwrite on
<Limit LIST NLST  STOR STOU  APPE  RETR  RNFR RNTO  MKD XMKD SITE_MKDIR  RMD XRMD SITE_RMDIR  SITE  PWD XPWD  SIZE  STAT  CWD XCWD  CDUP XCUP >
 AllowAll
</Limit>
<Limit DELE  SITE_CHMOD  SITE_CHGRP  MTDM >
 DenyAll
</Limit>
</Directory>
</Anonymous>


```

---

### Post by freebeer on 2008-02-02
I don't see any entry in your config for TransferRate.  I upped mine as I expect few simultaneous users:

TransferRate RETR 10000
TransferRate STOR 10000
TransferRate STOU 10000
TransferRate APPE 10000

is what mine are set at and that seems to work for me.

---

### Post by chris23 on 2008-02-04
That didn't seem to solve the problem 
any other  suggestions?

---

