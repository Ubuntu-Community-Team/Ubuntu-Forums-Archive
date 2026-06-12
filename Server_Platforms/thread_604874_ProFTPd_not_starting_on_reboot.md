---
title: "ProFTPd not starting on reboot"
date: 2007-11-06
forum: Server Platforms
---

### Post by Twindagger on 2007-11-06
Hi all-

I installed ProFTPd on my Ubuntu 7.10 box and configured it in standalone mode. It works just fine, but I have to start the daemon using "sudo /etc/init.d/proftpd start" every time I reboot my machine. When I start it, I receive this message:

 * Starting ftp server proftpd                                                   
- IPv6 getaddrinfo 'succubus' error: No address associated with hostname
  succubus - 127.0.1.1:21 masquerading as xxx.xxx.xxx.xxx (my external ip)
                                                                         [ OK ]

The ftp server works fine, but I'd rather not have to manually start it every time I reboot. I checked the /etc/rc[2-5].d folders and there is a symbolic link in each: S50proftpd -> ../init.d/proftpd

I checked my /var/log/syslog, but I can't find any entries with ftp in them. The /var/log/proftpd/proftpd.log file is empty.

I'm at a loss here. Any ideas?

Here's my proftpd.conf:

```

ServerType standalone
DefaultServer on
Umask 022
ServerName "0.0.0.0"
ServerIdent on "My FTPD"
ServerAdmin Admin@this.domain.topdomain
IdentLookups off
UseReverseDNS off
Port 21
PassivePorts 65434 65534
MasqueradeAddress my.external-host.name
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
TransferRate RETR 30
TransferRate STOR 40
TransferRate STOU 40
TransferRate APPE 40
SystemLog /var/log/secure
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
  AllowUser wwwadmin
  AllowUser guest
  AllowUser anonymous
  DenyALL
</Limit>

<Anonymous /var/ftp>
User wwwadmin
Group wwwwriters
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
<Limit STOR STOU  APPE  RNFR RNTO  DELE  MKD XMKD SITE_MKDIR  RMD XRMD SITE_RMDI
R  SITE  SITE_CHMOD  SITE_CHGRP  MTDM >
 DenyAll
</Limit>
<Directory /var/ftp/upload>
<Limit LIST NLST  STOR STOU  RETR  RNFR RNTO  PWD XPWD  SIZE  STAT  CWD XCWD  CD
UP XCUP >
 AllowAll
</Limit>
<Limit APPE  DELE  MKD XMKD SITE_MKDIR  RMD XRMD SITE_RMDIR  SITE  SITE_CHMOD  S
ITE_CHGRP  MTDM >
 DenyAll
</Limit>
</Directory>
<Directory /var/ftp/www>
AllowOverwrite on
<Limit LIST NLST  STOR STOU  RETR  RNFR RNTO  DELE  MKD XMKD SITE_MKDIR  RMD XRM
D SITE_RMDIR  PWD XPWD  SIZE  STAT  CWD XCWD  CDUP XCUP >
 AllowAll
</Limit>
<Limit APPE  SITE  SITE_CHMOD  SITE_CHGRP  MTDM >
 DenyAll
</Limit>
</Directory>
</Anonymous>

<Anonymous /var/ftp>
User guest
Group wwwwriters
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
<Limit STOR STOU  APPE  RNFR RNTO  DELE  MKD XMKD SITE_MKDIR  RMD XRMD SITE_RMDI
R  SITE  SITE_CHMOD  SITE_CHGRP  MTDM >
 DenyAll
</Limit>
<Directory /var/ftp/upload>
<Limit LIST NLST  STOR STOU  RETR  RNFR RNTO  PWD XPWD  SIZE  STAT  CWD XCWD  CD
UP XCUP >
 AllowAll
</Limit>
<Limit APPE  DELE  MKD XMKD SITE_MKDIR  RMD XRMD SITE_RMDIR  SITE  SITE_CHMOD  S
ITE_CHGRP  MTDM >
 DenyAll
</Limit>
</Directory>
</Anonymous>

<Anonymous /var/ftp>
User anonymous
Group anonymous
AnonRequirePassword off
MaxClients 5 "The server is full, hosting %m users"
DisplayLogin welcome.msg
</Limit>
</Directory>
</Anonymous>

<Anonymous /var/ftp>
User anonymous
Group anonymous
AnonRequirePassword off
MaxClients 5 "The server is full, hosting %m users"
DisplayLogin welcome.msg
<Limit LOGIN>
Allow from all
Deny from all
</Limit>
<Limit LIST NLST  RETR  PWD XPWD  SIZE  STAT  CWD XCWD  CDUP XCUP >
 AllowAll
</Limit>
<Limit STOR STOU  APPE  RNFR RNTO  DELE  MKD XMKD SITE_MKDIR  RMD XRMD SITE_RMDI
R  SITE  SITE_CHMOD  SITE_CHGRP  MTDM >
 DenyAll
</Limit>
</Anonymous>

```

---

