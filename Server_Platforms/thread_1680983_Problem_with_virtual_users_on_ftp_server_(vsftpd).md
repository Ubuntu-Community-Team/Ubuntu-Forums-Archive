---
title: "Problem with virtual users on ftp server (vsftpd)"
date: 2011-02-03
forum: Server Platforms
---

### Post by alfamuzjak on 2011-02-03
I followed few guide's about configuring virtual users but without success. Im trying to create few users(user1,user2) which will map into my main virtual user "virtual". After all this steps _i cant login with any of those users_(user1,user2,virtual). **Please check my steps and tell me what am i doing wrong**...NOTE that I type only this!!! 

```
logins.txt		/etc/vsftpd/logins.txt
user1
pass1
user2
pass2

Creating db:
$ sudo apt-get install db4.7-util

Creating actual database file:

$ sudo db4.7_load -T -t hash -f /etc/vsftpd/logins.txt /etc/vsftpd_login.db

...With restricted permission:
$ sudo chmod 600 /etc/vsftpd_login.db


sudo vi /etc/pam.d/vsftpd

auth required /lib/security/pam_userdb.so db=/etc/vsftpd/vsftpd_login
account required /lib/security/pam_userdb.so db=/etc/vsftpd/vsftpd_login


Creating main virtual user:

sudo mkdir /var/ftp/virtual
sudo useradd -d /var/ftp/virtual virtual

sudo chmod 700 /var/ftp/virtual

adding some files for download;
sudo cp /etc/hosts /var/ftp/virtual
sudo chwon virtual.virtual /var/ftp/virtual/hosts

Options in /etc/vsftpd.conf:
anonymous_enable=NO
local_enable=YES
write_enable=YES
local_umask=022
chroot_local_user=YES

guest_enable=YES
guest_username=virtual
user_sub_token=$USER
local_root=/var/ftp/$USER
hide_ids=YES
user_config_dir=/etc/vsftpd_user_config

sudo mkdir /etc/vsftpd_user_conf

example:
sudo vi /etc/vsftpd_user_config/user1

anon_world_readable_only=NO
write_enable=YES
anon_upload_enable=YES

```

---

