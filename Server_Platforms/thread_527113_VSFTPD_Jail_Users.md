---
title: "VSFTPD Jail Users"
date: 2007-08-16
forum: Server Platforms
---

### Post by md5hash on 2007-08-16
i just installed vsftpd and i want to add a user jailed to their home directory /home/USER_NAME 

i used this command adduser USER_NAME but this user is not jailed.

thanks,

---

### Post by RaZer0r on 2007-08-16
Set this option:
chroot_local_user=YES

If you want to chroot only some users, add the chroot list:
chroot_list_enable=YES
chroot_list_file=/etc/vsftpd.chroot_list

Put all the users you don't want to chroot in /etc/vsftpd.chroot_list

---

### Post by md5hash on 2007-08-16
what is the format when adding user to vsftpd.chroot_list

is it like this user1,user2 or user1 user2 or user per line?

---

### Post by md5hash on 2007-08-16
bump

---

### Post by md5hash on 2007-08-16
solved. :KS

---

