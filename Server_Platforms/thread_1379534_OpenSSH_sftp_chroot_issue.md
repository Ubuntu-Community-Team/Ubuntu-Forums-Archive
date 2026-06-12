---
title: "OpenSSH sftp chroot issue"
date: 2010-01-12
forum: Server Platforms
---

### Post by Tsquad on 2010-01-12
Hello, i followed this guide, [http://blog.markvdb.be/2009/01/sftp-on-ubuntu-and-debian-in-9-easy.html](http://blog.markvdb.be/2009/01/sftp-on-ubuntu-and-debian-in-9-easy.html), a few days ago and set up an sftp server no problem. The user can only see what is in there home folder which is only the examples file which is empty. Today i went to set up a 2nd ftp account for my own private use. I have it set up and all, followed exactly what he said the 2nd time around and my 2nd user is not chroot'd. I can explor the contents of the whole drive. 

My fist user that works fine is "ftpuser" and the group is "sftponly" just like in the guide. My 2nd user is named "ftptaylor". Now i did have an ftp server set up with vsftpd where i had the same ftpuser account in a different group, but it was jailed to /home/ftpuser. I cant tell you how i did it, i followed a number of guides untill one worked. But could it be that the guide above does not in face jail the users, but just that my user was already jail'd?

---

### Post by Lars Noodén on 2010-01-13
The way that tutorial has it set up is that the default is to allow full access, and access can be chrooted by adding an account to the group **sftponly**. The second user must also be in the group **sftponly**

There are ways to do the opposite, have all users chrooted by default but allow certain groups full access.  But the other way might be easier to get used to.

---

### Post by Tsquad on 2010-01-13
i have both usrs in that sftponly group. i dont get why i can still see the full contents tho...

---

