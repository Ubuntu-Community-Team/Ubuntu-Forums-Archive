---
title: "Default permissions umask ignored by vsftpd and apache2"
date: 2011-09-16
forum: Server Platforms
---

### Post by gabiosz on 2011-09-16
Hi,

I am pulling my hair out over this.

I have Ubuntu Server 11.04 with LAMP and VSFTPD setup, I have a normal user and www-data added to the a www-pub group with var/www/ as the users home directory.

I want to set the permissions to 775 and 664 respectively (owner and group r/w) so that both Apache and the FTP user can make changes to the contents of the /var/www/ directory.

I have used the chown and chmod to change the existing file permissions, all so far so good. However, when either apache or the ftp user upload something, or create something the other 'user' can't write to it as the permissions are 755 and 644.

I have tried changing the umask to 002 in:
/etc/apache2/envvars
/etc/profile/
/etc/login.defs
/etc/vsftpd.config
~/.bashrc
and probably a few more places along the way to no avail.

The umask works in the shell, but not via FTP or by anything that Apache creates.

Please help!

---

