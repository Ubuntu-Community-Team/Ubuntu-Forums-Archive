---
title: "vsftpd and local_enable"
date: 2007-11-20
forum: Server Platforms
---

### Post by Profik123 on 2007-11-20
I'm using Ubuntu 7.10 GG and I installed vsftpd. I wanna enable log in with default user "ftp", but it doesn't work. In my conf I use local_enable. But "ftp" is not normal user or I don't know. How to solve this problem? How to enable logging in with user "ftp"?

My conf:

```

# Standalone mode
listen=YES
max_clients=200
max_per_ip=4

# Access rights
anonymous_enable=NO
local_enable=YES
write_enable=YES
anon_upload_enable=NO
anon_mkdir_write_enable=NO
anon_other_write_enable=NO

# Security
anon_world_readable_only=YES
connect_from_port_20=YES
hide_ids=YES
pasv_min_port=50000
pasv_max_port=60000

# Features
xferlog_enable=YES
ls_recurse_enable=NO
ascii_download_enable=NO
async_abor_enable=YES

# Performance
idle_session_timeout=120
data_connection_timeout=300
accept_timeout=60
connect_timeout=60
anon_max_rate=20000


```

---

### Post by reckless2k2 on 2007-11-20
someone help me on this but i think ftp is the default environment if you have anonymous enabled. other than that, local user with a user and password can log into to their home directories.

---

### Post by netlogic on 2007-11-21
try these settings if you wan tto use local accounts. You should also chroot them to their home directories, so they can't browse to your configuration and var directories.

# starts right here!!!
listen=YES
anonymous_enable=NO
local_enable=YES
write_enable=YES
local_umask=022
anon_upload_enable=NO
anon_mkdir_write_enable=no
dirmessage_enable=YES
xferlog_enable=YES
connect_from_port_20=YES
idle_session_timeout=6000
data_connection_timeout=1200
ftpd_banner=DAMN GOOD FTP

#==============CHROOT settings=====================
# You may restrict ALL local users to their home directories.  See the FAQ for
# the possible risks in this before using chroot_local_user or
# chroot_list_enable below.
chroot_local_user=YES

# You may specify an explicit list of local users to chroot() to their home
# directory. If chroot_local_user is YES, then this list becomes a list of
# users to NOT chroot().
chroot_list_enable=YES
# (default follows)
chroot_list_file=/etc/vsftpd.chroot_list
# ==============================================
secure_chroot_dir=/var/run/vsftpd
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key

# enable this if you want SSL (secure FTP login)
ssl_enable=YES
allow_anon_ssl=NO
force_local_data_ssl=YES
force_local_logins_ssl=YES
ssl_tlsv1=YES
ssl_sslv2=YES
ssl_sslv3=YES
# end SSL stuff

force_dot_files=NO
# Connection limit for each IP:
max_per_ip=4
# Maximum number of clients:
# if you are behind a NAT firewall, you might want
# open some ports for your data transfer. 
# you don't need it, if this is your internal firewall.
pasv_min_port=12000
pasv_max_port=12100

---

