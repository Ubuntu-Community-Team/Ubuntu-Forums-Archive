---
title: "vsftpd &amp; openssl"
date: 2006-04-09
forum: Server Platforms
---

### Post by jworr on 2006-04-09
I installed both vsftpd & openssl on my box, I want local users to logon to my ftp site with their username and passwords encrypted.  Vsftpd says it was compiled with openssl in the man pages but as soon as I enable any ssl options in the vsftpd conf file the ftp server will not start.  However I can get anonymous and local logins to work, just without any ssl.  

Here is my config file:

listen=YES

#anonymous stuff
anonymous_enable=YES
anon_root=/home/ftp

local user logons
local_enable=YES
chroot_local_user=YES
force_local_logins_ssl=YES
passwd_chroot_enable=YES

#security
ssl_enable=YES
ssl_tlsv1=YES
ssl_sslv3=YES

dirmessage_enable=YES
xferlog_enable=YES
connect_from_port_20=YES

ftpd_banner=Welcome to My FTP server.

secure_chroot_dir=/var/run/vsftpd
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/vsftpd.pem



if I comment out the three ssl lines then I don't have a problem, but if I leave them in the server won't start

any ideas?

---

### Post by s7eam on 2006-04-11
Have you generated SSL certifications?

```

cd /etc/ssl/certs
openssl req -x509 -nodes -days 7300 -newkey rsa:2048 \
  -keyout /etc/ssl/certs/vsftpd.pem -out /etc/ssl/certs/vsftpd.pem

```

---

### Post by jworr on 2006-04-14
Thanks that did the trick

---

