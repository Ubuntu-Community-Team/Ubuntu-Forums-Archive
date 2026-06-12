---
title: "vsftpd with apache2"
date: 2010-03-10
forum: Server Platforms
---

### Post by Gizmokid2005 on 2010-03-10
I've got what, at least I'd assume, is an easy-to-fix problem.

I've got Ubuntu Server 9.10 running in a VPS and would like to get true FTP working. I currently access files by using SFTP with Filezilla and it works alright, but I want to add some more sites for friends and also allow them to do their own FTP.

I've done a lot of research and decided on using vsftpd would be the best way to do it, but I need some help getting everything setup.

I want to be able to setup users that ONLY have access via FTP through vsftpd and are jailed to their own directory (usually /var/www/<user> to keep things easy).

I've got vsftpd installed but I can't even login with my local root account, I keep getting invalid login:

```
15:38:06	Status:	Resolving address of gizmokid2005.com
15:38:06	Status:	Connecting to 69.162.123.43:21...
15:38:06	Status:	Connection established, waiting for welcome message...
15:38:07	Response:	220 Welcome to Gizmokid2005's FTP hosting.
15:38:07	Command:	USER root
15:38:07	Response:	331 Please specify the password.
15:38:07	Command:	PASS *********
15:38:10	Response:	530 Login incorrect.
15:38:10	Error:	Critical error
15:38:10	Error:	Could not connect to server
```

I do have a user on my system that I must've setup the last time I tried to get vsftpd working, "web" and it logs in just fine and I can transfer files, but they get the following in terms of permissions, so obviously apache can't access/display them:

```
-rw-------  1 web      web 
```

Here's what I've got in my conf:

```

listen=YES
local_enable=YES
write_enable=YES
dirmessage_enable=YES
xferlog_enable=YES
connect_from_port_20=YES
chroot_local_user=YES
ftpd_banner=Welcome to Gizmokid2005's FTP hosting.
secure_chroot_dir=/var/run/vsftpd
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key

```

So, can anyone help/point me in the right direction to accomplish what I want.

---

### Post by Gizmokid2005 on 2010-03-11
*bump* Anyone?

---

### Post by Midnight Star on 2010-03-11
I'm pretty new to Linux and it's utilities overall, but see if [this]("http://howto.gumph.org/content/setup-virtual-users-and-directories-in-vsftpd/") is what your looking to do.

---

### Post by Gizmokid2005 on 2010-03-11
> **Midnight Star said:**
> I'm pretty new to Linux and it's utilities overall, but see if [this]("http://howto.gumph.org/content/setup-virtual-users-and-directories-in-vsftpd/") is what your looking to do.

Thanks. I'll give that a shot.

---

### Post by Gizmokid2005 on 2010-03-11
Well, I tried the tutorial and I'm still getting login incorrect...I'm sure something isn't right with my auth process, but I can't figure out what it is...

---

