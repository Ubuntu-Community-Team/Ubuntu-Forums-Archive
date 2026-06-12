---
title: "vsftpd and client certificates"
date: 2010-05-16
forum: Server Platforms
---

### Post by mfrizzi on 2010-05-16
Hello all,

I'm trying to use the **require_cert=YES ** and **ca_certs_file PATH TO CERT** flags into vsftpd.conf

the configuration that I want to do is due to the fact that I want only workstations with certificate distribuited by me connecting to my vsftpd site.

below the complete configuration file: unfortunatly the last two line must be #-ed in order to VSFTPd to start.
my questions are:
- where (folder) do I have to put the certificate file?
- it's enought for me to create one client certificate with the command 'openssl req -x509 -nodes -days 365 -newkey rsa:1024 -keyout /etc/ssl/private/clientvsftpd.pem -out /etc/ssl/private/clientvsftpd.pem' and distribute it to clients that I want to let connect to my ftps site?

Thank you in advance!

listen=YES
anonymous_enable=NO
local_enable=YES
write_enable=YES
anon_upload_enable=NO
anon_mkdir_write_enable=NO
dirmessage_enable=YES
use_localtime=YES
xferlog_enable=YES
connect_from_port_20=YES
#chown_uploads=YES
#chown_username=whoever
xferlog_file=/var/log/vsftpd.log
xferlog_std_format=YES
idle_session_timeout=600
data_connection_timeout=120

#
# It is recommended that you define on your system a unique user which the
# ftp server can use as a totally isolated and unprivileged user.
#nopriv_user=ftpsecure
#ascii_upload_enable=YES
#ascii_download_enable=YES
#

ftpd_banner=Welcome to blah FTP service.
chroot_local_user=YES
chroot_list_enable=NO
chroot_list_file=/etc/vsftpd.chroot_list
ls_recurse_enable=NO
#
secure_chroot_dir=/var/run/vsftpd/empty
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/private/vsftpd.pem

ssl_enable=YES
allow_anon_ssl=NO
force_local_data_ssl=YES
force_local_logins_ssl=YES
ssl_tlsv1=YES
ssl_sslv2=YES
ssl_sslv3=YES
listen_port=990
pasv_min_port=62100
pasv_max_port=62150
# require_cert=YES
# ca_certs_file /etc/ssl/private/clientvsftpd.pem

---

