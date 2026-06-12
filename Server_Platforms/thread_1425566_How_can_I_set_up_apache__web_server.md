---
title: "How can I set up apache  web server"
date: 2010-03-09
forum: Server Platforms
---

### Post by hoboy on 2010-03-09
I have installed XAMPP on my a computer, and I have developed a website 
how can I configure xampp to deploy the website ?
I have also heard of httpd where is it on xampp ?
I want to set up apache server and deploy my web site...
I just don't know how to do this.

---

### Post by mavl4219 on 2010-03-09
Your story is a bit confusing...

XAMPP is a complete solution containing: Apache, PHP, MySQL and Perl.

I haven't used XAMPP before (i allways setup my own development environment), but if you put files to /var/www (on Linux), then web server should serve your files if you request [http://localhost](http://localhost) from your web browser.

---

### Post by NullHead on 2010-03-09
Ideally, you'd want to use a LAMP server, (Linux, apache, mysql, php).```
sudo tasksel install lamp-server
```

Place your web documents in /var/www, access your mysqldb with phpMyAdmin```
sudo apt-get install phpmyadimn
```[http://yoursite.com/phpMyAdmin](http://yoursite.com/phpMyAdmin)

Depending on the configuration of phpymadmin, the url might be [http://yoursite.com/php**m**y**a**dmin](http://yoursite.com/phpmyadmin) or [http://yoursite.com/php**M**y**A**dmin](http://yoursite.com/phpMyAdmin)

---

