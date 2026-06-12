---
title: "vsftpd 530 login error"
date: 2018-06-19
forum: Server Platforms
---

### Post by Andreyshel on 2018-06-19
Hello. I have a problem configuring vsftpd. Computer is not mine, but i have legitimate root access to it and have  asked for permission to publish this forum thread.

So. 

[B]vsftpd config file(comments omitted) 
[/B]```
 
listen=YES
listen_ipv6=NO
anonymous_enable=NO
userlist_deny=NO
userlist_enable=YES
userlist_file=/etc/vsftpd/list.conf
local_enable=YES
write_enable=YES
dirmessage_enable=YES
use_localtime=YES
xferlog_enable=YES
log_ftp_protocol=YES
connect_from_port_20=YES
nopriv_user=moon
ftpd_banner=Welcome to FTP service.
secure_chroot_dir=/var/run/vsftpd/empty
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
ssl_enable=NO

```

moon is a local user with possibility to login to the system. 

[B]connection log

[/B]

```
Tue Jun 19 12:11:36 2018 [pid 12331] CONNECT: Client "127.0.0.1"Tue Jun 19 12:11:36 2018 [pid 12331] FTP response: Client "127.0.0.1", "220 Welcome to FTP service."
Tue Jun 19 12:11:40 2018 [pid 12331] FTP command: Client "127.0.0.1", "USER moon"
Tue Jun 19 12:11:40 2018 [pid 12331] [moon] FTP response: Client "127.0.0.1", "331 Please specify the password."
Tue Jun 19 12:11:45 2018 [pid 12331] [moon] FTP command: Client "127.0.0.1", "PASS <password>"
Tue Jun 19 12:11:47 2018 [pid 12330] [moon] FAIL LOGIN: Client "127.0.0.1"
Tue Jun 19 12:11:48 2018 [pid 12331] [moon] FTP response: Client "127.0.0.1", "530 Login incorrect."
Tue Jun 19 12:11:48 2018 [pid 12331] FTP command: Client "127.0.0.1", "SYST"
Tue Jun 19 12:11:48 2018 [pid 12331] FTP response: Client "127.0.0.1", "530 Please login with USER and PASS."
Tue Jun 19 12:11:55 2018 [pid 12331] FTP command: Client "127.0.0.1", "QUIT"
Tue Jun 19 12:11:55 2018 [pid 12331] FTP response: Client "127.0.0.1", "221 Goodbye."
.. many identical tries  ommited

```

chmod data for home directory seems to be correct
```

drwxr-xr-x 3 moon moon 4096 &#1095;&#1077;&#1088; 19 12:02 share
```

So my question what is wrong with this configuration ?
Thank you for ideas.

---

### Post by LHammonds on 2018-06-19
EDIT: Nevermind....you did it.

---

