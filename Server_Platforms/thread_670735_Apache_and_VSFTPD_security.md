---
title: "Apache and VSFTPD security"
date: 2008-01-17
forum: Server Platforms
---

### Post by ecrissman on 2008-01-17
I am attempting to tighten up my server, but I am having difficulty wrapping my head around securing my filesystem so that it is not accessible through Apache or FTP.  First, how do I ensure that my /var/www directory is the ONLY directory accessible to the outside?  I have read some documentation about including a <Directory> tag somewhere in Apache, but I am not sure exactly where this would go.
 ```
For example:
<Directory>
Order Deny,Allow
Deny from all
Options None
</Directory>
```
Am I on the right track?

Secondly, I have set up VSFTPD, but when I browse on a local computer with an FTP client, I can see/access the entire filesystem of the server. Again, how would I limit access to only the /www directory?

Thanks

---

### Post by Vinno on 2008-01-18
1) /var/www is the only thing accessible that apache2 will serve out if thats your default web root. Just dont put anything in there you dont want to serve to the outside world, or you could use .htaccess file to restrict people from viewing.

2) Your after jailroot. Edit your vsftpd config file > /etc/vsftpd.conf

> # You may restrict local users to their home directories.  See the FAQ for
# the possible risks in this before using chroot_local_user or
# chroot_list_enable below.
chroot_local_user=YES

# Debian customization
#
# Some of vsftpd's settings don't fit the Debian filesystem layout by
# default.  These settings are more Debian-friendly.
#
# This option should be the name of a directory which is empty.  Also, the
# directory should not be writable by the ftp user. This directory is used
# as a secure chroot() jail at times vsftpd does not require filesystem
# access.
secure_chroot_dir=/var/run/vsftpd

If you want to go into it bit more.
> 
# You may specify an explicit list of local users to chroot() to their home
# directory. If chroot_local_user is YES, then this list becomes a list of
# users to NOT chroot().
chroot_list_enable=YES
# (default follows)
chroot_list_file=/etc/vsftpd.chroot_list


It will jailroot the user to his /home/username location. What you can do is link the /var/www to /home/username/ by using mount trick.

First make a directory in /home/username/ called www then in console type:
> mount --bind /var/www /home/username/www

That should do the trick. If you want the mount bit to be permanent even after you restart your computer.

Edit --> /etc/fstab
at the end of the file add.
> 
/var/www /home/username/www none defaults,bind 0 0


Hope that helps you.

---

