---
title: "vsftpd can't connect"
date: 2008-10-15
forum: Server Platforms
---

### Post by vegas588 on 2008-10-15
I cannot connect to my vsftpd that I recently set up. Basic error message is connection refused by server.

listen=YES
anonymous_enable=YES
local_enable=YES
write_enable=YES
dirmessage_enable=YES
xferlog_enable=YES
connect_from_port_20=YES
ftpd_banner=Welcome to MY COMPANY'S FTP SITE....
secure_chroot_dir=/var/run/vsftpd
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key

Mostly all defaults.

Names of server is ubuntuserver2, so when I try to connect from Windows XP workstation, i just go to [ftp://ubuntuserver2/homedirs/ftp](ftp://ubuntuserver2/homedirs/ftp)

I also added in a line in iptables to allow ftp connections:

jamesc@ubuntuserver2:~$ sudo iptables -L
[sudo] password for jamesc:
Chain INPUT (policy ACCEPT)
target     prot opt source               destination
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ftp

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

The /homedirs/ftp seems to be from the Samba installation and I am not sure why it would do that...

Thanks,

---

### Post by vegas588 on 2008-10-15
This is what I get when I try to connect via command-line

Microsoft Windows XP [Version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

X:\>c:

C:\>ftp
ftp> open
To 192.168.110.80
> ftp: connect :Unknown error number
ftp>

---

