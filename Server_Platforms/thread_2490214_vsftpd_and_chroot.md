---
title: "vsftpd and chroot"
date: 2023-08-26
forum: Server Platforms
---

### Post by klapvogn on 2023-08-26
Hi,

I have installed vsftpd on my Ubuntu 22.04 server. but I have an issue with chroot:

my conf :
```
listen=NO
listen_port=325
listen_ipv6=YES
anonymous_enable=NO
local_enable=YES
write_enable=YES
local_umask=022
nopriv_user=vsftpd
virtual_use_local_privs=YES
guest_enable=YES
local_root=/home/xxxx/data/local/downloads/FTP/
chroot_local_user=NO

hide_ids=YES
guest_username=vsftpd


rsa_cert_file=/etc/ssl/private/vsftpd.pem
rsa_private_key_file=/etc/ssl/private/vsftpd.pem
ssl_enable=YES

```

I have tried to switch between YES and NO in ```
chroot_local_user=NO
```

In ```
/etc/vsftpd/vsftpd_user_conf
``` I have two files with diffrent username and the content is:
```
local_root=/home/xxxx/data/local/downloads/FTP/klapvogn/
``` userfile number 2 and diffrent username at the end ofcouse 

I can login with the above, but i'm not chrooted, nor is the other user I have created.

I followed this guide: [https://askubuntu.com/questions/575523/how-to-setup-virtual-users-for-vsftpd-with-access-to-a-specific-sub-directory](https://askubuntu.com/questions/575523/how-to-setup-virtual-users-for-vsftpd-with-access-to-a-specific-sub-directory)

Can't figure out what i'm missing so the chroot can work ?

---

### Post by TheFu on 2023-08-26
Whenver I see people using vsftp, I have to ask why they don't just use the built-in sftp-server included in every openssh install?  There is a chroot that's pretty trivial for openssh's sftp-server AND well documented.

BTW, putting a chroot under any user's HOME directory is a bad idea.

---

### Post by klapvogn on 2023-08-26
thanks, i'll look into that :)

---

