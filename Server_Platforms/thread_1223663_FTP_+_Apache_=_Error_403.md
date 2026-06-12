---
title: "FTP + Apache = Error 403"
date: 2009-07-26
forum: Server Platforms
---

### Post by lks45 on 2009-07-26
Hello!

My proftpd is working fine, I add the users and after:

usermod -d /var/www/site_com <login here>
chown -R <login here> /var/www/site_com

Its to link the ftp user to your folder at the server, he can send and receive files without problems!

But! All he sends show as error 403 in apache, he needs send and after chmod all files sendede. If he do it, the files stop error 403. Dont have one way to fix it? Sending and auto-chmod all files? With root its works, but, with another users not.

Thanks for any help!:popcorn:

---

### Post by hessiess on 2009-07-26
You need to change the group/owner of the uploaded files to the same user that apache is running as, then chmod the files to 770. Or get Apache running as the same user as your FTP server is running as.

---

### Post by lks45 on 2009-07-26
> **hessiess said:**
> You need to change the group/owner of the uploaded files to the same user that apache is running as, then chmod the files to 770. Or get Apache running as the same user as your FTP server is running as.

Yes. But you know how to do it, my ftp server is vsftpd...

---

