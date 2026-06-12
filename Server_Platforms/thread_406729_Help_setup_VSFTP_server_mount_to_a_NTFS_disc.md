---
title: "Help setup VSFTP server mount to a NTFS disc"
date: 2007-04-11
forum: Server Platforms
---

### Post by jenhsun on 2007-04-11
Hi,
I have my Feisty mount to NTFS hard disc already. I want to setup a vsftpd server mount to this drive for me to storage my files internally. What am I supposed to do the vsftpd.conf setting?
Here is my conf file

```

listen=YES

#listen_ipv6=YES

anonymous_enable=NO

local_enable=YES

write_enable=YES

#local_umask=022

#anon_upload_enable=YES

#anon_mkdir_write_enable=YES

dirmessage_enable=YES

xferlog_enable=YES

connect_from_port_20=YES

#chown_uploads=YES
#chown_username=whoever

xferlog_file=/var/log/vsftpd.log

#xferlog_std_format=YES

#idle_session_timeout=600

#data_connection_timeout=120

#nopriv_user=ftpsecure

#async_abor_enable=YES

#ascii_upload_enable=YES
#ascii_download_enable=YES

#ftpd_banner=Welcome to blah FTP service.

#deny_email_enable=YES
# (default follows)
#banned_email_file=/etc/vsftpd.banned_emails

chroot_local_user=YES

#chroot_list_enable=YES
# (default follows)
#chroot_list_file=/etc/vsftpd.chroot_list

#ls_recurse_enable=YES

secure_chroot_dir=/var/run/vsftpd

pam_service_name=vsftpd

rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
```  

Do I need to setup a symbolic link for this ntfs to my home directory? 
I only can see the shortcut from ftp client other pc but can't go further.

---

