---
title: "error after install joomla /object not found"
date: 2010-04-02
forum: Server Platforms
---

### Post by tonjaa on 2010-04-02
Xampp 1.7.3a / joomla 1.5.15
after i create directory at  opt/lampp /htdocs/joomla99  and create new database in phpmyadmin
i install joomla to directory name joomla99 and use localhost/joomla99 for install joomla
but at second step Pre-installation check at > configuration.php Writable it's show No in red
i don't understand and i next to step for install to Finish . when i want to open [http://localhost/joomla99/administrator](http://localhost/joomla99/administrator)  it's show
**Object not found!**

        The requested URL was not found on this server.          If you entered the URL manually please check your     spelling and try again.      
  If you think this is a server error, please contact the [EMAIL="you@example.com"]webmaster[/EMAIL].  
  **Error 404**

    [localhost]("http://localhost/")
     Fri 02 Apr 2010 01:03:39 PM ICT
  Apache/2.2.14 (Unix) DAV/2 mod_ssl/2.2.14 OpenSSL/0.9.8l PHP/5.3.1 mod_apreq2-20090110/2.7.1 mod_perl/2.0.4 Perl/v5.10.1

and when i use [http://localhost/joomla99](http://localhost/joomla99)  it's show
No configuration file found and no installation code available. Exiting...

[COLOR=SeaGreen]how to fix this problem please guide me by step .[/COLOR]

---

### Post by tonjaa on 2010-04-04
i can install Joomla . the problem is about permission for write file configuration.php
i try to in stall again after i create new database and build directory i must to change permission of i directory when install for  can write configuration.php file.
and i edit function at Pre-installation check on,off for correct and green all at file php.ini
now it's ok.

---

