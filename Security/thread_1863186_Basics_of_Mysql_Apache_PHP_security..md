---
title: "Basics of Mysql Apache PHP security."
date: 2011-10-17
forum: Security
---

### Post by jaho22 on 2011-10-17
I have Mysql Apache PHP installed on Ubuntu Desktop edition as a server.

What are the basic things i need to setup for security for these programs.

What ports are in danger on default setups on these tree.

---

### Post by Dangertux on 2011-10-17
When you start getting into LAMP security it extends a lot farther than traditional "network" security, ie no longer just in terms of ports and buffer overflows.

You start running into the security of your web applications themselves. You have all sorts of issues like SQL injection, XSS, CSRF, remote file upload/inclusion, directory traversal etc etc..

The best all around solution , unless you are writing your web apps yourself (IE : you can fix vulnerable code) is Mod-Security for Apache.

To install the current version of Mod-Security on Ubuntu 10.04 Apache2 with the latest rules set I have written a procedure here : [http://dangertux.wordpress.com/tutorials/ubuntu-10-04-apache-current-mod-security/](http://dangertux.wordpress.com/tutorials/ubuntu-10-04-apache-current-mod-security/)

Additionally there are things you can do to harden your MySQL and PHP installations. For instance disabling certain functions in your php.ini (passthru , system, exec, etc) There is more about that here : [http://dangertux.wordpress.com/old-content/reasonably-secure-ubuntu-homesmall-business-server-tutorial/#mod4](http://dangertux.wordpress.com/old-content/reasonably-secure-ubuntu-homesmall-business-server-tutorial/#mod4)

Hope this is helpful.

---

### Post by Lars Noodén on 2011-10-17
If you're writing your own PHP scripts, then always validate data on the way in.  Some languages can track variable [taint](http://perldoc.perl.org/perlsec.html#Taint-mode) nearly automatically.  When writing data, always escape it.  When working with the database, always [escape](http://www.php.net/manual/en/function.mysql-escape-string.php) the data and be sure to use prepare-execute statements with place holders.  

As far as ports to watch out for, trouble will come to ports 80 and 443.  ;)

---

### Post by Lars Noodén on 2011-10-17
If you're writing your own PHP scripts, then always validate data on the way in.  Some languages can track variable [taint](http://perldoc.perl.org/perlsec.html#Taint-mode) nearly automatically.  When writing data, always escape it.  When working with the database, always [escape](http://www.php.net/manual/en/function.mysql-real-escape-string.php) the data and be sure to use [prepare-execute](http://dev.mysql.com/doc/refman/5.0/en/sql-syntax-prepared-statements.html) statements with place holders.  

As far as ports to watch out for, trouble will come to ports 80 and 443.  ;)

---

### Post by jmcgovern on 2011-10-17
using user supplied input on multiple different pages, ie a multi-step process (hidden fields, URL parameters, etc)?  Re-Validate at EVERY load. Mod-Security is a must even if you're writing from scratch, and, for God's sake, *make sure you're up to date!* Read up on injection attacks of all kinds, XSS, traversal, and everything else Dangertux mentioned.

---

