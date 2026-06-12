---
title: "FTP server, restrict access"
date: 2007-01-13
forum: Server Platforms
---

### Post by Mirrorball on 2007-01-13
I've just installed vsftpd in my server and now I'd like to create a user account that will only be able to access one directory (in /var/www). This user will only be able to upload/download files to that directory. How do I do this?

---

### Post by Mirrorball on 2007-01-14
Answering my own question, the solution is to set  chroot_local_user=YES in /etc/vsftpd.conf and create a user whose /home directory is the directory that you want him to be able to access.

---

