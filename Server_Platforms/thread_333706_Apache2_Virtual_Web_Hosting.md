---
title: "Apache2 Virtual Web Hosting"
date: 2007-01-07
forum: Server Platforms
---

### Post by lokeey on 2007-01-07
hey all, i've been racking the noggin over here trying to configure virtual web hosting off of my server. basically, i'm trying to configure my web server to host my brother's site using name-based virtual hosting. but everytime i try to hit my site (or his) it just shows the index / page. 

okay, so i created to conf files one with my web info and the other with my brother's which includes the following in each...then i added this to sites-available and creating a symlink to sites-enabled in /etc/apache2/sites*
<VirtualHost dev.example.com>
ServerAdmin webmaster@localhost
#We want to be able to access the web site using [www.dev.example.com](www.dev.example.com) or dev.example.com
ServerAlias [www.dev.example.com](www.dev.example.com)
DocumentRoot /home/myuser/public_html/example.com
#if using awstats
ScriptAlias /awstats/ /usr/lib/cgi-bin/
#we want specific log file for this server
CustomLog /var/log/apache2/example.com-access.log combined
</VirtualHost>

also in apache2.conf i uncommented the following lines
VirtualDocumentRoot /var/www/vhosts/%0/web
VirtualScriptAlias /var/www/vhosts/%0/cgi-bin

when i restart apache2 i get no errors

---

### Post by eric_stewart on 2007-01-07
This is how I did if for my site.  Per apache.org, I edited my httpd.conf file.  It is contained in the /etc/apache2 directory of your server.  I am running 3 sites on my little hobby webserver:  breezy.ca, stewart-clan.net, and intermediatemusicsubjectcouncil.org:
-----------------------------------------------------------------------------------------------
NameVirtualHost *:80

<VirtualHost *:80>
    ServerName [www.breezy.ca](www.breezy.ca)
    ServerAlias breezy.ca *.breezy.ca
    DocumentRoot /var/www
 </VirtualHost>

<VirtualHost *:80>
    ServerName [www.stewart-clan.net](www.stewart-clan.net)
    ServerAlias stewart.clan.net *.stewart-clan.net
    DocumentRoot /var/www/stewart-clan.net
</VirtualHost>
<VirtualHost *:80>
    ServerName [www.intermediatemusicsubjectcouncil.org](www.intermediatemusicsubjectcouncil.org)
    ServerAlias intermediatemusicsubjectcouncil.org *.intermediatemusicsubjectcouncil.org
    DocumentRoot /var/www/intermediatemusicsubjectcouncil.org
</VirtualHost>

I also have a little blurb on this very subject on my website, including a link to the Apache FAQ at apache.org.  Navigate over to [http://www.breezy.ca/?q=node/71](http://www.breezy.ca/?q=node/71)

/Eric
webmaster [www.breezy.ca](www.breezy.ca)

---

### Post by lokeey on 2007-01-07
cool! thnx i'll try that and i'll also check out your site.

thnx again!

---

