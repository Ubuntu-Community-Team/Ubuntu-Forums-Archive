---
title: "Apache VirtualHost with dyndns and com url"
date: 2007-07-16
forum: Server Platforms
---

### Post by thedruid on 2007-07-16
Hello

i got a .com adress that i'm forwarding to a dyndns adress.. I don't have a static ip so dyndns saved the day. Now i got a [www.my-url.com](www.my-url.com) adress and to make it easy i just forward it to the my-url.dyndns.org. The problem is when i enter the [www.my-url.com](www.my-url.com) site and navigating it will start to link to my-url.dyndns.org/phpfile.php .. 

As i understand you can solve that problem by using vhost.Tried to add a virutal host but i just get this error...

[Mon Jul 16 20:25:07 2007] [error] VirtualHost *:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results


<VirtualHost *:80>
  ServerName my-url.com
  ServerAlias [www.my-url.com](www.my-url.com)
  DocumentRoot /var/www/
  CustomLog /var/log/apache2/myurl.com-access.log combined
  ErrorLog /var/log/apache2/myrl.com-error.log
</VirtualHost>

---

### Post by jmazzarelli on 2007-07-16
It looks like it is complaining that somewhere you have <VirtualHost *:80> and <VirtualHost xxx.xxx.xxx.xxx:80> See if you have another virtual host defined (maybe the default one) with an actual ip, and change that one to a * too

---

### Post by primski on 2007-07-17
or just delete the ':80' part.

---

