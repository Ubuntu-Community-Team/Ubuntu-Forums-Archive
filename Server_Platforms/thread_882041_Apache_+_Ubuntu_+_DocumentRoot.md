---
title: "Apache + Ubuntu + DocumentRoot"
date: 2008-08-06
forum: Server Platforms
---

### Post by rauldinho on 2008-08-06
Hi, i have a Web Server and i want that when i type *[http://localhost](http://localhost)* in a browser in the server, the result page is one of my sites in the WWW folder, in other words, i want my localhost to be a diferent one from the default page that Apache uses. So i went and edited the */etc/apache2/httpd.conf* file and wrote *DocumentRoot "/var/www/my_folde"* (By the way, the *httpd.conf* file was empty, it didn't have anything inside). After i wrote the line, i restarted apache */etc/init.d/apache2 restart*. But when i try localhost in my browser it still gives me the default page from apache, the one that says "it works!". Can anyone help me on this? Thanks for any help i may get.

---

### Post by cpetercarter on 2008-08-06
Have a look at [https://help.ubuntu.com/community/ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP"). The section on Virtual Hosts explains how to do what you want.

---

### Post by mbeach on 2008-08-07
I wish the authors there chose something other than public_html in a users home directory, as that is the default for the userdir module.  

Basically, you want to get rid of that DocumentRoot in httpd.conf and change the /etc/apache2/sites-available/default file instead.  The httpd.conf file is only there for backwards compatibility - for general settings use /etc/apache2/apache2.conf.  In your particular case though, the "default" file mentioned is where you want to make that change, then run ```
 sudo /etc/init.d/apache2 reload
```

good luck,
mb

---

### Post by ryazkhan on 2008-08-08
> **rauldinho said:**
> Hi, i have a Web Server and i want that when i type *[http://blockedcontent](http://blockedcontent)* in a browser in the server, the result page is one of my sites in the WWW folder, in other words, i want my blockedcontent to be a diferent one from the default page that Apache uses. So i went and edited the */etc/apache2/httpd.conf* file and wrote *DocumentRoot "/var/www/my_folde"* (By the way, the *httpd.conf* file was empty, it didn't have anything inside). After i wrote the line, i restarted apache */etc/init.d/apache2 restart*. But when i try blockedcontent in my browser it still gives me the default page from apache, the one that says "it works!". Can anyone help me on this? Thanks for any help i may get.

That is not where you make changes. You just told it what is the name of your apache server, that is not what you looking for, you looking for to change the path to file served when you browse your apache server. Go to */etc/apache2/sites-enabled/*or */etc/apache2/sites-available/* they are pretty much same. Now you will see all of your sites you have but in your case you want to edit default so edit it *nano default* and change DocumentRoot, save the changes and restart apache2 and bingo!

---

