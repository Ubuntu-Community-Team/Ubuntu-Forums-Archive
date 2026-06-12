---
title: "vsftp changed??"
date: 2011-05-23
forum: Server Platforms
---

### Post by phibuntu on 2011-05-23
[SOLVED]

Hi everybody

I wanted to connect to my FTP Server (vsftp version 2.0.7) yesterday and could suddenly not connect:
```

>ftp gress.ly
Connected to gress.ly.
220 ProFTPD 1.3.1 Server (Debian) [::ffff:109.230.211.248]
Name (gress.ly:phi): phi
331 Password required for phi
Password:
530 Login incorrect.
Login failed.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> 
```

Actually I run a debian Server, but the forum of my provider does not know the word "vsftp" (thats why I ask here).

My vsftp.conf look like this:

```
listen=YES
anonymous_enable=NO
local_enable=YES
write_enable=YES
local_umask=022
dirmessage_enable=YES
xferlog_enable=YES
connect_from_port_20=YES
chown_uploads=YES
chown_username=phi
chroot_local_user=YES
secure_chroot_dir=/var/run/vsftpd
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/vsftpd.pem

```

restarting the server...
```
>/etc/init.d/vsftpd restart
```
... I get:
```
Restarting FTP server: vsftpdNo /usr/sbin/vsftpd found running; none killed.
.
```

Even if a /var/run/vsftp/vsftp.pid is generated, there is no process started (ps -A | grep "vsftp"  produces an empty output). I think the process kills itself. I have found nothing in the log files.


What happened? I have done nothing with the vsftp, it worked properly some weeks ago. But: Because the provider moved my virtual host to another PC and because I upgraded all debian-packages, I think, it has something to do with a firewall, restricted ports or simply with a new IPv6 address???

Any Ideas where to look further?


Every help is welcome.

&#632;

---

### Post by Lars Noodén on 2011-05-23
> **phibuntu said:**
> 
Any Ideas where to look further?


Do you have SSH already?  If so then you also already have SFTP and may switch to it.  FTP is insecure and can be retired.

---

### Post by phibuntu on 2011-05-24
Thanks Lars Noodén

I hava SSH to connect as root to the virtual host. 
So I think the essential drivers are there. I will give it a try in the next days.

Your answer does not solve the vsftp problem, but solves my issue at a far higher level!

Thanks again!

&#7602;

---

### Post by phibuntu on 2011-05-24
sftp works!

great, thanks again :-)

---

### Post by Lars Noodén on 2011-05-24
Great!  I knew it would.  It's that simple/reliable.  

There is also a fun assortment of [SFTP clients](http://en.wikibooks.org/wiki/OpenSSH/Client_Applications#GUI_Clients) available.

---

