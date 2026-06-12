---
title: "Apache on and off with refreshing domain page online"
date: 2009-01-26
forum: Server Platforms
---

### Post by SpiffyFrodootje on 2009-01-26
Hi!

Took me a month, but with the help of these forums, I managed to get a nice LAMP and email server working to a fair degree of accuracy (Cogeco blocks port 25 so I can't test completely until I relocate it to a static IP). So thank you all for such terrific community support!

But I've hit a roadblock that I'm completely stumped with. Two actually, but for the purposes of this thread, just one.

Here is my setup:

I have three domains pointing to an IP address. Dynamic for now, but as I said I'll be moving to a static one soon. The domain in question (for now) is [www.globalhort.ca](www.globalhort.ca). I know some people in this community get frustrated when we don't provide domains ;)

I can access it fine. But when I refresh it, the server is lost. If I reboot the server, it's up instantly, only to showcase the same symptoms once I actually visit the page and press refresh (may take a few tries). Whether I re-visit it after the server reboot immediately after or 30 minutes later shows no difference. It's there, then it's gone. With time it eventually works again (sporadic: within minutes or hours) but show the same symptoms.

Has anyone else experienced this behaviour? I used to check on these webpages often from time to time (showing friends, etc) and i never spotted it happening then, since I would never refresh it. It's only when I've been regularly using FileZilla and uploading/testing the new domain that this occurred.

It may be of some use to know that apache vhosts aren't 100% working. I get the following error in my logs:

4x: [warn] NameVirtualHost *:80 has no VirtualHosts

But the vhosts seemed to work correctly for all three domains. So I gave it little thought for now, as my time is becoming scarce.

The contents of my apache configuration file is below:

File: /etc/apache2/sites-available/www.globalhort.ca

NameVirtualHost *:80
<VirtualHost *:80>
       ServerAdmin [email]rob.blom@globalhort.ca[/email]

       DocumentRoot /var/www/global
       ServerName [www.globalhort.ca](www.globalhort.ca)
       ServerAlias globalhort.ca

       <Directory />
               Options FollowSymLinks
               AllowOverride None
       </Directory>
       <Directory /var/www/>
               Options Indexes FollowSymLinks MultiViews
               AllowOverride None
               Order allow,deny
               Allow from all
       </Directory>

       ScriptAlias /cgi-bin/ /var/www/global/cgi-bin/
       <Directory "/var/www/global/cgi-bin">
               AllowOverride None
               Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
               Order allow,deny
               Allow from all
       </Directory>

       ErrorLog /var/log/apache2/error.log

       LogLevel warn
       CustomLog /var/log/apache2/access.log combined
       ServerSignature On

   Alias /doc/ "/usr/share/doc/"
   <Directory "/usr/share/doc/">
       Options Indexes MultiViews FollowSymLinks
       AllowOverride None
       Order deny,allow
       Deny from all
       Allow from 127.0.0.0/255.0.0.0 192.168.1.0/255.255.255.0 ::1/128
   </Directory>
</VirtualHost>


I nabbed this code from the following walkthrough:
[http://www.njae.me.uk/Web_server_setup](http://www.njae.me.uk/Web_server_setup)

Any thoughts? And TIA!

---

