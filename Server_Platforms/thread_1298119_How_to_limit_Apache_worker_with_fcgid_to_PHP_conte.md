---
title: "How to limit Apache worker with fcgid to PHP content"
date: 2009-10-22
forum: Server Platforms
---

### Post by alexisbellido on 2009-10-22
Hello, I'm running a Ubuntu server and I've setup Apache in MPM worker mode to use mod_fcgi and PHP to reduce the use of resources for a Drupal website.

I followed this guide to setup: [http://ivan.gudangbaca.com/installing_apache2_and_php5_using_mod_fcgid](http://ivan.gudangbaca.com/installing_apache2_and_php5_using_mod_fcgid)

My sites works ok, PHP is fine.

Now I'm load testing and I wanted to make sure static content doesn't create PHP processes so I created a home.htm file, no PHP at all, and told [http://loadimpact.com](http://loadimpact.com) to hit that page at mydomain.com/home.htm

The problem is that I started seeing PHP processes on top when I ran this:

top -u www-data

I checked my Apache configuration and noticed I had:

AddType text/html .php

I removed the line, restarted Apache and tried again. No luck, I still see PHP processes on top when hitting home.htm.

Then I added:

AddType application/x-httpd-php .php

restarted Apache and same problem.

The only way to avoid PHP processes when hitting home.htm was removing this:

AddHandler fcgid-script .php
FCGIWrapper /usr/lib/cgi-bin/php5 .php

but of course that disables PHP.

Any ideas?

This is my complete virtual host configuration:

```

Listen 8000
<VirtualHost *:8000>

     ServerName [www.mydomain.com](www.mydomain.com)
     UseCanonicalName On
     
     DocumentRoot /home/website
      <DirectoryMatch  /\.git/|/\.svn/ >
       Deny from all
     </DirectoryMatch>
     <Directory "/home/website">
      Options FollowSymLinks ExecCGI
      AllowOverride None
      Include /home/website/.htaccess 
       FileETag Size
      Order allow,deny
      Allow from all
     </Directory>

     RewriteEngine On

     DirectoryIndex default.php index.php
    AddHandler fcgid-script .php 
    FCGIWrapper /usr/lib/cgi-bin/php5 .php
     #AddType text/html .php
     #AddType application/x-httpd-php .php

     # Enable status page for monitoring purposes 
     RewriteCond %{REMOTE_ADDR} ^(127.0.0.1)
     RewriteRule ^(/server-status) $1 [H=server-status,L]

     # Redirects to a maintenance page if the specified file below exists
     # ...but it still allows images to be served
     RewriteCond %{DOCUMENT_ROOT}/system/maintenance.html -f
     RewriteCond %{SCRIPT_FILENAME} !/system/maintenance.html
     RewriteCond %{SCRIPT_FILENAME} !^(.+).(gif|png|jpg|css|js|swf)$
     RewriteRule ^.*$ /system/maintenance.html [L]

     # Setup the logs in the appropriate directory
     CustomLog /var/log/apache2/access_log combined
     #ErrorLog  /var/log/apache2/error_log

     #Remote logging -- handle by syslog
     ErrorLog "|logger -p local3.info -t httperror"
     CustomLog "|logger -p local3.info -t http" combined

     LogLevel warn

     # Deflate
     AddOutputFilterByType DEFLATE text/html text/plain text/xml application/xml application/xhtml+xml text/javascript text/css application/x-javascript
     BrowserMatch ^Mozilla/4 gzip-only-text/html
     BrowserMatch ^Mozilla/4.0[678] no-gzip
     BrowserMatch bMSIE !no-gzip !gzip-only-text/html
     DeflateCompressionLevel 9
     SetEnvIf User-Agent ".*MSIE.*" nokeepalive ssl-unclean-shutdown downgrade-1.0 force-response-1.0

</VirtualHost>

```

---

