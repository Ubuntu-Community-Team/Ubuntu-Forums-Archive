---
title: "VSFTPD Configuration Issues"
date: 2014-02-11
forum: Server Platforms
---

### Post by matt59 on 2014-02-11
I am trying to use VSFTPD on one of my web servers but I am having issues with virtual users. When I try to login with my test user I get the following error:

> 530 Login incorrect.
Login failed.

Here is my pam.d vsftpd file:

```
auth required pam_mysql.so user=[user] passwd=[password] host=localhost db=vsftpd table=accounts usercolumn=username passwdcolumn=pass crypt=0
account required pam_mysql.so user=[user] passwd=[password] host=localhost db=vsftpd table=accounts usercolumn=username passwdcolumn=pass crypt=0
```

Here is my vsftpd.conf file:

```
listen=YES
anonymous_enable=NO
local_enable=YES
write_enable=YES
local_umask=022
dirmessage_enable=YES
xferlog_enable=YES
connect_from_port_20=YES
nopriv_user=sites
chroot_local_user=YES
secure_chroot_dir=/var/run/vsftpd
pam_service_name=vsftpd
guest_enable=YES
guest_username=sites
local_root=/home/sites/$USER
user_sub_token=$USER
virtual_use_local_privs=YES
user_config_dir=/etc/vsftpd_user_conf
```

Does anyone know why I would get a login failure with these configurations?

---

### Post by matt59 on 2014-02-13
I started using pure-ftpd instead of vsftpd and it is working now.

---

