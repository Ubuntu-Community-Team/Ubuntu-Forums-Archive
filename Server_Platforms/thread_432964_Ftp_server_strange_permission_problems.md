---
title: "Ftp server strange permission problems"
date: 2007-05-04
forum: Server Platforms
---

### Post by 5thgendriver on 2007-05-04
Ok so this is my second go at setting up a ubuntu ftp server and what i have is one user right now (just me) for testing and i want 3 drives fully accessible 2 fat32 and 1 ext3 -- so i setup an empty folder with all permissions and everything seems to work then i mount these three drivers in there one is called video one is called audio -the 2 fat drives -- and the ext3 drive is called software now i chown this directory and all three mountpoints to root - then i chmod all three directories exactly the same as one another with all permissions. The result is i have complete access to video which is perfect - I cant even open the audio folder permission is always denied - and software i can only brows to certain areas and only download a few things im very confused by all of this - any help would be great

---

### Post by nomb on 2007-05-04
which ftp server r u running?

---

### Post by 5thgendriver on 2007-05-04
proftpd

heres my proftpd.conf

ServerType standalone
DefaultServer on
Umask 022
ServerName "192.168.1.8"
ServerIdent on "PappasFTP"
ServerAdmin [email]nicholasdpappas@gmail.com[/email]
IdentLookups off
UseReverseDNS off
Port 21
PassivePorts 49151 65534
#MasqueradeAddress None
TimesGMT off
MaxInstances 30
MaxLoginAttempts 20
TimeoutLogin 300
TimeoutNoTransfer 120
TimeoutIdle 120
User ftpuser
Group root
DirFakeUser off ftpuser
DirFakeGroup off root
DefaultTransferMode binary
AllowForeignAddress on
AllowRetrieveRestart on
AllowStoreRestart on
DeleteAbortedStores off
TransferRate RETR 1000
TransferRate STOR 1000
TransferRate STOU 1000
TransferRate APPE 1000
SystemLog /var/log/secure
RequireValidShell off
#gp_random_username_length 6
#gp_random_password_length 6
#gp_randomize_case lower
#gp_useradd_homedir_path /var/ftp
#gp_useradd_upload_path /upload
#gp_html_path /var/www/ftp.htm
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
  AllowUser deepspace
  DenyALL
</Limit>

<Anonymous /media/SOFTWARE/>
User deepspace
Group root
AnonRequirePassword off
MaxClients 49 "The server is full, hosting %m users"
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
<Directory /media/SOFTWARE/Audio>
AllowOverwrite on
<Limit LIST NLST  STOR STOU  APPE  RETR  RNFR RNTO  DELE  MKD XMKD SITE_MKDIR  RMD XRMD SITE_RMDIR  SITE  SITE_CHMOD  SITE_CHGRP  MTDM  PWD XPWD  SIZE  STAT  CWD XCWD  CDUP XCUP >
 AllowAll
</Limit>
<Limit NOTHING >
 DenyAll
</Limit>
</Directory>
<Directory /media/SOFTWARE/Software>
AllowOverwrite on
<Limit LIST NLST  STOR STOU  APPE  RETR  RNFR RNTO  DELE  MKD XMKD SITE_MKDIR  RMD XRMD SITE_RMDIR  SITE  SITE_CHMOD  SITE_CHGRP  MTDM  PWD XPWD  SIZE  STAT  CWD XCWD  CDUP XCUP >
 AllowAll
</Limit>
<Limit NOTHING >
 DenyAll
</Limit>
</Directory>
<Directory /media/SOFTWARE/Video>
AllowOverwrite on
<Limit LIST NLST  STOR STOU  APPE  RETR  RNFR RNTO  DELE  MKD XMKD SITE_MKDIR  RMD XRMD SITE_RMDIR  SITE  SITE_CHMOD  SITE_CHGRP  MTDM  PWD XPWD  SIZE  STAT  CWD XCWD  CDUP XCUP >
 AllowAll
</Limit>
<Limit NOTHING >
 DenyAll
</Limit>
</Directory>
</Anonymous>

---

### Post by nomb on 2007-05-04
I had a similar problem.  I ended up installing the gui for it and setting up permissions that way.  After that it worked great.  Do you have the gui program installed for it?

---

### Post by 5thgendriver on 2007-05-04
yeah gproftpd - i have it installed but no such luck - i have tried alot of different methods - are there other ftp servers for ubuntu that work well - really i would like one with the ability to print activity to screen in a terminal - like the windows based gene6 i think does that

---

### Post by nomb on 2007-05-04
There is also vsftpd which you can get with the standard apt-get command.  Maybe you'll have better luck with that.  Altho I'm not sure that this is an ftp error persay.  Have you tried connecting in another way to test the permissions?

---

### Post by 5thgendriver on 2007-05-04
- what other way should i try  - i have tried from multiple operating system types with different types of client software and also from the private ip as well as the public after configuring port forwarding of course -

---

### Post by nomb on 2007-05-04
ssh in as the user you are having trouble with and see what you are able to do.  If you still get permission denied errors even with ssh you know it isn't a ftp problem.  (This is just what I would do, it might not be the best option.)

---

### Post by 5thgendriver on 2007-05-04
nick@systemadmin:~$ ssh -p 21 deepspace@192.168.1.8
ssh_exchange_identification: Connection closed by remote host


this all im getting - is my syntax correct

---

### Post by nomb on 2007-05-04
ssh by default is on port 22.

---

### Post by 5thgendriver on 2007-05-04
nick@systemadmin:~$ ssh deepspace@192.168.1.8
ssh: connect to host 192.168.1.8 port 22: Connection refused

---

### Post by nomb on 2007-05-04
We might as well be iming... :D

Do me a favor, look in /etc/ssh/.
Do you have sshd_conf
or
Do you just have ssh_conf?

---

### Post by 5thgendriver on 2007-05-04
I know huh - but thanks alot for the help - 

nick@systemadmin:~$ ls /etc/ssh
moduli  ssh_config

---

### Post by 5thgendriver on 2007-05-04
to be honest i thing your right - im pretty sure its a permissions issue rather than an ftp issue

---

### Post by nomb on 2007-05-04
Ok if that is on the computer you are trying to get to and not the computer you are trying from:

That means you only have the ssh client installed, not the server.

basically do a 'sudo apt-get install openssh-server'
open port 22 on your firewall
then from the client you should be able to connect to the server w/o any problems and test the permissions.

---

### Post by 5thgendriver on 2007-05-04
yeah open ssh works fine and i copied a file from audio which i wouldnt normally even be able to browse to via ftp

---

### Post by 5thgendriver on 2007-05-04
i guess i could try that other server - does it have a gui too?

---

### Post by nomb on 2007-05-04
well once the ssh server is installed you can use the 'connect to server' function from the bar on your client and select ssh.  Then it will look like your just browsing files on your computer when your actually on your server.

---

