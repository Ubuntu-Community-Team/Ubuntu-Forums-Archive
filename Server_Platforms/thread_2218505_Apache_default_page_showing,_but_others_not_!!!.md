---
title: "Apache default page showing, but others not !!!"
date: 2014-04-21
forum: Server Platforms
---

### Post by uzumakifahim on 2014-04-21
Hi,

I'm using Ubuntu 14.04. Have installed LAMP server using this tutorial [http://www.n00bsonubuntu.net/content/how-to-install-lamp-server-on-ubuntu-13-04/](http://www.n00bsonubuntu.net/content/how-to-install-lamp-server-on-ubuntu-13-04/)

Installation was successful. Even "Apache2 Ubuntu Default Page" is showing accurately. I can access PhpMyAdmin perfectly. My problem is that, browser can't show any files (php/html), which I'm keeping in the /var/www/ directory.

To test the PHP version and details, I've created a file named "testing.php". Keep that file in the www directory, but my browser is showing "NOT FOUND" !!!

Please check the attached screen shot. This is a really weird problem.

Please help me experts. Thanks in advance.

---

### Post by Doug S on 2014-04-21
The default document root location is now /var/www/html whereas it used to be /var/www.
Please note that documenting this change missed the deadline for [the 14.04 Ubuntu Serverguide]("https://help.ubuntu.com/14.04/index.html").

Edit: see also the [bug report]("https://bugs.launchpad.net/serverguide/+bug/1305313").

---

### Post by uzumakifahim on 2014-04-21
> **Doug S said:**
> The default document root location is now /var/www/html whereas it used to be /var/www.
Please note that documenting this change missed the deadline for [the 14.04 Ubuntu Serverguide]("https://help.ubuntu.com/14.04/index.html").

Edit: see also the [bug report]("https://bugs.launchpad.net/serverguide/+bug/1305313").

Thanks for your quick and great reply. Unfortunately, I can access the files in the /var/www/html location. please check screen shot that, I've tried to access the *index.html* file in the /var/www/html location (index.html file was there from the beginning), but it's showing the same message.

---

### Post by Doug S on 2014-04-21
> **uzumakifahim said:**
> Thanks for your quick and great reply. Unfortunately, I can access the files in the /var/www/html location. please check screen shot that, I've tried to access the *index.html* file in the /var/www/html location (index.html file was there from the beginning), but it's showing the same message.In your new screen shot you seem to be trying to access /var/www/html/html/index.html. So no, the file would not be found. In your first set of screen shots, 2 of 2, you are accessing the file /var/www/html/index.html. You should find more information in the /var/log/apache2/error.log file.

---

### Post by uzumakifahim on 2014-04-21
> **Doug S said:**
> In your new screen shot you seem to be trying to access /var/www/html/html/index.html. So no, the file would not be found. In your first set of screen shots, 2 of 2, you are accessing the file /var/www/html/index.html. You should find more information in the /var/log/apache2/error.log file.

PERFECT!!! Great answer!!! My problem is solved!!! Really thanks for this solution. Marking this post as SOLVED.

---

