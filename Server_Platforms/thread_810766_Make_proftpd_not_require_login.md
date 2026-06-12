---
title: "Make proftpd not require login"
date: 2008-05-28
forum: Server Platforms
---

### Post by Baufo on 2008-05-28
Hello,

I am currently trying to configure the FTP server proftpd. Currently it will only allow to be accessed when I login with a username and a password, however I would like it also to be accessed anonymously (without a username) (e.g. like [ftp://ftp.debian.org/debian/](ftp://ftp.debian.org/debian/) (the first FTP server that came to my mind :) ).

Here is my /etc/proftpd/proftpd.conf:

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
PassivePorts 49152 65534
#MasqueradeAddress None
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
TLSRSACertificateFile /etc/gadmin-proftpd/gadmin-proftpd.pem
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
  AllowUser thomas
  DenyALL
</Limit>

<Anonymous /var/ftp/>
User thomas
Group ftp
AnonRequirePassword on
MaxClients 10 "The server is full, hosting %m users"
DisplayLogin welcome.msg
<Limit LOGIN>
Allow from all
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

Thanks in advance,
Thomas

---

### Post by The Devil Is A Squirrel on 2008-05-28
> For setting up anonymous logins, there is the <Anonymous> configuration context. If there are no <Anonymous> sections in your proftpd.conf, then no anonymous logins will be allowed - simple.

[http://www.castaglia.org/proftpd/doc/contrib/ProFTPD-mini-HOWTO-ConfigFile.html](http://www.castaglia.org/proftpd/doc/contrib/ProFTPD-mini-HOWTO-ConfigFile.html)

Hope that helps.

---

### Post by Baufo on 2008-05-28
Well, not really, sorry - i had had a look at this page before.

The thing I don't understand is that even though I have an <Anonymous> section it requires me to log in and that this section looks like

<Anonymous /var/ftp/>
User thomas
...
</Anonymous>

for if I log in as the user "thomas" I am not anonymous.

---

### Post by Monicker on 2008-05-28
That just means anonymous users will automatically run as that account.  The normal configuration is to bind anonymous users to a restricted account which limits their acccess on the system.

I think this section explains it fairly well:

[http://www.proftpd.org/docs/directives/linked/config_ref_Anonymous.html]("http://www.proftpd.org/docs/directives/linked/config_ref_Anonymous.html")

---

### Post by Baufo on 2008-05-28
Thank you, now it's clear to me :)

---

