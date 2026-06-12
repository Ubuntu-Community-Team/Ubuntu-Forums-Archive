---
title: "vsftpd and ftps"
date: 2008-10-30
forum: Server Platforms
---

### Post by will0 on 2008-10-30
Hi all

I'm trying to set up a secure ftp server - vsftpd and use ftp over ssl. 

I just get these messages with filezilla:

Status:	Connection established, initializing TLS...
Error:	Could not connect to server

/var/log/vsftpd.log shows nothing at all.

Here's my conf file:

vsftpd.conf
=========================================
listen=YES
anonymous_enable=YES
local_enable=YES
write_enable=YES
dirmessage_enable=YES
xferlog_enable=YES
connect_from_port_20=YES
ftpd_banner=Welcome to blah FTP service.
#pam_service_name=vsftpd
rsa_cert_file=/etc/vsftpd/vsftpd.pem

ssl_enable=YES
force_local_logins_ssl=NO
force_local_data_ssl=YES
ssl_tlsv1=YES
ssl_sslv2=YES
ssl_sslv3=YES
check_shell=NO
=========================================

Can anyone help? I've spent hours on this now - normally Ubuntu admin is so smooth.

Even a more explicit error would be something...

Cheers

Will

---

### Post by cdenley on 2008-10-30
Are you connecting with explicit or implicit SSL? Which port?

---

### Post by Lars Noodén on 2008-10-30
Why not SFTP instead of trying to do the extra effort of tunneling FTP over SSL?

SFTP is part of the package OpenSSH-Server.

---

