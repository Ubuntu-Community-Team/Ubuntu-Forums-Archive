---
title: "How to make subdomain ?"
date: 2008-09-07
forum: Server Platforms
---

### Post by emadwilliam on 2008-09-07
How to make a subdomain for my domain name ?
Like making members.myname.com ...

---

### Post by lazyart on 2008-09-07
Please use the search function.  [This was just answered yesterday]("http://ubuntuforums.org/showthread.php?t=912884").

---

### Post by emadwilliam on 2008-09-07
Sorry, but what is vHost ?

---

### Post by mbeach on 2008-09-07
vhost refers to a virtual host.  I won't go into detail, but basically it allows you to host multiple independent sites using your one ip address, one server.  More here: [http://httpd.apache.org/docs/2.0/vhosts/](http://httpd.apache.org/docs/2.0/vhosts/)

You can create those vhost files in /etc/apache2/sites-available.  Copy the default file there, edit as needed, enable with "sudo a2ensite yourfilename", then reload apache (sudo /etc/init.d/apache2 reload).

---

