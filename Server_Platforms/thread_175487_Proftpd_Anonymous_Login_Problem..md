---
title: "Proftpd Anonymous Login Problem."
date: 2006-05-13
forum: Server Platforms
---

### Post by jfx on 2006-05-13
When i try to login on my ftp server i get this error:

> 
ftp> open 127.0.0.1
Connected to 127.0.0.1.
220 Sons of Liberty
Name (127.0.0.1:foxx): solhacker
331 Password required for solhacker.
Password:
530-Unable to set anonymous privileges.
530 Login incorrect.
Login failed.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp>


the user solhacker is member of the group ftpgroup and its home is in "/home/ftp" that is also the home directory of a test ftp account.

> 
foxx@solhacker:~$ ls -l /home/
total 68
drwxr-xr-x  6 foxx ftpgroup  4096 2006-05-13 16:16 ftp
foxx@solhacker:~$ ls -l /home/ftp
total 16
drwxrwxr-x 6 foxx ftpgroup 4096 2006-05-13 12:18 download
drwxrwxr-x 3 foxx ftpgroup 4096 2006-05-13 12:18 homes
drwxrwxrwx 2 foxx ftpgroup 4096 2006-05-13 11:22 upload
foxx@solhacker:~$


and my config looks like this:

> 
ServerType standalone
DefaultServer on
Umask 022
ServerName "Solhacker FTP Deamon"
ServerIdent on "Sons of Liberty"
ServerAdmin [email]juny@solhack.com[/email]
IdentLookups off
UseReverseDNS off
Port 21
PassivePorts 49152 65534
#MasqueradeAddress None
TimesGMT off
MaxInstances 10
MaxLoginAttempts 4
TimeoutLogin 300
TimeoutNoTransfer 120
TimeoutIdle 120
User foxx
Group ftpgroup
DirFakeUser off foxx
DirFakeGroup off ftpgroup
DefaultTransferMode binary
RequireValidShell off
AllowForeignAddress on
AllowRetrieveRestart off
AllowStoreRestart off
DeleteAbortedStores on
TransferRate RETR 80
TransferRate STOR 80
TransferRate STOU 80
TransferRate APPE 80
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
  AllowUser solhacker
  AllowUser test
  AllowUser foxx
  DenyALL
</Limit>

<limit READ>
  AllowUser solhacker
  AllowUser test
  AllowUser foxx
  DenyALL
</limit> 

<Anonymous /home/ftp>
User solhacker
Group ftpgroup
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
<Directory /home/ftp/upload/*>
AllowOverwrite on
<Limit UPLOAD_DIR_ALLOW LIST NLST >
 AllowAll
</Limit>
<Limit UPLOAD_DIR_DENY STOR STOU  APPE  RETR  RNFR RNTO  DELE  MKD XMKD  RMD XRMD  SITE_CHMOD  SITE_CHGRP  STAT  MDTM  PWD XPWD  SIZE  CWD XCWD  CDUP XCUP  SITE >
 DenyAll
</Limit>
</Directory>
</Anonymous>

<Anonymous /home/ftp/>
User test
Group ftpgroup
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
<Directory /home/ftp/upload/*>
AllowOverwrite on
<Limit UPLOAD_DIR_ALLOW LIST NLST  STOR STOU  APPE  RETR  MKD XMKD  STAT  MDTM  PWD XPWD  SIZE  CWD XCWD  CDUP XCUP  SITE >
 AllowAll
</Limit>
<Limit UPLOAD_DIR_DENY RNFR RNTO  DELE  RMD XRMD  SITE_CHMOD  SITE_CHGRP >
 DenyAll
</Limit>
</Directory>
</Anonymous>


I really don't know what the problem is here, i can login with the user foxx, but with test and solhacker i get the 530 error.

Can anyone tell me what i'm doin wrong here?
tell me if you need more info

Greets Juny

---

### Post by jfx on 2006-05-14
is it a hard one or what? :confused: :D

---

### Post by frodon on 2006-05-15
Hi jfx,

I think the problem should be on how you use **<Anonymous>** tags, because from what i understood (i can be wrong) you use <Anonymous> tags when you want to share a directory without user access.
So when you specify a user within **<Anonymous>** tags that means that anonimous logins will be linked to this user for login and i'm not sure that you are able to login using this username.

So what do you wish ? anonimous or user access ?
If you want to set a ftp server with user access i would set it like that.

---

### Post by jfx on 2006-05-15
> So what do you wish ? anonimous or user access ?

ooh boy yeah, thats a REALY good question! i don't know why this didnt cross my mind. I was planning to make it for user access but i thought that it also can be done this way, and thats why i did it with the <anonymous> tags. I'm gonna think about how i want to set it and remove the tags and change it to the way i used to do it. 

The strange thing is that i managed to login as "solhacker" but that was just after i fnisched installing so that would explain everything.

Thnx alot!

Greets Juny

---

### Post by kolaloka on 2007-05-02
I have also had this problem, however, it was only the problem of rights inside the system. Careless what unix or linux you are using, you have to set the permissions inside your system, not only in the proftpd.conf,  so that people can login and operate with ftp. That means:

# we will assume that /home/ftp is the folder we want to share, you must create an ftp user and ftp group first, #  unless you already have it

# lets dedicate the folder and all its contents to the ftp owner and ftp group
sudo chown -R ftp:ftp /home/ftp

# now lets adjust the permitions so that the owner and group can read,write and execute, others only read
sudo chmod -R 775 /home/ftp


now, all the members of the group will be able to access the ftp with writing mode
and all the visitors will be able to read and download things
of course, you can make the system more sophisticated, but for the beginning....

# and if you really want more you can try e.g: 
# for the upload we could have more courageously - but I do not advice this, it allows everyone 
# to delete everything in upload
sudo chmod -R 777 /home/ftp/upload/

good luck

Kolaloka 
(and if you get tired of the overautomagicUbuntu, try the NetBSD - the touch of a real unix)

---

