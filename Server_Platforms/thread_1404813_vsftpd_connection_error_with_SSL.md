---
title: "vsftpd connection error with SSL"
date: 2010-02-11
forum: Server Platforms
---

### Post by shahansudu on 2010-02-11
Hi,
   I installed vsftpd (for the first time) and followed couple of howtos. I can connect to the server as the anonymous user which does not require SSL. But when I actually use one of the user accounts it throws this error

530 Non-anonymous sessions must use encryption.
Login failed.


I saw couple of people solving this issue by using Filezilla, but this is not an option for me. Can anyone help me with this issue.

user config file:

```

write_enable=YES
anon_mkdir_write_enable=YES
anon_other_write_enable=YES
anon_upload_enable=YES
local_root=/home/ftpuser
chroot_local_user=YES
dirlist_enable=YES
download_enable=YES
guest_username=ftpuser

```

SSL paet in the main config:

```

pam_service_name=ftp
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
ssl_enable=YES
ssl_tlsv1=YES
ssl_sslv2=YES
ssl_sslv3=YES
allow_anon_ssl=YES
force_local_data_ssl=YES
force_local_logins_ssl=YES
guest_enable=YES
guest_username=ftp

```

basically I can connect as ftp not as user1

---

### Post by shahansudu on 2010-02-12
Have some new information. I ran vsftpdin debug mode and this is in the log

```

Fri Feb 12 11:23:48 2010 [pid 9380] FTP response: Client "70.110.23.254", "220 Welcome to blah FTP service."
Fri Feb 12 11:23:49 2010 [pid 9380] FTP command: Client "70.110.23.254", "FEAT"
Fri Feb 12 11:23:49 2010 [pid 9380] FTP response: Client "70.110.23.254", "211-Features:"
Fri Feb 12 11:23:49 2010 [pid 9380] FTP response: Client "70.110.23.254", " AUTH SSL??"
Fri Feb 12 11:23:49 2010 [pid 9380] FTP response: Client "70.110.23.254", " AUTH TLS??"
Fri Feb 12 11:23:49 2010 [pid 9380] FTP response: Client "70.110.23.254", " EPRT??"
Fri Feb 12 11:23:49 2010 [pid 9380] FTP response: Client "70.110.23.254", " EPSV??"
Fri Feb 12 11:23:49 2010 [pid 9380] FTP response: Client "70.110.23.254", " MDTM??"
Fri Feb 12 11:23:49 2010 [pid 9380] FTP response: Client "70.110.23.254", " PASV??"
Fri Feb 12 11:23:49 2010 [pid 9380] FTP response: Client "70.110.23.254", " PBSZ??"
Fri Feb 12 11:23:49 2010 [pid 9380] FTP response: Client "70.110.23.254", " PROT??"
Fri Feb 12 11:23:49 2010 [pid 9380] FTP response: Client "70.110.23.254", " REST STREAM??"
Fri Feb 12 11:23:49 2010 [pid 9380] FTP response: Client "70.110.23.254", " SIZE??"
Fri Feb 12 11:23:49 2010 [pid 9380] FTP response: Client "70.110.23.254", " TVFS??"
Fri Feb 12 11:23:49 2010 [pid 9380] FTP response: Client "70.110.23.254", " UTF8??"
Fri Feb 12 11:23:49 2010 [pid 9380] FTP response: Client "70.110.23.254", "211 End"
Fri Feb 12 11:23:49 2010 [pid 9380] FTP command: Client "70.110.23.254", "AUTH TLS"
Fri Feb 12 11:23:49 2010 [pid 9380] FTP response: Client "70.110.23.254", "234 Proceed with negotiation."
Fri Feb 12 11:23:49 2010 [pid 9380] DEBUG: Client "70.110.23.254", "SSL version: TLSv1/SSLv3, SSL cipher: DES-CBC3-SHA, not reused, no cert"
Fri Feb 12 11:23:49 2010 [pid 9380] FTP command: Client "70.110.23.254", "OPTS UTF8 ON"
Fri Feb 12 11:23:49 2010 [pid 9380] FTP response: Client "70.110.23.254", "200 Always in UTF8 mode."
Fri Feb 12 11:23:49 2010 [pid 9380] FTP command: Client "70.110.23.254", "USER user1"
Fri Feb 12 11:23:49 2010 [pid 9380] [user1] FTP response: Client "70.110.23.254", "331 Please specify the password."
Fri Feb 12 11:23:49 2010 [pid 9380] [user1] FTP command: Client "70.110.23.254", "PASS <password>"
Fri Feb 12 11:23:49 2010 [pid 9379] [user1] OK LOGIN: Client "70.110.23.254"
Fri Feb 12 11:23:49 2010 [pid 9381] [user1] FTP response: Client "70.110.23.254", "230 Login successful."
Fri Feb 12 11:23:49 2010 [pid 9381] [user1] FTP command: Client "70.110.23.254", "PWD"
Fri Feb 12 11:23:49 2010 [pid 9381] [user1] FTP response: Client "70.110.23.254", "257 "/""
Fri Feb 12 11:23:49 2010 [pid 9381] [user1] FTP command: Client "70.110.23.254", "PBSZ 0"
Fri Feb 12 11:23:49 2010 [pid 9381] [user1] FTP response: Client "70.110.23.254", "200 PBSZ set to 0."
Fri Feb 12 11:23:49 2010 [pid 9381] [user1] FTP command: Client "70.110.23.254", "PROT P"
Fri Feb 12 11:23:49 2010 [pid 9381] [user1] FTP response: Client "70.110.23.254", "200 PROT now Private."
Fri Feb 12 11:23:49 2010 [pid 9381] [user1] FTP command: Client "70.110.23.254", "PASV"
Fri Feb 12 11:23:49 2010 [pid 9381] [user1] FTP response: Client "70.110.23.254", "227 Entering Passive Mode (<nat-ip,224,121)"
Fri Feb 12 11:23:49 2010 [pid 9381] [user1] FTP command: Client "70.110.23.254", "LIST"


```

The DEBUG line in the log for SSL is it an error?

---

### Post by hessiess on 2010-02-12
The FTP protocol is a mess, FTP with SSL is a hack. Use SFTP (a sub-protocol of SSH) instead.

This page explains the problems:
[http://www.enterprisedt.com/products/edtftpjssl/doc/manual/html/howtoftpthroughafilewall.html](http://www.enterprisedt.com/products/edtftpjssl/doc/manual/html/howtoftpthroughafilewall.html)

---

