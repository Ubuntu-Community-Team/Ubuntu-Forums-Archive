---
title: "Problem with vsftpd (Anonymous cannot upload file)"
date: 2009-04-30
forum: Security
---

### Post by g00rkha75 on 2009-04-30
Hello all,

I just setup an ftp server using vsfpd on Heron (8.04 LTS).  The problem is if I log in as anonymous user, I cannot upload file.  

Here is my vsftpd.conf, and any replies will be much appreciated:
------------------------------------------------------------------------
[FONT="Courier New"]anonymous_enable=YES

write_enable=YES

anon_upload_enable=YES

anon_mkdir_write_enable=YES

dirmessage_enable=YES

xferlog_enable=YES

connect_from_port_20=YES

xferlog_file=/var/log/vsftpd.log

ftpd_banner=Welcome to Exercise FTP service.

ls_recurse_enable=YES

pam_service_name=vsftpd

rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem

rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key

user_config_dir=/data/vsftpd_user_conf[/FONT]
------------------------------------------------------------------------

Rgds,
NP

---

### Post by sahabcse on 2009-04-30
paste the o/p of 
sudo tail -f /var/log/vsftpd.log

---

