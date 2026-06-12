---
title: "Question about vsftpd"
date: 2008-12-25
forum: Server Platforms
---

### Post by madcreation on 2008-12-25
I am running a ubuntu server and I installed vsftpd for my ftp service. What I'm wondering is there a way I can have the local users to login and anonymous with no login. At the moment it is set up and the local user can login and everything works fine, but when I add yes to anonymous_enable in the vsftpd.conf file no local users or anonymous can  login. And also where is the anonymous directory, I'm assuming it is the ftp folder that was created at install but I just want to make sure. 

anonymous_enable=NO
local_enable=YES
write_enable=YES
dirmessage_enable=YES
xferlog_enable=YES
connect_from_port_20=YES
ftpd_banner=Welcome to Mad's FTP service
chroot_local_user=YES
chroot_list_enable=YES
chroot_list_file=/etc/vsftpd.chroot_list
secure_chroot_dir=/var/run/vsftpd
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
chmod_enable=YES

---

