---
title: "500 OOPS: priv_sock_get_result"
date: 2015-01-05
forum: Server Platforms
---

### Post by liste on 2015-01-05
I'm trying to get virtual users set up on my server.  I have forwarded port 21 to the correct computer on my router, and opened port 21 on my firewall (ufw).  I'm using Ubuntu Server 14.04 for my server.  I have installed vsftpd, db-util, and libpam-pwdfile.  Whenever I try to connect via FTP, I get the following error:

```
500 OOPS: priv_sock_get_result
Login failed.
421 Service not available, remote server has closed connection
```

I created the /etc/vsftpd/ directory, belongs to root:root, 755.  I added the vusers.txt with user on line 1 and 3, and password on line 2 and 4.  Then I used the following command to conver the plain text to .db  The generated file has rw for user (root:root), and 0 permission for group and others.

```
sudo db_load -T -t hash -f vusers.txt /etc/vsftpd/vsftpd-virtual-user.db
```

The contents of /etc/pam.d/vsftpd.virtual :

```
#%PAM-1.0
auth       required     pam_userdb.so db=/etc/vsftpd/vsftpd-virtual-user
account    required     pam_userdb.so db=/etc/vsftpd/vsftpd-virtual-user
session    required     pam_loginuid.so
```

The contents of /etc/vsftpd.conf (minus comments)

```
listen=YES
anonymous_enable=NO
local_enable=YES
virtual_use_local_privs=YES
write_enable=YES
write_enable=YES
user_sub_token=$USER
local_umask=002
local_root=/var/www/virtual/$USER
listen_port=21
dirmessage_enable=YES
use_localtime=YES
xferlog_enable=YES
connect_from_port_20=YES
chroot_local_user=YES
allow_writeable_chroot=YES
passwd_chroot_enable=YES
chroot_list_enable=YES
chroot_list_file=/etc/vsftpd.chroot_list
tcp_wrappers=YES
user_config_dir=/etc/vsftpd_user_conf
secure_chroot_dir=/var/run/vsftpd/empty
pam_service_name=vsftpd.virtual
guest_enable=YES
hide_ids=YES
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
```

I'm guessing it's something wrong with my vsftpd.conf file, but I'm still new to this.

---

### Post by liste on 2015-01-05
Well, I don't know if it's a great solution, but it works.  This thread helped me find my answer:  [http://ubuntuforums.org/showthread.php?t=1941545](http://ubuntuforums.org/showthread.php?t=1941545)

Specifically, these two lines (sufficient) are what made it work, though I fiddled around with a few other settings as well:

auth sufficient
account sufficient

---

