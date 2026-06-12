---
title: "VSFTP freezes immediately after logging in"
date: 2006-08-08
forum: Server Platforms
---

### Post by kerinin on 2006-08-08
I'm trying to set up an FTP server so that our office can put large file online and people can download them.  I'm using VSFTP because it allows me to chroot people so they don't have access to the rest of the server.

I installed VSFTP and set everything up, but now as soon as i log in i get the following output (in Active mode):

```
wright:~ calvinchen$ ftp bcstudio.dnsalias.net
Connected to bcstudio.dnsalias.net.
220 Welcome to the Bercy Chen Studio LLP FTP Server
Name (bcstudio.dnsalias.net:calvinchen): ftpuser
331 Please specify the password.
Password:
230 Login successful.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> passive
Passive mode: off; fallback to active mode: off.
ftp> ls
500 Illegal EPRT command.
200 PORT command successful. Consider using PASV.
```

If i try it in passive mode i get this:
```
wright:~ calvinchen$ ftp bcstudio.dnsalias.net
Connected to bcstudio.dnsalias.net.
220 Welcome to the Bercy Chen Studio LLP FTP Server
Name (bcstudio.dnsalias.net:calvinchen): ftpuser
331 Please specify the password.
Password:
230 Login successful.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> ls
229 Entering Extended Passive Mode (|||31423|)

```

it then sit there until the connection times out.

Here is my configuration file (/etc/vsftpd.conf):
```
listen=YES
anonymous_enable=NO
local_enable=YES
local_umask=022
dirmessage_enable=YES
xferlog_enable=YES
connect_from_port_20=YES
ftpd_banner=Welcome to the Bercy Chen Studio LLP FTP Server
chroot_local_user=YES
chroot_list_enable=YES
chroot_list_file=/etc/vsftpd.chroot_list
secure_chroot_dir=/var/run/vsftpd
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key

```

Does anyone know what's going on?  Any help would be greatly appreciated.

---

### Post by kerinin on 2006-08-09
Anyone?

---

