---
title: "Apache2 help"
date: 2008-12-10
forum: Server Platforms
---

### Post by Gregz on 2008-12-10
Have all the apache2,php,sql downloaded and if I go to local host I get IT WORKS. Now I have problem with this:

To create a new site:

    *

      Copy the default website as a starting point. sudo cp /etc/apache2/sites-available/default /etc/apache2/sites-available/mysite 
    *

      Edit the new configuration file in a text editor "sudo nano" on the command line or "gksudo gedit", for example: gksudo gedit /etc/apache2/sites-available/mysite
    *

      **Change the DocumentRoot to point to the new location. For example, /home/user/public_html/**
    *

      **Change the Directory directive, replace <Directory /var/www/> to <Directory /home/user/public_html/>**
    *

      You can also set separate logs for each site. To do this, change the ErrorLog and CustomLog directives. This is optional, but handy if you have many sites
    * Save the file 



I'm not real sure on the change document root???? 

gksudo gedit does not work all I ever get is blank pages. (found this out doing my nvidia  set-up). So I use sudo nano which does work.

I'm very new to this so please bear with me here


Ubuntu 8.10 server
G

---

### Post by cdenley on 2008-12-10
```

<VirtualHost *:80>
        ServerAdmin webmaster@localhost

        **DocumentRoot /var/www/**
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        **<Directory /var/www/>**
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

```

"gksudo gedit" works for me. What version of ubuntu are you running?
```

gksudo gedit /etc/apache2/sites-available/default

```

---

### Post by Gregz on 2008-12-10
Thank you, I don't see how I missed that :oops:. Working now.  Also gksudo working now... It did'nt when I was trying to get my nvidia card working. Strange....

Also in the {Set mysql bind address} is this where I set my laptop and other pc to connect to it.


Is there a good guide on how to setup Joomla with apache2 ? 

As in downloading to apache??

---

### Post by Gregz on 2008-12-10
Ok, I have all up and running I think, BUT I cannot run this test. I try and make script and when I go to "save as" it says I don't have permission.



 Thats is trying copy paste... 





Once you have completed the necessary installation of your server software it is worth running a quick test to
ensure that all the necessary, minimum requirements are met.
Warning!: Remove the phpinfo.php file from your Web root as soon as you have the necessary
information. Leaving it in situ is a security risk. Your Joomla! installation has a built in version of the same
script in the Help Menus for future reference.
You can do this very simply by creating a basic PHP script:
   <?php
   // Show all information
   phpinfo();
   ?>
Save this as phpinfo.php for example, and save the file to the root of your Web site, then simply enter the
address of your Web site into your browser as follows: [http://www.yourdomain.com/phpinfo.php](http://www.yourdomain.com/phpinfo.php) or
[http://localhost/phpinfo.php](http://localhost/phpinfo.php) and you should receive a detailed summary and state of all the PHP compilation
options and extensions (such as the Zlib, XML, and MySQL modules), the PHP version in use, server
information and environment (if t is compiled as a module), the PHP environment, Operating System version
information, paths, master and local values of configuration options, HTTP headers, and the PHP License.

---

### Post by mbeach on 2008-12-10
its been awhile since I installed joomla, but for the most part I suspect you need to take ownership of the files (or at least the documentroot).

so lets assume your username is greg, and that the joomla document root is /var/www/joomla
you might want to run something like
```
sudo chown greg:greg /var/www/joomla
```
then try to create your phpinfo file in that folder.

also not sure if you've completely settled on Joomla just yet, but a nice up and coming cms (imo) is concrete5.  
[http://www.concrete5.org](http://www.concrete5.org)

---

### Post by Gregz on 2008-12-12
actually need to mv cofig php-dist to config php 

don't quit understand that but ok.

also it's installed but can't access it something with php  as stated above

---

