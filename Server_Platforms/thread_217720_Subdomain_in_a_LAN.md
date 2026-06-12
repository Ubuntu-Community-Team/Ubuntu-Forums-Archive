---
title: "Subdomain in a LAN"
date: 2006-07-17
forum: Server Platforms
---

### Post by Jates on 2006-07-17
I have a lan where I edited /etc/host in all computers of my lan to simulate a  dns  and works fine.
The problem is that I can`t create a subdomain.
I want the subdomain in the same computer but in other port.

I did 
#mkdir /var/www/sub
#vi /var/www/sub/index.php
<?php
phpinfo();
?>
#vi /etc/apache2/sites-available/sub
<VirtualHost 192.168.1.68:8083>

ServerAdmin webmaster@local
ServerName 192.168.1.68:8083
ServerAlias sub.server.mynet

DocumentRoot /var/www/sub

</VirtualHost>

#vi /etc/apache2/ports
Listen 8083

#a2ensites sub

#/etc/init.d/apache2 reload

I think with that must works but it doesnt.
I have read a lot and make many changes tried many ways but nothing works.

When I type [http://server.mynet](http://server.mynet) in firefox
I get the page I want.

But if I type [http://sub.server.mynet](http://sub.server.mynet) in firefox
I get the same page.

Now if I type [http://sub.server.mynet:8083](http://sub.server.mynet:8083) or  [http://server.mynet:8083](http://server.mynet:8083) in firefox
I get the page of sub.
What I need is type [http://sub.server.mynet](http://sub.server.mynet) in firefox and get the page of my subdomain.

Advancing thanks

---

