---
title: "vsftpd SSL login problem"
date: 2008-07-27
forum: Server Platforms
---

### Post by andrewms on 2008-07-27
I am having troubles getting vsftpd to run using ssl. Here is vsftpd.conf:


listen=YES
anonymous_enable=NO
local_enable=YES
write_enable=YES
dirmessage_enable=YES
xferlog_enable=YES
connect_from_port_20=YES
ftpd_banner=Welcome to blah FTP service.
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
#
ssl_enable=YES
force_local_logins_ssl=YES
force_local_data_ssl=YES
ssl_tlsv1=YES
ssl_sslv2=YES
ssl_sslv3=YES
check_shell=NO

Using these settings I get the following message when attempting to connect:

Connected to 192.168.1.103.
220 Welcome to blah FTP service.
Name (192.168.1.103:user1): user1
530 Non-anonymous sessions must use encryption.
Login failed.
ftp>

If I comment out the last section of the vsftpd.conf (the last 7 lines with the ssl settings) I can login just fine. Can anyone show me what I'm doing wrong?

---

### Post by RealPSL on 2008-07-27
Your ftp server is doing what you told it to do. If you try to login as a local use you must use and ssl enabled client as indicated by 

```
force_local_logins_ssl=YES
```

If that was NO what you sent would most likely work. Otherwise you need to use an ftp client that is understands the ftps protocol.

---

### Post by andrewms on 2008-07-27
Yes, that does work. What are some clients that do use the ftps protocol? I am trying to access it from Windows, and I have mostly been trying FileZilla (which does not work using the suggestion you made; using the ftp commands from the terminal in either Vista or Ubuntu does).

I am also curious how I can make this accessible through Firefox or IE. I know that the domain is working correctly, because FileZilla can find it (I am using an account with dyndns and using ddclient to update my IP). I have been unable to get anything through browsers, though. Any suggestions? And thanks for your help!

---

### Post by dietkinnie on 2008-07-28
Not sure if this can be of some use.. There is an addon for firefox called FireFTp..

---

