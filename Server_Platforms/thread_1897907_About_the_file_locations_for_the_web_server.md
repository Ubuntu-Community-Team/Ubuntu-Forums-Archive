---
title: "About the file locations for the web server"
date: 2011-12-20
forum: Server Platforms
---

### Post by anon0 on 2011-12-20
Apparently if I try to access the web server locally, my browser will display the index.html file located at /var/www/index.html 

But if I try to access it over the internet, the browser displays the index.html file located at /var/lib/tomcat6/webapps/ROOT/index.html 

Can anyone explain the purpose behind this? Thanks.

Edit: I just found out that PHP is not working properly in the tomcat6 folder. For example, calling "<?php phpinfo(); ?>" works under /var/www/ when accessed locally, but doesn't work under /var/lib/tomcat6/webapps/ROOT/ when accessed over the web. (reference: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP) )


Update: I kind of figured it out. I was using a custom port which was automatically directed to tomcat6. So I had to change the port and specify it for Apache by editing the files:
/etc/apache2/ports.conf
/etc/apache2/sites-enabled/000-default

---

