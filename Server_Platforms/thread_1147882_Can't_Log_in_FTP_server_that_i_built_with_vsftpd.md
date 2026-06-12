---
title: "Can't Log in FTP server that i built with vsftpd"
date: 2009-05-03
forum: Server Platforms
---

### Post by Kelen.Chang on 2009-05-03
Can't Log in ftp but local user visit fine. what's the problem is?
```
>>> grep -v "^#" /etc/vsftpd.conf                 ~/Work/
listen=YES
anonymous_enable=YES
local_enable=YES
write_enable=NO
dirmessage_enable=YES
xferlog_enable=YES
connect_from_port_20=YES
xferlog_file=/var/log/vsftpd.log
xferlog_std_format=YES
ftpd_banner=Welcome to Kelen.Chang's FTP service.
pam_service_name=vsftpd
no_anon_password=YES
pasv_enable=yes
anon_root=/home/ftp
```

---

### Post by paul99 on 2009-10-29
Hi Kelen,

Did you ever get this to work?  I'm having the same problem.

Thx,

Paul

---

### Post by ApEkV2 on 2009-10-29
Is your router forwarding the port needed? If not the router is probably blocking the connection.

---

