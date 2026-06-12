---
title: "how to setup a sftp server that users can change passwd by self."
date: 2009-09-13
forum: Server Platforms
---

### Post by Frankin888 on 2009-09-13
I had set up a sftp-server using chroot() function, so the user can log the ftp.
But another question appear, how the use change password? the user cannot login the system using putty, the putty either hang out or no response, i dont know how to reslove it, could anyone can help me? thanks!

---

### Post by fakrulalam on 2009-09-14
what mechanism you are using to authenticate FTP users? Is it /etc/passwd or mysql based authentication. If it is mysql based authentication than you can come up with some PHP syntex to change the users password. If it is /etc/passwd you can use chetcpasswd; though it is mainly used to change email password. You can also try usermin.

---

