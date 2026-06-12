---
title: "Apache and FTP"
date: 2006-06-06
forum: Server Platforms
---

### Post by bambala2002 on 2006-06-06
Hi,

I need a LAMP server for my project in the university, and I chose Ubuntu 6.
I installed Ubuntu Server LAMP, it is running ok, no problem here.
Now I need an FTP server to upload, download, edit, chmod files that are in /var/www directory.
I installed vsftpd. Now I'm a little lost. How do I make /var/www directory the root directory for the vsftpd ?

As a temporary solution, my ftp root dir is in /home/myUserName
I created a www directory and mounted the /var/www in it. The problem is that when I upload files, the are uploaded with other permissions, and Apache cannot even read them. The CHMOD over FTP is not working for some reason and I have to login to shell and CHMOD my uploaded files to 777. That sucks :(


So, please, can anyone tell me how to set a WWW Server with FTP access to the root www dir? :-k 

Thank you

---

### Post by Randomskk on 2006-06-06
Why not set the Apache website directory to your FTP directory?

---

### Post by bambala2002 on 2006-06-06
How?
And it would still not solve my problem. How can I make that Apache has the privileges to read, write the files of Ftp Server and vice versa?

---

### Post by diotro on 2007-11-29
Yes, I'd love to know what info can be given on this subject.

---

### Post by qix on 2007-11-30
I don't know vsftpd, but in proftpd you can set the umask option, which specifies which permissions is applied to files uploaded via the ftp.
So my advice is to look through some vsftpd documentation and look for umask.

---

