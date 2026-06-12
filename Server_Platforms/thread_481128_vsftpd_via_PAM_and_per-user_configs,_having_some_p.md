---
title: "vsftpd via PAM and per-user configs, having some problems"
date: 2007-06-22
forum: Server Platforms
---

### Post by 0x45455844 on 2007-06-22
Hello.

I want to have vstfpd running on my ubuntu 7.04 with PAM users db, and 
with separate configs for every user.

What i've done successfully, is:

+ install vsftpd
+ set up PAM and created db
+ added pam to vsftpd config, so i can login with login/password from PAM db
+ created virtual user for vsftpd guest (with home in /home/virtual)
+ added userlist to vsftpd config, and userdir for user configs

what i can't get is:

- per user config to work

here is contents of my onfigs, maybe it can help to get the proglem...
```

root@dxee:/home/eleeot# cat /etc/vsftpd.conf
# Example config file /etc/vsftpd.conf

listen=YES
anonymous_enable=NO
local_enable=YES
local_umask=022
write_enable=YES
xferlog_enable=YES
chroot_local_user=YES
chown_uploads=YES
chown_username=virtual
connect_from_port_20=YES

rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key

pam_service_name=vsftpd
tcp_wrappers=YES
local_root=/home/virtual
guest_enable=YES
guest_username=virtual
user_config_dir=/etc/vsftpd_users
userlist_enable=YES
userlist_deny=NO
userlist_file=/etc/vsftpd_userlist
hide_ids=YES
root@dxee:/home/eleeot# cat /etc/vsftpd_userlist
dykzei
elli
root@dxee:/home/eleeot# cat /etc/vsftpd_users/dykzei
anon_world_readable_only=NO
write_enable=YES
anon_upload_enable=YES
anon_mkdir_write_enable=YES
anon_other_write_enable=YES
root@dxee:/home/eleeot# ls -l /home
total 12
drwxr-xr-x 44 eleeot  eleeot 4096 2007-06-22 12:33 eleeot
drwxr-xr-x  2 elli    root   4096 2007-06-20 18:42 elli
drw-rw-rw-  3 virtual root   4096 2007-06-21 23:29 virtual
root@dxee:/home/eleeot# ls -l /home/virtual
total 4
drw-rw-rw- 2 root root 4096 2007-06-21 15:23 dir1
root@dxee:/home/eleeot# ftp localhost
Connected to localhost.
220 (vsFTPd 2.0.5)
Name (localhost:eleeot): dykzei
331 Please specify the password.
Password:
230 Login successful.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> ls
200 PORT command successful. Consider using PASV.
150 Here comes the directory listing.
226 Transfer done (but failed to open directory).
ftp>


```

while virtual home has "dir1" directory i should see it with "dykzei" account, but i got "failed to open directory".

any ideas, please?

update:

when changed /home/virtual to 744 i can see it's contents, but upload doesn't work.. can you help me with making it clear what rights are needed to virtual and it's home for upload work?

---

