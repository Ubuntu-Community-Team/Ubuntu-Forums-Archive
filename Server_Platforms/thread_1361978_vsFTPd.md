---
title: "vsFTPd"
date: 2009-12-22
forum: Server Platforms
---

### Post by mkormendy on 2009-12-22
I cannot log into vsFTPd using simple FTP.
I can however log in with sFTP. I am not concerned with FTP SSL.
The server hangs after my password is provided.

I don't need to have a secure FTP connection because I am only utilizing this locally on my lan with some web-based FTP operations that are required for my site and server.

I have read about something to do with PAM, but I am confused with all of this.

This is my config file for vsftpd:

listen=YES
local_enable=YES
write_enable=YES
local_umask=077
dirmessage_enable=YES
use_localtime=YES
xferlog_enable=YES
connect_from_port_20=YES
ftpd_banner=Something Interactive Server.
secure_chroot_dir=/var/run/vsftpd/empty
pam_service_name=vsftpd
pasv_enable=YES
pasv_min_port=1025
pasv_max_port=1045
#rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
#ssl_enable=YES
#allow_anon_ssl=NO
#force_local_data_ssl=YES
#force_local_logins_ssl=YES
#ssl_tlsv1=YES
#ssl_sslv2=YES
#ssl_sslv3=YES
force_dot_files=YES
hide_ids=YES
max_per_ip=5
max_clients=20

Can anyone help?

---

### Post by mkormendy on 2010-01-11
No-one can help?

---

