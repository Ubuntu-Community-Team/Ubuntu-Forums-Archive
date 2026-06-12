---
title: "PHP Pulls Apache as a Dependency, and I don't want Apache..."
date: 2009-12-14
forum: Server Platforms
---

### Post by crazydrclaw on 2009-12-14
Hey everyone.  I'm trying to install PHP and Lighttpd.  Unfortunately, PHP automatically pulls in Apache, and I don't want Apache.  How can I install the php5 package without pulling in Apache as a dependency?

Thanks!

James

---

### Post by toddedw on 2009-12-14
PHP works with Lighttpd through Fast CGI so you'll need the php5-cgi package as opposed to the main php5 package. 

This tutorial explains it better than I can in my limited time: 
[http://www.ubuntugeek.com/lighttpd-webserver-setup-with-php5-and-mysql-support.html](http://www.ubuntugeek.com/lighttpd-webserver-setup-with-php5-and-mysql-support.html)

---

