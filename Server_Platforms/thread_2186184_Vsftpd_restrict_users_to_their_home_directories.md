---
title: "Vsftpd: restrict users to their home directories"
date: 2013-11-06
forum: Server Platforms
---

### Post by Renaissance2011 on 2013-11-06
Hello,

My public ftp uses Ubuntu 12.04 LTS operating system. I want restrict users to their home directories.

My /etc/vsftpd.conf look like this:

Uncomment chroot_local_user=YES
Uncomment chroot_list_enable=YES
Uncomment chroot_list_file=/etc/vsftpd.chroot_list

Result is that no user can log in.

Please help

---

