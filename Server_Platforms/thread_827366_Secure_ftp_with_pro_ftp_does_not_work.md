---
title: "Secure ftp with pro ftp does not work"
date: 2008-06-12
forum: Server Platforms
---

### Post by Walub on 2008-06-12
I have recently setup ubuntu 8.10 server with proftp and I can log in without encryption fine but when I try to connect with secure ftp I get this in filezilla.
"Connected with *.*.*.*, negotiating SSL connection...
Response:	220 ProFTPD 1.3.1 Server ready.
Command:	AUTH TLS
Response:	234 AUTH TLS successful
Error:	Can't establish SSL connection
Error:	Disconnected from server
Error:	Unable to connect!
"

In my tls.log file I get this error

"Jun 11 18:19:22 mod_tls/2.1.2[5821]: TLS/TLS-C negotiation failed on control channel
Jun 11 18:19:40 mod_tls/2.1.2[5822]: error loading TLSRSACertificateFile '/etc/ftpcert/server.crt':
  (1) error:0906D06C:PEM routines:PEM_read_bio:no start line
  (2) error:140AD009:SSL routines:SSL_CTX_use_certificate_file:PEM lib"

I am guessing that I created the cert wrong but I don't really know.  I was following this tutorial. [http://ubuntuforums.org/showthread.php?t=79588&highlight=ftp+server+howto](http://ubuntuforums.org/showthread.php?t=79588&highlight=ftp+server+howto) 


I can post my proftpd.conf if needed.  any help would be apreciated.

---

### Post by nix4me on 2008-06-12
Create your cert file like this:

First:  Make a dir for it:
mkdir /etc/proftpd/ssl

Next:  Make a cert file:
openssl req -new -x509 -days 365 -nodes -out /etc/proftpd/ssl/proftpd.cert.pem -keyout /etc/proftpd/ssl/proftpd.key.pem

Next:  Change proftpd config file options for TLS to this:
<IfModule mod_tls.c>
TLSEngine                  on
TLSLog                     /var/log/proftpd/tls.log
TLSProtocol                SSLv23
TLSOptions                 NoCertRequest
TLSRSACertificateFile      /etc/proftpd/ssl/proftpd.cert.pem
TLSRSACertificateKeyFile   /etc/proftpd/ssl/proftpd.key.pem
TLSVerifyClient            off
TLSRequired                off
</IfModule>

This will allow both encrypted and non-encrypted connections.  If you want only encrypted, then change TLSRequired to on.

nix4me

---

### Post by Walub on 2008-06-13
> **nix4me said:**
> Create your cert file like this:

First:  Make a dir for it:
mkdir /etc/proftpd/ssl

Next:  Make a cert file:
openssl req -new -x509 -days 365 -nodes -out /etc/proftpd/ssl/proftpd.cert.pem -keyout /etc/proftpd/ssl/proftpd.key.pem

Next:  Change proftpd config file options for TLS to this:
<IfModule mod_tls.c>
TLSEngine                  on
TLSLog                     /var/log/proftpd/tls.log
TLSProtocol                SSLv23
TLSOptions                 NoCertRequest
TLSRSACertificateFile      /etc/proftpd/ssl/proftpd.cert.pem
TLSRSACertificateKeyFile   /etc/proftpd/ssl/proftpd.key.pem
TLSVerifyClient            off
TLSRequired                off
</IfModule>

This will allow both encrypted and non-encrypted connections.  If you want only encrypted, then change TLSRequired to on.

nix4me

That worked perfectly thanks for your help

---

### Post by nix4me on 2008-06-13
No problem, glad i could help.

---

### Post by technotika on 2008-08-04
hi guys having a night mare getting TLS with proftp to work, done all the guides and also this new bit that has worked for some one  - please tell me whats going on  - respect in advance

_error on client test is _
Status:	Connecting to 192.168.2.5:666...
Status:	Connection established, waiting for welcome message...
Response:	220 My FTPD
Command:	AUTH TLS
Response:	234 AUTH TLS successful
Status:	Initializing TLS...
Command:	USER potts
Error:	Could not connect to server

[U]
confile file[/U]

Include /etc/proftpd/modules.conf
ServerType standalone
DefaultServer on
Umask 022
ServerName "192.168.2.5"
ServerIdent on "My FTPD"
ServerAdmin [email]Admin@this.domain.topd[/email]omain
IdentLookups off
UseReverseDNS off
Port 666
PassivePorts 2000 2002
MasqueradeAddress 81.96.129.110
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
TLSEngine on
TLSRequired on
TLSVerifyClient on
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
  AllowUser potts
  DenyALL
</Limit>

<Anonymous /media/DATA/JERRY/Downloads/ISO's>
User potts
Group potts
AnonRequirePassword on
MaxClients 5 "The server is full, hosting %m users"
DisplayLogin welcome.msg
<Limit LOGIN>
Allow from all
Deny from all
</Limit>
<Limit LIST NLST  STOR STOU  APPE  RETR  MKD XMKD SITE_MKDIR  PWD XPWD  SIZE  STAT  CWD XCWD  CDUP XCUP >
 AllowAll
</Limit>
<Limit RNFR RNTO  DELE  RMD XRMD SITE_RMDIR  SITE  SITE_CHMOD  SITE_CHGRP  MTDM >
 DenyAll
</Limit>
</Anonymous>
<IfModule mod_tls.c>
TLSEngine on
TLSLog /var/log/proftpd/tls.log
TLSProtocol SSLv23
TLSOptions NoCertRequest
TLSRSACertificateFile /etc/proftpd/ssl/proftpd.cert.pem
TLSRSACertificateKeyFile /etc/proftpd/ssl/proftpd.key.pem
TLSVerifyClient on
TLSRequired on
</IfModule>

---

### Post by technotika on 2008-08-04
no worrys dudes sorted it  - duplicate tls entries  - hitting first lot and they were wrong 

the tls fix described above are the way forward though!!!!!

---

### Post by Jisstus on 2008-09-13
I tried to get my proftp to work with encryption following this guide but it doesn´t work. I have specified that I only want encrypted connections but I can still login without Auth SSL in my client.

This is my proftpd.conf

ServerName                      "xxxxxxxx"
ServerType                      standalone
DefaultServer                   on
Port                            21
PassivePorts                    60000 60100
MasqueradeAddress               xxxxxxxx.mine.nu
DefaultRoot                     /var/tmp
AllowOverwrite                  on
UseFtpUsers                     on
User                            proftpd
Group                           nogroup
Umask                           022  022

UseReverseDNS                   off
IdentLookups                    off

MaxInstances                    4
MaxLoginAttempts                2
TimeoutIdle                     600
TimeoutNoTransfer               0
TimeoutStalled                  0

<Global>
  RootLogin                     off
  RequireValidShell             off
  AuthUserFile                  /etc/passwd
  AllowStoreRestart             on
</Global>

<Limit SITE_CHMOD>
  DenyAll
</Limit>

<IfModule mod_tls.c>
TLSEngine on
TLSLog /var/log/proftpd/tls.log
TLSProtocol SSLv23
TLSOptions NoCertRequest
TLSRSACertificateFile /etc/proftpd/ssl/proftpd.cert.pem
TLSRSACertificateKeyFile /etc/proftpd/ssl/proftpd.key.pem
TLSVerifyClient off
TLSRequired on
</IfModule>

ExtendedLog                     /var/log/proftpd/ftp.log
TransferLog                     /var/log/proftpd/xferlog.log
SystemLog                       /var/log/proftpd/syslog.log

---

### Post by cariboo on 2008-09-13
Both of you would get better responses if you started your own thread instead of hijacking this one.

Jim

---

### Post by Vegan on 2008-09-13
Don't wast your time, I did with vsftpd and whathave you.

To get WinSCP to use SSL I needed to install sftp

sudo apt-get install sftp

and poof I was in.

---

### Post by diazjavier on 2011-01-08
> **nix4me said:**
> Create your cert file like this:

First:  Make a dir for it:
mkdir /etc/proftpd/ssl

Next:  Make a cert file:
openssl req -new -x509 -days 365 -nodes -out /etc/proftpd/ssl/proftpd.cert.pem -keyout /etc/proftpd/ssl/proftpd.key.pem

Next:  Change proftpd config file options for TLS to this:
<IfModule mod_tls.c>
TLSEngine                  on
TLSLog                     /var/log/proftpd/tls.log
TLSProtocol                SSLv23
TLSOptions                 NoCertRequest
TLSRSACertificateFile      /etc/proftpd/ssl/proftpd.cert.pem
TLSRSACertificateKeyFile   /etc/proftpd/ssl/proftpd.key.pem
TLSVerifyClient            off
TLSRequired                off
</IfModule>

This will allow both encrypted and non-encrypted connections.  If you want only encrypted, then change TLSRequired to on.

nix4me


@nix4me: thank you, your solution works for me

---

