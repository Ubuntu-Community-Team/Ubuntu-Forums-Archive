---
title: "Control Panel Help"
date: 2008-10-26
forum: Server Platforms
---

### Post by Yizi on 2008-10-26
Hello,

I managed to get the server installed and get the SSH running! The server is a LAMP and all i want to do is run some PHP/MySQL application on it, but i like to make it easier for myself, is there anything out there like cPanel for Ubuntu server?

Thanks,
Yizi

---

### Post by ad_267 on 2008-10-26
Gnupanel might be what you're looking for, although I haven't tried it myself. [http://www.gnupanel.org/](http://www.gnupanel.org/)

ISPConfig and EHCP might also be worth a look:
[http://www.ispconfig.org/](http://www.ispconfig.org/)
[http://www.ehcp.net/](http://www.ehcp.net/)

---

### Post by Yizi on 2008-10-27
I like the sound of ISPconfig! looks really detailed, but i seen a new one called webmin? what do you think of that? which one is easier to manage?

---

### Post by lykwydchykyn on 2008-10-27
Webmin is pretty popular, I use it myself.  It is not real helpful sometimes in letting you know what all the options are, but it does a good job of laying out all the options.

If your server is just for your own use and you just need the ability to administrate the basics, webmin will usually do handsomely.

---

### Post by Yizi on 2008-10-27
I have just tested webmin and i found it hard to upload then extract a file or create a MySQL DB compared to Cpanel.

---

### Post by bvidinli on 2008-10-28
you may download and install ehcp by:
open console, enter/copy and paste following :

wget [www.ehcp.net/download](www.ehcp.net/download)
tar -zxvf ehcp_latest.tgz
cd ehcp
./install.sh
#


ver 0.27 features:
new features:
* Easy Script installs (one-click installs)
* custom http
* custom dns
* subdomains
* password protected domains
* email forwardings
* domain transfer to another user
* webftp (net2ftp)
* multiple templates
* security, installer improved


Existing features:

* Mangement of :domains, dns, email, ftp, mysql, phpmyadmin, webmail (squirrelmail), resellers, panelusers,
* Opensource, GPL, full php, object oriented, modular, easily modifiable/extendable design..
* server backup/restore,
* Different Menus for Server Admin, Reseller, domain admin



You may contact me if you need help on ehcp.

---

### Post by Yizi on 2008-10-28
I installed your system, i just can't see how i can simply upload a zipped file and then create a DB to get a working, i'm looking for some simple like Cpanel if there is any.

---

### Post by bvidinli on 2008-12-27
to upload a zipped file,
you need first to create an ftp account inside ehcp.

then, you need to create a db in ehcp..

then you can use that ftp and db to install whatever you like.. 

ehcp is a hosting control panel, 
so, you need to create ftp and db youself.. there is no predefined ftp or db ..

---

