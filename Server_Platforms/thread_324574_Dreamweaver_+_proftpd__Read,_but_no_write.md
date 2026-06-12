---
title: "Dreamweaver + proftpd : Read, but no write"
date: 2006-12-23
forum: Server Platforms
---

### Post by Littleweseth on 2006-12-23
G'day;

I'm trying to bludgeon proftpd into working with Dreamweaver 8 so that I can write to /var/www (put files, create directories, delete things, all that jazz) with Dreamweaver's builtin FTP client. Note : Security is not so much of an issue as actually getting this to work  - this is a private network. Secure working solutions accepted though :)

I've tried to use gproftpd, the GTK+ config tool, and got as far as creating a 'wwwftp' user with root directory /var/www, upload directory /var/www and all the privileges. Dreamweaver will happily connect to the FTP server and _get_ files, but refuses to put files, make directories, or delete files.

I've tried a few other things;
- Changed the user/group proftpd runs as to www-data:www-data
- chmod 777 /var/www (yes, I am a naughty boy). /var/www still belongs to root:root.
- disabling/enabling passive FTP in dreamweaver's options
- disabling/enabling ftp performance optimisation in dreamweaver's options

I of course suspect permissions problems, because everyone knows that at least 517% of linux-related issues involve permissions in some way, shape, or form. :D

The following is my /etc/proftpd.conf;

```

ServerType standalone
DefaultServer on
Umask 022
ServerName "pellinore"
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
User nobody
Group nogroup
DirFakeUser off nobody
DirFakeGroup off nobody
DefaultTransferMode binary
AllowForeignAddress on
AllowRetrieveRestart on
AllowStoreRestart on
DeleteAbortedStores off
TransferRate RETR 30
TransferRate STOR 40
TransferRate STOU 40
TransferRate APPE 40
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
  AllowUser wwwftp
  AllowUser anonymous
  DenyALL
</Limit>

<Anonymous /var/www/>
User wwwftp
Group wwwftp
AnonRequirePassword on
MaxClients 20 "The server is full, hosting %m users"
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
<Directory /var/www/>
AllowOverwrite on
<Limit UPLOAD_DIR_ALLOW LIST NLST  STOR STOU  APPE  RETR  RNFR RNTO  DELE  MKD XMKD  RMD XRMD  SITE_CHMOD  SITE_CHGRP  STAT  MDTM  PWD XPWD  SIZE  CWD XCWD  CDUP XCUP  SITE >
 AllowAll
</Limit>
<Limit UPLOAD_DIR_DENY>
 DenyAll
</Limit>
</Directory>
#gplockstats
</Anonymous>

<Anonymous /mnt/shared>
User anonymous
Group anonymous
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
<Directory /mnt/shared/*>
AllowOverwrite on
<Limit UPLOAD_DIR_ALLOW LIST NLST MDTM SIZE SITE STAT APPE RETR STOR STOU MKD XMKD CWD XCWD PWD XPWD CDUP XCUP>
 AllowAll
</Limit>
<Limit UPLOAD_DIR_DENY DELE SITE_CHMOD SITE_CHGRP RMD XRMD RNFR RNTO>
 DenyAll
</Limit>
</Directory>
</Anonymous>



```

---

### Post by chrisfay on 2006-12-24
Try changing the ownership of /var/www to whatever your ftp user is, not the user Proftp runs as. So if you log into your ftp server using username ftpuser, and he belongs to group ftp, do the following:

```
sudo chown -R ftpuser:ftp /var/www
```

Obviously replace ftpuser and ftp with your ftp user and group.

When you upload files from Dreamweaver they will have the user and group settings of your ftp user, not the user Proftpd created to run under. Make sure they match the permission settings. 

You could also use Samba to network the server and your develpment machine. Then use Dreamweaver to access the network share, bypassing the need for FTP completely. This was a much easier method for me.

---

### Post by Littleweseth on 2006-12-24
Thanks chrisfay, worked perfectly. I'm unsure if Bad Things are going to happen when apache tries to read things, but i'll let you know :)

---

### Post by chrisfay on 2006-12-24
NP...:D 

> I'm unsure if Bad Things are going to happen when apache tries to read things

You won't have any issues....

---

