---
title: "vsftpd unonymous upload &amp; download"
date: 2006-12-27
forum: Server Platforms
---

### Post by glederfein on 2006-12-27
Hi all!
I'm having some trouble configuring vsftpd. All files uploaded by anonymous users are set with permissions "-rw-------". I want anyone to be able to view the files uploaded by anonymous users.

Here is some information:
vsftpd.conf:
```

listen=YES
anonymous_enable=YES
local_enable=YES
write_enable=YES
anon_upload_enable=YES
anon_mkdir_write_enable=YES
anon_umask=022
local_umask=022
file_open_mode=0777
ascii_upload_enable=YES
dirmessage_enable=YES
xferlog_enable=YES
connect_from_port_20=YES
chown_uploads=YES
chown_username=glederfein
ftpd_banner=Welcome to the FTP service.
secure_chroot_dir=/var/run/vsftpd
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/vsftpd.pem
anon_root=/home/ftp

```

/home/ftp permissions:
```

drwxr-xr-x 3 root       root       4096 2006-12-20 14:16 .
drwxr-xr-x 4 root       root       4096 2006-12-18 18:44 ..
drwxrwxrwx 2 glederfein glederfein 4096 2006-12-27 16:24 upload

```

/home/ftp/upload permissions:
```

drwxrwxrwx 2 glederfein glederfein      4096 2006-12-27 16:24 .
drwxr-xr-x 3 root       root            4096 2006-12-20 14:16 ..
-rw------- 1 glederfein       nogroup          264 2006-12-27 16:24 hspell

```

Any help achieving my goal will be greatly appreciated...

---

