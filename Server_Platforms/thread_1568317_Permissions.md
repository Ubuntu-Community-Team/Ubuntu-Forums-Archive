---
title: "Permissions"
date: 2010-09-05
forum: Server Platforms
---

### Post by mofire on 2010-09-05
Hi all.

I have a ubuntu server which I have configured to act as an FTP server but i have an issue with the permissions on the directory in the server. I have created a new user account which i want remote users to use to access the FTP server,but when they use Filezilla on their client computers they can access all the folders in the server which I dont want,i want them just to access the home directory where they will upload data into. so guys any help on how i can achieve this ?

---

### Post by Ryan Dwyer on 2010-09-05
You want to set up a chroot. Which FTP server are you using?

---

### Post by mofire on 2010-09-05
Thanks for your quick response. Am using vsftpd on ubuntu 10.04 and on the client computers they are using filezilla. I was trying to use chmod, i dont know about chroot may be you can assist me on that.

---

### Post by Ryan Dwyer on 2010-09-05
In /etc/vsftpd/vsftpd.conf, set chroot_local_user=YES. Then restart vsftpd.

---

### Post by mofire on 2010-09-05
Thanks alot it has worked.

---

