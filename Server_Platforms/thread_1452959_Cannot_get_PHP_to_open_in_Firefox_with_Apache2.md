---
title: "Cannot get PHP to open in Firefox with Apache2"
date: 2010-04-12
forum: Server Platforms
---

### Post by triwing on 2010-04-12
Howdy,

I'm using Ubuntu 9.10 with Firefox 3.5.  I am trying to open a local php file in Firefox.  I already installed Apache2.  I already installed the PHP5 modules for Apache2.  I already tried restarting Apache2 and I cleared Firefox's cookies and cache.  Apache2 is currently running and PHP is in the "mods-enabled" folder.  Yet every single time I try to open a local PHP file, Firefox asks me what program I want to use to open it.

I have no idea how to proceed at this point.  I've seen similar problems posted on this board but all of the solutions have not helped.

Any help would be appreciated.

---

### Post by cdenley on 2010-04-12
I realize you already did some of these, I'm just double-checking. Post this output.
```

sudo apt-get install libapache2-mod-php5
sudo a2enmod php5
sudo /etc/init.d/apache2 restart
echo -e "<?php\necho 'it works\n';\n?>"|sudo tee /var/www/phptest.php
echo -e "GET /phptest.php HTTP/1.0\n"|nc 127.0.0.1 80

```

---

### Post by triwing on 2010-04-13
Thanks for the response, here it is:

sudo apt-get install libapache2-mod-php5
[sudo] password for kit: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libapache2-mod-php5 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

sudo a2enmod php5
Module php5 already enabled

sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                 ... waiting                                                             [ OK ]

echo -e "<?php\necho 'it works\n';\n?>"|sudo tee /var/www/phptest.php
<?php
echo 'it works
';
?>

echo -e "GET /phptest.php HTTP/1.0\n"|nc 127.0.0.1 80
HTTP/1.1 200 OK
Date: Tue, 13 Apr 2010 18:03:03 GMT
Server: Apache/2.2.12 (Ubuntu)
X-Powered-By: PHP/5.2.10-2ubuntu6
Vary: Accept-Encoding
Content-Length: 9
Connection: close
Content-Type: text/html

Afterwards I cleared Firefox's cache and still no go.

---

### Post by cdenley on 2010-04-13
Are you sure you're not missing a line of output there? In fact, I can tell you are because the response indicates there is 9 bytes of content which you did not post. Since it is only 9 bytes, it must have been "it works\n", so php is working properly.
```

echo -e "<?php\necho 'IT WORKS\nIT WORKS\nIT WORKS\n';\n?>"|sudo tee /var/www/phptest.php
echo -e "GET /phptest.php HTTP/1.0\n"|nc 127.0.0.1 80

```
```
cdenley@ubuntu:~$ echo -e "<?php\necho 'IT WORKS\nIT WORKS\nIT WORKS\n';\n?>"|sudo tee /var/www/phptest.php
<?php
echo 'IT WORKS
IT WORKS
IT WORKS
';
?>
cdenley@ubuntu:~$ echo -e "GET /phptest.php HTTP/1.0\n"|nc 127.0.0.1 80
HTTP/1.1 200 OK
Date: Tue, 13 Apr 2010 18:08:04 GMT
Server: Apache/2.2.12 (Ubuntu)
X-Powered-By: PHP/5.2.10-2ubuntu6.4
Vary: Accept-Encoding
Content-Length: 27
Connection: close
Content-Type: text/html

IT WORKS
IT WORKS
IT WORKS
cdenley@ubuntu:~$
```
Also, it is easier to read your output if you use "CODE" tags.
[NOPARSE]
```

my output here

```
[/NOPARSE]

What URL seems to not work for you?

---

### Post by s_ø on 2010-04-13
If you just open the php file directly it will not be parsed.
You need to open it in [http://localhost/phptest.php](http://localhost/phptest.php)
If its not working check the config files.
```
 nano /etc/apache2/mods-available/php5.conf
```should have something like this in it
```
<IfModule mod_php5.c>
  AddType application/x-httpd-php .php .phtml .php3
  AddType application/x-httpd-php-source .phps
</IfModule>
```

---

### Post by cdenley on 2010-04-13
> **s_ø said:**
> If you just open the php file directly it will not be parsed.
You need to open it in [http://localhost/phptest.php](http://localhost/phptest.php)
If its not working check the config files.
```
 nano /etc/apache2/mods-available/php5.conf
```should have something like this in it
```
<IfModule mod_php5.c>
  AddType application/x-httpd-php .php .phtml .php3
  AddType application/x-httpd-php-source .phps
</IfModule>
```

It is parsing that file correctly. Even with the missing line, the output he posted confirms it was parsed correctly.

---

### Post by lisati on 2010-04-13
I appreciate that the OP has already looked at the steps suggested but mention it passing: [https://help.ubuntu.com/community/ApacheMySQLPHP#Troubleshooting%20PHP%205](https://help.ubuntu.com/community/ApacheMySQLPHP#Troubleshooting%20PHP%205)

---

### Post by triwing on 2010-04-18
It's working, thanks.  The problem is that I need to open it by typing the URL in Firefox rather than trying to open the file directly in the file browser.

---

