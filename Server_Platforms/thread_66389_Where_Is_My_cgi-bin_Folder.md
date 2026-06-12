---
title: "Where Is My cgi-bin Folder?"
date: 2005-09-17
forum: Server Platforms
---

### Post by limva on 2005-09-17
I've just installed Apache2.  My website is in /var/www and my cgi-bin is in /var/www/cgi-bin.

I can access my webpages ok, but when I execute my cgi scripts, I get an "Internal Server Error" page.  The error log shows "No such file or directory" error.

In the 000-default file:

 DocumentRoot /var/www
 <Directory />
  Options FollowSymLinks
  AllowOverride None
 </Directory>
 <Directory "/var/www">
  Options Indexes FollowSymLinks MultiViews
  AllowOverride None
  Order allow,deny
  allow from all
 </Directory>

 ScriptAlias /cgi-bin/ /var/www/cgi-bin/
 <Directory "/var/www/cgi-bin">
  AllowOverride None
  Options ExecCGI -MultiViews +SymLinksIfOwnerMatch
  Order allow,deny
  Allow from all
 </Directory>

I made sure that my cgi script file has a chmod value of 755.

What else can I do to find the problem?

---

### Post by LordHunter317 on 2005-09-17
What are the permissions on /var/www/cgi-bin?

---

### Post by limva on 2005-09-17
The cgi-bin folder also has 755 (rwxrwxrwx).

---

