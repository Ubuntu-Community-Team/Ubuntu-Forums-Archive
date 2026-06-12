---
title: "XAMPP, Apache, MySQL Problem"
date: 2009-02-21
forum: Server Platforms
---

### Post by Will_00 on 2009-02-21
I recently installed and was running XAMPP on Ubuntu 8.10 fine, until I attempted to install some other web server. Apparently they have interfered with each other and now I am unable to correctly load XAMPP in localhost or the mysql server.

I have tried multiple things (including restarting XAMPP, of course), yet nothing seems to work. Is there any way I could remove everything related to mysql, php, xampp, apache, etc. and reinstall XAMPP?

---

### Post by Iowan on 2009-02-22
Did you load XAMPP (and/or the other server) as a package?  I presume there should be a "remove" or "un-install" option on the package manager.

---

### Post by Will_00 on 2009-02-22
Well, I believe I got it fixed. I am simply using Apache now instead of XAMPP. I am unable to use PHPMyAdmin, though, it is not necessary.

---

### Post by dmizer on 2009-02-22
Moved to server platforms, you should get more specific help here.

---

### Post by hankinator on 2009-02-22
If you installed it to the right directory this should clear it.


```
rm -rf /opt/lampp 
```


Just so I have proof so I don't get banned for having a remove command.

[http://www.apachefriends.org/en/xampp-linux.html](http://www.apachefriends.org/en/xampp-linux.html)

go to the bottom of the page.

---

