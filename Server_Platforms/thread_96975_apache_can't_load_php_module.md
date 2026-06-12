---
title: "apache can't load php module"
date: 2005-11-30
forum: Server Platforms
---

### Post by akurashy on 2005-11-30
david@akulinux:/usr/local/apache2/bin$ sudo ./apachectl restart
Syntax error on line 232 of /usr/local/apache2/conf/httpd.conf:
Cannot load /usr/local/apache2/modules/libphp5.so into server: /usr/local/apache2/modules/libphp5.so: undefined symbol: zend_ini_string
david@akulinux:/usr/local/apache2/bin$

I really can't say for sure what's that, i mean its the first time i get something like that from it =/, anyone knows how to fix it?

---

### Post by J.C. Denton on 2005-11-30
Interesting.  Can you post line 232 of your httpd.conf, and the output of:
```
dpkg --get-selections | grep php5
```

---

### Post by akurashy on 2005-11-30
line 232 is LoadModule php5_module        modules/libphp5.so

and well i'm using a custom build, i compiled apache 2.0.55 and compiled php5.1.1 

david@akulinux:~/Files/php-5.1.1$ dpkg --get-selections | grep php5
libapache2-mod-php5                             deinstall
php5-cgi                                        deinstall
php5-common                                     install
php5-mysql                                      deinstall
php5-xsl                                        deinstall

---

### Post by J.C. Denton on 2005-11-30
[QUOTE=akurashy]line 232 is LoadModule php5_module        modules/libphp5.so

and well i'm using a custom build, i compiled apache 2.0.55 and compiled php5.1.1 

david@akulinux:~/Files/php-5.1.1$ dpkg --get-selections | grep php5
libapache2-mod-php5                             deinstall
php5-cgi                                        deinstall
php5-common                                     install
php5-mysql                                      deinstall
php5-xsl                                        deinstall[/QUOTE]
Did it work before? What ./configure options did you use with PHP, and Apache?

---

### Post by akurashy on 2005-11-30
in apache i used

./configure --enable-so

and in php i used hmm

./configure --with-apxs2=path --with-mysql --enable-gd --with-gd --with-xslt --with-xml
i think that were the flags, i can't remember well

---

### Post by akurashy on 2005-12-01
[J.C. Denton]("http://ubuntuforums.org/member.php?u=54254") , thanks a lot lot lot lot for helping me out!

---

### Post by J.C. Denton on 2005-12-02
For those who are curious how we fixed this.  We ended up defining the correct --with-apxs2 path, as well as adding --with-config-file-path, and --prefix to the PHP ./configure.

---

### Post by goneskiing on 2005-12-02
Could you write a few lines to show all the details of how you compiled to get this to work - it could really help a lot of us that have had no success (and keep some of us from moving distros).  I see the the apache configure above but not the php, etc.  Thanks.

---

### Post by akurashy on 2005-12-02
I will write one soon, unless J.C. is planning to do one in mind, but whatever works.

---

### Post by goneskiing on 2005-12-02
I realize this is strictly voluntary, but I hope it can be real soon, like in the next few hours :)    The apache/php problems have cost us almost two weeks and we can't wait any longer and the Fedora rpm CD's are sitting on my desk.   But if I can avoid the conversion hassle I would be most grateful.

---

### Post by akurashy on 2005-12-02
goneskiing: [http://ubuntuforums.org/showthread.php?t=98215](http://ubuntuforums.org/showthread.php?t=98215)

ENjoy :)

---

