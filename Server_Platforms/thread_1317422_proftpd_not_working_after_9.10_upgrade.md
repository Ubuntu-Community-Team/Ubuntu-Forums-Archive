---
title: "proftpd not working after 9.10 upgrade"
date: 2009-11-06
forum: Server Platforms
---

### Post by Foeburner on 2009-11-06
Since I upgraded to 9.10, my FTP server wont give me access to all the folder I specified in Gadmin-Proftp (which was working perfectly).

I am only getting access to my FTP folder which I can create a folder in it but cannot see or access my IT folder. 

At first I thought it was Gadmin acting up but I was able to create a new user with it with access to the same folder (Not the IT folder)

This is my proftpd.conf

```

ServerType standalone
DefaultServer on
Umask 022
ServerName "0.0.0.0"
ServerIdent on "My FTP Server"
ServerAdmin email@example.org
IdentLookups off
UseReverseDNS off
Port 21
PassivePorts 49152 65534
#MasqueradeAddress None
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
  AllowUser jherrera
  AllowUser salezguest
  AllowUser salez
  AllowUser kmcclune
  AllowUser skeesey
  AllowUser solzguest
  AllowUser foeburner
  AllowUser afuentes
  DenyALL
</Limit>

<Anonymous /var/ftp>
User jherrera
Group admin
AnonRequirePassword on
MaxClients 5 "The server is full, hosting %m users"
DisplayLogin welcome.msg
<Limit LOGIN>
 Allow from all
 Deny from all
</Limit>
AllowOverwrite off
AllowOverwrite on
<Limit LIST NLST  STOR STOU  APPE  RETR  RNFR RNTO  DELE  MKD XMKD SITE_MKDIR  PWD XPWD  SIZE  STAT  CWD XCWD  CDUP XCUP >
 AllowAll
</Limit>
<Limit RMD XRMD SITE_RMDIR  SITE  SITE_CHMOD  SITE_CHGRP  MTDM >
 DenyAll
</Limit>
<Directory /var/SolzShares/Shares/IT>
<Limit LIST NLST  STOR STOU  APPE  RETR  MKD XMKD SITE_MKDIR  PWD XPWD  SIZE  STAT  CWD XCWD  CDUP XCUP >
 AllowAll
</Limit>
<Limit RNFR RNTO  DELE  RMD XRMD SITE_RMDIR  SITE  SITE_CHMOD  SITE_CHGRP  MTDM >
 DenyAll
</Limit>
</Directory>
</Anonymous>

<Anonymous /var/ftp/solz/solzguest>
User salezguest
Group salezguest
AnonRequirePassword on
MaxClients 5 "The server is full, hosting %m users"
DisplayLogin welcome.msg
<Limit LOGIN>
Allow from all
Deny from all
</Limit>
AllowOverwrite on
<Limit LIST NLST  STOR STOU  APPE  RETR  RNFR RNTO  DELE  MKD XMKD SITE_MKDIR  PWD XPWD  SIZE  STAT  CWD XCWD >
 AllowAll
</Limit>
<Limit RMD XRMD SITE_RMDIR  SITE  SITE_CHMOD  SITE_CHGRP  MTDM  CDUP XCUP >
 DenyAll
</Limit>
</Anonymous>

<Anonymous /var/ftp/solz/salezguest>
User salez
Group guest
AnonRequirePassword on
MaxClients 5 "The server is full, hosting %m users"
DisplayLogin welcome.msg
<Limit LOGIN>
Allow from all
Deny from all
</Limit>
<Limit LIST NLST  STOR STOU  APPE  RETR  MKD XMKD SITE_MKDIR  PWD XPWD  SIZE  STAT  CWD XCWD >
 AllowAll
</Limit>
<Limit RNFR RNTO  DELE  RMD XRMD SITE_RMDIR  SITE  SITE_CHMOD  SITE_CHGRP  MTDM  CDUP XCUP >
 DenyAll
</Limit>
<Directory /var/ftp/solz/Salez>
<Limit LIST NLST  STOR STOU  APPE  RETR  MKD XMKD SITE_MKDIR  PWD XPWD  SIZE  STAT  CWD XCWD >
 AllowAll
</Limit>
<Limit RNFR RNTO  DELE  RMD XRMD SITE_RMDIR  SITE  SITE_CHMOD  SITE_CHGRP  MTDM  CDUP XCUP >
 DenyAll
</Limit>
</Directory>
</Anonymous>

<Anonymous /var/ftp/solz/salezguest>
User kmcclune
Group solz
AnonRequirePassword on
MaxClients 5 "The server is full, hosting %m users"
DisplayLogin welcome.msg
<Limit LOGIN>
 Allow from all
 Deny from all
</Limit>
AllowOverwrite off
AllowOverwrite on
<Limit LIST NLST  STOR STOU  APPE  RETR  RNFR RNTO  DELE  MKD XMKD SITE_MKDIR  RMD XRMD SITE_RMDIR  PWD XPWD  SIZE  STAT  CWD XCWD >
 AllowAll
</Limit>
<Limit SITE  SITE_CHMOD  SITE_CHGRP  MTDM  CDUP XCUP >
 DenyAll
</Limit>
<Directory /var/ftp/solz/Salez>
AllowOverwrite on
<Limit LIST NLST  STOR STOU  APPE  RETR  RNFR RNTO  DELE  MKD XMKD SITE_MKDIR  RMD XRMD SITE_RMDIR  PWD XPWD  SIZE  STAT  CWD XCWD >
 AllowAll
</Limit>
<Limit SITE  SITE_CHMOD  SITE_CHGRP  MTDM  CDUP XCUP >
 DenyAll
</Limit>
</Directory>
<Directory /var/ftp/solz/kmcclune>
AllowOverwrite on
<Limit LIST NLST  STOR STOU  APPE  RETR  RNFR RNTO  DELE  MKD XMKD SITE_MKDIR  RMD XRMD SITE_RMDIR  PWD XPWD  SIZE  STAT  CWD XCWD  CDUP XCUP >
 AllowAll
</Limit>
<Limit SITE  SITE_CHMOD  SITE_CHGRP  MTDM >
 DenyAll
</Limit>
</Directory>
</Anonymous>

<Anonymous /var/ftp>
User skeesey
Group admin
AnonRequirePassword on
MaxClients 5 "The server is full, hosting %m users"
DisplayLogin welcome.msg
<Limit LOGIN>
 Allow from all
 Deny from all
</Limit>
AllowOverwrite off
AllowOverwrite on
<Limit LIST NLST  STOR STOU  APPE  RETR  RNFR RNTO  DELE  MKD XMKD SITE_MKDIR  PWD XPWD  SIZE  STAT  CWD XCWD  CDUP XCUP >
 AllowAll
</Limit>
<Limit RMD XRMD SITE_RMDIR  SITE  SITE_CHMOD  SITE_CHGRP  MTDM >
 DenyAll
</Limit>
<Directory /var/SolzShares/Shares/IT>
<Limit LIST NLST  STOR STOU  APPE  RETR  MKD XMKD SITE_MKDIR  PWD XPWD  SIZE  STAT  CWD XCWD  CDUP XCUP >
 AllowAll
</Limit>
<Limit RNFR RNTO  DELE  RMD XRMD SITE_RMDIR  SITE  SITE_CHMOD  SITE_CHGRP  MTDM >
 DenyAll
</Limit>
</Directory>
</Anonymous>

<Anonymous /var/ftp/solz/solzguest>
User solzguest
Group guest
AnonRequirePassword on
MaxClients 5 "The server is full, hosting %m users"
DisplayLogin welcome.msg
<Limit LOGIN>
Allow from all
Deny from all
</Limit>
AllowOverwrite on
<Limit LIST NLST  STOR STOU  APPE  RETR  RNFR RNTO  DELE  MKD XMKD SITE_MKDIR  PWD XPWD  SIZE  STAT  CWD XCWD >
 AllowAll
</Limit>
<Limit RMD XRMD SITE_RMDIR  SITE  SITE_CHMOD  SITE_CHGRP  MTDM  CDUP XCUP >
 DenyAll
</Limit>
</Anonymous>

<Anonymous /var/ftp>
User foeburner
Group admin
AnonRequirePassword on
MaxClients 5 "The server is full, hosting %m users"
DisplayLogin welcome.msg
<Limit LOGIN>
Allow from all
Deny from all
</Limit>
AllowOverwrite on
<Limit LIST NLST  STOR STOU  APPE  RETR  RNFR RNTO  DELE  MKD XMKD SITE_MKDIR  PWD XPWD  SIZE  STAT  CWD XCWD  CDUP XCUP >
 AllowAll
</Limit>
<Limit RMD XRMD SITE_RMDIR  SITE  SITE_CHMOD  SITE_CHGRP  MTDM >
 DenyAll
</Limit>
<Directory /var/SolzShares/Shares/IT>
<Limit LIST NLST  STOR STOU  APPE  RETR  MKD XMKD SITE_MKDIR  PWD XPWD  SIZE  STAT  CWD XCWD  CDUP XCUP >
 AllowAll
</Limit>
<Limit RNFR RNTO  DELE  RMD XRMD SITE_RMDIR  SITE  SITE_CHMOD  SITE_CHGRP  MTDM >
 DenyAll
</Limit>
</Directory>
</Anonymous>

<Anonymous /var/ftp>
User afuentes
Group admin
AnonRequirePassword on
MaxClients 5 "The server is full, hosting %m users"
DisplayLogin welcome.msg
<Limit LOGIN>
Allow from all
Deny from all
</Limit>
AllowOverwrite on
<Limit LIST NLST  STOR STOU  APPE  RETR  RNFR RNTO  DELE  MKD XMKD SITE_MKDIR  PWD XPWD  SIZE  STAT  CWD XCWD  CDUP XCUP >
 AllowAll
</Limit>
<Limit RMD XRMD SITE_RMDIR  SITE  SITE_CHMOD  SITE_CHGRP  MTDM >
 DenyAll
</Limit>
<Directory /var/SolzShares/Shares/IT>
<Limit LIST NLST  STOR STOU  APPE  RETR  MKD XMKD SITE_MKDIR  PWD XPWD  SIZE  STAT  CWD XCWD  CDUP XCUP >
 AllowAll
</Limit>
<Limit RNFR RNTO  DELE  RMD XRMD SITE_RMDIR  SITE  SITE_CHMOD  SITE_CHGRP  MTDM >
 DenyAll
</Limit>
</Directory>
</Anonymous>

```

---

