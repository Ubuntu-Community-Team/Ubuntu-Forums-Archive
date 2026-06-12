---
title: "vsftpd local user cannot write"
date: 2013-05-27
forum: Server Platforms
---

### Post by prodigy10 on 2013-05-27
Hi All,
        I am new to the forum, so please school me on protocol if needed. That been said. I just set up a vsftp server. I am able to login with a local user, the problem is that I am not able to write to the user home folder. I am connecting through Mac OS X client.  Any pointers.

[B]/etc/vsftpd.conf
[/B]
[I]listen=YES
anonymous_enable=NO
local_enable=YES
write_enable=YES
local_umask=022
dirmessage_enable=YES
use_localtime=YES
xferlog_enable=YES
connect_from_port_20=YES
secure_chroot_dir=/var/run/vsftpd/empty
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key[/I]

---

### Post by DJ_Max on 2013-05-27
Who's the owner of the directory you're trying to write to?

---

### Post by prodigy10 on 2013-05-28
The owner is the same user I am using on the ftp session.

---

