---
title: "server isnt redirecting to my second site"
date: 2008-04-08
forum: Server Platforms
---

### Post by kustomjs on 2008-04-08
Hi Guys
I need to know why my server isn't redirecting to my 2nd site.

---

### Post by tamoneya on 2008-04-08
we are going to need a lot more information than that to be able to solve your problem.

What type of server is this? http?
What are your sites? IP addresses? Networking configuration?
Did this work in the past?
What have you done to attempt to fix this?

---

### Post by kustomjs on 2008-04-08
its a small business server hosted out of my apt and I got static ip address on the server and the first site its OSC and the 2nd one im trying to setup is for a forum and what I tried to fixing it as stop apache2 and restarting apache 2.

---

### Post by tamoneya on 2008-04-08
how exactly do you see this working.  Do you want people trying to visit the OSC to go directly to the forum?  Do you want a link on the OSC that gets you to the forum?  Where do you want this link.  You should post the relevant html or php files.

---

### Post by kustomjs on 2008-04-08
see I want my customers to go the OSC but I want a link to my forum if possible
and here is my file for /etc/apache2/sites-available
NameVirtualHost *
<VirtualHost *:80>
  ServerName site1
  ServerAlias [www.site1.com](www.site1.com)
  DocumentRoot /var/www/site1.com/catalog/catalog/
  CustomLog /var/log/apache2/site1.com-access.log combined
  ErrorLog /var/log/apache2/site1.com-error.log
</VirtualHost>
<VirtualHost *:80>
ServerName site2
ServerAlias [www.site2.com](www.site2.com)
DocumentRoot /var/www/site2/forum
CustomLog /var/log/apache2/site2.com-access.log combined
ErrorLog /var/log/apache2/site2.com-error.log
</VirtualHost>

---

### Post by tamoneya on 2008-04-08
take a look at this post then.  This should solve your problems
[http://ubuntuforums.org/showthread.php?t=745511](http://ubuntuforums.org/showthread.php?t=745511)

---

### Post by kustomjs on 2008-04-08
I tried that and still getting that same error.

---

### Post by kustomjs on 2008-04-08
thanks to tamoneya I got my problem fix.

---

