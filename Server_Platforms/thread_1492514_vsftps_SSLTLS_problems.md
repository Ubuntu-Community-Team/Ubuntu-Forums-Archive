---
title: "vsftps SSL/TLS problems"
date: 2010-05-24
forum: Server Platforms
---

### Post by deekthesqueak on 2010-05-24
I was able to get vsftps (2.0.7) working over an unsecured connection no problem at all.  When I enabled SSL with the following configuration I am not able to connect with SmartFTP, Filezillz, FireFTP, etc.  I am however able to connect from the server itself using ftp-ssl (I am still using the external FQDN to connect)

```
listen=YES
anonymous_enable=NO
local_enable=YES
write_enable=YES
local_umask=022
dirmessage_enable=YES
xferlog_enable=YES
chroot_local_user=YES
chroot_list_enable=NO
secure_chroot_dir=/var/run/vsftpd
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
debug_ssl=YES
ssl_enable=YES
ssl_tlsv1=YES
ssl_ciphers=DES-CBC3-SHA
force_local_data_ssl=NO
force_local_logins_ssl=YES
allow_anon_ssl=NO
```

When connecting using Filezilla I am able to connect and the FTP programs will issue the AUTH TLS command. I get a status saying Initializing TLS... and it will time out. Other programs have the same response. This error appears in the /var/log/vsftpd.log for all of the different programs.
```
Mon May 24 17:22:43 2010 [pid 21799] CONNECT: Client "67.XX.XX.XX"
Mon May 24 17:22:59 2010 [pid 21797] DEBUG: Client "67.XX.XX.XX", "SSL_accept failed: error:00000000:lib(0):func(0):reason(0)"
```

When I connect using ftp-ssl on the server itself this is what is logged.
```
Mon May 24 17:37:08 2010 [pid 21836] CONNECT: Client "74.XX.XX.XX"
Mon May 24 17:37:09 2010 [pid 21836] DEBUG: Client "74.XX.XX.XX", "SSL version: TLSv1/SSLv3, SSL cipher: DES-CBC3-SHA, not reused, no cert"
Mon May 24 17:37:12 2010 [pid 21835] [deekthesqueak] OK LOGIN: Client "74.XX.XX.XX"
```
 and this is what is displayed locally.
```
deekthesqueak@<server>:~$ ftp-ssl <server>.com
Connected to <server>.com.
220 (vsFTPd 2.0.7)
Name (<server>.com:deekthesqueak): deekthesqueak
234 Proceed with negotiation.
[SSL Cipher DES-CBC3-SHA]
331 Please specify the password.
Password:
230 Login successful.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> exit
```

Just for information here is the permissions on the cert and key files.
```
deekthesqueak@<server>:~$ sudo ls -al /etc/ssl/certs/ssl-cert-snakeoil.pem
-rw-r--r-- 1 root root 615 May 14  2009 /etc/ssl/certs/ssl-cert-snakeoil.pem
```
```
deekthesqueak@<server>:~$ sudo ls -al /etc/ssl/private/ssl-cert-snakeoil.key
-rw-r----- 1 root ssl-cert 887 May 14  2009 /etc/ssl/private/ssl-cert-snakeoil.key
```

Does anyone have any suggestions because I am at a loss of what to try next?

---

### Post by Bachstelze on 2010-05-24
You have a lot of useless stuff in your conf. Here's mine (only the SSL-related part):

```
ssl_enable=YES
allow_anon_ssl=NO
require_ssl_reuse=NO
force_local_data_ssl=YES
force_local_logins_ssl=YES

ssl_tlsv1=YES
ssl_sslv2=YES
ssl_sslv3=YES

rsa_cert_file=/etc/ssl/certs/vsftpd.pem

```

---

### Post by deekthesqueak on 2010-05-25
Well regardless of the extra stuff the variable require_ssl_reuse=NO will make it so that the server doesn't even respond.

I had a friend trying to connect with the same credentials and he was partially successful.  Here is the log from his client (also Filezilla, same version)

```
Status:	Resolving address of <server>.com
Status:	Connecting to 74.XX.XX.XX.XX:21...
Status:	Connection established, waiting for welcome message...
Response:	220 (vsFTPd 2.0.7)
Command:	AUTH TLS
Response:	234 Proceed with negotiation.
Status:	Initializing TLS...
Status:	Verifying certificate...
Command:	USER deekthesqueak
Status:	TLS/SSL connection established.
Response:	331 Please specify the password.
Command:	PASS *******
Response:	230 Login successful.
Command:	SYST
Response:	215 UNIX Type: L8
Command:	FEAT
Response:	211-Features:
Response:	 AUTH SSL
Response:	 AUTH TLS
Response:	 EPRT
Response:	 EPSV
Response:	 MDTM
Response:	 PASV
Response:	 PBSZ
Response:	 PROT
Response:	 REST STREAM
Response:	 SIZE
Response:	 TVFS
Response:	 UTF8
Response:	211 End
Command:	OPTS UTF8 ON
Response:	200 Always in UTF8 mode.
Command:	PBSZ 0
Response:	200 PBSZ set to 0.
Command:	PROT P
Response:	200 PROT now Private.
Status:	Connected
Status:	Retrieving directory listing...
Command:	PWD
Response:	257 "/"
Command:	TYPE I
Response:	200 Switching to Binary mode.
Command:	PASV
Response:	227 Entering Passive Mode (74,XX,XX,XX,XX,XX)
Command:	LIST
Error:	Connection timed out
Error:	Failed to retrieve directory listing
```

And the log from vsftpd
```
Mon May 24 18:27:44 2010 [pid 22709] CONNECT: Client "24.XX.XX.XX"
Mon May 24 18:27:44 2010 [pid 22709] DEBUG: Client "24.XX.XX.XX", "SSL version: TLSv1/SSLv3, SSL cipher: DES-CBC3-SHA, not reused, no cert"
Mon May 24 18:27:50 2010 [pid 22708] [deekthesqueak] OK LOGIN: Client "24.XX.XX.XX"
```

So it seems to be coming from my network that is the problem.  Does anyone have any suggestions of what might cause a problem like this to occur?

---

