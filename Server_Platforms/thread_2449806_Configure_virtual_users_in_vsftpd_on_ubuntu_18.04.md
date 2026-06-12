---
title: "Configure virtual users in vsftpd on ubuntu 18.04"
date: 2020-09-02
forum: Server Platforms
---

### Post by lafayettes on 2020-09-02
Hello,

I have to configure several virtual users in vsftpd service on an Ubuntu 18.04 server without su or sudo permissions, although I have permissions to edit this files:


    /etc/ssh/sshd_config
    /etc/vsftpd.userlist
    /etc/vsftpd.chroot_list
    /etc/vsftpd.conf


Is it possible to configure virtual users by editing only these files?


I have been told that yes, although the guides I find indicate that a virtual user repository will be needed, either in a db file or through pam.


Thank you.

---

### Post by LHammonds on 2020-09-03
The way I have created users for vsftpd was the use of a normal user account but prevent shell access as [noted here](https://hammondslegacy.com/forum/viewtopic.php?p=735#p735)

I have not yet used a non-sudo way of creating users.

LHammonds

---

