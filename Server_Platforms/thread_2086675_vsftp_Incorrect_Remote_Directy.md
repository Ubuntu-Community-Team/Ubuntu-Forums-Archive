---
title: "vsftp: Incorrect Remote Directy"
date: 2012-11-21
forum: Server Platforms
---

### Post by datavoyager on 2012-11-21
Hi Folks,

I've set up VSFTPD on Ubuntu Server 12.04 LTS largely following the instructions here:

[http://howto.gumph.org/content/setup-virtual-users-and-directories-in-vsftpd/](http://howto.gumph.org/content/setup-virtual-users-and-directories-in-vsftpd/)

and taking into account

[http://www.garron.me/bits/500-oops-vsftpd-refusing-to-run-with-writable-root-inside-chroot-solved.html](http://www.garron.me/bits/500-oops-vsftpd-refusing-to-run-with-writable-root-inside-chroot-solved.html)

Here's the relevant config:

listen=YES
anonymous_enable=NO
local_enable=YES
write_enable=YES
local_umask=022
use_localtime=YES
xferlog_enable=YES
connect_from_port_20=YES
chroot_local_user=YES
secure_chroot_dir=/var/run/vsftpd/empty
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/private/vsftpd.pem
userlist_enable=YES
userlist_deny=YES
userlist_file=/etc/vsftpd/user_list
virtual_use_local_privs=YES
guest_enable=YES
guest_username=ftp
user_sub_token=$USER
local_root=/usr/local/ftp
hide_ids=YES
download_enable=YES

I can connect via ftp, I am chained to the correct directory but when I try to upload a file via put, I get a 553 Could not create file.

vsftpd tells me that the remote location is "remote: /home/smeg/text.txt" when I've logged into (and been chained to) a completely different location (/usr/local/ftp with directory of ftpuser available)

/home/smeg doesn't exist on the server - smeg is the name of the unix user I'm logged in as on my local pc

Connected to XXX:XXX:XXX:XXX
220 (vsFTPd 2.3.5)
Name (XXX:XXX:XXX:XXX:user): ftpuser
331 Please specify the password.
Password:
230 Login successful.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> cd ftpuser
250 Directory successfully changed.
ftp> put ~/test.txt
local: /home/smeg/test.txt remote: /home/smeg/text.txt
200 PORT command successful. Consider using PASV.
553 Could not create file.

Any help would be most appreciated!

Thanks,

DV

---

