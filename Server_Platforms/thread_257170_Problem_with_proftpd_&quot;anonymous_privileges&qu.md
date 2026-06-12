---
title: "Problem with proftpd &quot;anonymous privileges&quot;"
date: 2006-09-14
forum: Server Platforms
---

### Post by cfBuba on 2006-09-14
Hi mates,

that´s my first posting, usually I´m in "read-only"-mode because most questions are answered properly before.

I´m from Germany, so don´t blame me for any grammatical errors :)


My problem:

I´m using proftpd in combination with its GUI, gproftpd...it worked a few weeks without problems, until a few days ago.

I want it that way:
Only user-access, no anonymous login. Sounds simple, doesn´t it? :)

When I want to login, I receive the following message:

```

[R] Connected to 127.0.0.1
[R] 220 Buba FTP 
[R] USER movies 
[R] 331 Password required for movies. 
[R] PASS (hidden) 
[R] 530-Unable to set anonymous privileges. 
[R] 530 Login incorrect. 
[R] Connection failed 

```

I don´t get the point what "anonymous privileges" means, because i do not even want anything anonymous :(

My proftpd.conf looks like this:
```

ServerType standalone
DefaultServer on
Umask 022
ServerName "0.0.0.0"
ServerIdent on "Buba FTP"
Bind "0.0.0.0"
ServerAdmin Admin@this.domain.topdomain
IdentLookups off
UseReverseDNS off
Port 21
PassivePorts 49152 65534
#MasqueradeAddress None
TimesGMT off
MaxInstances 10
MaxLoginAttempts 3
TimeoutLogin 300
TimeoutNoTransfer 120
TimeoutIdle 120
User nobody
Group nobody
DirFakeUser off nobody
DirFakeGroup off nobody
DefaultTransferMode binary
AllowForeignAddress on
AllowRetrieveRestart on
AllowStoreRestart on
DeleteAbortedStores off
TransferRate RETR 220
TransferRate STOR 220
TransferRate STOU 220
TransferRate APPE 220
SystemLog /var/log/secure
#gp_random_username_length 6
#gp_random_password_length 6
#gp_randomize_case lower
#gp_useradd_root_path /home/ftp
#gp_useradd_upload_path /upload
#gp_html_path /var/www/ftp.html
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
  AllowUser serien
  AllowUser movies
  DenyALL
</Limit>

<Anonymous /media/DOWNLOADS/TV-Serien>
User serien
Group nobody
AnonRequirePassword on
MaxClients 3 "The server is full, hosting %m users"
DisplayLogin welcome.msg
DisplayFirstChdir .msg
AllowOverwrite off
<Limit LOGIN>
 Allow from all
</Limit>
<Limit ROOT_DIR_ALLOW RETR LIST NLST MDTM SIZE STAT CWD XCWD PWD XPWD CDUP XCUP>
 AllowAll
</Limit>
<Limit ROOT_DIR_DENY DELE APPE STOR STOU SITE_CHMOD SITE_CHGRP RNFR RNTO MKD XMKD RMD XRMD>
 DenyAll
</Limit>
</Anonymous>

<Anonymous /media/DOWNLOADS/Filme>
User movies
Group nobody
AnonRequirePassword on
MaxClients 3 "The server is full, hosting %m users"
DisplayLogin welcome.msg
DisplayFirstChdir .msg
AllowOverwrite off
<Limit LOGIN>
 Allow from all
 Deny from all
</Limit>
<Limit ROOT_DIR_ALLOW RETR LIST NLST MDTM SIZE STAT CWD XCWD PWD XPWD CDUP XCUP>
 AllowAll
</Limit>
<Limit ROOT_DIR_DENY DELE APPE STOR STOU SITE_CHMOD SITE_CHGRP RNFR RNTO MKD XMKD RMD XRMD>
 DenyAll
</Limit>
</Anonymous>

```

Might you tell me what´s the problem within my config, I´m quite frustrated because i changed nothing :(

Thank you for your help!

cfBuba

---

### Post by FakeOutdoorsman on 2006-09-14
I'm guessing it is either permission problems of the folder you are accessing or your proftpd.conf is wrong.  Start reading this thread at post #13:

[HOW TO : Create a FTP server with user access (proftpd)]("http://ubuntuforums.org/showthread.php?t=51611&page=2")

or this:

[Proftpd Anonymous Login Problem]("http://ubuntuforums.org/showthread.php?t=175487")

---

