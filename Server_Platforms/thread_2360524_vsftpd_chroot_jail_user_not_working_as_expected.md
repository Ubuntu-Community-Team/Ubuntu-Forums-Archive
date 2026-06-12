---
title: "vsftpd chroot jail user not working as expected"
date: 2017-05-05
forum: Server Platforms
---

### Post by kosmokramer314 on 2017-05-05
I've gone through the config file and can't figure out where I'm going wrong in trying to keep a user locked into one directory.  I've got the home directory for the user set to /home/ftpfriend/ftp/files and these are the permissions on that dir tree

```
root@windoge2:/# ls -ltrh /
drwxr-xr-x   5 root      root  4.0K May  5 08:05 home

root@windoge2:/home# ls -ltrh
total 12K
drwxr-xr-x 8 mediauser media   4.0K Jan  5 18:39 mediauser
drwxr-xr-x 4 nobody    nogroup 4.0K May  5 08:50 ftpfriend

root@windoge2:/home/ftpfriend# ls -ltrh
total 4.0K
dr-xr-xr-x 3 nobody nogroup 4.0K May  5 08:11 ftp

root@windoge2:/home/ftpfriend/ftp# ls -ltrh
total 4.0K
drwxr-xr-x 3 ftpfriend ftpfriend 4.0K May  5 08:58 files
```

Here's my vsftpd config file:

```
listen=YES
listen_ipv6=NO
anonymous_enable=NO
local_enable=YES
dirmessage_enable=YES
use_localtime=YES
xferlog_enable=YES
connect_from_port_20=YES
user_sub_token=$USER
local_root=/home/$USER/ftp/files
pasv_min_port=40000
pasv_max_port=50000
chroot_local_user=YES
chroot_list_enable=YES
chroot_list_file=/etc/vsftpd.chroot_list
secure_chroot_dir=/var/run/vsftpd/empty
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
ssl_enable=YES
```

---

### Post by LHammonds on 2017-05-05
I don't have time to look at this but I did recently update my [vsftpd tutorial ]("http://hammondslegacy.com/forum/viewtopic.php?f=40&t=228")which does do chroot'd folders.

---

