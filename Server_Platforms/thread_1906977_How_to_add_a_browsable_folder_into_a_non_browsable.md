---
title: "How to add a browsable folder into a non browsable Apache conf?"
date: 2012-01-10
forum: Server Platforms
---

### Post by Romu on 2012-01-10
Hi there,
I run a 10.04 LTS server with apache 2 for my web site.

The apache 2 configuration is the following:

```
<VirtualHost *:80>
    ServerAdmin webmaster@localhost

    DocumentRoot /home/runner/www/
    <Directory />
        Options FollowSymLinks
        AllowOverride None
    </Directory>
    <Directory /home/runner/www/>
        Options -Indexes FollowSymLinks MultiViews
        AllowOverride None
        Order allow,deny
        allow from all
        RewriteEngine on
        RewriteBase /
        # Add www (change www.example.com to example.com to remove www)  
        # RewriteCond %{HTTP_HOST} !^www.mondomaine.com$ [NC]  
        # RewriteRule ^(.*)$ http://www.mondomaine.com/$1 [R=301,L]  
        RewriteRule ^index\.php$ - [L]
        RewriteCond %{REQUEST_FILENAME} !-f
        RewriteCond %{REQUEST_FILENAME} !-d
        RewriteRule . /index.php [L]

        # 5G:[QUERY STRINGS]
        <IfModule mod_rewrite.c>
         RewriteCond %{QUERY_STRING} (environ|localhost|mosconfig|scanner) [NC,OR]
         RewriteCond %{QUERY_STRING} (menu|mod|path|tag)\=\.?/? [NC,OR]
         RewriteCond %{QUERY_STRING} boot\.ini  [NC,OR]
         RewriteCond %{QUERY_STRING} echo.*kae  [NC,OR]
         RewriteCond %{QUERY_STRING} etc/passwd [NC,OR]
         RewriteCond %{QUERY_STRING} \=\\%27$   [NC,OR]
         RewriteCond %{QUERY_STRING} \=\\\'$    [NC,OR]
         RewriteCond %{QUERY_STRING} \.\./      [NC,OR]
         RewriteCond %{QUERY_STRING} \:         [NC,OR]
         RewriteCond %{QUERY_STRING} \[         [NC,OR]
         RewriteCond %{QUERY_STRING} \]         [NC]
         RewriteRule .* - [F]
        </IfModule>

        # 5G:[USER AGENTS]
        <IfModule mod_setenvif.c>
         SetEnvIfNoCase User-Agent ^$ keep_out
         SetEnvIfNoCase User-Agent (casper|cmsworldmap|diavol|dotbot)   keep_out
         SetEnvIfNoCase User-Agent (flicky|ia_archiver|jakarta|kmccrew) keep_out
         SetEnvIfNoCase User-Agent (libwww|planetwork|pycurl|skygrid)   keep_out
         <Limit GET POST PUT>
          Order Allow,Deny
          Allow from all
          Deny from env=keep_out
         </Limit>
        </IfModule>

        # 5G:[REQUEST STRINGS]
        <IfModule mod_alias.c>
         RedirectMatch 403 (https?|ftp|php)\://
         RedirectMatch 403 /(cgi|https?|ima|ucp)/
         RedirectMatch 403 (\=\\\'|\=\\%27|/\\\'/?|\)\.css\()$
         RedirectMatch 403 (\,|//|\)\+|/\,/|\{0\}|\(/\(|\.\.\.|\+\+\+|\|)
         RedirectMatch 403 \.(cgi|asp|aspx|cfg|dll|jsp|mdb|sql|ini|rar)$
         RedirectMatch 403 /(contac|fpw|install|pingserver|register)\.php
         RedirectMatch 403 (base64|crossdomain|localhost|wwwroot)
         RedirectMatch 403 (eval\(|\_vti\_|\(null\)|echo.*kae)
         RedirectMatch 403 \.well\-known/host\-meta
         RedirectMatch 403 /function\.array\-rand
         RedirectMatch 403 \)\;\$\(this\)\.html\(
         RedirectMatch 403 proc/self/environ
         RedirectMatch 403 msnbot\.htm\)\.\_
         RedirectMatch 403 /ref\.outcontrol
         RedirectMatch 403 com\_cropimage
         RedirectMatch 403 indonesia\.htm
         RedirectMatch 403 \{\$itemURL\}
         RedirectMatch 403 function\(\)
         RedirectMatch 403 labels\.rdf
        </IfModule>

        <IfModule mod_deflate.c>
            # Insert filter
            SetOutputFilter DEFLATE
            # Netscape 4.x has some problems...
            BrowserMatch ^Mozilla/4 gzip-only-text/html
            # Netscape 4.06-4.08 have some more problems
            BrowserMatch ^Mozilla/4\.0[678] no-gzip
            # MSIE masquerades as Netscape, but it is fine
            BrowserMatch \bMSIE !no-gzip !gzip-only-text/html
            # Don't compress images
            SetEnvIfNoCase Request_URI \.(?:gif|jpe?g|png)$ no-gzip dont-vary
            SetEnvIfNoCase Request_URI \.(?:exe|t?gz|zip|bz2|sit|rar)$ no-gzip dont-vary
            SetEnvIfNoCase Request_URI \.pdf$ no-gzip dont-vary
            # Make sure proxies don't deliver the wrong content
            Header append Vary User-Agent env=!dont-vary
        </IfModule>

        <IfModule mod_expires.c>
            ExpiresActive On
            ExpiresDefault "access plus 1 seconds"
            ExpiresByType text/html "access plus 1 seconds"
            ExpiresByType image/gif "access plus 1 weeks"
            ExpiresByType image/jpeg "access plus 1 weeks"
            ExpiresByType image/png "access plus 1 weeks"
            ExpiresByType text/css "access plus 1 weeks"
            ExpiresByType text/javascript "access plus 1 weeks"
            ExpiresByType application/x-javascript "access plus 1 weeks"
            ExpiresByType text/xml "access plus 1 weeks"
            ExpiresByType text/.js  "access plus 1 weeks"
        </IfModule>

        php_flag display_startup_errors off  
        php_flag display_errors off  
        php_flag html_errors off  
        php_value docref_root 0  
        php_value docref_ext 0  
        
        <Files .htaccess>  
         Order Allow,Deny  
         Deny from all  
        </Files>  

        <Files wp-config.php>  
         Order Deny,Allow  
         Deny from all  
        </Files>  
    </Directory>
</VirtualHost>
```

And this works pretty, this is a configuration found on the web to secure Wordpress which powers my web site. So by default, the folder within the www folder are not browsable (-Indexers).

Now, I want make one folder browsable in my web site, I know this is related to the +Indexers directive, but I don't know how to setup such an addition.

I've tried many ideas without any success. Thanks for your help.

---

### Post by SeijiSensei on 2012-01-10
Suppose you want to make /home/runner/www/visible be the browseable directory.  Add a stanza like this inside the <VirtualHost></VirtualHost> container:

```

<Directory "/home/runner/www/visible">
   Options +Indexes
</Directory>

```

Note that this will only work if /home/runner and /home/runner/www have at least 711 privileges and /home/runner/www/visible has 755 privileges.  Only files visible to the Apache user will be listed, so if you have a file in the /visible/ directory owned by user runner with 600 permissions, it won't be displayed by the web server.

---

### Post by Romu on 2012-01-11
Thanks for help, I'll try this, on another forum, someone also pointed the fact the "AllowOverride None" directive could block this "+Indexes" rule, I'll test that.

---

### Post by SeijiSensei on 2012-01-11
> **Romu said:**
> Thanks for help, I'll try this, on another forum, someone also pointed the fact the "AllowOverride None" directive could block this "+Indexes" rule, I'll test that.

The AllowOverride directive applies to [.htaccess]("http://httpd.apache.org/docs/current/howto/htaccess.html") files which are used to modify the server configuration on a directory-by-directory basis.  Placing the +Indexes directive in a <Directory> container within the <VirtualHost> definition itself works regardless of the AllowOverride setting.

---

### Post by Romu on 2012-01-13
Hi,
I finally made it work by adding "Allow from All" to your proposition.

Thanks for your help.

---

### Post by Habitual on 2012-01-13
> **seijisensei said:**
> the allowoverride directive applies to [.htaccess]("http://httpd.apache.org/docs/current/howto/htaccess.html") files which are used to modify the server configuration on a directory-by-directory basis.  Placing the +indexes directive in a <directory> container within the <virtualhost> definition itself works regardless of the allowoverride setting.

+1

---

