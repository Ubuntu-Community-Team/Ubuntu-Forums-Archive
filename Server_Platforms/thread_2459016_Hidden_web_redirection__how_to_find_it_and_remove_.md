---
title: "Hidden web redirection : how to find it and remove it ?"
date: 2021-03-08
forum: Server Platforms
---

### Post by hedy-dargere on 2021-03-08
I have an Ubuntu 20.04 server which running a HestiaCP for managing websites.

I try to migrate a prestashop website from an old server, to the new one.
It's part of my job and normally everything is OK.
But with this website, there is an hidden redirection somewhere and it give me headache !

Here the point : if you try to go to [https://biovie.mio.spheerys.net/](https://biovie.mio.spheerys.net/) (the new server) you will be immediately redirected to [https://biovie.joy.spheerys.net/](https://biovie.joy.spheerys.net/) (the old server powered with VestaCP)

On this website, I have a "functionnal" Prestashop with files, sql database.
I have checked and changed all occurences of biovie.joy.spheerys.net to biovie.mio.spheerys.net url :
[LIST]
[*]inside the mysql database
[*]inside the prestashop files (config files...)
[*]inside the .htaccess file
[*]
[/LIST]
I also remove the cache files on the new server.

Clue : in the apache log, there is nothing written during the redirection. So it's happen on another level, but which one ?

My question is the following : do you have any idea where the redirection could be hidden ? Is there a tool like traceroute or something else which can help me to find the issue ?

---

### Post by QIII on 2021-03-08
Does the new server have a different external IP?  Did you update your DNS records?

---

### Post by LHammonds on 2021-03-09
Redirects can happen at your DNS provider...where you go to set IP addresses for your domain (GoDaddy, NetworkSolutions, etc.)

They can also happen at your firewall if setup incorrectly.  If GoDaddy DNS for mia says 198.200.200.1 and your firewall directs any traffic on 198.200.200.1 to 10.10.10.2 (and 10.10.10.2 was not the server you were expecting) then that is an incorrectly configured route.  Same goes for the software firewall on the server.

They can also happen at the web server via the web configuration files.  In Apache, that would be something like /etc/apache2/sites-available/mia.conf.  Settings inside the config file can tell it to re-direct traffic from this site to another.

Redirection can also happen inside the website files itself via HTTP redirect, server-side (e.g. PHP) redirects or .htaccess redirects.

What you need to do is trace the path.  Look at your external DNS provider and see what IP that domain is configured to point to.  Then go into your hardware firewall / router where that IP address points to and check its routing rules for that IP.  Once you get the internal IP, then access that internal server and start to check the software firewall for any routing rules, then look at the webserver configuration files, then look at the website files for .htaccess, or HTTP/PHP coding inside the default index (e.g. index.php or index.html, etc.)

LHammonds

---

