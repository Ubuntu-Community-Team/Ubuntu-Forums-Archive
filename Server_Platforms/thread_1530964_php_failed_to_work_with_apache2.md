---
title: "php failed to work with apache2"
date: 2010-07-14
forum: Server Platforms
---

### Post by shva on 2010-07-14
Hi everyone, 


I installed apache2 in Ubuntu Server 8.04, and now want it to work with php. I installed libapache2-mod-php5 and php5-cgi, enabled both php5 and cgi modules in apache, and set cgi.fix_pathinfo = 1 in /etc/php5/cgi/php.ini as indicated [here]("http://nanotux.com/blog/the-ultimate-server/3/"). When I visited a php file after these steps, the server still told me to download this "application/x-httpd-php" file instead of parsing it. What was I missing? Thanks.

---

### Post by shva on 2010-07-14
Never mind... I just figure it out by adding 
 ```
   <IfModule mod_php5.c>
        DirectoryIndex index.php index.html
    </IfModule>
    <IfModule mod_php5.c>
        AddType application/x-httpd-php .php
        AddType application/x-httpd-php-source .phps
    </IfModule>

```

to httpd.conf

---

### Post by ruffEdgz on 2010-07-14
You actually don't need to have two <IfModule ...> and you can consolidate one with the other so it should read:
```

<IfModule mod_php5.c>
        DirectoryIndex index.php index.html
        AddType application/x-httpd-php .php
        AddType application/x-httpd-php-source .phps
</IfModule>

```

Glad you found and solved it yourself :D

---

### Post by cdenley on 2010-07-14
The correct way to enable the module in ubuntu is:
```

sudo a2enmod php5
sudo /etc/init.d/apache2 restart

```
You probably don't need "php5-cgi".

---

### Post by cavh on 2010-07-15
I know this has been marked as solved and it doesn't refer in any way to MySQL, but for people who come across this thread in future - I find the easiest way to set up a LAMP server is to 

```
sudo tasksel
```

and choose the LAMP option.

---

