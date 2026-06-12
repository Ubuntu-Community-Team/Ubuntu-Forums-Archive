---
title: "Ubuntu Server Apache permissions"
date: 2010-11-19
forum: Server Platforms
---

### Post by DanHorniblow on 2010-11-19
Hi, I am quite new to linux and am struggling when it comes to setting permissions for appache. To create my server I followed this tutorial:

[http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/comment-page-8/#comment-325564]("http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/comment-page-8/#comment-325564")

I have also installed phpmyadmin.

I now want to install a webmail interface "AfterLogic Webmail Lite" on the server, but I am getting the following errors:

  Creating/deleting folders 	Error, can't create/delete sub-folders in the data folder.

Read/write settings file 	OK / Error, can't write "/var/www/webmail/data/settings/adminpanel.xml" file.

   Read/write settings file 	OK / Error, can't write "/var/www/webmail/data/settings/settings.xml" file.

I belive that it is the /var/www/webmail/data/ directory that has incorrect permissions set?

How do I fix?

Dan

---

### Post by surfer on 2010-11-19
i have no idea about "AfterLogic Webmail Lite" but i guess you downloaded it and unpacked it as root. apache runs under 'www-data'.

did you do this?
```
$ sudo chown -R www-data:www-data /var/www/webmail
```

---

### Post by DanHorniblow on 2010-11-20
> **surfer said:**
> i have no idea about "AfterLogic Webmail Lite" but i guess you downloaded it and unpacked it as root. apache runs under 'www-data'.

did you do this?
```
$ sudo chown -R www-data:www-data /var/www/webmail
```
Thanks a bunch its all working brill now :)

---

### Post by James78 on 2010-11-20
Make sure to mark as solved. Thread tools -> Mark as "solved"

---

