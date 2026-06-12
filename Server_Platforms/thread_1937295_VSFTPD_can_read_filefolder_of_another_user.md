---
title: "VSFTPD: can read file/folder of another user"
date: 2012-03-07
forum: Server Platforms
---

### Post by antmanx3 on 2012-03-07
I setting my ftp server with vsftpd and it not working.
And it still how all folder when i login with user ftp.
I only want user only see his home directory.

This is my file vsftpd.conf
> userlist_enable=YES
write_enable=YES
session_support=YES
anon_world_readable_only=NO
no_anon_password=YES
chmod_enable=YES
background=YES
chroot_local_user=NO
guest_enable=NO
local_root=/var/www/
ftp_username=/var/www/
dirlist_enable=YES
download_enable=YES
listen_port=21
local_umask=002
anon_upload_enable=NO
anon_mkdir_write_enable=NO
anon_other_write_enable=NO
use_localtime=YES
xferlog_enable=YES
connect_from_port_20=YES
secure_chroot_dir=/var/run/vsftpd/empty
rsa_cert_file=/etc/ssl/private/vsftpd.pem

Please help me!!! Sorry by my English.
Thanks you!!!

---

### Post by antmanx3 on 2012-03-08
Hi, anybody help me???

---

