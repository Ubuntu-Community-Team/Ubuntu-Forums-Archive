---
title: "vsftpd download files problem."
date: 2008-12-07
forum: Server Platforms
---

### Post by din on 2008-12-07
Hi. I run 8.10 server.
After vsftpd installation i have problem with
downloading file from Internet Explorer xp clients.
If i do right click on any file -> save target as,
i get 

"Internet Explorer cannot download *** from ***
The login request was denied.

From Firefox everything working perfect!!!
Also from cmd -> ftp

The problem only Explorer, but most of users use it :(

My vsftpd.conf

listen=YES
anonymous_enable=NO
local_enable=YES
write_enable=YES
local_umask=022
dirmessage_enable=YES
xferlog_enable=YES
connect_from_port_20=YES
chroot_local_user=YES
chroot_list_file=/etc/vsftpd.chroot_list
secure_chroot_dir=/var/run/vsftpd
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key

---

### Post by Krupski on 2008-12-07
> **din said:**
> Hi. I run 8.10 server.
After vsftpd installation i have problem with
downloading file from Internet Explorer xp clients.
If i do right click on any file -> save target as,
i get 

"Internet Explorer cannot download *** from ***
The login request was denied.

From Firefox everything working perfect!!!
Also from cmd -> ftp

The problem only Explorer, but most of users use it :(

My vsftpd.conf

listen=YES
[COLOR="Red"]**anonymous_enable=NO**[/COLOR]
local_enable=YES
write_enable=YES
local_umask=022
dirmessage_enable=YES
xferlog_enable=YES
connect_from_port_20=YES
chroot_local_user=YES
chroot_list_file=/etc/vsftpd.chroot_list
secure_chroot_dir=/var/run/vsftpd
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key

Your "anonymous" setting should be "yes" since Internet Explorer logs into FTP that way.

---

### Post by din on 2008-12-08
Thanks for reply.
I don't want to allow anonimous login:confused:
So, what can i do ?

---

### Post by bmathis on 2008-12-08
Either enable Anonymous or have your users use a FTP program like FileZilla. Thats pretty much your only options if theyre using MS.

---

