---
title: "vsftpd SSL problems"
date: 2010-09-04
forum: Server Platforms
---

### Post by cocose on 2010-09-04
Hi there!
I am currently having some trouble setting up FTPS with vsftpd on Ubuntu 10.04.
(Unfortunately the project specification requires me to use FTPS and not SFTP, which of course would be much simpler.)

This is my vsftpd.conf:

```

# General Settings
listen=YES
listen_ipv6=NO
connect_from_port_20=NO
listen_port=21
pasv_enable=YES
pasv_min_port=2000
pasv_max_port=2999
local_umask=022
chroot_local_user=YES
secure_chroot_dir=/var/run/vsftpd
ftpd_banner=Welcome to my FTP server!
use_localtime=YES

# Virtual User Login
local_enable=YES
guest_enable=YES
nopriv_user=vsftpd
pam_service_name=vsftpd
guest_username=vsftpd
local_root=/home/vsftpd/$USER
user_sub_token=$USER
virtual_use_local_privs=YES
user_config_dir=/etc/vsftpd_user_conf

# SSL
ssl_enable=YES
implicit_ssl=NO
rsa_cert_file=/etc/vsftpd/server.pem
force_local_data_ssl=NO
force_local_logins_ssl=YES
ssl_tlsv1=YES
ssl_sslv2=NO
# SSLv3 is required by the client
ssl_sslv3=YES
require_ssl_reuse=NO

# Logs
debug_ssl=YES
xferlog_enable=YES
log_ftp_protocol=YES

# Restrictions
write_enable=YES
dirlist_enable=YES
download_enable=YES
dirmessage_enable=YES

# Anonymous user
anonymous_enable=NO
allow_anon_ssl=NO
anon_mkdir_write_enable=NO
anon_other_write_enable=NO
anon_upload_enable=NO

```

Now, when I connect via ftp-ssl (or any other SSL-enabled client) the vsftpd.log reports the following SSL errors:

```

Sat Sep  4 11:51:31 2010 [pid 2] CONNECT: Client "xxx.xxx.xxx.xxx"
Sat Sep  4 11:51:31 2010 [pid 2] FTP response: Client "xxx.xxx.xxx.xxx", "220 Welcome to my FTP server!"
Sat Sep  4 11:51:34 2010 [pid 2] FTP command: Client "xxx.xxx.xxx.xxx", "AUTH SSL"
Sat Sep  4 11:51:34 2010 [pid 2] FTP response: Client "xxx.xxx.xxx.xxx", "234 Proceed with negotiation."
Sat Sep  4 11:51:34 2010 [pid 2] DEBUG: Client "xxx.xxx.xxx.xxx", "SSL version: TLSv1/SSLv3, SSL cipher: DES-CBC3-SHA, not reused, no cert"
Sat Sep  4 11:51:34 2010 [pid 2] FTP command: Client "xxx.xxx.xxx.xxx", "USER demouser"
Sat Sep  4 11:51:34 2010 [pid 2] [demouser] FTP response: Client "xxx.xxx.xxx.xxx", "331 Please specify the password."
Sat Sep  4 11:51:36 2010 [pid 2] [demouser] FTP command: Client "xxx.xxx.xxx.xxx", "PASS <password>"
Sat Sep  4 11:51:36 2010 [pid 1] [demouser] OK LOGIN: Client "xxx.xxx.xxx.xxx"
Sat Sep  4 11:51:36 2010 [pid 3] [demouser] FTP response: Client "xxx.xxx.xxx.xxx", "230 Login successful."
Sat Sep  4 11:51:36 2010 [pid 3] [demouser] FTP command: Client "xxx.xxx.xxx.xxx", "SYST"
Sat Sep  4 11:51:36 2010 [pid 3] [demouser] FTP response: Client "xxx.xxx.xxx.xxx", "215 UNIX Type: L8"
Sat Sep  4 11:51:38 2010 [pid 3] [demouser] FTP command: Client "xxx.xxx.xxx.xxx", "PORT 87,237,120,58,225,128"
Sat Sep  4 11:51:38 2010 [pid 3] [demouser] FTP response: Client "xxx.xxx.xxx.xxx", "200 PORT command successful. Consider using PASV."
Sat Sep  4 11:51:38 2010 [pid 3] [demouser] FTP command: Client "xxx.xxx.xxx.xxx", "LIST"
Sat Sep  4 11:51:38 2010 [pid 3] [demouser] FTP response: Client "xxx.xxx.xxx.xxx", "150 Here comes the directory listing."
Sat Sep  4 11:51:38 2010 [pid 2] [demouser] DEBUG: Client "xxx.xxx.xxx.xxx", "SSL version: TLSv1/SSLv3, SSL cipher: DES-CBC3-SHA, not reused, no cert"
Sat Sep  4 11:51:38 2010 [pid 2] [demouser] DEBUG: Client "xxx.xxx.xxx.xxx", "SSL shutdown state is: NONE"
Sat Sep  4 11:51:38 2010 [pid 2] [demouser] DEBUG: Client "xxx.xxx.xxx.xxx", "SSL shutdown state is: SSL_SENT_SHUTDOWN"
Sat Sep  4 11:51:38 2010 [pid 2] [demouser] DEBUG: Client "xxx.xxx.xxx.xxx", "SSL shutdown state is: SSL_SENT_SHUTDOWN"
Sat Sep  4 11:51:38 2010 [pid 2] [demouser] DEBUG: Client "xxx.xxx.xxx.xxx", "SSL shutdown state is: SSL_SENT_SHUTDOWN"
Sat Sep  4 11:51:38 2010 [pid 2] [demouser] DEBUG: Client "xxx.xxx.xxx.xxx", "SSL ret: 0, SSL error: error:00000000:lib(0):func(0):reason(0), errno: 0"
Sat Sep  4 11:51:38 2010 [pid 3] [demouser] FTP response: Client "xxx.xxx.xxx.xxx", "226 Directory send OK."
Sat Sep  4 11:51:39 2010 [pid 3] [demouser] FTP command: Client "xxx.xxx.xxx.xxx", "QUIT"
Sat Sep  4 11:51:39 2010 [pid 3] [demouser] FTP response: Client "xxx.xxx.xxx.xxx", "221 Goodbye."

```

What especially irritates me are the following lines:

```
SSL shutdown state is: SSL_SENT_SHUTDOWN
```

and 

```
SSL ret: 0, SSL error: error:00000000:lib(0):func(0):reason(0), errno: 0
```

I have spend quite some time consulting Google to find a solution for this problem, but without success. So I performed the following test to resolve the issue:

[LIST=1]
[*]Disableing ssl_sslv2 and ssl_sslv3
[*]Changing the SSL certificate
[*]Changing the PAM authentication mechanism (you never know...)
[*]Manually compiling vsftpd (version 2.3.1) in case it's a bug in vsftpd (my version is 2.2.2)
[/LIST]

The certificate was created with the following command:

```
openssl req -x509 -nodes -days 730 -newkey rsa:1024 -keyout /etc/vsftpd/vsftpd.pem -out /etc/vsftpd/vsftpd.pem
```

My /etc/pam.d/vsftpd looks like this (enabling virtual user accounts via MySQL):

```

auth required pam_mysql.so user=vsftpd passwd=xxxxxx
host=127.0.0.1 db=vsftpd table=accounts usercolumn=username passwdcolumn=password crypt=3
account required pam_mysql.so user=vsftpd passwd=xxxxxx
host=127.0.0.1 db=vsftpd table=accounts usercolumn=username passwdcolumn=password crypt=3

```

Has anybody else encountered these problems before?

All the best and thanks for your help!


Cocose

---

