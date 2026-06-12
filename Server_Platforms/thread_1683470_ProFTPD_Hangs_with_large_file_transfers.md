---
title: "ProFTPD Hangs with large file transfers"
date: 2011-02-07
forum: Server Platforms
---

### Post by Darkness Des on 2011-02-07
I have ProFTPD running on a server machine and so far it has worked beautifully. The only problem is that now I'm trying to use it as a sort of home streaming server (with WiiMC) and to do that I need to remove Windows from the second hard drive in there and use it as storage space. However, when I attempt to move data onto my backup drive remotely, it freezes after copying about 189 MB (depending on how big the file is). Is there some way to get around this limit? This is my ProFTPD.conf file:
```

ModulePath /usr/lib/proftpd
LoadModule mod_ctrls_admin.c
LoadModule mod_tls.c
LoadModule mod_radius.c
LoadModule mod_quotatab.c
LoadModule mod_quotatab_file.c
LoadModule mod_quotatab_radius.c
LoadModule mod_wrap.c
LoadModule mod_rewrite.c
LoadModule mod_load.c
LoadModule mod_ban.c
LoadModule mod_wrap2.c
LoadModule mod_wrap2_file.c
LoadModule mod_dynmasq.c
LoadModule mod_vroot.c
LoadModule mod_ifsession.c
ServerType standalone
DefaultServer on
Umask 022
ServerName "0.0.0.0"
ServerIdent on "Home Server"
ServerAdmin (my email is here)
IdentLookups off
UseReverseDNS off
Port 21
PassivePorts 49152 65534
#MasqueradeAddress None
TimesGMT off
MaxInstances 30
MaxLoginAttempts 3
TimeoutLogin 0
TimeoutNoTransfer 0
TimeoutIdle 0
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
TLSOptions AllowClientRenegotiation
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
  AllowUser mark
  DenyALL
</Limit>

<Anonymous /root/..>
User mark
Group mark
AnonRequirePassword on
MaxClients 5 "The server is full, hosting %m users"
DisplayLogin welcome.msg
DisplayChdir .msg
<Limit LOGIN>
Allow from All
Deny from all
</Limit>
AllowOverwrite on
<Limit LIST NLST  STOR STOU  APPE  RETR  RNFR RNTO  DELE  MKD XMKD SITE_MKDIR  RMD XRMD SITE_RMDIR  SITE  SITE_CHMOD  SITE_CHGRP  MTDM  PWD XPWD  SIZE  STAT  CWD XCWD  CDUP XCUP >
 AllowAll
</Limit>
<Limit NOTHING >
 DenyAll
</Limit>
</Anonymous>

```

---

