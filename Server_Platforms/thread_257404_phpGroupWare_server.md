---
title: "phpGroupWare server"
date: 2006-09-14
forum: Server Platforms
---

### Post by spottraining on 2006-09-14
Hi

I try here to get phpGroupware server to work.
My Apache working now, MySQL is installed also. I have  also MySQL user phpgroupware and database phpgroupware.
I found, that phpGroupware is in Universe repositories also. So I make install with command:
sudo apt-get install phpgroupware

Its installs everything, what needed. During the installation I have asked some questions about database and administrator passwords.

But I have problem - this database phpgroupware - what password and usernames I given - is still emty.
And also - when I open in browser this server web page (this will be only samba and phpgroupware server - so no virtual domains) - I see only apache default page. There is no directory phpgroupware.

So - what I make wrong with instillation? How I can access to phpgroupware.

---

### Post by spottraining on 2006-09-16
no ideas?

---

### Post by Orestes on 2006-10-09
You sure you set up mysql correctly?

ie using mysqladmin to set a root password?

---

### Post by spottraining on 2006-10-09
MySQL is OK.
Problem whas, that from repositories PGW is installed not to the www directory. And thats needed extra lines to Apache conf.

---

### Post by skwashd on 2006-10-11
Please log this as a bug report against the package on launchpad.  

I am one of the upstream developers and we use the same scripts to build our debs, so we like them to be bug free :)

I hope you enjoy using phpGroupWare

---

### Post by backu on 2007-01-29
During the intial installation of phpGW by Apt, it makes a configuration change in Apache2, all you had to do was goto [http://yourserver/phpgroupware](http://yourserver/phpgroupware)

---

### Post by trippinnik on 2007-06-22
OK, i've got mine setup for localhost for some testing, but [http://localhost/phpgroupware/login.php](http://localhost/phpgroupware/login.php) shows a blank page.  I know apache is working, because if I go to [http://localhost/](http://localhost/) I get a file list and one directory.  I checked mysql admin and the phpgroupware table has been created, so the root password is correct.  Is there some other config I need to do?

---

