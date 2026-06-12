---
title: "Fixing my hpptd.cong"
date: 2009-03-22
forum: Server Platforms
---

### Post by Vegan on 2009-03-22
I am trying to get tomcat6 to let me use JSP and JSPX files on the web site.

Needed to allow for mass numbers of virtual hosts on one IP address

#Need the default document root
DocumentRoot /web
#ServerSignature On

DirectoryIndex index.html index.php index.cgi index.pl index.xhtml default.asp $
AddType application/x-httpd-php .php
Addtype application/x-java-jnlp-file .jlnp
AddType application/java-archive .jar
AddType application/x-httpd-php-source .phps
Addtype application/vnd.adobe.air-application-installer-package+zip .air
AddType application/x-shockwave-flash .swf
AddOutputFilterByType DEFLATE text/html text/plain text/xml

#Needed to install a CGI directory in each virtual host
<Directory "/usr/lib/cgi-bin">
  AllowOverride None
  Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
  Order allow,deny
  Allow from all
</Directory>

<Directory />
  Options FollowSymLinks
  AddOutputFilterByType DEFLATE text/html text/plain text/css text/javascript a$
  AllowOverride None
  Order allow,deny
  Allow From All
</Directory>

<Directory /web>
  Options Indexes FollowSymLinks -MultiViews
  AddOutputFilterByType DEFLATE text/html text/plain text/css text/javascript a$
  AllowOverride None
  Order allow,deny
  Allow From All
</Directory>

---

