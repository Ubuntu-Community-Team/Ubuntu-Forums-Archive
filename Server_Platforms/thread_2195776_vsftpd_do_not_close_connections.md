---
title: "vsftpd do not close connections"
date: 2013-12-26
forum: Server Platforms
---

### Post by renoproc on 2013-12-26
Hi,
I've set up a vsftpd server with virtual users, and limited connections to 10 by user.
If I try to upload files vsftpd accumulate the threads to 10 and after that refused the next uploads.
With a "ps -fe | grep ftp" I can see all my connections, all unclosed.

In example :
```
root      5052     1  0 15:10 ?        00:00:00 vsftpd: LISTENER
999      12585  5052  0 15:48 ?        00:00:00 vsftpd: xxx.xxx.xxx.xxx: connected
999      12586  5052  0 15:48 ?        00:00:00 vsftpd: xxx.xxx.xxx.xxx: connected
virtual  12591 12586  0 15:48 ?        00:00:00 vsftpd: xxx.xxx.xxx.xxx/myuser: STOR loading.gif
virtual  12592 12585  0 15:48 ?        00:00:00 vsftpd: xxx.xxx.xxx.xxx/myuser: STOR aix_calendar.css
999      12646  5052  0 15:49 ?        00:00:00 vsftpd: xxx.xxx.xxx.xxx: connected
virtual  12650 12646  0 15:49 ?        00:00:00 vsftpd: xxx.xxx.xxx.xxx/myuser: STOR logo_ecole_aix.png
999      12651  5052  0 15:49 ?        00:00:00 vsftpd: xxx.xxx.xxx.xxx: connected
virtual  12653 12651  0 15:49 ?        00:00:00 vsftpd: xxx.xxx.xxx.xxx/myuser: STOR gui.js
999      12656  5052  0 15:49 ?        00:00:00 vsftpd: xxx.xxx.xxx.xxx: connected
virtual  12660 12656  0 15:49 ?        00:00:00 vsftpd: xxx.xxx.xxx.xxx/myuser: STOR layer.js
999      12661  5052  0 15:49 ?        00:00:00 vsftpd: xxx.xxx.xxx.xxx: connected
virtual  12664 12661  0 15:49 ?        00:00:00 vsftpd: xxx.xxx.xxx.xxx/myuser: STOR doc_player_enclosure.html
```

A "service vsftpd restart" do not solve the problem, and I have to kill unclosed processes to be able to upload again.
What's this problem ?!!

Here is my vsftpd.conf :
```
listen=YES
max_clients=10
max_per_ip=10

nopriv_user=ftpsecure
setproctitle_enable=YES
pasv_enable=YES
port_enable=NO
connect_from_port_20=YES

ssl_enable=NO
ssl_tlsv1=YES
ssl_sslv2=NO
ssl_sslv3=NO
ssl_ciphers=HIGH
rsa_cert_file=/etc/ssl/certs/vsftpd.pem
rsa_private_key_file=/etc/ssl/certs/vsftpd.pem
force_local_data_ssl=YES
force_local_logins_ssl=YES
require_ssl_reuse=NO
debug_ssl=YES

vsftpd_log_file=/var/log/vsftpd.log
syslog_enable=NO
xferlog_enable=YES
log_ftp_protocol=YES

anonymous_enable=NO
anon_upload_enable=NO
anon_mkdir_write_enable=NO
anon_other_write_enable=NO

local_enable=YES
local_umask=022
local_root=/var/www
user_config_dir=/etc/vsftpd/users
local_max_rate=0

guest_enable=YES
guest_username=virtual

chroot_local_user=YES
chroot_list_enable=YES
chroot_list_file=/etc/vsftpd.chroot_list

ftpd_banner=Welcome to the xxxxx ftp service.
dirmessage_enable=YES
message_file=.message

dirlist_enable=YES
ls_recurse_enable=YES

download_enable=NO
write_enable=NO
force_dot_files=NO

secure_chroot_dir=/var/run/vsftpd/empty
pam_service_name=vsftpd
```

And myuser specific conf :
```

local_root=/var/ftp/my_user

dirlist_enable=YES
ls_recurse_enable=YES

download_enable=YES
anon_world_readable_only=NO

write_enable=YES
anon_upload_enable=YES

anon_mkdir_write_enable=YES
anon_other_write_enable=YES

file_open_mode=0755
force_dot_files=YES
virtual_use_local_privs=YES

local_umask=022
anon_umask=022
```

Thanks for your help!

---

