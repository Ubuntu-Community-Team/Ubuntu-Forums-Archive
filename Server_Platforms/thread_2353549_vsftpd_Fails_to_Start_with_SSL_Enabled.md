---
title: "vsftpd Fails to Start with SSL Enabled"
date: 2017-02-22
forum: Server Platforms
---

### Post by xExekut3x on 2017-02-22
vsftpd.conf

```
listen=YES
anonymous_enable=NO
local_enable=YES
write_enable=YES
#xferlog_enable=YES
syslog_enable=NO
vsftpd_log_file=/var/log/vsftpd.log
#nopriv_user=ftpsecure
chroot_local_user=NO
#allow_writable_chroot=YES
secure_chroot_dir=/var/run/vsftpd/empty
#secure_chroot_dir/home/ftpsecure
#pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/private/vsftpd.pem
rsa_private_key_file=/etc/ssl/private/vsftpd.pem
ssl_enable=YES
allow_anon_ssl=NO
force_local_data_ssl=YES
force_local_logins_ssl_YES
ssl_tlsv1=YES
ssl_sslv2=NO
ssl_sslv3=NO
#require_ssl_reuse=NO
#ssl_ciphers=HIGH
#utf8_filesystem=YES
force_dot_files=YES
hide_ids=YES
max_per_ip=2
max_clients=2
```

syslog

```
Feb 22 20:44:16 srv1 systemd[1]: vsftpd.service: Main process exited, code=exited, status=2/INVALIDARGUMENT
Feb 22 20:44:16 srv1 systemd[1]: vsftpd.service: Unit entered failed state.
Feb 22 20:44:16 srv1 systemd[1]: vsftpd.service: Failed with result 'exit-code'.
```

If I comment out the SSL lines, it works fine.

---

### Post by xExekut3x on 2017-02-22
Got it working with:


```
listen=YES
#listen_ipv6=YES
anonymous_enable=NO
local_enable=YES
write_enable=YES
dirmessage_enable=YES
secure_chroot_dir=/var/run/vsftpd/empty
xferlog_enable=YES
connect_from_port_20=YES
ftpd_banner=Unathorized access is monitored!
pam_service_name=vsftp
#rsa_cert_file=/etc/ssl/private/vsftpd.pem
#rsa_private_key_file=/etc/ssl/private/vsftpd.pem
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
ssl_enable=YES
#allow_anon_ssl=NO
#force_local_data_ssl=YES
#force_local_logins_ssl_YES
#ssl_tlsv1=YES
#ssl_sslv2=NO
#ssl_sslv3=NO
#require_ssl_reuse=NO
#ssl_ciphers=HIGH
#utf8_filesystem=YES
#force_dot_files=YES
#hide_ids=YES
#max_per_ip=2
#max_clients=2
```

---

