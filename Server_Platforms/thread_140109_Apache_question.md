---
title: "Apache question"
date: 2006-03-05
forum: Server Platforms
---

### Post by brickbat on 2006-03-05
Hi,  I am trying to run Apache and I keep getting this error;

[Sun Mar 05 20:30:06 2006] [error] VirtualHost *:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
(98)Address already in use: make_sock: could not bind to address [::]:80
no listening sockets available, shutting down
Unable to open logs


Any suggestions about where my problem is and howe I can fix it?

Thanks,
bb

---

### Post by MJN on 2006-03-06
Post the contents of your /etc/apache2/sites-available/ folder...
 
(It'll likely be due to your VirtualHost config directives contained therein)
 
Mathew

---

### Post by brickbat on 2006-03-06
the only item listed is

default

In my httpd.conf I have this;

<VirtualHost *:80>
  ServerName apex
  DocumentRoot "/home/brickbat/sfprojects/Apex/web"
  DirectoryIndex index.php
  Alias /sf /usr/share/php/data/symfony/web/sf

  <Directory "/home/brickbat/sfprojects/Apex/web">
   AllowOverride All
  </Directory>
</VirtualHost>


I have checked...all the directories exist.  This was a cut and paste job from the Symfony website.

---

### Post by brickbat on 2006-03-06
ok.  here is what I did.  I put a comment on the line

Server apex

and it fixed it.  Do I need to tell it that the name of the server is apex.  If it is preferable to do this, then how would I do it?

Thanks for your questions.  They pointed me in the right direction.

---

### Post by MJN on 2006-03-06
What's the content of 'default'?

Your virtualhost config ought to be in there (and not httpd.conf) now that Ubuntu (being Debian based) is using a modularised configuration approach to Apache.

If you don't follow this modularisation you'll get may get undesired results from conflicting statements in httpd.conf and default.

If the above describes your situation, move the config you quoted into /etc/apache2/sites-available/default as appropriate (it all needs going inside a <virtualhost> directive).

Then report back... :-)

Mathew

P.S. You also need a **NameVirtualHost *:80** directive too (not inside a <virtualhost> directive) inside either /etc/apache2/apache2.conf or (and probably there by default) inside /etc/apache2/sites-available/default.

---

