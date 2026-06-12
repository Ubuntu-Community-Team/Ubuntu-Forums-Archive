---
title: "Ftp root folder in vsftp"
date: 2006-09-03
forum: Server Platforms
---

### Post by Daveyboy on 2006-09-03
Trying to create a ftp root folder for authenticated users in vsftp. Do not see any settings in vsftpd.conf. Curently when users login, they can see the whole linux directory structure.

---

### Post by apiper on 2006-09-03
If you want the users to have read-only access (ie they won't be able to upload files) then use the "secure_chroot_dir" option. Here's the Ubuntu default setting:

[INDENT][FONT="Courier New"]secure_chroot_dir=/var/run/vsftpd[/FONT][/INDENT]

If you want users to be able to upload files, add this option to your /etc/vsftpd.conf file

[INDENT][FONT="Courier New"]write_enable=YES[/FONT][/INDENT]

For other options have a look at the manpage for vsftpd.conf

[INDENT][FONT="Courier New"]man vsftpd.conf[/FONT][/INDENT]

Hope this helps! :)

---

