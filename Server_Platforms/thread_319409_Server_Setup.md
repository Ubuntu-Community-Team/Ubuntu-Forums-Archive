---
title: "Server Setup"
date: 2006-12-15
forum: Server Platforms
---

### Post by rado_london on 2006-12-15
Hello people.
I just installed apache2, mysql and PHP5. I decided to install Moodle so me and my mates can use it to share data for our courses.
Everything went perfectly smooth. Now when I type in [http://localhost](http://localhost) the website appears just fine. 
But then I tried to access it using my ip address ([http://82.27.199.134](http://82.27.199.134)) from my brothers pc and didnt get anything. I did access it when I did [http://192.168.0.2](http://192.168.0.2) as this is my local IP address.
So here is the situation on my LAN. DHCP LAN with 3 pcs behind router. MY ISP is NTL. 
I just want to know is everything ok with this setup in order to have server on it?

Cheers

---

### Post by tturrisi on 2006-12-15
Use router port-forwarding to forward port 80 to the lan ip of the server.  If no joy, then your isp blocks port 80, in which case you have to config apache to listen on a different port, such as 8080.  The apache file to edit is: /etc/apache2/ports.conf  change from Listen 80 to Listen 8080.  You must restart apache after making changes to the configs: ~# /etc/init.d/apache2 restart

---

### Post by rado_london on 2006-12-15
> **tturrisi said:**
> Use router port-forwarding to forward port 80 to the lan ip of the server.  If no joy, then your isp blocks port 80, in which case you have to config apache to listen on a different port, such as 8080.  The apache file to edit is: /etc/apache2/ports.conf  change from Listen 80 to Listen 8080.  You must restart apache after making changes to the configs: ~# /etc/init.d/apache2 restart

Worked as a charm when I forwarded port 80. Thanks a lot. I even go .TK domain assigned to my IP:)

---

### Post by tturrisi on 2006-12-15
Glad it's working.
Now, you need to config apache for that ip address instead of localhost because all the auto-generated links on the pages are [http://localhost](http://localhost), which will cause links to breal in any browser other than the server browser.

---

### Post by rado_london on 2006-12-15
OK I just restarted and tried to see if everything loads on boot. Unfortunaley when I tried localhost I ened up with the following:
```
Error: Database connection failed.

It is possible that the database is overloaded or otherwise not running properly.

The site administrator should also check that the database details have been correctly specified in config.php
```

Any ideas how to run mysql on boot?

---

### Post by tturrisi on 2006-12-15
It does load at boot.  That message refers to some 3rd party php application you are using.  Check its config.php.  You may also have to port forward port 3306 (mysql) & port 21 (ftp).  Your router shows FTP exists on the server but port 21 is closed.

---

### Post by rado_london on 2006-12-16
> **tturrisi said:**
> It does load at boot.  That message refers to some 3rd party php application you are using.  Check its config.php.  You may also have to port forward port 3306 (mysql) & port 21 (ftp).  Your router shows FTP exists on the server but port 21 is closed.

I did this but still get the error. I suspect it is the config.php file but I dont have knowledge of PHP at all. Any ideas?

---

### Post by digen on 2006-12-16
Can you post the config.php the relevant Database details like :

Database username
Database password for that user
Host

Make sure your Mysql server is running:
#mysql -u root -p

---

### Post by rado_london on 2006-12-16
> **digen said:**
> Can you post the config.php the relevant Database details like :

Database username
Database password for that user
Host

Make sure your Mysql server is running:
#mysql -u root -p

I tried the command you suggested and here is the output:
```
rado@ubuntu:~$ mysql -u root -p
Enter password: 
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

```

Here is the config.php file:
[PHP]<?php  /// Moodle Configuration File 

unset($CFG);

$CFG->dbtype    = 'mysql';
$CFG->dbhost    = 'localhost';
$CFG->dbname    = 'moodle';
$CFG->dbuser    = 'moodleuser';
$CFG->dbpass    = 'yourpassword';
$CFG->dbpersist =  false;
$CFG->prefix    = 'mdl_';

$CFG->wwwroot   = 'http://82.27.199.134';
$CFG->dirroot   = '/var/www';
$CFG->dataroot  = '/home/rado/moodledata';
$CFG->admin     = 'admin';

$CFG->directorypermissions = 00777;  // try 02777 on a server in Safe Mode

$CFG->unicodedb = true;  // Database is utf8

require_once("$CFG->dirroot/lib/setup.php");
// MAKE SURE WHEN YOU EDIT THIS FILE THAT THERE ARE NO SPACES, BLANK LINES,
// RETURNS, OR ANYTHING ELSE AFTER THE TWO CHARACTERS ON THE NEXT LINE.
?>
[/PHP]

Hope this helps you to help me:)

---

### Post by reenyg on 2006-12-18
> **rado_london said:**
> 

Here is the config.php file:
[PHP]<?php  /// Moodle Configuration File 

unset($CFG);

$CFG->dbtype    = 'mysql';
$CFG->dbhost    = 'localhost';
$CFG->dbname    = 'moodle';
$CFG->dbuser    = 'moodleuser';
$CFG->dbpass    = 'yourpassword';
$CFG->dbpersist =  false;
$CFG->prefix    = 'mdl_';

$CFG->wwwroot   = 'http://82.27.199.134';
$CFG->dirroot   = '/var/www';
$CFG->dataroot  = '/home/rado/moodledata';
$CFG->admin     = 'admin';

$CFG->directorypermissions = 00777;  // try 02777 on a server in Safe Mode

$CFG->unicodedb = true;  // Database is utf8

require_once("$CFG->dirroot/lib/setup.php");
// MAKE SURE WHEN YOU EDIT THIS FILE THAT THERE ARE NO SPACES, BLANK LINES,
// RETURNS, OR ANYTHING ELSE AFTER THE TWO CHARACTERS ON THE NEXT LINE.
?>
[/PHP]

Hope this helps you to help me:)

Refer to this thread " [ http://moodle.org/mod/forum/discuss.php?d=13413 ]( http://moodle.org/mod/forum/discuss.php?d=13413 ) "  for a possible solution to this problem.

Change ' $CFG->wwwroot   = 'http://82.27.199.134';  

to

                   $CFG->wwwroot   =  "http://".$_SERVER["HTTP_HOST"]."/";

---

### Post by bsmith1051 on 2006-12-18
> **tturrisi said:**
> you need to config apache for that ip address instead of localhost because all the auto-generated links on the pages are [http://localhost](http://localhost), which will cause links to break in any browser other than the server browser.
How do you do this, please?

---

### Post by tturrisi on 2006-12-19
> **bsmith1051 said:**
> How do you do this, please?
see /etc/apache2/apache2.conf

---

### Post by rado_london on 2006-12-19
Hey people I removed the whole thing and installed XAMPP. Now everything works fine and I see no problems. Can you just give me links to some ebooks about MySQL and Apache. Thanks in advance.

---

