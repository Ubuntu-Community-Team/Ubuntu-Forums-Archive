---
title: "Apache2 .htaccess files"
date: 2005-03-23
forum: Server Platforms
---

### Post by Ric_ on 2005-03-23
Hi all,

I have a default apache2 install via apt-get. This server is just for my own rapid development.

changed the 000-default site to

AllowOverride All

created a .htaccess file in /var/www

if i add a <Directory /var/www/> or <File ...> type element to the .htaccess i get a Internal server error 500.

the /var/log/apache2/error.log gives this little gem

[Wed Mar 23 11:39:47 2005] [alert] [client 127.0.0.1] /var/www/apache2-default/.htaccess: <Directory not allowed here

What am I missing???

Any help greatly apprichated.

---

### Post by jdonnell on 2005-03-23
I don't think you can put <Directory> directives in a .htaccess. The .htaccess is in the directory it affects :)

---

