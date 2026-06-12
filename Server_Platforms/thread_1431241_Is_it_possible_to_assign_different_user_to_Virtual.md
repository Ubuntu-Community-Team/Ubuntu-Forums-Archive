---
title: "Is it possible to assign different user to VirtualHosts?"
date: 2010-03-16
forum: Server Platforms
---

### Post by gzbadboy on 2010-03-16
I am new with Linux but really be interested in it,
I would like to ask that if it is possible to make each VirtualHost only controllable by a specific and different user ?
If so , how to ?

Thank you :)

---

### Post by bodhi.zazen on 2010-03-16
You may do this in a variety of ways. 

1. Define the root directory 

[http://www.zaphu.com/2007/08/21/ubuntu-lamp-server-guide-configure-apache-mysql-and-cgi-bin/](http://www.zaphu.com/2007/08/21/ubuntu-lamp-server-guide-configure-apache-mysql-and-cgi-bin/)

[https://help.ubuntu.com/community/ApacheMySQLPHP#Virtual%20Hosts](https://help.ubuntu.com/community/ApacheMySQLPHP#Virtual%20Hosts)

2. If you have multiple users you may automate this with userdir

[http://www.ivankristianto.com/operating-system/ubuntu-linux/howto-make-apache-user-directory-on-ubuntu/1019/](http://www.ivankristianto.com/operating-system/ubuntu-linux/howto-make-apache-user-directory-on-ubuntu/1019/)

---

### Post by gzbadboy on 2010-03-16
> **bodhi.zazen said:**
> You may do this in a variety of ways. 

1. Define the root directory 

[http://www.zaphu.com/2007/08/21/ubuntu-lamp-server-guide-configure-apache-mysql-and-cgi-bin/](http://www.zaphu.com/2007/08/21/ubuntu-lamp-server-guide-configure-apache-mysql-and-cgi-bin/)

[https://help.ubuntu.com/community/ApacheMySQLPHP#Virtual%20Hosts](https://help.ubuntu.com/community/ApacheMySQLPHP#Virtual%20Hosts)

2. If you have multiple users you may automate this with userdir

[http://www.ivankristianto.com/operating-system/ubuntu-linux/howto-make-apache-user-directory-on-ubuntu/1019/](http://www.ivankristianto.com/operating-system/ubuntu-linux/howto-make-apache-user-directory-on-ubuntu/1019/)


I have done this with apache2-mpm-itk
[http://httpd.apache.org/docs/2.0/mod/perchild.html](http://httpd.apache.org/docs/2.0/mod/perchild.html)

Thank you anyway ;)

---

### Post by KB1JWQ on 2010-03-16
That's the beauty of *nix; there's almost always multiple ways to achieve the same goal.

Glad you got it sorted. :-)

---

