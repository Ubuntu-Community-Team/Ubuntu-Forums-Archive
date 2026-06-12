---
title: "running public site from 12.04 desktop"
date: 2013-04-02
forum: Server Platforms
---

### Post by vapblack on 2013-04-02
Greetings all.
I recently installed a program called [Booktype]("http://www.sourcefabric.org/en/booktype/") and I would like the ability for other people to connect through my IP address and be able to use the program. I have done this before, but don't remember how. The Apache.conf file is where I think I should be working, if I'm wrong, please let me know> # Apache configuration for Booktype server V1.0.1

<VirtualHost *:80>

     # CHANGE THIS
     ServerName booktype
     SetEnv HTTP_HOST "booktype"

     SetEnv LC_TIME "en_GB.UTF-8"
     SetEnv LANG "en_GB.UTF-8"

     WSGIScriptAlias / /var/www/mybooktype/booki.wsgi

     <Location "/">
       Allow from all
       Options FollowSymLinks
     </Location>

     Alias /static/ "/var/www/mybooktype/static/"
     <Directory "/var/www/mybooktype/static/">
       Order allow,deny
       Options Indexes
       Allow from all
       IndexOptions FancyIndexing
     </Directory>

     Alias /site_static/ "/usr/local/src/Booktype/lib/booki/site_static/"
     <Directory "/usr/local/src/Booktype/lib/booki/site_static/">
       Order allow,deny
       Options Indexes
       Options FollowSymLinks
       Allow from all
       IndexOptions FancyIndexing
     </Directory>

     Alias /media/ "/usr/lib/python2.7/dist-packages/django/contrib/admin/media/"
     <Directory "/usr/lib/python2.7/dist-packages/django/contrib/admin/media">
       Order allow,deny
       Options Indexes
       Options FollowSymLinks
       Allow from all
       IndexOptions FancyIndexing
     </Directory>

     ErrorLog /var/log/apache2/booktype-error.log
     LogLevel warn
     CustomLog /var/log/apache2/booktype-access.log combined
</VirtualHost>

**to reiterate,** right now I connect to [http://booktype](http://booktype) to use the software, and would like to allow people to connect to it through my IP

---

### Post by mojorising on 2013-04-03
Taking a quick look, it appears you have everything set properly here to allow from all (see the "Allow from all" lines in the directory directives). That explains why it works for you already.

That said, there are a few other things you need to to to allow such access. Your server firewall needs to allow access on port 80, the standard web server port (unless your server is set to listen on a different port, which doesn't appear to be the case). Type "sudo ufw status" without the quotes to see what's happening there. If you need help with the Ubuntu firewall, type man ufw at the command line -- it's quite easy to use. 

If you will be accessing this server from outside the local network, the other main things to look at are your network firewall settings and port forwarding (probably all set on the same perimeter device). You'll need to forward traffic on 80 of your router/firewall to port 80 of your server. Of course, that port also needs to be open in order to accept and forward this traffic. Check your device documentation to find out how to do those things. 

Back to your last statement at the end of your message. When you say, "right now I connect to [http://booktype](http://booktype) to use the software, and would like to allow people to connect to it through my IP" Do you mean you are connecting to this application from the same computer your web server is running on? Bear in mind, IP addresses can change if you are using DHCP. It is best to set a static IP if you haven't already and put that IP in DNS for this so the other users can just type a network name instead of an IP address as well.

Hope that helps. 

Mike

---

### Post by spynappels on 2013-04-03
Hi,

If you want to be able to connect from the internet at http://booktype.<yourdomain>.com you will need to add a server alias to that conf file so Apache will respond to requests for that URL with this site. For more details, see:

[http://httpd.apache.org/docs/2.2/mod/core.html#serveralias](http://httpd.apache.org/docs/2.2/mod/core.html#serveralias)

You will also need to forward ports from your router/firewall to the server hosting the site, as previously said.

---

