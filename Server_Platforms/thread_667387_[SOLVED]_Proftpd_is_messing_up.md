---
title: "[SOLVED] Proftpd is messing up"
date: 2008-01-14
forum: Server Platforms
---

### Post by Dr Small on 2008-01-14
Ok, so I have proftpd and gproftpd on my server, to manage my FTP accounts (yes, I know, ftp is very insecure, but it's on a closed network with all family members, so I really don't care).

I have 4 users. One is drsmall, and it's current home directory is /var/ftp/drsmall. Likewise with the rest of the users, except that they go to /var/ftp/USER

Ok. At one time of the day, I changed drsmall's home directory to /opt/lampp/htdocs/ so he could manage the HTTP directory, and I have a system link in that directory to /var/ftp so the ftp files can be viewed over HTTP.

So anyhow, I couldn't go into the system link with FTP, because it said it wasn't a directory, so I added myself back to /var/ftp/drsmall. Well now, every time I shut the server down, ANY FTP account that connects to the server, they Home directory is pointing to /opt/lampp/htdocs.

If I open gproftpd, and click deactivate, and then reactivate, then everybody's home directory is set correctly, and then we FTP into our directories. I don't know how to solve this, and I really don't want to ssh into the server and deactivate + activate the FTP server every time I restart the server.

Here the the contents of /etc/proftpd/proftpd.conf:
```
ServerType standalone
DefaultServer on
Umask 022
ServerName "192.168.0.70"
ServerIdent on "Mycroft FTP"
ServerAdmin drsmall@hackermail.com
IdentLookups off
UseReverseDNS off
Port 21
PassivePorts 49150 65534
#MasqueradeAddress None
TimesGMT off
MaxInstances 30
MaxLoginAttempts 2
TimeoutLogin 300
TimeoutNoTransfer 30000
TimeoutIdle 30000
DisplayLogin welcome.msg
DisplayFirstChdir .message
User nobody
Group nobody
DirFakeUser off nobody
DirFakeGroup off nobody
DefaultTransferMode binary
AllowForeignAddress on
AllowRetrieveRestart on
AllowStoreRestart on
DeleteAbortedStores off
TransferRate RETR 10000
TransferRate STOR 10000
TransferRate STOU 10000
TransferRate APPE 10000
SystemLog /var/log/secure
RequireValidShell off
#gp_random_username_length 6
#gp_random_password_length 6
#gp_randomize_case lower
#gp_useradd_homedir_path /var/ftp
#gp_useradd_upload_path /upload
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
<Limit LOGIN>
  AllowUser toplevel
  AllowUser drsmall
  AllowUser bill
  AllowUser firefoxwiz
  AllowUser donna
  DenyALL
</Limit>

<Anonymous /opt/lampp/htdocs>
User toplevel
Group toplevel
AnonRequirePassword on
MaxClients 6 "The server is full, hosting %m users"
DisplayLogin welcome.msg
DisplayFirstChdir .msg
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

<Anonymous /var/ftp/drsmall>
User drsmall
Group drsmall
AnonRequirePassword on
MaxClients 5 "The server is full, hosting %m users"
DisplayLogin welcome.msg
DisplayFirstChdir .msg
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

<Anonymous /var/ftp/bill>
User bill
Group bill
AnonRequirePassword on
MaxClients 5 "The server is full, hosting %m users"
DisplayLogin welcome.msg
DisplayFirstChdir .msg
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

<Anonymous /var/ftp/firefoxwiz>
User firefoxwiz
Group firefoxwiz
AnonRequirePassword on
MaxClients 5 "The server is full, hosting %m users"
DisplayLogin welcome.msg
DisplayFirstChdir .msg
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

<Anonymous /var/ftp/donna>
User donna
Group donna
AnonRequirePassword on
MaxClients 5 "The server is full, hosting %m users"
DisplayLogin welcome.msg
DisplayFirstChdir .msg
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

And it doesn't state anything in it about /opt/lampp/htdocs/ before, or after I restart the FTP server.

So, I am confused, and if anyone could shed some light on this, I would be most grateful :)

Thanks,
Dr Small


Edit, I just went and removed proftpd and gproftpd and started over, but I still am having the same problem. I even deleted the proftpd.conf file, and it recreated it, but now every time I restart the server, it is taking me to /opt/lampp/htdocs/

---

### Post by Dr Small on 2008-01-14
Problem Solved.
It was a startup issue.

The XAMPP ftp daemon was running before the proftpd one, which deactivated it, and was then setting my FTP directory at /opt/lampp/htdocs/

So I changed the startup order in /etc/rc2.d/ and made proftpd start before lampp, and now my problems are solved :)

Dr Small

---

