---
title: "mod_rewrite not working in ubuntu apache2"
date: 2011-09-13
forum: Server Platforms
---

### Post by danishbacker on 2011-09-13
mod_rewrite not working in ubuntu 10.04
i have  apache2 installed

please help me :(

[http://localhost/mysite/newlink/](http://localhost/mysite/newlink/)
says 404 error
but it is working in my remote server and windows local machine.

please forgive me for posting the dump

danny@danny-desktop:~$ sudo a2enmod rewrite
[sudo] password for danny: 
ERROR: Module rewrite not properly enabled: /etc/apache2/mods-enabled/rewrite.load is a real file, not touching it
danny@danny-desktop:~$ sudo gedit /etc/apache2/sites-available/default
danny@danny-desktop:~$ sudo a2enmod rewrite
ERROR: Module rewrite not properly enabled: /etc/apache2/mods-enabled/rewrite.load is a real file, not touching it
danny@danny-desktop:~$ sudo updatedb
danny@danny-desktop:~$ locate mod_rewrite.so
/home/danny/Downloads/lampp/modules/mod_rewrite.so
/usr/lib/apache2/modules/mod_rewrite.so
danny@danny-desktop:~$ sudo updatedb
danny@danny-desktop:~$ locate mod_rewrite.so
/usr/lib/apache2/modules/mod_rewrite.so
danny@danny-desktop:~$ sudo gedit /etc/apache2/mods-enabled/
danny@danny-desktop:~$ cd /etc/apache2/mods-enabled/
danny@danny-desktop:/etc/apache2/mods-enabled$ touch rewrite.load
touch: cannot touch `rewrite.load': Permission denied
danny@danny-desktop:/etc/apache2/mods-enabled$ sudo touch rewrite.load
danny@danny-desktop:/etc/apache2/mods-enabled$ sudo gedit rewrite.load
danny@danny-desktop:/etc/apache2/mods-enabled$ sudo /etc/apache2/sites-available/default
sudo: /etc/apache2/sites-available/default: command not found
danny@danny-desktop:/etc/apache2/mods-enabled$ gedit sudo /etc/apache2/sites-available/default
danny@danny-desktop:/etc/apache2/mods-enabled$ sudo gedit /etc/apache2/sites-available/default
danny@danny-desktop:/etc/apache2/mods-enabled$ sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
 ... waiting apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                         [ OK ]
danny@danny-desktop:/etc/apache2/mods-enabled$ sudo a2enmod rewrite
ERROR: Module rewrite not properly enabled: /etc/apache2/mods-enabled/rewrite.load is a real file, not touching it
danny@danny-desktop:/etc/apache2/mods-enabled$ cd ..
danny@danny-desktop:/etc/apache2$ cd ..
danny@danny-desktop:/etc$ cd httpd
bash: cd: httpd: No such file or directory
danny@danny-desktop:/etc$ sudo /etc/init.d/apache2 reload
 * Reloading web server config apache2                                          apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                         [ OK ]
danny@danny-desktop:/etc$ sudo a2enmod rewrite
ERROR: Module rewrite not properly enabled: /etc/apache2/mods-enabled/rewrite.load is a real file, not touching it
danny@danny-desktop:/etc$ sudo chmod 755 apache2/sites-enabled/000-default
[sudo] password for danny: 
danny@danny-desktop:/etc$ sudo gedit apache2/sites-enabled/000-default
danny@danny-desktop:/etc$ sudo a2enmod rewrite
ERROR: Module rewrite not properly enabled: /etc/apache2/mods-enabled/rewrite.load is a real file, not touching it
danny@danny-desktop:/etc$ 

Thanks in advance,

---

### Post by Ryan Dwyer on 2011-09-13
This should fix it:
sudo rm /etc/apache2/mods-enabled/rewrite.load
sudo a2enmod rewrite
sudo service apache2 restart

When you run a2enmod, it creates a symlink in the mods-enabled folder pointing to the item in the mods-available folder. It's failing because there's already a plain file with the same name. You don't need to "touch" stuff.

---

### Post by danishbacker on 2011-09-14
:D thank you Ryan Dwyer the problem solved
you are right. i was using the old method i think.

also i found the same in another thread 
[http://ubuntuforums.org/showthread.php?t=1180112](http://ubuntuforums.org/showthread.php?t=1180112)

---

