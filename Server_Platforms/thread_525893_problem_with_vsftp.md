---
title: "problem with vsftp"
date: 2007-08-14
forum: Server Platforms
---

### Post by guilly on 2007-08-14
I used to have proftpd configured and running fine, but I decided to install vsftp for security purposes. But i can not seem to get this thing running, when i try to connect it seems to hang giving me this prompt in gftp Connected to x.x.x.x:xx
SSH-2.0-OpenSSH_4.3p2 Debian-8ubuntu1

i'm assuming i'm missing something with the SSL key? i haven't configure SSL in my vsftp.conf file yet i just want to get connected first and have that all sorted out. Here is my vsftp.conf file.

also as a side note i have removed proftpd, by doing an sudo apt-get remove proftpd and my vsftpd.conf dosen't have any comments since i'm just testing let me know if you would like a more descriptive config file

is there something still running that is blocking vsftp from working properly???

thanks for the help!!

anonymous_enable=NO

local_enable=YES

write_enable=YES

local_umask=022

connect_from_port_20=YES

chmod_enable=NO

ftpd_banner=Welcome to Guilly's ftp!

chroot().
chroot_list_enable=YES
chroot_list_file=/etc/vsftpd.chroot_list

pam_service_name=vsftpd

userlist_enable=NO

listen=YES

---

### Post by guilly on 2007-08-15
no one has every had this problem, Every thread i've read regarding vsftpd installs seem to have gone smoothly therefore i'm really leaning towards the problem being with proftpd ? but like i said it has been installed and diong a quick netstat in the terminal i see no evidence of it still listening ??

anyone? plz!!

---

### Post by airmertana on 2007-09-05
I'm having the same problem with vsftp. I've been trying to connect from XP using Filezilla. Heres my conf. file.
listen=YES
ssl_enable=YES
anonymous_enable=NO
local_enable=YES
write_enable=YES
dirmessage_enable=YES
xferlog_enable=YES
connect_from_port_20=YES
secure_chroot_dir=/var/run/vsftpd
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/home-server-cert.pem
rsa_private_key_file=/etc/ssl/private/home-server-key.pem

---

### Post by mattyB on 2007-09-06
Try [this tutorial]("http://wiki.vpslink.com/index.php?title=Configuring_vsftpd_for_secure_connections_%28TLS/SSL/SFTP%29"), it's geared towards CentOS but translates nicely for Ubuntu (I'm using Feisty).  Pay particular attention to creating the certificate. Before you create the Cert, ```
mkdir /etc/vsftpd
``` This is where you'll stick the Cert (if that's where you want to store it).

Next generate the Cert:
```
openssl req -x509 -nodes -days 365 -newkey rsa:1024 -keyout /etc/vsftpd/vsftpd.pem -out /etc/vsftpd/vsftpd.pem
```

Don't forget to point to the Cert in you vsftp.conf file. [URL="http://wiki.vpslink.com/index.php?title=Configuring_vsftpd_for_secure_connections_%28TLS/SSL/SFTP%29#Configure_vsftpd"]See howto...
[/URL]
Cheers,

matt

9.7.07 -
This might also be of interest for trouble shooting needs...[click here]("http://www.linuxquestions.org/questions/showthread.php?t=120158").

---

