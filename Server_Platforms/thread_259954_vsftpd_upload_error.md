---
title: "vsftpd upload error"
date: 2006-09-18
forum: Server Platforms
---

### Post by freewolf on 2006-09-18
i use apt-get install the vsftpd
and enable the build in account to access,
but i can not upload anythings 

Response:	200 Switching to Binary mode.
Command:	PORT 192,168,0,3,12,17
Response:	200 PORT command successful. Consider using PASV.
Command:	STOR header.jpg
Response:	553 Could not create file.
Error:	Upload failed

i do not know why report the 553 error~

my vsftpd.conf

listen=YES
#listen_ipv6=YES
anonymous_enable=YES
local_enable=YES
write_enable=YES
#local_umask=022
anon_upload_enable=YES
anon_mkdir_write_enable=YES
dirmessage_enable=YES
xferlog_enable=YES
connect_from_port_20=YES
#chown_uploads=YES
#chown_username=whoever
#xferlog_file=/var/log/vsftpd.log
#xferlog_std_format=YES
#idle_session_timeout=600
#data_connection_timeout=120
#nopriv_user=ftpsecure
#async_abor_enable=YES
ascii_upload_enable=YES
ascii_download_enable=YES
ftpd_banner=Welcome to freewolf's FTP service.
#deny_email_enable=YES
#banned_email_file=/etc/vsftpd.banned_emails
chroot_local_user=YES
#chroot_list_enable=YES
#chroot_list_file=/etc/vsftpd.chroot_list
#ls_recurse_enable=YES
secure_chroot_dir=/var/run/vsftpd
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key

is anyone can help me thx alot~

---

