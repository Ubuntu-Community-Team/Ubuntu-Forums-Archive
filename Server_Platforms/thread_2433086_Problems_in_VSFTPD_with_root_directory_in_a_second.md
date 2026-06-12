---
title: "Problems in VSFTPD with root directory in a secondary HDD"
date: 2019-12-13
forum: Server Platforms
---

### Post by xavif on 2019-12-13
Hi,

first of all, my Ubuntu/linux skills are so poor.

Following an internet tutorial I could install a VSFTP in Ubuntu 18.04 LTS, working correctly with the root folder in /home/**ftpuser**/ftp
**ftpuser** is not the same as ubuntu main user, which we will call **mainuser**
The /home directory was in a 250GB SSD, too little storage space for a FTP Server. 
Then I decided to move the server's root directory to a second 1TB HDD which I already formatted as EXT4.
I gave the permissions to the directories in the same way (using the same tutorial), but it doesn't work
Filezilla connects properly with the server but it rejects with a 530 error (user autorization I think,... is it?)

As always the secondary HDD was in **/media/mainuser** and FTP root directory is [B]/media/mainuser/1TB/FTP
[/B]These are the permisions of this folders
[INDENT][FONT=courier new]/media[/FONT]
[/INDENT]
[INDENT][FONT=courier new]lrwxrwxrwx  1 root root    7 de de  3 23:22 floppy -> floppy0
drwxrwxr-x  2 root root 4096 de de  3 23:22 floppy0
drwxr-x---+ 2 root root 4096 de de 13 11:18 **mainuser**

/mainuser
dr-xr-xr-x 4 root     root      4096 de de 13 01:03 **[COLOR=#ff0000]1TB  <- this is the EXT4 unit[/COLOR]**
drwxrwxrwx 1 mainuser mainuser 20480 de de 12 23:36 2TB

/1TB
dr-xr-xr-x 4 ftpuser  ftpuser   4096 de de 13 01:09[COLOR=#ff0000] FTP   <- FTP folder (no writable)[/COLOR]
drwx------ 2 root     root     16384 de de 13 01:01 lost+found

/FTP
drwxr-xr-x 2 [/FONT][FONT=courier new][FONT=courier new]ftpuser [/FONT] [/FONT][FONT=courier new][FONT=courier new]ftpuser [/FONT] 4096 de de 13 01:08 [COLOR=#ff0000]workfolder1  <- only these folders are writable[/COLOR]
drwxr-xr-x 2 [/FONT][FONT=courier new][FONT=courier new]ftpuser [/FONT] [/FONT][FONT=courier new][FONT=courier new]ftpuser [/FONT] 4096 de de 13 01:09 [COLOR=#ff0000]workfolder2[/COLOR][/FONT]
[/INDENT]

And this is the VSFTPD.CONF
[INDENT][COLOR=#0000ff]listen=NO
listen_ipv6=YES
anonymous_enable=NO
local_enable=YES
write_enable=YES
dirmessage_enable=YES
use_localtime=YES
xferlog_enable=YES
connect_from_port_20=YES
ftpd_banner=Bienvenido a este servidor FTP de mierda!
chroot_local_user=YES
secure_chroot_dir=/var/run/vsftpd/empty
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
ssl_enable=NO

#Extras
user_sub_token=ftpuser
local_root=**/media/mainuser/1TB/FTP**
pasv_min_port=10090
pasv_max_port=10100
userlist_enable=YES
userlist_file=/etc/vsftpd.userlist    [/COLOR][COLOR=#ff0000] *-> ftpuser are in this userlist*[/COLOR][COLOR=#0000ff]
userlist_deny=NO[/COLOR]
[/INDENT]
What's wrong in this configuration/permisions/config file?

Thanks for advance,
Xavi

---

### Post by Morbius1 on 2019-12-13
> [FONT=courier new] drwxr-x---+ 2 root root 4096 de de 13 11:18 **mainuser**[/FONT]
That little plus ( + ) sign at the end of the permissions of /media/mainuser indicates an access control list ( ACL ). The only user allowed to traverse that folder to get to what is under it is mainuser. This is done to all /media/$USER directories by the system in order to isolate one user from the other for things like usb sticks and such.

I suggest you change the mount point of this HDD. Perhaps something one level up for example: /media/1TB.

---

### Post by xavif on 2019-12-13
> **Morbius1 said:**
> That little plus ( + ) sign at the end of the permissions of /media/mainuser indicates an access control list ( ACL ). The only user allowed to traverse that folder to get to what is under it is mainuser. This is done to all /media/$USER directories by the system in order to isolate one user from the other for things like usb sticks and such.

I suggest you change the mount point of this HDD. Perhaps something one level up for example: /media/1TB.

Have mounted HDD on /media/1TB, and have changed vsftp.conf too, but reject with** 530 again**

/media
[FONT=courier new]**dr-xr-xr-x  4 root root 4096 de de 13 01:03 1TB**
lrwxrwxrwx  1 root root    7 de de  3 23:22 floppy -> floppy0
drwxrwxr-x  2 root root 4096 de de  3 23:22 floppy0
drwxr-x---+ 3 root root 4096 de de 13 20:15 mainuser[/FONT]

[FONT=courier new]/1TB
dr-xr-xr-x 4 ftpuser  ftpuser   4096 de de 13 01:09[COLOR=#ff0000] FTP   <- FTP folder (no writable)[/COLOR]
drwx------ 2 root     root     16384 de de 13 01:01 lost+found

/FTP
drwxr-xr-x 2 [/FONT][FONT=courier new][FONT=courier new]ftpuser [/FONT] [/FONT][FONT=courier new][FONT=courier new]ftpuser [/FONT] 4096 de de 13 01:08 [COLOR=#ff0000]workfolder1  <- only these folders are writable[/COLOR]
drwxr-xr-x 2 [/FONT][FONT=courier new][FONT=courier new]ftpuser [/FONT] [/FONT][FONT=courier new][FONT=courier new]ftpuser [/FONT] 4096 de de 13 01:09 [COLOR=#ff0000]workfolder2[/COLOR][/FONT]

:confused:

---

