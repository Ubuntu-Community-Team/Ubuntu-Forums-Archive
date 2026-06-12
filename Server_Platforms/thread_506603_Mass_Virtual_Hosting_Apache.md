---
title: "Mass Virtual Hosting Apache"
date: 2007-07-21
forum: Server Platforms
---

### Post by killerdragon on 2007-07-21
What would be the best way to do mass virtual hosting in apache?

I was thinking of doing something like this: [http://httpd.apache.org/docs/2.0/vhosts/mass.html](http://httpd.apache.org/docs/2.0/vhosts/mass.html)

I'm hoping there is a mysql system out there.
I am going to do some messing around to see if I can work something out.

Also could someone explain this:

RewriteEngine on

RewriteMap lowercase int:tolower

# define the map file
RewriteMap vhost txt:/www/conf/vhost.map

# deal with aliases as above
RewriteCond %{REQUEST_URI} !^/icons/
RewriteCond %{REQUEST_URI} !^/cgi-bin/
RewriteCond ${lowercase:%{SERVER_NAME}} ^(.+)$
# this does the file-based remap
RewriteCond ${vhost:%1} ^(/.*)$
RewriteRule ^/(.*)$ %1/docs/$1

RewriteCond %{REQUEST_URI} ^/cgi-bin/
RewriteCond ${lowercase:%{SERVER_NAME}} ^(.+)$
RewriteCond ${vhost:%1} ^(/.*)$
RewriteRule ^/(.*)$ %1/cgi-bin/$1 [T=application/x-httpd-cgi]

---

### Post by killerdragon on 2007-07-21
Ok so after doing some google digging I find this:

[http://gentoo-wiki.com/Apache_Modules_mod_vhost_alias](http://gentoo-wiki.com/Apache_Modules_mod_vhost_alias)

> # example.com              -->  /var/www/vhosts/example.com
      # [www.example.com](www.example.com)          -->  /var/www/vhosts/example.com
      # a.[www.example.com](www.example.com)        -->  /var/www/vhosts/example.com
      # [www.example.com/cgi-bin](www.example.com/cgi-bin)  -->  /var/www/vhosts/example.com/cgi-bin
      #VirtualDocumentRoot /var/www/vhosts/%-2.0.%-1.0
      #VirtualScriptAlias /var/www/vhosts/%-2.0.%-1.0/cgi-bin


This is beautiful...but I'm hoping for some mysql based system.

---

