---
title: "VSFTPD Help Needed"
date: 2009-06-28
forum: Server Platforms
---

### Post by Dr.Frequency on 2009-06-28
Hello Everyone!

I'm needing help to create virtual Users into my VSFTPD Server.

I use to Log-in using my Account (admin) that it's the same account that I use to Log-in locally into the Server.

Now I need to create just an FTP User with access, and permissions Only to his Folder.

I'm quite new in Ubuntu, sorry for my basic question... ;)

Here is the conf file:

```
listen=YES
anonymous_enable=YES
local_enable=YES
write_enable=YES
anon_upload_enable=YES
dirmessage_enable=YES
xferlog_enable=YES
connect_from_port_20=YES
ftpd_banner=Bienvenido al FTP de Dr.Frequency
chroot_local_user=YES
secure_chroot_dir=/var/run/vsftpd
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
local_max_rate=0
nopriv_user=vsftpd
guest_username=vsftpd
```

---

