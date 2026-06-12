---
title: "Website Ubuntu Server"
date: 2011-06-13
forum: Server Platforms
---

### Post by ChosenOreo on 2011-06-13
EVERY article I have read has confused me on how to setup a website with Apache and Ubuntu 10.04. By setting up a website, I mean making my .co.cc domain name point to my server box and the /var/www directory inside it. And also - With DNS it has two different IP addresses. How would I set that up on the box too?
Thanks!
Oreo

---

### Post by cherva on 2011-06-13
First make your domain name point to your boxs ip address. (usually this is done in the control panel at the site you registered your domain ) 
Then edit the /etc/apache2/apache2.conf file and append at the end of the file something like this:

```
<VirtualHost *:80>
DocumentRoot /var/www
ServerName YOURDOMAIN.co.cc
ServerAdmin YOURE-MAIL@MAIL.MAIL
</VirtualHost>
```

You can put your site wherever you want. I put mine at /home/site_name/html 

Then restart apache 
```
/etc/init.d/apache2 restart
```

NOTE: When you change the ip address that your domain name resolves to, you have to wait a day or two to refresh all DNS servers around the world (including yours) so be patient. ;)

---

### Post by pcarlos853 on 2011-06-14
You need to have a static IP or use a free service such as no-ip or dyndns.

---

