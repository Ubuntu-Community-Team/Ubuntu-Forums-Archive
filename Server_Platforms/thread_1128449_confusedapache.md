---
title: "confused/apache"
date: 2009-04-17
forum: Server Platforms
---

### Post by macjak on 2009-04-17
I'm trying to emulate a lamp stack I have in fedora using 8.04 lts. For one thing the httpd.conf file is empty. I have  starting using a tutorial in LXF Magazine jan 09 and moved my website to /var/www/localhost/htdocs. When I try to chown the website to apache it says there is no group apache. Do I need to upgrade this default apache installation somehow? The sites enabled and sites available configs are there but they are bare bones. I do get the "It Works" default page with the index file in /var/www . Thanks New to ubuntu

---

### Post by sp0nge on 2009-04-17
hello, 

I'm still experimenting with apache, so I may be off base, but I'm pretty sure I can help! Ubuntu uses /etc/apache2/apache.conf in lieu of httpd.conf. 

If you want to change the default document root you need to edit the /etc/apache2/sites-available/default file and look for this line “DocumentRoot /var/www/” here you can change where ever you want to change.For example if you want to change /home/www the above line looks like this “DocumentRoot /home/www/”.

I hope this helps.

---

### Post by spiderbatdad on 2009-04-17
I'll try to help. The ubuntu distribution uses apache2.conf for the default configuration. You should however make any changes in httpd.conf...which will override anything in apache2.conf
htdocs in ubuntu generally are owned by www-data and belong to the same group.

---

### Post by cdenley on 2009-04-17
> **spiderbatdad said:**
> I'll try to help. The ubuntu distribution uses apache2.conf for the default configuration. You should however make any changes in httpd.conf...which will override anything in apache2.conf
htdocs in ubuntu generally are owned by www-data and belong to the same group.

I don't think httpd.conf is supposed to be used at all. It used to have nothing but comments indicating it was only there in case something expected it, and it should not be used.

[https://help.ubuntu.com/community/ApacheMySQLPHP#Installing%20Apache%202](https://help.ubuntu.com/community/ApacheMySQLPHP#Installing%20Apache%202)

---

### Post by spiderbatdad on 2009-04-18
> **cdenley said:**
> I don't think httpd.conf is supposed to be used at all. It used to have nothing but comments indicating it was only there in case something expected it, and it should not be used.

[https://help.ubuntu.com/community/ApacheMySQLPHP#Installing%20Apache%202](https://help.ubuntu.com/community/ApacheMySQLPHP#Installing%20Apache%202)

Community docs are very useful and valid. Not always written by those who thoroughly understand official documentation. Which can be found here: [http://httpd.apache.org/docs/2.2/](http://httpd.apache.org/docs/2.2/)

There used to be some comments in ubuntu's apache version, explaining to edit httpd.conf rather than apache2.conf. Try it yourself.

---

### Post by macjak on 2009-04-18
Thanks everone! especially for the links on the virtual apache which is what the magazine is basically describing. Now my only confusion is why apache is owned by root and there is no user:group apache. However I know the the ubuntu apache 2.2.8 I have is a re-designed version with many changes so is this supposed to be this way as apposed to fedora and the LXF article mentioned above which have User:Group apache?

---

### Post by spiderbatdad on 2009-04-18
[http://www.linuxsecurity.com/content/view/133913/171/](http://www.linuxsecurity.com/content/view/133913/171/)

I believe you should find apache running as www-data
```
ps aux | grep apache2
```
The user apache runs as is defined in apache2.conf, but if you read the file, you'll see it is a variable set in /etc/apache2/envvars

---

