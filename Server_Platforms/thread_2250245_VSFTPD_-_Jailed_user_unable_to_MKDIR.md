---
title: "VSFTPD - Jailed user unable to MKDIR"
date: 2014-10-27
forum: Server Platforms
---

### Post by Xriva on 2014-10-27
I have a user named    devon

I jailed his ftp activity to his home directory using:     chroot_local_user=YES             in vsftpd.conf

Then I changed his home directory using:                 usermod --home /var/www/html/devon devon

This user can download files . . .  but can't upload any, nor can they create a new sub-folder.

ideas ?

---

### Post by Xriva on 2014-10-27
[http://howto.gumph.org/content/setup-virtual-users-and-directories-in-vsftpd/](http://howto.gumph.org/content/setup-virtual-users-and-directories-in-vsftpd/)

This looks like the answer for me. 

I'm posting in case other are looking for the same info.

---

