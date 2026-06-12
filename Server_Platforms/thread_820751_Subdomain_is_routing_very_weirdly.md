---
title: "Subdomain is routing very weirdly"
date: 2008-06-06
forum: Server Platforms
---

### Post by twistedtwig on 2008-06-06
Hi all,

I am rather confused as to why this is happening and have exhausted my limited knowledge on how to debug it.

Ok, so my main domain is [http://www.housofhawkins.com](http://www.housofhawkins.com) this has been up and works great.  I use easydns.com to do my ddns for me.

I also have a couple of other domains pointing to houseofhawkins.com and use virtualhost's to server their sites, these also still work just fine.

I have just got a new domain [http://www.aipoker.co.uk](http://www.aipoker.co.uk).  I am using zonedit.com to do my ddns.

I have the thing registered and basics setup, (IP is correct etc).  This is forwarded to a windows server inside my network with proxypassreverse.  Which also works fine.

I also have a number of subdomains, two added recently are blogs.  one being csjblog.houseofhawkins.com which works fine and blog.aipoker.co.uk.  This is where my issue comes in.  A while ago this was called pokerblog.houseofhawkins.com.  I changed it to the new name in the host file (see below) but it still tries to resolve to the old name.

If you type blog.aipoker.co.uk it seems to get to my site then change to pokerblog.houseofhawkins.com and then fails.

I have no idea why this is happening and am completely at a loss at how I find out how to solve it.

Can someone help a confused man please?

Thanks

here is my full vhosts.conf file for the virtualhosts:

```

################### default root directory #################

<VirtualHost *>
ServerName houseofhawkins.com
ServerAlias www.houseofhawkins.com
ServerAdmin jonadmin@houseofhawkins.com
DocumentRoot /var/www/root
<Directory />
Options FollowSymLinks +ExecCGI
AllowOverride All
</Directory>

#display error page if we get 502 error
ErrorDocument 502 /error.html
#if we get 503 unavailable give out different page
ErrorDocument 503 /sitedown.html
#display error page for error 404 page not found
ErrorDocument 404 /404.php

ErrorLog /var/log/apache2/error.log

#Possible values include: debug, info, notice, warn, error, crit, alert, emerg
logLevel warn
CustomLog /var/log/apache2/access.log combined
ServerSignature On

 RewriteEngine on
 RewriteLog "/var/log/apache2/rewrite_log"
 RewriteRule ^/sitemap.xml$ /sitemapxml.php
 RewriteRule ^/sitemap.html$ /sitemaphtml.php
 RewriteRule ^/projects/testarea$ /projects/testarea/ [R]
 RewriteRule ^/projects/csjawbreaker$ /projects/csjawbreaker/ [R]
 RewriteRule ^/projects/holdem$ /projects/holdem/ [R]
 RewriteRule ^/projects/tardis$ /projects/tardis/ [R]


ProxyRequests Off

<Proxy *>
  Order deny,allow
  Deny from all
  Allow from all
</Proxy>

ProxyPass        /projects/testarea/ http://192.168.10.101:8080/testArea/
ProxyPassReverse /projects/testarea/ http://192.168.10.101:8080/testArea/

ProxyPass        /projects/csjawbreaker/ http://192.168.10.101:8080/csjawbreaker/
ProxyPassReverse /projects/csjawbreaker/ http://192.168.10.101:8080/csjawbreaker/

ProxyPass        /projects/holdem/ http://192.168.10.101:8080/holdem/
ProxyPassReverse /proejcts/holdem/ http://192.168.10.101:8080/holdem/

ProxyPass        /projects/tardis/ http://192.168.10.101:8080/Tardis/
ProxyPassReverse /projects/tardis/ http://192.168.10.101:8080/Tardis/

SetEnv force-proxy-request-1.0 1
SetEnv proxy-nokeepalive 1

</VirtualHost>

################### Charlotte home page #################

<VirtualHost *>
ServerName charlotte.houseofhawkins.com
ServerAdmin jonadmin@houseofhawkins.com
DocumentRoot /var/www/charlotte
<Directory />
Options FollowSymLinks Indexes
AllowOverride None
</Directory>

ErrorLog /var/log/apache2/error.log

#Possible values include: debug, info, notice, warn, error, crit, alert, emerg
logLevel warn

CustomLog /var/log/apache2/access.log combined
ServerSignature On
</VirtualHost>


################### Foot faerie home page #################

<VirtualHost *>
ServerName footfaerie.me.uk
Serveralias www.footfaerie.me.uk footfaerie.me.uk
ServerAdmin jonadmin@houseofhawkins.com
DocumentRoot /var/www/footfaerie
<Directory />
Options FollowSymLinks Indexes
AllowOverride None
</Directory>

ErrorLog /var/log/apache2/error.log

#Possible values include: debug, info, notice, warn, error, crit, alert, emerg
logLevel warn

CustomLog /var/log/apache2/access.log combined
ServerSignature On
</VirtualHost>


################### gareth west home page #################

<VirtualHost *>
ServerName gareth-west.co.uk
Serveralias www.gareth-west.co.uk gareth-west.co.uk
ServerAdmin jonadmin@houseofhawkins.com
DocumentRoot /var/www/garethwest
<Directory />
Options FollowSymLinks Indexes
AllowOverride None
</Directory>

ErrorLog /var/log/apache2/error.log

#Possible values include: debug, info, notice, warn, error, crit, alert, emerg
logLevel warn

CustomLog /var/log/apache2/access.log combined
ServerSignature On
</VirtualHost>



################### dale home page #################

<VirtualHost *>
ServerName dale.houseofhawkins.com
ServerAdmin jonadmin@houseofhawkins.com
DocumentRoot /var/www/dale
<Directory />
Options FollowSymLinks Indexes
AllowOverride None
</Directory>

ErrorLog /var/log/apache2/error.log

#Possible values include: debug, info, notice, warn, error, crit, alert, emerg
logLevel warn

CustomLog /var/log/apache2/access.log combined
ServerSignature On
</VirtualHost>



################### Ethan home page #################

<VirtualHost *>
ServerName ethan.houseofhawkins.com
ServerAdmin jonadmin@houseofhawkins.com
DocumentRoot /var/www/ethan
<Directory />
Options FollowSymLinks Indexes
AllowOverride None
</Directory>

ErrorLog /var/log/apache2/error.log

#Possible values include: debug, info, notice, warn, error, crit, alert, emerg
logLevel warn

CustomLog /var/log/apache2/access.log combined
ServerSignature On
</VirtualHost>



################### Shak home page #################

<VirtualHost *>
ServerName shak.houseofhawkins.com
ServerAdmin jonadmin@houseofhawkins.com
DocumentRoot /var/www/shak
<Directory />
Options FollowSymLinks Indexes
AllowOverride All
</Directory>

ErrorLog /var/log/apache2/error.log

#Possible values include: debug, info, notice, warn, error, crit, alert, emerg
logLevel warn

CustomLog /var/log/apache2/access.log combined
ServerSignature On
</VirtualHost>


################### test home page #################

<VirtualHost *>
ServerName test.houseofhawkins.com
ServerAdmin jonadmin@houseofhawkins.com
DocumentRoot /var/www/test
<Directory />
Options FollowSymLinks Indexes
AllowOverride All
</Directory>

ErrorLog /var/log/apache2/error.log

#Possible values include: debug, info, notice, warn, error, crit, alert, emerg
logLevel warn

CustomLog /var/log/apache2/access.log combined
ServerSignature On
</VirtualHost>


################### CS Jawbreaker blog  page #################

<VirtualHost *>
ServerName csjblog.houseofhawkins.com
ServerAdmin jonadmin@houseofhawkins.com
DocumentRoot /var/www/csjblog
<Directory />
Options FollowSymLinks Indexes
AllowOverride All
</Directory>

ErrorLog /var/log/apache2/error.log

#Possible values include: debug, info, notice, warn, error, crit, alert, emerg
logLevel warn

CustomLog /var/log/apache2/access.log combined
ServerSignature On
</VirtualHost>


#########################################################
##########    subdomain with proxypass  #################

<VirtualHost *>
    ServerAdmin jonadmin@houseofhawkins.com
    DocumentRoot /var/www/root/
    ServerName windows.houseofhawkins.com
    ProxyPass / http://192.168.10.100/
    ProxyPassReverse / http://192.168.10.100/
    DirectoryIndex index.html default.aspx index.aspx
</VirtualHost>

<VirtualHost *>
ServerName presents.houseofhawkins.com
ServerAlias www.presents.houseofhawkins.com
<Proxy *>
Order deny,allow
Allow from all
</Proxy>

    ProxyRequests Off
    
    ProxyPass / http://192.168.10.101/
    ProxyPassReverse / http://192.168.10.101/

 RewriteEngine on
 RewriteLog "/var/log/apache2/rewrite_log"
 RewriteRule ^$ /presentlist/ [R]
 RewriteRule ^/$ /presentlist/ [R]

</VirtualHost>


############## aipoker.co.uk #######################

<VirtualHost *>
ServerName aipoker.co.uk 
ServerAlias www.aipoker.co.uk
<Proxy *>
Order deny,allow
Allow from all
</Proxy>

    ProxyRequests Off

    ProxyPass / http://192.168.10.101/
    ProxyPassReverse / http://192.168.10.101/

</VirtualHost>


################### AI Poker blog  page #################


<VirtualHost *>
ServerName blog.aipoker.co.uk
Serveralias blog.aipoker.co.uk
ServerAdmin jon@aipoker.co.uk
DocumentRoot /var/www/pokerblog
<Directory />
Options FollowSymLinks Indexes
AllowOverride None
</Directory>

ErrorLog /var/log/apache2/error.log

#Possible values include: debug, info, notice, warn, error, crit, alert, emerg
logLevel warn

CustomLog /var/log/apache2/access.log combined
ServerSignature On
</VirtualHost>

```

---

### Post by osjak on 2008-06-06
Have you checked your rewrite rules? Those can act unexpectedly sometimes.

---

### Post by twistedtwig on 2008-06-06
Your brilliant.... That triggered a thought in my head, it was wordpress.  As I had set it up with the old URL it was doing a rewrite and changing it.

With a bit of fiddling it all works perfectly now.

Thank you so much!!!

---

